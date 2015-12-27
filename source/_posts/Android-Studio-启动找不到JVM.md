title: "Android Studio 启动时找不到JVM"
date: 2015-03-29 21:56:34
tags: [Android]

---
Mac OS-Android studio was unable to find a valid JVM解决办法

---
Mac OSx 上安装Anroid Studio v1.0，官方说明是需要JDK 1.6以上&JRE 6以上版本的支持。

出现找不到JVM时，请先检查是否安装了Java的环境。

如果确认已经安装，但仍然出现这样的错误提示。原因是校验版本的时候出现问题。

修改配置文件，将JVM版本信息改成你本机版本。

---




##具体步骤

1.
在应用程序中找到Android Studio.app 

2.
右键显示包内容，在目录下找到 info.plist 并用任意文本编辑器打开

3.
找到 JVMVersion 并将 <string>1.6*</string>中的版本号改为你当前的JDK的版本号。 
