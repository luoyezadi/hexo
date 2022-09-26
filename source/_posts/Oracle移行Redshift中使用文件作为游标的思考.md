title: Oracle移行Redshift中使用文件作为游标的思考
author: LZH
tags:
  - Oracle
  - Redshift
categories: []
date: 2019-04-20 18:59:00
---
实现好实现
主要问题在于动态变化
解决方式是使用HashMap作为db变化的载体
