title: "React 学习 笔记 "
date: 2015-07-06 17:30:08
tags: [React]
---
其实早就有听闻React很火了，但脑子里一直没有概念，于是花了一个小时去找了几篇相关介绍。

其中知乎上的一篇翻译的文章[ReactJS 傻瓜教程](http://zhuanlan.zhihu.com/FrontendMagazine/19896745)

然后就记住了两点。

    1. React是组件化的，而且是仅仅View层面的，还需要配合其他MVC的框架。
    2. React有自己的渲染方式，一种类似XML的，将Html和Javascript结合的叫JSX的东西。

虽然这个时候还是不清楚什么是JSX，也对组件化的概念很模糊。

于是就去React官网找了快速入门来看。有中文版当然还是看[中文版](http://reactjs.cn/react/docs/getting-started.html)。

仅是看quick start这一篇，只记住了一点。

    1.html分离，在单独的js文件中通过React.render来渲染html

接着继续看下一篇[教程](http://reactjs.cn/react/docs/tutorial.html)。
这个看起来就相当于更完整的一个例子了，实现评论+展示评论列表。

教程里一步一步讲的很详细。到这里就稍微清晰一些之前的两个概念。

    1.组件化
    2.JSX

不得不说，中文理解起来就是方便快捷。如果是英文，虽然能看懂单词但理解还是会有偏差。【英语不好的借口

先理解下组件化。

CommentBox组件中包括CommentList组件和CommentForm组件。而CommentList组件又循环渲染Comment组件。
每个组件都是React Create出来的一个element,它们包含但不仅限于html。
     
        
        var CommentBox = React.createClass({
          render: function() {
            return (
              <div className="commentBox">
                <h1>Comments</h1>
                <CommentList data={this.props.data} />
                <CommentForm />
              </div>
            );
          }
        });
数据的传递在自定义标签的属性中，所以这里又出现了一个新的名词props。但数据处理和渲染还是在自定义的组件中。
        
        var CommentList = React.createClass({
          render: function() {
            var commentNodes = this.props.data.map(function (comment) {
              return (
                <Comment author={comment.author}>
                  {comment.text}
                </Comment>
              );
            });
            return (
              <div className="commentList">
                {commentNodes}
              </div>
            );
          }
        }); 
   
然后什么是JSX？
   
我们看到在进行Html渲染的时候，出现了很多自定义html标签，或者说是类xml的标签。
React里有一个简单的预编译器，用于将JSX这种语法糖转换成纯的JavaScript代码。作为语法糖，确实JSX 语句比纯 JavaScript 更加容易使用

>>>
   这个 div 标签不是真实的DOM节点；他们是 React div 组件的实例。

这句话我不是很理解。明明在chrome运行的时候，审查元素能看到div，为什么说不是真实的DOM节点呢？