title: "mac调出adb shell"
date: 2015-07-07 21:30:01
tags: [mac, Android]
---

已安装了android studio， 但在mac的命令行输入adb，提示-bash: adb: command not found

解决办法：

1. 首先找到你的android sdk目录。比如我的目录是在 /Users/Alice/Library/Android/sdk
2. 终端切换至sdk目录下的platform-tools中，adb就在这个目录中。输入pwd命令，拷贝这个目录路径XXXX。
3. 然后输入下面两个命令
    
        touch .bash_profile
        open -e .bash_profile
4. 如果打开的文档里面已经有内容,我们只要之后添加;XXXX(注意前面一定要用分号隔开)，
   如果是一个空白文档的话，我们就输入以下内容,然后保存。

        export PATH=${PATH}:/Users/Alice/Library/Android/sdk/platform-tools    
   
5. 更新一下这个文件：
    
        source .bash_profile
    
6. 之后再输入adb,应该就不会提示adb: command not found了。        
   
   
