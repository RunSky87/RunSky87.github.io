---
title: init-hexo.md
date: 2021-03-10 20:08:37
tags:
---
## hexo 初始化
``` bash
hexo init <dirname>
cd <dirname>
npm install

--- 假设报错
npm ERR! ejs@2.7.4 postinstall: `node ./postinstall.js`

: 执行
npm install ejs@2.7.4 --ignore-scripts
再 npm install
---
```
