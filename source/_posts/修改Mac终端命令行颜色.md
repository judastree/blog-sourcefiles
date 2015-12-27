title: "修改Mac终端命令行颜色"
date: 2015-05-20 22:15:55
tags: [mac]
---
打开终端，输入命令

	$sudo vim .bash_profile
	
这时在出来的编辑器中输入下面两行配置，然后保存

	export CLICOLOR=1
	export LSCOLORS=cxfxaxdxcxegedabagacad
	
重新打开一个命令行终端，输入“ls”命令，你就能看到颜色变成了绿色。

###详解

LSCOLORS是用来设置当CLICOLOR被启用后，各种文件类型的颜色。LSCOLORS的值中每两个字母为一组，分别设置某个文件类型的文字颜色和背景颜色。

	a 黑色  
	b 红色  
	c 绿色  
	d 棕色  
	e 蓝色  
	f 洋红色  
	g 青色  
	h 浅灰色  
	A 黑色粗体  
	B 红色粗体  
	C 绿色粗体  
	D 棕色粗体  
	E 蓝色粗体  
	F 洋红色粗体  
	G 青色粗体  
	H 浅灰色粗体  
	x 系统默认颜色 


LSCOLORS中一共 11 组颜色设置（所以一共22个字符），按照先后顺序，分别对以下的文件类型进行设置：

	-directory  
	-symbolic link  
	-socket  
	-pipe  
	-executable  
	-block special  
	-character special  
	-executable with setuid bit set  
	-executable with setgid bit set  
	-directory writable to others, with sticky bit  
	-directory writable to others, without sticky bit  
