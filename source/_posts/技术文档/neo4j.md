title: neo4j安装
author: LZH
categories: ["neo4j"]
date: 2022年12月16日18:20:20
tags:

  - 图数据库

---



## neo4j安装

1.下载jdk17  https://www.oracle.com/cn/java/technologies/downloads/
配置环境JAVA17_HOME(名字是无所谓)
2.下载neo4j安装包 https://neo4j.com/download-center/
修改bin\Neo4j-Management\Invoke-Neo4jUtility.ps1文件中JAVA_HOME为上步添加的环境变量如JAVA17_HOME
配置环境NEO4J_HOME
配置环境Path添加%NEO4J_HOME%\bin

3.下载apoc插件

https://github.com/neo4j-contrib/neo4j-apoc-procedures/releases

4.配置插件权限

在conf/neo4j.conf中添加

`dbms.security.procedures.unrestricted=apoc.*`

5.启动或重启

`neo4j.bat console`

