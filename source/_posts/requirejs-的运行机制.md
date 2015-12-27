title: "requirejs 的运行机制"
date: 2015-07-28 17:06:25
tags: [JavaScript]
---


在requirejs的官网找到这样一段话：
    RequireJS loads each dependency as a script tag, using head.appendChild().
    RequireJS waits for all dependencies to load, figures out the right order in which to call the functions that define the modules,
    then calls the module definition functions once the dependencies for those functions have been called. 
    
翻译过来是：

    RequireJS通过head.appendChild()将每一个依赖加载为一个script标签。
    
    等到所有的依赖都加载完成之后，RequireJS计算出模块定义函数的调用顺序。
    
    一旦依赖这些功能的地方被调用时requiredjs会调用这些功能的模块定义。
    
  
**requirejs是怎么做到模块化的？** 
   
requirejs有个loader来保存和监听所有依赖的状态。script标签来加载这些文件，加载成功和失败都会更新依赖的状态。

*是否有重复引用?*

Requirejs是单例的设计，只要同名的被引入过一次（这里的同名相当于amd define的id）就一直是用这个模块的定义。

为了避免全局污染，遵循AMD的规范，define和export。

理想状况下，每个加载的脚本都是通过define()来定义的一个模块；

但有些"浏览器全局变量注入"型的传统/遗留库并没有使用define()来定义它们的依赖关系，就必须为此使用shim config来指明它们的依赖关系。 







    
