---
title: 待辦事項
tags:
  - 持續更新
  - 施工中
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