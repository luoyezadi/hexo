title: oracle导入dmp文件 替换现有表
author: LZH
tags:
  - oracle
  - dmp
categories: []
date: 2019-04-25 08:06:00
---
# 当使用IMPDP完成数据库导入时，如遇到表已存在时，Oracle提供给我们如下四种处理方式：

```
a.忽略（SKIP，默认行为）；
b.在原有数据基础上继续增加（APPEND）；
c.先DROP表，然后创建表，最后完成数据插入（REPLACE）；
d.先TRUNCATE，再完成数据插入（TRUNCATE）。

先用EXPDP生成一份dump文件
sec@secDB /expdp$ expdp sec/sec directory=expdp_dir dumpfile=`date +"%Y%m%d%H%M%S"`_sec.dmp logfile=`date +"%Y%m%d%H%M%S"`_sec.log

分别使用四中方式真实的感知一下具体效果
用到的IMPDP语句统一汇总在这里，方便参考。
SKIP：
impdp system/sys directory=expdp_dir dumpfile=20100401102917_sec.dmp logfile=20100401102917_sec_impdp.log TABLE_EXISTS_ACTION=SKIP

APPEND：
impdp system/sys directory=expdp_dir dumpfile=20100401102917_sec.dmp logfile=20100401102917_sec_impdp.log TABLE_EXISTS_ACTION=APPEND

REPLACE：
impdp system/sys directory=expdp_dir dumpfile=20100401102917_sec.dmp logfile=20100401102917_sec_impdp.log TABLE_EXISTS_ACTION=REPLACE

TRUNCATE：
impdp system/sys directory=expdp_dir dumpfile=20100401102917_sec.dmp logfile=20100401102917_sec_impdp.log TABLE_EXISTS_ACTION=TRUNCATE
```
 impdp user/password@pdborcl FROMUSER=ICM_DEV TOUSER=user directory=TEST dumpfile=XXXXXXXXXXXXXXXX.dmp logfile=X.log table_exists_action=truncate