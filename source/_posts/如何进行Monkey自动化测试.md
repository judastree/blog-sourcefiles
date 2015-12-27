title: "如何进行monkey自动化测试"
date: 2015-09-08 19:30:06
tags: [Monkey, Android]
---

##简介
  Android Monkey自动化测试：Monkey是Android SDK中自带的一个命令行工具，可以运行在模拟器里或实际设备中。
  它向系统发送伪随机的用户事件流(如按键输入、触摸屏输入、手势输入等)，实现对正在开发的应用程序进行压力测试。

##准备条件
  
  1. Android SDK
  2. USB数据线
  3. 将sdk中的adb加入全局环境变量
  
##步骤
  
  1. 确认设备已经连接到PC上
  
        adb devices
    
  2.你可以指定要测试的app的包名，如果没有指定的话是测试所有的app。将日志输出到c盘monkeylog.txt中
  
        adb shell monkey -p com.android.test  --throttle 1000 -s 600 -v -v -v 1000>C:\monkeylog.txt
  
  
##如何停止Monkey测试
    
   1. adb shell(登录设备)。
   
   2. ps|grep monkey(查找进程)。
   
   3. kill ID(结束进程)。 

##如何获取ANR文件？（需要具备root权限）

   1. adb shell(登录设备)
   2. cd /data/anr(进入到anr文件夹)
   3. ll(查看文件)
   4. adb pull /data/anr/traces.txt C:\traces.txt(文件复制)       
    
##Monkey命令行参数详解
    
   -p: 所要测试的包。
         示例：-p com.android.test
   -throttle: 在事件之间插入固定延迟。
         示例：--throttle 1000（毫秒）
   -s: 伪随机数生成器的seed值。
         示例： -s 600（如果用相同的seed值再次运行monkey，它将生成相同的事件序列。）
   -v: 用于指定日志的详细程度。
         示例： -v -v -v 100（3个-v代表最详细的日志级别）（数字1000： 表示测试事件数）
         
   [其他命令参数](http://developer.android.com/tools/help/monkey.html)      