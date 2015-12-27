title: "ADB server didn't ACK"
date: 2015-08-17 17:06:41
tags: [Android, adb]
---

##问题描述

  Android真机调试的时候，出现ADB server didn't ACK，明明设备已经连接上，开发者选项也打开了。
  
##原因

  cmd，启动adb服务发现启动失败。
  
  ![adb失败](/images/adbserverfail.jpg)
    
  看下为什么会失败。
  
    adb nodaemon server
    
  ![nodaemonserver](/images/nodaemon.jpg)  
  
  原来是端口被占用了。
  
  找到占用端口的进程，杀掉，重启adb server
  
    netstat -aon|findstr "5037"
    
  
  ![adbstart](/images/startadb.jpg)
  
  
##Note:
  转自[百度经验](http://jingyan.baidu.com/article/454316aba27e49f7a7c03ab1.html)