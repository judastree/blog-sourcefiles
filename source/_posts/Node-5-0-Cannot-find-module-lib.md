title: "Node 5.0: Cannot find module ./lib"
date: 2015-11-11 16:33:41
tags: [mac,node]
---

##问题描述(Issue)

  it throws "Cannot find module './lib'" when I run "npm install -g xxx" command.
  
  Mac升级到node 5.0之后，执行npm install命令出现Cannot find module './lib'的错误。
  
  
##问题原因（Cause）

   The current theory is that a change made to the OS X installer for Node is causing two npm installations to be overlaid, which is understandably causing problems. 


##解决办法（Solution）

   If you remove /usr/local/lib/node_modules/npm and rerun the Node 5.0 installer, you should be left with a working npm.
   
   移除 /usr/local/lib/node_modules/npm目录，重装node 5.0.
  
  
##参考(Refer)    

   [Error with install of npm 3 via Node.js v5](https://github.com/npm/npm/issues/10166)
    