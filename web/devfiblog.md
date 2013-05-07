title:制作fiblog
date:22:42 2013/2/26
tag:web

接上文，我开始制作fiblog，为什么叫fiblog，原因很简单，因为这是基于文件的blog。

它自动生成。适合完全不懂程序的人用。写在记事本里，放进目录，网页上就自动生成对应的博客。

wordpress的数据库就比较高端了。不过wordpress本身就脱离了博客的本质。它更像是论坛。

我们所需要的轻量级博客，不需要什么登陆，也不需要后台管理，需要的就是静态的页面展示，要是能自动像文件夹那样分类就太好了

所以fiblog就是file blog的简称。。

fiblog安装非常简单。一句命令就能安装。`npm install fiblog`

在同目录下放好blog目录，blog中对应所有的markdown博客，当然也可以是html的，引用的图片也在里面。

fiblog下默认有一个template，对应的是模板，这个模板引擎是我寒假无聊写的，现在用的非常欢。

要不是早点知道html模板引擎，我可能现在还在吭哧吭哧写字符串相加呢。

提醒想用nodejs做markdown2blog的童鞋，markdown解析用`marked`这个package最好。markdown那个好坑爹。pre都解析不对。

github上的星标也不能说明全部的好坏啊。

技术博客免不了代码高亮，这里我用了highlight这个package，能自动检测语言。虽然不大对，但确实能用，高亮则是自己写的css。模仿sublime txet2的高亮真好看呀！

至于博客同步，我用了自己写的百度pcs的sdk。这个我非常自豪，因为貌似没人写过百度pcs的nodejs的sdk，写完的时候我觉得自己终于不再是只会抄抄代码的菜鸟了。

fiblog中的template暂且我叫它simple red。但其实它叫farbox更合适，因为我完全模仿了farbox。再次感谢farbox

第一个模板使用了680px的宽度，没有用920-960px这种默认宽度。我觉得没有sidebar，博客更为专注，清晰。

为啥不做成多屏兼容的页面？因为我实在太懒了。先写个最最简单的出来，以后一定会写响应式CSS的博客。我常手机上网，喜欢响应式的网页。

同步方法也是模仿farbox。没错，就是访问一个url。服务器就激活同步blog文件夹。这样我不用跑到远程服务器去点同步文件的脚本了。

虽然farbox给了我太多灵感

我还是要在这里吐槽下farbox，我觉得farbox未必能成。除非它只有一小圈子用

远程服务器不可控，无法知道同步情况，让人感觉延迟又笨重，建议增加后台管理监控页面。

这种markdown式的博客如果博客少于1000那必然比数据库式的好很多。但是超过1000就会越来越不如数据库。

farbox如果用户10000，那markdown文件数也是巨大的。要10w多吧，遍历这些文件只能说非常可怕。

为什么非要遍历一个人的所有博文？像rest api那样不行么？

确实不行，因为博客肯定有一个目录，而获取目录对于这种文件式博客是非常困难的，不像数据库一句select就能搞定。

文件式博客需要遍历所有文件，才能获取文章中的博客名（未必是文件名，所以必须读取内容）。tag同理。

总之，离线写文章确实很爽，但是同步和遍历文件必将耗费大量资源。要知道改变一个文件夹路径名对于文件式博客就是同步整个文件夹。

所以fiblog同样也只适合一个人用，多人用就不好了，而且我的pcssdk完全是异步的（至今不会限制异步数量），文件太多就会IO溢出。

写这又臭又长的小博完全是为了纪念寒假唯一做的东西。都说做博客是学习一门语言的练手第一步，我觉得我做到了。





