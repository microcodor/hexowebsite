title: hexo-admin插件安装
cover: 'http://ww4.sinaimg.cn/mw690/bca78afdgw1ehdj5kskk4j218g0zkdpp.jpg'
author:
  nick: BruceYJ
  link: 'https://www.github.com/BruceYuj'
tags: []
categories: []
date: 2019-05-06 08:30:00
---
之前刚搭建的时候,是使用命令行

hexo new '新建一个文章'

打开编辑器,使用markdown格式写好文章后再执行

hexo g

hexo d

这样操作感觉并不方便,

于是查到了 可以使用hexo-admin插件来实现,

很方便

 
![upload successful](/images/pasted-0.png)

进入hexo 目录

 

执行 npm install --save hexo-admin

即可

 

然后再执行 hexo g

hexo s

 

打开具体显示如下



 

 



 

 

如果要设置登录账号和密码

在配置文件中设置









 

在配置文件加入



其中 hexo-publish.sh



#!/usr/bin/env sh
hexo clean
hexo g -d
你也可以加入自己想要的命令

 

记得修改执行权限 chmod +x hexo-publish.sh



 

# hexo-admin authentification
admin:
  username: test
  password_hash: $121212121212zLCFe/fn6p4dTmHIVCIRLCFe/fn6p4dTmHIVCIRiZNF2aTYlptpq
  secret: docker2019is01best
  Command: 'hexo-publish.sh' # expire: 60*1
