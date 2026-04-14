# Hexo使用进阶篇（一）

> **发表于**：2018-02-01　　**分类**：兴趣　　**标签**：hexo　　**原文**：[http://tyronblog.com/2018/02/01/hexoAdvanced1/](http://tyronblog.com/2018/02/01/hexoAdvanced1/)

---

- 豆瓣插件集成
- 插入网易云音乐
- 插入图片的方式
- 支持https
- hexo-admin的集成
- markdown的使用
- 网站SEO

前言
或许是源于兴趣，在有空的时候便会想着去装扮装扮自己的博客。本文将一些有趣好用的插件和hexo使用心得做记录与大家分享。关于基础入门篇可以参考[hexo入门篇](https://tyronblog.com/2018/01/18/first-article/)，希望对大家有帮助。

正文
### 豆瓣插件集成

这是我使用到现在最喜欢的一个插件，封装了豆瓣api，获取个人豆瓣读书、电影、游戏中的记录。使用很简单，可参考[hexo-douban](https://github.com/mythsman/hexo-douban)。该插件是一位在校生根据前人经验开发，佩服之至，有兴趣的话可看[hexo-douban插件的开发过程](https://blog.mythsman.com/2017/06/17/1/)。

### 插入网易云音乐

个人比较习惯使用网易云音乐，用上手的了很难改变。另外在看文章的时候听一首好听的音乐，岂不美哉！

具体使用方式：①网页打开[网易云音乐](http://music.163.com/)，搜索你想要的歌曲；②在音乐播放页面中，在音乐头像下方有 `生成外链播放器`  的按钮；（有的音乐会提示“由于版权保护，无法生成外链。”，那就很可惜没办法使用网易云音乐的外链了，当然不止可以使用网易云音乐的外链，也可以使用其他的，会在后面的文章中讲解O(∩_∩)O）③选择使用iframe插件，插入HTML代码，即可播放。

### 插入图片的方式

使用hexo中麻烦的一点就是插入图片（主要是非人民币玩家而言），需要先上传到存储，拿到地址后再插入Markdown文档中。

我现在的插入图片方案：

##### 本地备份

在自己电脑上将上传的图片放在一个文件夹中（留作以后网站迁移用）；

##### 七牛云对象存储

使用方便，申请稍麻烦点。有优点也有缺点，优点是永久免费，缺点是空间只有10G，下图由七牛云存储上传：![七牛云对象存储](http://img.tyronblog.com/%E4%B8%83%E7%89%9B%E4%BA%91.png)

##### 阿里云对象存储

使用方式和七牛云对象存储差不多，同样有优点和缺点，优点是使用空间有40G，缺点是使用时间为2年，下图由阿里云对象存储上传：![阿里云对象存储](https://tyron-blog.oss-cn-beijing.aliyuncs.com/hexo/aliyun-oss.png?Expires=1580482821&OSSAccessKeyId=LTAIxIpnFmXmeVUr&Signature=4Mg/i4mQPFQXe4qQfxxd0oWZ7xY=)暂时方案是将图片放在七牛云上，10G用用已经差不多了，并本地备份。

### 网站支持https

改用https虽然会降低访问速度，但是基于长久运营和防止运营商网络劫持，避免被人强行插入广告的考虑，决定在建站初期将站点改成https。

##### 申请证书

在七牛云和阿里云都可以申请到免费的有效期一年的证书，我申请的是阿里云的免费证书；

##### 修改Nginx配置

将证书上传到服务器，修改Nginx的配置文件，别忘了服务器的安全组中增加443端口。具体操作可参考：[用阿里云的免费 SSL 证书让网站从 HTTP 换成 HTTPS](https://ninghao.net/blog/4449)

### hexo-admin的集成

待完成项，方便后台管理，参考文档：[https://github.com/jaredly/hexo-admin](https://github.com/jaredly/hexo-admin)

### markdown的使用

一直在学习中，经常使用后你也会爱上它！

推荐文档：

- https://github.com/younghz/Markdown
- https://www.zybuluo.com/mdeditor

### 网站SEO

网站主要还要以高质量的内容为主，做SEO只是为了让更多的人发现正在努力中的你我。量变会发生质变，只是时间的问题！话题太大，后面会写专门的文章来讲述我的seo之路。

做seo当然少不了站长工具，先附一张站长工具截图：![站长工具](http://img.tyronblog.com/%E7%AB%99%E9%95%BF%E5%B7%A5%E5%85%B7.png)

写在最后
这是hexo进阶篇的第一篇，后面会继续更新，敬请期待！适合自己的才是最好的，多去实践，我们会发现更多更美更广的天空。

---

> **版权声明**：本文采用 [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/) 许可协议，转载请注明出处。