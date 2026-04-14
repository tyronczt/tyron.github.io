# Hexo+github 终于有了自己的博客！

> **发表于**：2018-01-18　　**分类**：兴趣　　**标签**：hexo　　**原文**：[http://tyronblog.com/2018/01/18/first-article/](http://tyronblog.com/2018/01/18/first-article/)

---

博客终于有了最初的雏形，兴奋之情难以言表。搭建博客是我很早之前的一个小目标，在通过自己努力后终于迈开了小小的一步，兴奋之余便要着手准备把此博客好好运营下去。

 

为什么写博客？

**摘自–刘未鹏–《暗时间》**写一个博客有很多的好处，却没有任何明显的坏处。更明确的说：用博客的形式来记录下你有价值的思考，会带来很多好处，却没有任何明显的坏处。Note：碎碎念不算思考，心情锁记不算思考，唠唠叨叨也不算思考，没话找话也不算思考，请以此类推。写一个长期的价值博客最大的几点好处：

- 能够交到很多志同道合的朋友。 书写是为了更好地思考。
- “教”是最好的“学”。如果一件事情你不能讲清楚，十有八九你还没有完全理解。
- 激励你去持续学习和思考。
- 学会持之以恒地做一件事情。
- 一个长期的价值博客是一份很好的简历。

很赞同以上的观点，我也在慢慢实践中，有兴趣也可以阅读他写的《暗时间》以及[博客](http://mindhacks.cn/)。学习优秀的人，我们也会变得优秀。

为什么选择用hexo？
在技术选择上，第一个用到的便是WordPress，这个号称5秒钟建站的神器。给我的印象是上手简单，搭建快，扩展插件也很多，但是让我不能忍受的是加载速度慢，还有给人的感觉是很重，懒得去折腾和捣鼓，直接上手了hexo，界面简洁，加载速度快，支持Makedown，还支持部署到Github上。作为小白的我，既能学习Makedown的使用，也可以学着用用GitHub，好处多多。等熟悉使用了hexo后，下一阶段便是自己动手搭建个人博客，正所谓“自己动手，丰衣足食”，知其然，知其所以然，[视频教程](https://coding.imooc.com/class/125.html%20%E2%80%9CSpring%20Boot%E5%B8%A6%E5%89%8D%E5%90%8E%E7%AB%AF%20%E6%B8%90%E8%BF%9B%E5%BC%8F%E5%BC%80%E5%8F%91%E4%BC%81%E4%B8%9A%E7%BA%A7%E5%8D%9A%E5%AE%A2%E7%B3%BB%E7%BB%9F%E2%80%9D)已找好，只等自己把这个教程的一些准备课程学习到位了。

hexo的使用
具体的使用操作，网上已经有很多教程，在这里给大家推荐几篇优秀文章供大家参考：

- NexT 使用文档 — 开发者文档是一手资料，推荐指数5颗星
- hexo从零开始到搭建完整
- 手把手教你用Hexo+Github 搭建属于自己的博客
- 小白独立搭建博客–Github Pages和Hexo简明教程
- Hexo 3.1.1 静态博客搭建指南
- Hexo博客Git-VPS部署完整记录

hexo安装中出现的问题
**1. 出错描述**

`node: relocation error: node: symbol SSL_set_cert_cb, version libssl.so.10 not defined in file libssl.so.10 with link time reference`亲测有效：[解决方案](https://stackoverflow.com/questions/46473376/node-relocation-error-node-symbol-ssl-set-cert-cb-version-libssl-so-10-not-d)

**2. 万能方法** ①使用搜索引擎，如百度，Google（*建议自己搭梯子*）等，很大一部分问题都能得到解决； ②学会读异常，如在配置_config.yml文件时，经常会因为没有输入空格，导致网站无法显示，但是在hexo g是会提示第几行第几列出错的，要注意仔细阅读，并以此类推。 ③上面两种方法均无法解决问题，试了很多方法并不能奏效时，可是尝试向朋友或者相关博客中的作者提问，得到解决方案，做技术的在有人向他提问题时，除非是不动脑子的问题，一般都会回答你。如果大家在博客搭建中有相关问题，我们也可以一起讨论，文后有我公众号地址。

域名和服务器选择
**1. 域名选择**[tyron.xyz](http://tyron.xyz/)，是用来过渡的域名，是因为它之前备案过，所以现在暂时用这个域名，tyronblog.com域名再过十天就会备案通过，以后会一直用tyronblog.com。上述的两个域名均是在万网购买的，国内域名都要备案，可参考[网站/域名如何备案？](https://www.cnblogs.com/chenwolong/p/beian.html)如果嫌麻烦可以国外买域名，如[GoDaddy](https://sg.godaddy.com/zh/)。![tyron.xyz域名备案](https://tyron-blog.oss-cn-beijing.aliyuncs.com/hexo/%E5%9F%9F%E5%90%8D%E5%A4%87%E6%A1%88.png?Expires=1579578985&OSSAccessKeyId=LTAIxIpnFmXmeVUr&Signature=eO1AL5y7UR5t3FEqsBqIUDYEZ/g=)备案如同**政审**，大家自行体会吧。 **2. 服务器选择** 现在使用的是阿里云服务器，9元9使用半年，点击[活动地址](https://free.aliyun.com/?spm=5176.8499797.727319.5.04UbFW&type=personal)，送了一大推服务，上面显示的图片就是用的oss对象存储，考虑到后期续费问题，也会把博客之前放到GitHub上。

后记

- 接下来也会更新一些hexo的进阶教程，主要是插件的使用，及博客的优化。
- 技术路上，当你知道越多的时候，发现不懂的也会越来越多，只要用心去探索，会感受到技术生动的一面，而且也会遇到一起努力学技术的你们。

---

> **版权声明**：本文采用 [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/) 许可协议，转载请注明出处。