title: "Chrome和Chromium的区别"
date: 2015-07-20 12:06:10
tags: [工具]
---

昨天下了QQ浏览器来用，查看关于发现QQ浏览器的内核是Chromium的。那个Chrome和Chromium是什么关系呢？

chromium是谷歌的开源项目，有很多开发者共同的去改进，谷歌收集改进后会发布安装包，也就是chromium，然后会将chromium的东西更新到chrome中，chrome不是开源项目，而在chrome内的更新也有一个过程，先更新到chrome的金丝雀版（未验证bug），接着到dev版（大问题已经验证），接着beta（小问题已经验证），都没问题了，再更新到稳定版。

Chrome浏览器各版本的特点：
1、Chromium
Chromium是Google为发展Chrome浏览器而启动的开源项目，Chromium相当于Chrome的工程版或称实验版（尽管Chrome自身也有β版阶段），新功能会率先在Chromium上实现，待验证后才会应用在Chrome上，故Chrome的功能会相对落后但较稳定（实际上稳定性也差不多）；Chromium的更新速度很快，每隔数小时即有新的开发版本。
2、Chrome dev
基于最新的Chromium Build，经常每周就更新推出新功能；与Beta版十分相似，但稳定性较差，不适合公共使用。
3、Chrome beta
基于Chrome dev；按月更新；崩溃等重大故障较少发生，功能比dev更加完善。
4、Chrome stable

然后...然后我瞬间找到了我的QQ浏览器为什么一直崩溃he的原因了。