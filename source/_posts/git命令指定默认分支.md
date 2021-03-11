---
title: git命令指定默认分支
date: 2021-03-11 12:06:07
tags:
---
## git命令指定默认分支
> git 对于push操作有个default行为，但是根据git版本不同，push的默认行为不同。
> 在Git的2.0之前，push.default属性默认被设为'matching'，2.0之后被改成为'simple'。
> push.default的可选值：nothing , current , upstream , simple , matching

### push.default 的可选值
- nothing : 无默认操作，需要显示地指定远程分支；eg : git push origin branchname
- current :  push当前分支到远程同名分支，如果远程同名分支不存在则自动创建同名分支
- upstream : push当前分支到它的upstream分支上
- simple : 与upstream类似，但有一点不同，就是simple必须保证本地分支和它的远程分支upstream分支同名，否则会拒绝push操作。
- matching : push所有本地和远程两端都存在的同名分支

### 改变 push.default
```bash
git config --global push.default current
```
