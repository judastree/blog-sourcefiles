title: "Mitmproxy 抓包工具"
date: 2015-12-27 16:13:49
tags: [工具]
---

Windows下的Fiddler是神器，具备抓包，代理，文件替换等各种功能。但因为Fiddler是由.netframework开发的，不能在mac下跑。

虽然官方也出过fiddler的mac版，但不好用。所以在寻求mac下的替换工具时找到了这个Mitmproxy。


###安装

    brew install mitmproxy
    
###启动

绑定你电脑的IP和Port, 需要抓移动端数据包时,在移动端wifi连接时设置该ip和port的代理.

    mitmproxy -b 192.168.1.41 -p 8888
    
###效果

  ![mitmproxylist](/images/mitmproxylist.png)
  
  
  ![mitmproxydetail](/images/mitmproxydetail.png)
    

###抓https的包

要捕获https证书，就得解决证书认证的问题，因此需要在通信发生的客户端安装证书，并且设置为受信任的根证书颁布机构。

 ~/.mitmproxy文件夹，其中该文件下包含4个文件，这就是我们要的证书了。

　　mitmproxy-ca.pem 私钥

　　mitmproxy-ca-cert.pem 非windows平台使用

　　mitmproxy-ca-cert.p12 windows上使用

　　mitmproxy-ca-cert.cer 与mitmproxy-ca-cert.pem相同，android上使用

　　1. Firefox上安装

　　preferences-Advanced-Encryption-View Certificates-Import (mitmproxy-ca-cert.pem)-trust this CA to identify web sites

　　2. chrome上安装

　　设置-高级设置-HTTPS/SSL-管理证书-受信任的根证书颁发机构-导入mitmproxy-ca-cert.pem

　　2. osx上安装

　　双击mitmproxy-ca-cert.pem - always trust

　　3.windows7上安装

　　双击mitmproxy-ca-cert.p12-next-next-将所有的证书放入下列存储-受信任的根证书发布机构

　　4.iOS上安装

　　将mitmproxy-ca-cert.pem发送到iphone邮箱里，通过浏览器访问/邮件附件

　　我将证书放在了vps上以供下载

　　http://tanjiti.com/crt/mitmproxy-ca-cert.pem mitmproxy iOS

　　http://tanjiti.com/crt/mitmproxy-ca-cert.cer mitmproxy android

　　http://tanjiti.com/crt/mitmproxy-ca-cert.p12 windows

　　http://tanjiti.com/crt/PortSwigger.cer BurpSuite (burpsuite的证书，随便附上)

　　5.iOS模拟器上安装

　　git clone https://github.com/ADVTOOLS/ADVTrustStore.gitcd ADVTrustStore/

　　DANI-LEE-2:ADVTrustStore danqingdani$ python iosCertTrustManager.py -a ~/iostools/mitmproxy-ca-cert.pem

　　subject= CN = mitmproxy, O = mitmproxyImport certificate to iPhone/iPad simulator v5.1 [y/N] yImporting to /Users/danqingdani/Library/Application Support/iPhone Simulator/5.1/Library/Keychains/TrustStore.sqlite3 Certificate added

　　实际上上面的操作就是给 ~/Library/Application\ Support/iPhone\ Simulator/5.1/Library/Keychains/TrustStore.sqlite3 数据库中表tsettings表中插入证书数据

　　6.Android上安装

　　将mitmproxy-ca-cert.cer 放到sdcard根目录下

　　选择设置-安全和隐私-从存储设备安装证书


    
参考资料:[mitmproxy——中间人攻击的神器](http://sec.chinabyte.com/412/12771912.shtml)