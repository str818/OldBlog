---
layout: post
title: Windows系统下安装Jekyll
categories: [Jekyll]
tags: Jekyll
---
　　Jekyll是一个简单的博客形态的静态站点生成机器，我们能通过Jekyll方便的搭建并维护一个博客。       
　　除此之外，Jekyll也可以运行在GitHub Page上，也就是说，你可以使用GitHub的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

　　下面来看一下如何在Windows系统下正确安装Jekyll：

### 1.安装Ruby
[下载链接](https://rubyinstaller.org/downloads/)      
版本的差异可能会出现一些不确定的问题，笔者在这方面吃过亏，这里建议下载2.3.3版本。
![Ruby安装](\images\posts\2018\0301\RubyInstall.png){:height="60%" width="60%"}
	安装过程一路"Next"，需要注意记得勾选下图中的选项。
![Ruby安装选项](\images\posts\2018\0301\RubyInstall_1.png){:height="60%" width="60%"}
	安装完成后输入"ruby -v"，显示版本号表明安装成功。
![Ruby安装成功](\images\posts\2018\0301\RubyInstall_2.png){:height="60%" width="60%"}

### 2.安装DevKit
[下载链接](https://rubyinstaller.org/downloads/)，地址与Ruby下载地址相同，注意要安装与Ruby版本相对应的DevKit
![DevKit下载](\images\posts\2018\0301\DevKitInstall.png){:height="60%" width="60%"}
	
　　进入到DevKit的安装目录，在命令行窗口输入下列命令：    
　　`ruby dk.rb init`    
　　`ruby dk.rb install`    
![DevKit配置](\images\posts\2018\0301\DevKitInstall_1.png){:height="60%" width="60%"}

### 3.安装Jekyll
首先检查是否安装gem:`gem -v`，输入`gem install jekyll`安装Jekyll（科学上网）。

### 4.启动Jekyll
`jekyll new myblog`    
`cd myblog`    
`jekyll serve`    
启动过程可能出现下图中的错误信息：
![Jekyll启动Error](\images\posts\2018\0301\JekyllError.png)
这是由于Jekyll启动需要的默认端口4000已被占用，只需要打开_config.yml 在最后加上一行 port:5002 (其它端口也可)问题解决

### 参考
[1] [Jekyll官方文档](http://jekyllcn.com/)    
[2] [升级Jekyll 3.0](http://blog.csdn.net/itmyhome1990/article/details/50443826)