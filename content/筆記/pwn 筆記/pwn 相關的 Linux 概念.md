---
title: pwn 相關的 Linux 概念
tags:
  - Linux
  - pwn
  - 施工中
---
# ELF

 - ELF：Executable and Linkable Format
 - 種類
	 - 可執行檔（executable）：經過連結的可執行檔
	 - 可重定位檔（relocatable）：尚未連結的檔案
	 - 共用目標檔（shared object file）：用於動態連接的可重定位檔
	 - 核心轉儲（core dump）：發生錯誤的時候產生的檔案
 - 常用指令
	 - ELF section header 相關：
		 - 列出 section header：
			 - `readelf -S [binary]`
		 - ELF section header 是可選的資訊（給人和 debugger 看的），但是 ELF program header 是必要的（segmentation 的資訊是程式執行時必須提供的）
		 - 多個相同的 section 在連接的時候會被合併到一個屬性相同的段落，可以利用 `readelf -l [binary]` 查看哪些 section 被合併到一個 segment 裡面
	 - ELF symbol table 相關：
		 - 列出所有符號：
			 - 方法一：`readelf -s [binary]`
			 - 方法二：`nm [binary]`
		 - local symbol 在 `.symtab` section 中，但是 external symbol 在 `.dynsym` 中，其中`.dynsym` 是 `.symtab` 的子集
		 - 可以參考 [How the ELF Ruined Christmas](http://web.archive.org/web/20241228014124/https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-di-frederico.pdf) 這篇論文，雖然是在講 ret2dl-resolve 的攻擊手法，但是對於理解符號表也很有幫助！

# pipe 和 stream

| file descriptor | stream |
| --------------- | ------ |
| 0               | stdin  |
| 1               | stdout |
| 2               | stderr |
 - 指令界面操作：
	 - `cmd > file`：把 `cmd` 的 stdout 寫入 `file` 中（注意：如果 `file` 不為空會覆蓋）
	 - `cmd >> file`：把 `cmd` 的 stdout 寫入 `file` 中（注意：如果 `file` 不為空會把內容寫入尾端）
	 - `cmd < file`：把 `file` 的內容當作  `cmd` 的 stdin
	 - `cmd << tag`：輸出 `cmd` 的 stdout，直到遇到 `tag` 為止
	 - `cmd < file1 > file2`：可以想成 `(cmd < file1) > file2`
	 - `cmd FD> file`：把 `cmd` 的第 `FD` 個 file descriptor 的輸出導到 `file`（注意：如果 `file` 不為空會覆蓋）
		 - 例如： `cmd 2> file` 會把 stderr 寫到 `file`
	 - `cmd FD>> file`：把 `cmd` 的第 `FD` 個 file descriptor 的輸出導到 `file`（注意：如果 `file` 不為空會把內容寫入尾端）
		 - 例如：`cmd 2>> file` 會把 stderr 追加到 `file`
 - 其他實用作法：
	 - `cmd 2>&1` 把 `cmd` 的 stderr 合併到 stdout 輸出
		 - 也可以結合其他的方法，例如： `cmd 2>&1 > /dev/null` 會把 stdout 和 stderr 一起丟到 `/dev/null` 中（不輸出任何東西）

# 檔案權限

| 檔案類型                            | 擁有者（U）      | 群組（G）       | 其他人（O）      |
| ------------------------------- | ----------- | ----------- | ----------- |
| D \| I \| S \| P \| C \| B \| - | R \| W \| X | R \| W \| X | R \| W \| X |
 - 更改檔案權限： `chmod`
 - 更改擁有者：`chown`



# 環境變數

 - 列出所有環境變數：`env`
 - 可能會常常用到的環境變數：
	 - `LD_PRELOAD` 和 `_LD_LIBRARY_PATH_`：
		 - `LD_PRELOAD` 中的函式會先被解析，因此可以用來 hook 特定的函式
		 - `LD_LIBRARY_PATH`：會優先尋找並載入該目錄中的函式庫，因此用於更換 `libc` 版本很方便
		 - 注意：這兩個環境變數會讓 suid 失效
 - 定義環境變數
	 - 臨時（關閉 shell 之後就沒有了）： `export VAR=VAL` 
		 - 也可以用新增的方式：例如 `export PATH=$PATH:path/to/append`
	 - 永久（單個使用者）：更改該使用者 `~` 目錄下的設定檔，bash 是 `~/.bashrc`
	 - 永久（整個系統）：編輯 `/etc/profile` 中的內容


# 緩解機制

 - stack canary
	 - aka stack cookies, stack guard, SSP
	 - 原理：buffer overflow 時一定要概到 return address，所以在 return address 和舊的 base pointer 之前塞一個 canary，如果 canary 的值被更改，就會觸發保護機制
	 - 可以參考 [StackGuard: Automatic Adaptive Detection and Prevention of Buffer-Overflow Attacks](https://web.archive.org/web/20241213183742/https://www.usenix.org/legacy/publications/library/proceedings/sec98/full_papers/cowan/cowan.pdf)
	 - canary 的位置：在 TLS （thread local storage）中，每個執行緒都有自己的副本
		 - x86：
			 - TLS 中的偏移：`[GS:0x14]`
			 - stack 上偏移：`[ebp - 0xc]`
		 - x86_64
			 - TLS 中的偏移：`[FS:0x28]`
			 - stack 上的偏移：`[rbp - 0x8]`
	 - `checksec` 對於 canary 的檢查：是否有 `__stack_chk_fail` 或 `__intel_security_cookie`
	 - canary 也可能會在最後一個位元組放置截斷字元（`0x00`）來防止 canary 被讀出來
	 - 如何繞過 canary：
		 - 同時改 TLS 和 stack 上的 canary
		 - 如果有使用到 fork 函式：新的 canary 會和舊的 canary 一樣，可以一次猜一個位元組
		 - 可以參考 [Four different tricks to bypass stackshield and stackguard protection](https://web.archive.org/web/20221025223713/https://www.cs.purdue.edu/homes/xyzhang/fall07/Papers/defeat-stackguard.pdf)
 - NX（No-eXecute）
	 - aka DEP（Windows 上的 NX 叫做 Data Execution Protection）
	 - 原理：把記憶體分頁標示為不可執行，由 `GNU_STACK` 這個 segment 的屬性紀錄（該段為空）
	 - `checksec` 對於 NX 的檢查：`GNU_STACK` 的屬性是 `RW` 還是 `RWX`
 - ASLR
	 - Address Space Layout Randomization，由 kernel 提供的緩解措施
	 - 等級： 0 / 1 / 2 三種，可由 `/proc/sys/kernel/randomize_va_space` 調整
	    
| ASLR | heap | stack | library | vdso | mmap |
| ---- | ---- | ----- | ------- | ---- | ---- |
| 0    | no   | no    | no      | no   | no   |
| 1    | no   | yes   | yes     | yes  | yes  |
| 2    | yes  | yes   | yes     | yes  | yes  |

 - PIE
	 - Position-Independent Executable，由 ELF loader 實作
	 - 隨機化了可執行檔的基址
	 - PIE：Position-Independent Executable：對於可執行檔的 PIE（可以想成，可執行檔對於動態連結器是一種特殊的 shared object）
	 - PIC：Position-independent Code：對於 shared object 的 PIE
 - FORTIFY_SOURCE
	 - 原理：編譯時檢查，比免在執行時的危險
	 - `gcc` 對於 FORTIFY_SOURCE 各種程度的檢查
		 - 0：不檢查
		 - 1：buffer overflow 的檢查
		 - 2：buffer overflow + format string 的檢查
	 - `gcc` 可以用 `-D_FORTIFY_SOURCE=[level]` 來指定 FORTIFY_SOURCE 的程度
	 - `checksec` 對於 FORTIFY_SOURCE 的檢查：函式是否有 `_chk` 後綴
 - RELRO
	 - 尚未整理