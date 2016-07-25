---
layout: post
title: nginx常用命令一
date: 2016-05-19 20:49:25
comments: true
categories: [nginx]
tags: [nginx]
---

###nginx常用命令

>1、查看nginx进程 
1
ps -ef|grep nginx  
说明：nginx的进程由主进程和工作进程组成。   
<!--more-->

>2、启动nginx  
1
nginx  
启动结果显示nginx的主线程和工作线程，工作线程的数量跟nginx.conf中的配置参数worker_processes有关。 
 
>3、平滑启动nginx   
1  
kill -HUP `cat /var/run/nginx.pid`     
2    
或者   
3   
nginx -s reload		    
其中进程文件路径在配置文件nginx.conf中可以找到。     
平滑启动的意思是在不停止nginx的情况下，重启nginx，重新加载配置文件，启动新的工作线程，完美停止旧的工作线程。
 
>4、完美停止nginx 
1    
kill -QUIT `cat /var/run/nginx.pid`    
 
>5、快速停止nginx     
1    
kill -TERM `cat /var/run/nginx.pid`    
2    
或者    
3    
kill -INT `cat /var/run/nginx.pid`    
 
>6、完美停止工作进程（主要用于平滑升级）     
1   
kill -WINCH `cat /var/run/nginx.pid`     
 
>7、强制停止nginx    
1    
pkill -9 nginx    
 
>8、检查对nginx.conf文件的修改是否正确     
1    
nginx -t -c /etc/nginx/nginx.conf 或者 nginx -t    
 
>9、停止nginx的命令     
1   
nginx -s stop    

>10、查看nginx的版本信息        
1   
nginx -v    
 
>11、查看完整的nginx的配置信息     
1   
nginx -V   
