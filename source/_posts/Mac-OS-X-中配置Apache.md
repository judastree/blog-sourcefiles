title: "Mac OS X 中配置Apache 相关"
date: 2015-03-30 22:23:41
tags: [mac]
---

### 启动服务


Mac中自带了Apache环境，直接一行命令搞定了。

     $sudo apachectl start

这时，打开你得浏览器，输入“http://localhost”, 可以看到“It Works！”的页面。这个**index.html** 文件位于“/Library(资源库)/WebServer/Documents/”下。这是Apache的默认根目录。

---

###修改配置


Apache 的安装目录在:**/etc/apache2/** 默认是隐藏的。

    $open /etc/apache2
      
让隐藏文件可以见，或者让隐藏文件不可见的命令如下：

    $defaults write com.apple.finder AppleShowAllFiles -bool true
    
    $defaults write com.apple.finder AppleShowAllFiles -bool false
    

修改**/etc/apache2/httpd.conf** 文件，就是修改apache的配置文件。这个文件默认是只读的，修改请加管理员权限 **sudo**


修改完之后，记得重启apache 服务

    $sudo apachectl restart
 

---



###修改Apache默认根目录

1. 打开 **/etc/apache2/httpd.conf**文件

       $sudo vim /etc/apache2/httpd.conf
     
      
2. 找到**/Library/WebServer/Documents**,你换成你自己的目录：

       如/Users/{username}/Sites
      
3. 重启服务。

       $sudo apachectl restart   
 

---


###访问权限问题

可能会遇到403 Forbidden，这时就需要修改<Directory/>的配置了。

1. 打开 **/etc/apache2/httpd.conf**文件

       $sudo vim /etc/apache2/httpd.conf
       
2. 找到**Directory**标签,将标签内的配置Deny from all删掉，改成allow from all

        <Directory />
            Options Indexes FollowSymLinks
            AllowOverride None
            Order deny,allow
            allow from all
        </Directory>

3. 然后继续重启

Ps：Options Indexes FollowSymLinks中得Indexes是指如果你的文件根目录里有 index.html，浏览器就会显示 index.html的内容。
如果没有 index.html，浏览器就会显示文件根目录的目录列表，目录列表包括文件根目录下的文件和子目录。
要关闭文件目录显示的话，只需将Indexes去掉即可。


###修改默认端口

1. 打开 **/etc/apache2/httpd.conf**文件

       $sudo vim /etc/apache2/httpd.conf
       
2. 找到**Listen** 关键字,后面跟的就是端口号了，改掉！

        Listen 8089

3. 然后继续重启
        

