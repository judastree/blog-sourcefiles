title: "Mac中修改host"
date: 2015-05-20 21:43:24
tags: [mac]
----

###打开终端

	$sudo vim /etc/hosts
	
###输入开机密码出现如下所示界面

	##
	# Host Database#
	# localhost is used to configure the loopback 	interface
	# when the system is booting.  Do not change this 	entry.
	##
	127.0.0.1       localhost
	255.255.255.255 broadcasthost
	::1             localhost

	#74.125.237.1   dl-ssl.google.com

	~                                                                               
	~                                                                               
	~                                                                               
	~                                                                               
	~                                                                               
	~                                                                               
	~                                                                               
	-- INSERT --

###输入‘i’进入insert模式，修改你要配置的host，
编辑完成后，先按esc，然后输入:wq
最后回车。

