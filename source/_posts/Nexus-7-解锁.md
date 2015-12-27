title: "Nexus 7 解锁"
date: 2015-09-07 11:50:46
tags: [Android, 工具]
---

##安卓设备解锁和不解锁有什么区别？

手机加锁是因为在出厂时，厂商已经安装好了操作系统和预置应用，这些东西都装在手机ROM中。
为了防止意外情况，比如不慎删除了系统重要应用导致系统不稳定甚至崩溃，因此厂商对ROM加了锁使你不能对系统文件做任何动作。
这就影响了后续的root和刷机。所以在刷机前一般都要先解锁。

##解锁过程

  1. 下载解压[nexus_unlock](http://pan.baidu.com/share/link?shareid=3769076633&uk=3793975982)
  
  2. Nexus 7 USB连接电脑，打开开发者选项，然后关机。
  
  3. 再同时按住音量-键和电源键进入fastboot模式。
  
  4. 运行解锁.bat，nexus7中出现是否要解锁的界面，选择yes。
  
  5. 解锁完成后，再开机，可以看到google下面有个解开的锁，就表明解锁完成了。
  
##图片步骤

  ![fastboot mode](/images/fastbootmode.jpg)
  ![bootlock](/images/bootlock.jpg)
  ![bootunlock](images/bootunlock.jpg)
  
  
  
  
