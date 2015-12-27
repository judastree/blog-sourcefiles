title: "Mac ox 默认环境变量"
date: 2015-11-10 13:47:55
tags: [mac]
---

  今天设置环境变量设置错了，导致整个mac的终端命令（sudo,ls,open,vi等）都不能用了。
  
  执行下面的命令，保证一些默认的可以用：
  
    export PATH=/bin:/sbin/:/usr/bin:/usr/sbin:/usr/local/bin:/opt/local/sbin:/opt/local/sbin

  之后再设置你要的环境变量
    
    vim ~/.bash_profile
    
  立即生效命令
    
    source ~/.bash_profile
