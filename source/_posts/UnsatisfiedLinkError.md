title: "UnsatisfiedLinkError"
date: 2015-08-17 20:22:37
tags: [Android,异常]
---

这两天被这个异常搞死了：

    java.lang.UnsatisfiedLinkError:dlopen failed: “**/*/arm/*.so” has unexpected e_machine: 3
    
**原因是一个在x86机器编译的so文件放到了arm机器上。**

apk安装时，系统把armeabi下的so动态库都放入应用的私有目录中了。
但这个so不是arm的，而是x86编译的。
所以运行时，系统检察ELF文件中的e_machine字段的值，跟arm的不匹配，就会抛出这个异常了！

参考资料:[精神哥讲Crash（一）：UnsatisfiedLinkError](http://bugly.qq.com/blog/?p=34)