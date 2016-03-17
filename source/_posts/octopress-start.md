---
layout: post
title: "在github上配置octopress博客"
date: 2016-03-17 17:02:09 +0800
comments: true
categories: [git, github,octopress]
---

# 配置git通过SSH连接到github

> 使用的是windows平台
> 

1. git配置用户信息
	> git config --global user.name "Zeillion" 
	> 
	> git config --global user.email "zeillion@163.com"
<!-- more -->
2. 生成SSHkey信息
	> ssh-keygen -t rsa -C "zeillion@163.com"
	> 
	> 把生成的公钥添加到github站上的sshkeys里面。

3. 测试github上的sshkeys是否配置成功
	> git -T git@github.com
	>
	> 查看到欢迎就表示成功。

# Ruby环境配置

1. 安装ruby和devkit
2. 进入devkit目录后加开git bash
3. ruby dk.rb init   运行后会生成一个config.yml，在里面添加到ruby的安装目录 - D:/Ruby21-x64
4. ruby dk.rb install 提示安装成功会出现两条信息。


# 安装Octopress并设置默认主题
1. 克隆Octopress至本地 
	>git clone https://github.com/imathis/octopress.git octopress
2. 安装依赖项 
	> 首先更改安装的软件源 gem sources -a https://ruby.taobao.org  
	>
	> gem sources -r https://rubygems.org  
	> 
	> 还需要把Gemfile里面的sourcess也改为https://taobao.org
	>
	> gem install bundler 
	> 
	> bundle install
3. 安装并使用默认主题   
	> rake install


	> rake generate  
	> 
	> rake preview

# 提高博客访问速度

1. Octopress默认使用的是Google的JS公共库地址，加载的过程无比的缓慢。因此我们要把它改为百度的JS公共库，需要把/source/_includes/head.html文件中的Google公共库地址改为：
	> ```<script src="//libs.baidu.com/jquery/1.9.1/jquery.min.js"></script>```
2. 从上图可以看出加载失败的还有twitter，这个也得给去掉。把在根目录下的_config.yml文件中Twitter内容给注释掉。
	> ```# Twitter#twitter_user:#twitter_tweet_button: true```
	> 
	>把\source\_includes\after_footer.html文件中的twitter内容给注释掉：
	>
	>```<!--{% include twitter_sharing.html %}-->```

3. 删除Google font
	> 把在\source\_includes\custom\head.html中的Google font样式给删除：
	>
	>```<link href="//fonts.googleapis.com/css?family=PT+Serif:regular,italic,bold,bolditalic" rel="stylesheet" type="text/css">```
	>
	>```<link href="//fonts.googleapis.com/css?family=PT+Sans:regular,italic,bold,bolditalic" rel="stylesheet```

# 生成博客与单面页
1. 新建博客
	> rake new_post["title"]
2. 新建单页面
	> rake new_page[title]
	>
	>  >creates/source/title/index.markdown
	> 
	> rake new_page[title/page.html]
	> 
	> > creates/source/title/page.html

# 部署blog到github
1. 在github上创建仓库username.github.io
2. git bash里面输入rake setup_github_pages
	> 输入url@git@github.com:zeillion/zeillion.github.io.git
3. rake generate 让_deploy里面内容最新
4. rake deploy部署到github上

# 把octopress源代码托管到github
- git add .
- git commit -m "xxxx"
- git push origin source

# 安装主题
> 安装主题需要先在github上clone主题到octopress目录下面的.theme目录下
> 
> 然后执行rake install['themenaem']
>
> Tip: 安装主题的时候会覆盖一些配置文件

# 自定义域名指向github
> echo  "iamzhongyi.com" > srouce/CNAME
> 在阿里云解析到192.30.252.153(154)
