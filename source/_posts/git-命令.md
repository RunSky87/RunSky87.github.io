---
title: git-命令
date: 2021-03-15 14:58:35
tags: Git
---

### git checkout 命令
- 创建并切换到新的分支
```bash
$ git checkout -b new-branch-name
```

- 强制创建并切换到新的分支，如果有同名分支则将其覆盖
``` bash
$ git checkout -B new-branch-name
```

- 使用暂存区内容覆盖工作区内容
```bash
$ git checkout file-name
```

<!-- more -->

- 使用暂存区内容覆盖工作区所有文件内容
```bash
$ git checkout .
```

- 切换分支
```bash
$ git checkout branch-name
```

- 为了防止暂存区内容覆盖和切换分支误判，建议用下面的命令获取暂存区内容
```bash 
$ git checkout -- file-name
```

- 使用指定commit内容覆盖工作区
```bash 
$ git checkout commit-hash-id -- file-name
```

- 使用指定分支的最新暂存区内容覆盖当前工作区内容
```bash
$ git checkout branch-name -- file-name
```


### git branch 命令



### git remote 命令
- 查看远程仓库信息
```bash
$ git remote -v
```

- 查看远程仓库的各个分支信息
```bash
$ git remote show origin
```
这个命令列出了当你在特定的分支上执行 git push 会自动地推送到哪一个远程分支。它也同样地列出了哪些远程分支不在你的本地，哪些远程分支已经从服务器上移除了。

- 刷新本地仓库与远程仓库保持同步改动
```bash
$ git remote prune origin
```

- 查看无效的远程分支
```bash
$ git remote prune origin --dry-run
```

- 清理无效的远程分支
```bash
$ git remote prune origin
```
