title: WebSSH2安装教程
author: LZH
tags:
  - WebSSH2
categories: []
date: 2019-04-23 02:48:00
---
github源码[https://github.com/billchurch/WebSSH2](https://github.com/billchurch/WebSSH2)

# 以下所有npm可以使用cnpm（淘宝源）没试过
# 1.安装git npm Node.js
# 2.clon
```
git clone https://github.com/billchurch/WebSSH2
cd WebSSH2
cp app/package.json package.json
nano package.json
--!!!!!!!!!此处修改start对应的index.js前加上app/
npm init
npm install --production
```

## 上面之前一直缺少package.json，后来发现被放到了app路径下，要哭了！！！

# 3.开一个远程画面
```
cd WebSSH2
npm start
```