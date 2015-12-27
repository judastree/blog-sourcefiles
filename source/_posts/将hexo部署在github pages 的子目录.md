title: "将hexo部署在github pages 的子目录"
date: 2015-09-29 11:25:07
tags: [工具]
---

##场景：

  个人博客和个人一些项目都想放到github pages这个静态服务器上。
  
##冲突：

  1. 最简单的想到的是在根目录下分blog和project的目录。
  
  但是我之前搭hexo的时候已经把博客的东西放到了根目录，试了一下整体搬迁到blog目录，会出现css，图片，js的路径问题。
  
  这里就要逐个修改hexo的路径配置。
  
  2. 还有另外一种办法就是，博客继续保留在github.io的根目录上，同时再建一个project目录。
  
  project目录下是一些需要运行在静态服务器上的代码，比如做demo。
  
  但用hexo deploy进行部署的时候，只能deploy 博客的代码，不能把自己project的代码也push上去。
  
  这里就需要修改hexo自带的deployer.js的文件。自行添加文件拷贝的任务。
  
##修改hexo的路径配置

  1. 首先是博客目录下的_config.yml 文件
  
        url: http://judastree.github.io/blog/
        root: /blog/

  2. 然后是主题目录下的_config.yml 文件
        
        #菜单
        menu:
          home: /blog/
          archives: /blog/archives
          about: /blog/about
          tags: /blog/tags            
        #头像
        avatar: /blog/images/profile.jpeg
  
  3. 再接下来是需要自己细看的修改的，比如图片的引用地址。

##修改hexo deployer.js文件
  
  1. 打开文件:node_modules/hexo-deployer-git/lib/deployer.js
  
  2. 找到对应代码片段，拷贝project目录，还有gitignore的文件，hexo的.deploy_git目录下原来没有gitignore文件
  
        return fs.exists(deployDir).then(function(exist){
          if (exist) return;
          log.info('Setting up Git deployment...');
          return setup();
        }).then(function(){
          //log.info('Git pull first');
          //git('pull');
          log.info('Clearing .deploy folder...');
          return fs.emptyDir(deployDir);
        }).then(function(){
          //log.info('Copying files from public folder...');
          return fs.copyDir(publicDir, deployDir);
          //log.info('Copying gitignore...');
          //fs.copyFile(gitignoreFile,deployDir+"/.gitignore");
          //log.info('Copying files from other project folder...');
          //return fs.copyDir(otherProjectFolderDir,deployDir+"/projects");
        }).then(function(){
          return parseConfig(args);
        }).map(function(repo){
          return push(repo);
        });
        
  3. 注意这里还要加入git pull 的命令，因为当你在project的目录提交了代码，博客的目录不拉取最新的commit的话，提交会有问题的。
        
##博客文章的push问题
        
   我用第一种方法，将博客从根目录搬到blog子目录。 除了路径的问题，和第二种方法一样，也遇到了push的问题。
   
   因为git本地仓库和远程仓库对应，不能只push博客的目录，要push整个本地仓库都要push上去。
      
   这里还是修改hexo 的deployer.js ，添加自定义的任务。
   
   比如将hexo的public目录不是复制到.deploy_git目录，而是复制到我们本地的仓库的blog目录。
   
     //var deployDir = pathFn.join(baseDir, '.deploy_git');
     var deployDir = "/Users/judastree/Documents/code/github/judastree.github.io/blog";
   
      
   这里commit可以，但是push可能会遇到问题。 
   
   继续修改deployer.js里的push代码。将push -u origin branch --force 改成直接push。github默认会给我们-u的。
   
         //return git('push', '-u', repo.url, 'master:' + repo.branch, '--force');
         return git('push','-u','origin',repo.branch);
         
         
   
      