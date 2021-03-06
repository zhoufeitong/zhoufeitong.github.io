---
title: Build blog using Github Page and Jekyll
date: "2019-04-12"
summary: "关于写博客，其实早就想写了。写博客的好处也从各种渠道都听说过，奈何实在是懒。现在由于看到了ARTS，觉得挺有用的，也想养成长期主动学习的习惯，因此就把博客搞起来，作为这个计划的集合地，当然其它想写的时候也会随便写一些文章" 
---
关于写博客，其实早就想写了。写博客的好处也从各种渠道都听说过，奈何实在是懒。现在由于看到了ARTS，觉得挺有用的，也想养成长期主动学习的习惯，因此就把博客搞起来，作为这个计划的集合地，当然其它想写的时候也会随便写一些文章。  

搭建博客的教程网上有很多，随便找一个基本上就能搭建完成。我也是拼拼凑凑搭出来的，现在也还只是个雏形。这里还是做个记录，毕竟别人的经验始终是别人的，自己写出来的才是自己的。  

## 一、利用github pages托管网站  
搭建自己的博客首先得有自己的网站，要有自己的网站首先得有服务器主机来维护它，作为非土豪人士，自己买服务器托管网站这种事是干不出来的。因此，可以使用github pages来托管自己的网站。  

github pages是一个静态站点服务，主要就用来直接从github repo生成网站。因为之前一直也用github，因此一些基本操作也是轻车熟路了，使用它也是基于这个考虑。  

github pages也有一些缺陷，这里简单的列举几点：  
* 它是静态站点服务，不支持服务端代码，例如PHP，Ruby或者Python  
* github pages所在的repo最好不要超过1GB  
* 发布的github pages网站不能超过1GB  
* github pages站点的软带宽每个月不超过100GB  

对于一般的个人博客网站来说，这些限制应该问题不大。  

接下去说说具体的流程。  

1. 在github上创建一个repo，这个repo的名字必须是*username*.github.io,其中*username*就是你在github上的用户名  
2. 选择一个文件夹作为github repo的存放地，例如就在$HOME目录下，在终端下输入下面的命令：  
`git clone https://github.com/username/username.github.io`  
3. 进入上面的文件夹，创建一个index.html文件。命令如下：  
`cd username.github.io`  
`echo "Hello World" > index.html`  
4. 将改变上传到github端。命令如下：  
`git add -all`  
`git commit -m "Initial commit"`  
`git push -u origin master`  

至此，网站就可以查看了。可以在浏览器中输入  
**https://*username*.github.io**  
查看自己的网站  
## 二、利用jkeyll编辑自己的博客  
有了github pages托管网站之后，接下去就是要将网站变成博客形式了。虽然之前稍微学过一点前端的知识，但要自己从头搭建还是有些困难。在github pages上发现大力推荐的一个静态网页和博客生成框架jekyll，可以直接把markdown格式的文件转化成网页，因此干脆就入坑jekyll了。  

目前我也只是过了两遍jekyll的教程，具体使用还需要摸索，这里就简单的讲一下基础的内容。如果想要详细了解，还是得去[jekyll官网](https://jekyllrb.com/)

jekyll首先需要安装Ruby的运行环境，在Linux Ubuntu环境下是很简单的，输入下面的命令：
`sudo apt-get install ruby-full build-essential zlib1g-dev`
接着设置一下环境变量  
```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc`
```
最后，安装jekyll以及bundler插件  
`gem install jekyll bundler`  
至此，jekyll的安装就完成了。  

jekyll的使用也很简单，如果不使用github pages，直接
`jekyll new [foldername]`
其中`foldername`就是文件夹名字，jekyll就会在文件夹中生成一个网站的雏形。想要在本地浏览网页只需要`jekyll serve`就可以在浏览器中输入[http://127.0.0.1:4000](http://127.0.0.1:4000)浏览网页的样子了。(注意，这里`jekyll new`可能花费较长时间，其实不用该命令也可以，自己手动建立目录就行了)  

如果使用github pages，也很简单，在之前的第一步生成的github repo里面创建对应目录结构也一样可以浏览。一般的目录结构如下：  
```
.  
+-- _site  
+-- _layouts  
|   +--  default.html  
|   +--  post.html  
+-- _posts  
|   +-- 2019-11-11-new-post.md  
|   +-- 2019-1-1-old-post.md  
+-- _data  
+-- _includes  
+-- assets  
|   +-- css  
|   +-- images  
|   +-- js  
+-- _sass  
+-- _config.yml  
+-- index.html  
```
其中,\_layouts目录放置的是网页文件的布局样式，\_posts目录放置的是博客文章(注意，文件名字必须是yyyy-mm-dd-*article_title*样式的)，\_includes目录放置的是导入文件，assets目录放置的是资源文件，包括css和js等。\_config.yml是配置文件，index.html则是网页文件。  

在github pages上还可以直接使用jekyll的主题，虽然主题不多，但暂时可以将就着用，后期再自己改进。  

## 三、总结  
博客搭建的过程到这里算是暂时结束了，后期还需要对jekyll作进一步的深入了解以调整自己的博客。目前暂时就先这样吧。  
