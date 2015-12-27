title: "ubuntu 上安装最新版本的express"
date: 2015-09-30 16:58:37
tags: [工具]
---

##问题描述

  在ubuntu上通过apt-get install node-express命令安装的express版本只有2.5.8
  
  用npm install express@4.13.1 -g 命令可以安装高版本的express
  
  但是执行express --version时却返现并没有这个目录。
  
##解决办法

  这个问题是express的安装目录并不在系统的环境变量之中。
  
  1 将 express的实际安装目录加入环境变量。
  
    sudo vi /etc/environment 
  
  2 保存
  
  3 使它立即生效
    
    source /etc/environment 
    
    
  

  
