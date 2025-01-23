---
title: GDB 筆記
tags:
  - Linux
  - pwn
  - gdb
---

## 安裝 gef 的坑
 - gdb 要 10.0 以上
 - 要裝好 `readelf` 和 `file` 和 python3
 - [Github](https://github.com/hugsy/gef) 上面的指示很清楚，照著上面做就好了
## gdb 基礎指令
這邊除了紀錄常用指令，還會附上一些實用的用法
### 程式執行
 - `start`
     - 執行程式，並在 entry point （或 `main`）停止執行
 - `r` / `run`
     - 可以用檔案當輸入，例如： `r < payload` 會把 `payload` 這個檔案裡面的內容當作輸入，並執行程式
     - 執行到一半在 gdb 下 `r` 指令的話，可以讓程式重新執行
 - `c` / `continue`
     - 用 control + c 可以中斷程式執行，回到 debugger
 - `at` / `attach`
     - 把 debugger 附加到已經在執行的程式
     - 有時候可能會需要 root 才能完成
 - `target`
     - `target remote ip:port` 會向在 `ip:port` 執行的 gdb server 溝通，remote debugging 對於 multi-arch 或是模擬環境很有用
     - 例如：`
     - `qemu-aarch64-static -g 4444 executable_file` 會在 `localhost:4444` 開一個 gdb server
     - `gdb-multiarch executable_file` 後輸入 `target remote localhost:4444
` 即可開始除錯 arm64 的程式碼

### 斷點和執行流操控
 - `b` / `break`
     - `b *address`：在地址下斷點
     - `b file:n`：在 `file` 的第 `n` 行下斷點
     - `b func`：在 `func` 函式下段點
 - `i b` / `info break`：看所有的斷點
 - `del b1 b2 b3 ...`：刪除 `b1` `b2` `b3` 等斷點（也可以只刪一個）
 - `watch` 和 `rwatch`：硬體斷點
 - `catch`：可以攔截 system call，並在其準備要呼叫時回到 debugger
 - `ni` / `next`：步進，執行下一條指令
 - `si` / `step`：步入，執行下一條指令，但是遇到 `call` 時會進入函式裡面（但是遇到跳轉指令的時候 `ni` 和 `si` 行為是一樣的）
 - `n` 和 `s`：和 `ni` 以及 `si` 是一樣的，只是這條指令是在 source-level debugging 的時候用的，以行為單位，而不是以指令為單位

### 資料檢視和搜尋
 - `x`：印出資料，請下 `help x` 看自己需要下的參數
 - `print`
     - 印出表達式的結果
     - 也可以當簡易計算機算地址
 - `deref`
     - 印出一段記憶體，如果沒有參數的話預設是 esp 或 rsp
     - `-l` 可以調整長度，很有用
 - `ptype`
     - 印出結構體，請下 `help ptype` 自己看需要下的參數
 - `grep`
     - gef 專屬的指令，可以搜尋記憶體
     - 可以在某個 section 搜尋，也可以指定大小端，細節請見 `help secion`
 - `dump memory`
     - 把記憶體內容寫到檔案裡面
- `list function_name`
	- 印出檔案的 source code（如果有 debug symbol 的話）
### 其他
 - `bt` / `backtrace`：stack 的 backtrace
 - `vmmap` / `info proc mappings`：看記憶體布局
     - `vmmap` 是 gef 才有的指令
     - `vmmap` 的額外用法：`vmmap address` 可以查看 `address` 所在的記憶體區域
 - `define`：可以自定義指令，例如：

    ```
    gef➤  define run_til_main
    Type commands for definition of "run_til_main".
    End with a line saying just "end".
    >start
    >b *main
    >c
    >end
    gef➤  run_til_main 
    ...
    ```
 - 分析 coredump
	 - `gdb executable_file coredump_file`
## 除錯參數設定
 - `disable-randomization`：
     - `on` 會將 ASLR 關閉（預設）
     - `off` 會將 ASLR 再次打開
 - `follow-fork-mode`：
     - `parent` 會在 fork 之後跟著 parrent process（預設）
     - `child` 會在 fork 之後跟著 child process

## 其他紀錄（非 gdb）
 - ASAN
     - `gcc` 的 `-fsanitize=address` 可以把 ASAN 打開
 - debug symbol
     - `gcc` 的 `-g` 可以讓編譯後的東西有額外的除錯資訊