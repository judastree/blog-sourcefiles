title: "Android 录制操作视频"
date: 2015-09-16 14:49:49
tags: [Android, adb]
---

利用adb screenrecord的命令，系统Android4.4(API level 19)以上，支持mp4的视频格式

##开始录制的命令

    adb shell screenrecord /sdcard/demo.mp4

##导出视屏

    adb pull /sdcard/demo.mp4 D:/
    
##其他命令参数
    
    adb shell screenrecord --help
    
    