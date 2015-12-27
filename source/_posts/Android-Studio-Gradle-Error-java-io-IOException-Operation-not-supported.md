title: "Android Studio Gradle Error:java.io.IOException: Operation not supported"
date: 2015-07-28 10:38:06
tags: [Android]
---

在mac上每次build gradle 都报这样的错误，java.io.IOException: Operation not supported

原因是我的代码放在了windows上共享给mac，gradle不支持远程

##参考

[same problem in stackoverflow](http://stackoverflow.com/questions/28751793/android-studio-on-mac)