title: https在nginx下简单配置
subtitle: 记录自己配置nginx的过程
cover: 'http://ww4.sinaimg.cn/mw690/67ad23d6gw1eh7xlommaxj21kw11x7cz.jpg'
author:
  name: 蜗牛
  link: 'https://wxdroid.com'
tags:
  - nginx
categories: []
date: 2019-05-06 18:14:00
---
1.阿里云申请免费ssl证书

2.下载nginx证书版本文件

3.在nginx配置下新建个专门存放密钥的文件夹：/etc/nginx/cert/，上传密钥到服务器

4.在/etc/nginx/conf.d/ 下新建一个单独的服务配置.conf

5.我的配置如下：  
配置http都跳转到https:  
```
server {
    listen 80;
    server_name wxdroid.com;
    rewrite ^(.*) https://$server_name$1 permanent;
}
```
配置https证书：  
```
server {
		listen	80;
        listen  443 ssl;
        server_name  wx.jingxiaodi.com;
		ssl on;
        include /etc/nginx/default.d/*.conf;
        ssl_certificate   cert/1552396_wx.jingxiaodi.com.pem;
        ssl_certificate_key  cert/1552396_wx.jingxiaodi.com.key;
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;	
}
```