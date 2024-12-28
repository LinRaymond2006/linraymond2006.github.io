---
title: 待辦事項
tags:
  - 持續更新
  - 施工中
  - 待整理
---


 - TODO：之後寫一個關於 `LD_PRELOAD` 細節的紀錄和實例
 - TODO：之後寫關於分析 coredump 和 gdb 的紀錄
	 - 啟用 coredump：
		 - 臨時：`ulimit -c unlimited`
		 - 永久：把 `/etc/security/limits.conf` 改成 `unlimited`（如果要禁用的話改成 `0`）
	 - coredump pattern：
		 - 改 `/proc/sys/kernel/core_pattern`
 - TODO：新增 Linux 檔案權限的更多敘述
	 - 每個 bit 的說明
	 - 和 suid 的利用方式和技巧
 - ASLR、PIE 的隨機性
	 - 參考的論文
	 - 真正隨機的 bit 數
	 - `libc.so.6` 和 `ld-linux.so` 的相對偏移量的可預測程度
 - 整理所有的呼叫慣例
	 - 列表
		 - system v
		 - stdcall
		 - cdecl
		 - fastcall
		 - aapcs
		 - ...
	 - 內容
		 - 傳參方式
		 - 清理方式
		 - 對齊特性
 - TODO： checksec 對於 PIE 的檢測方式
 - FORTIFY_SOURCE 整理
	 - A Eulogy for format strings 中的一個 vsprintf() 中的一個 integer overflow漏洞可以達到任意地址寫入
	 - CVE-2012-0809 是 sudo 1.8 中的 format string 漏洞
	 - longld 的文章exploiting format strings vulnerability 中也用同樣的方法繞過了 FORTIFY_SOURCE