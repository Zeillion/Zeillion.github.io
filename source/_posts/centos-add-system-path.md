---
layout: post
title: "centos add system path"
date: 2016-05-19 16:09:10 +0800
comments: true
categories: [centos] 
---


##有些命令的路径没有在PATH环境变量中，可以用echo $PATH命令查询得知，添加路径到PATH环境变量的方法如下：

###(如添加/sbin到PATH环境变量中)
1. 如果只想在本次开机过程中临时性的添加修改，下次开机就无效的话，可以：输入export PATH=$PATH:/sbin
2. 如果只给当前用户永久添加，则：在~/.bash_profile中的靠近末尾有类似这样的一行PATH=$PATH:$HOME/bin后添加:/sbin，就变成PATH=$PATH:$HOME/bin:/sbin 文件修改并保持完以后，运行source ~/.bash_profile命令即可使修改操作立即生效
3. 如果给系统中所有的用户都永久添加，则: 
在/etc/profile文件末尾添加export PATH=$PATH:/sbin文件修改并保持完以后，运行source etc/profile命令即可使修改操作立即生效