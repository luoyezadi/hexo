title: Hexo添加音乐/视频
author: LZH
tags:
  - Hexo
categories:
  - catbbb
date: 2019-04-14 18:23:00
---
#以下命令记得换源或者cnpm
# 音乐
```
npm install hexo-tag-aplayer
```

```
{% aplayer "她的睫毛" "周杰伦" "http://home.ustc.edu.cn/~mmmwhy/%d6%dc%bd%dc%c2%d7%20-%20%cb%fd%b5%c4%bd%de%c3%ab.mp3"  "http://home.ustc.edu.cn/~mmmwhy/jay.jpg" "autoplay=false" %}
```
# 视频
```
npm install hexo-tag-dplayer
```

```
{% dplayer "url=http://home.ustc.edu.cn/~mmmwhy/GEM.mp4"  "pic=http://home.ustc.edu.cn/~mmmwhy/GEM.jpg" "loop=yes" "theme=#FADFA3" "autoplay=false" "token=tokendemo" %}
```
# 视频网站都有嵌入式代码
<iframe src="//player.bilibili.com/player.html?aid=10992574&cid=18194228&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>