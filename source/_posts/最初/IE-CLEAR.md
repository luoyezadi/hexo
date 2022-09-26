title: IE_CLEAR
author: LZH
tags:
  - IE
  - CLEAR
categories: []
date: 2019-06-28 16:21:00
---
```
echo Cookiesクリア
  
@Rundll32 InetCpl.cpl,ClearMyTracksByProcess 2  
  
@echo 閲覧の歴史クリア
  
@Rundll32 InetCpl.cpl,ClearMyTracksByProcess 1  
  
@echo TEMPファイルクリア
  
@Rundll32 InetCpl.cpl,ClearMyTracksByProcess 8  
  
rem @echo パスワードクリア 
  
rem @Rundll32 InetCpl.cpl,ClearMyTracksByProcess 32  
  
rem @echo データクリア  
  
rem @Rundll32 InetCpl.cpl,ClearMyTracksByProcess 16  
  
rem @echo 全部クリア  
  
rem @Rundll32 InetCpl.cpl,ClearMyTracksByProcess 255
```