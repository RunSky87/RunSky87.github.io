---
title: 解决FTP因windows防火墙拦截的方法.md
date: 2021-03-11 10:42:46
tags:
---

## 解决FTP因windows防火墙拦截的方法
- 打开 控制面板 -> 防火墙 -> 允许应用或功能通过windows防火墙
- 点击 允许其他应用
- 添加 C:\Windows\System32\svchost.exe
- 再次连接即可
