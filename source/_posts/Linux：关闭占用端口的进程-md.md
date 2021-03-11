---
title: Linux：关闭占用端口的进程.md
date: 2021-03-11 11:52:04
tags:
---

## Linux：关闭占用端口的进程
- 使用端口号
```bash
[root@localhost _posts]# lsof -i:8888
bash: lsof: 未找到命令
[root@localhost _posts]# yum install lsof
.....

[root@localhost _posts]# lsof -i:8888
COMMAND   PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
node    47161 root   20u  IPv6 1354694      0t0  TCP *:ddi-tcp-1 (LISTEN)
[root@localhost _posts]# kill -9 47161
[root@localhost _posts]# lsof -i:8888
[6]+  已杀死               hexo s
```
