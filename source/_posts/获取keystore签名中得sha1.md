title: "获取安卓签名keystore中的sha1"
date: 2015-10-16 14:43:23
tags: [Android]
---


keytool的命令，可以获取keystore中的很多信息。

cmd 到用户根目录下的.android目录。

    cd .android
    
将你的keystore(比如叫yourdebug.keystore)文件拷到.android目录，然后执行命令：

    keytool -list -v -keystore yourdebug.keystore
    
    
    
    
