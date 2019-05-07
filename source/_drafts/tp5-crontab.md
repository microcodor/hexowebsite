title: tp5 crontab 开启定时任务
subtitle: 定时任务写法
cover: 'http://ww3.sinaimg.cn/mw690/bca78afdgw1ehdlsah23ij218g0zkk15.jpg'
author:
  name: 蜗牛
  link: 'https://wxdroid.com'
tags: []
categories: []
date: 2019-05-06 19:07:00
---
1.在tp5项目根目录下创建crond.sh脚本文件，内容如下：  
```
#!/bin/sh  
cd /var/www/html/jdwechatapp/  
php think CouponScheduler
```
2.编辑crontab定时代码  
crontab -e  
```
* 7-23/1 * * * /var/www/html/jdwechatapp/crond.sh
* 7-23/1 * * * /var/www/html/dev_jdwechatapp/crond.sh
0 4 * * * /var/www/html/jdwechatapp/goods.sh
```
早7点到晚上23点每隔一小时执行一次更新优惠券命令

每十分钟执行一次订单更新功能 
```
*/10 * * * * /var/www/html/xue_jingletuiapp/crond.sh
```
3.常用crontab命令  
```
/sbin/service crond start  
/sbin/service crond stop  
/sbin/service crond restart  
/sbin/service crond reload
```
4.格式  
以下是 crontab 文件的格式：  
{minute} {hour} {day-of-month} {month} {day-of-week} {full-path-to-shell-script}  

o minute: 区间为 0 – 59  
o hour: 区间为0 – 23  
o day-of-month: 区间为0 – 31  
o month: 区间为1 – 12. 1 是1月. 12是12月  
o Day-of-week: 区间为0 – 7. 周日可以是0或7
