---
title: linux不能使用ftp命令
date: 2021-03-15 20:46:44
tags: FTP
---

### 异常
```bash
[root@localhost RunSky87.github.io]# ftp 192.168.1.115
bash: ftp: 未找到命令
```

### 解决
```bash
$ yum -y install ftp
```

### 如下图所示
<!-- more -->
![install-ftp-svg](https://zhangbaoyuan.oss-cn-shanghai.aliyuncs.com/test/install_ftp.svg)
