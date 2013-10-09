---
layout: default
title: 用Jekyll写博客（一）
category: Jekyll
---
## {{ page.title }}

# 前言

Jekyll是一个非常酷的静态页面生成程序，用它来做博客系统很极客，不过这年头要么文艺犯装点小极客，要么理工僧装点小文艺，总要给人以文武双全的感觉。所以这篇文章适用于如何快速构建小白眼中狂拽炫酷帅的“个人文艺思想站”，相信大家装着装着可能也就真成了思想家了。

# 第一步：所需环境

确定你的电脑已经有了Ruby环境，以及安装了gem，0基础的同学可以参考[Ruby-China的超快速无脑安装指南](http://ruby-china.org/wiki/install_ruby_guide)，安装完步骤3即可。

# 第二步：安装 Jekyll

运行

    gem install jekyll 

# 第三步：创建文件目录

运行

    jekyll new myblog

这样你就已经有了自己的完整的博客生成系统了，_posts目录用来存放写好的文章，但是要以 年-月-日-标题.md 的格式命名，这里用 md 是因为选择使用 markdown 语言来写，别下意识地逃避，其实这语言记住很简单的几个写法就可以使用，而如果要使排版更好看，那就需要一点时间去学习和记住特殊的写法了。

# 第四步：修改配置

根目录下的_config.yml文件是配置文件，现在只要修改其中的 name 为你自己想要的博客名称就可以了，需要注意，后缀为 yml 的文件是严格要求书写格式的，空格数量不同也会出错。

# 第五步：修改首页

根目录下的 index.html 文件用来生成博客首页，可以将它删除，新建一个名为 index.md 的 markdown 格式文件。输入下列代码：

``---``  
``layout: default``   
``title: 我的第一篇文章``    
``---``

    {% raw %}## {{ page.title }}{% endraw %}
    
    最新文章
    {% raw %}{% for post in site.posts %}{% endraw %}
    {% raw %}+ {{ post.date | date_to_string }} [{{ post.title }}]({{site.baseurl}}{{post.url}}){% endraw %}
    {% raw %}{% endfor %}{% endraw %}

---
其中前四行也是严格书写的，意味着 layout:前面不能有空格，后面的空格不能多也不能少。    
剩下的东西可以先不去深究。
# 第六步：写第一篇文章

好了，下面可以开始写文章了，首先在_posts目录下创建一个 markdown 格式的文章生成文件，如 2013-10-09-first-post.md 。   
在最前面仍然需要写上页面基本设定的语句，如：

``---``
``layout: default``  
``title: 我的第一篇博客``  
``category: Blog``  
``---``

这三句分别指定了这篇文章的页面使用什么模板、页面的标题、文章所属目录。 
在下面开始写文章内容，如：

    {% raw %}## {{ page.title }}{% endraw %}

    今天我用2分钟搞定了一个很酷的网站！

至于 markdown 的写法，可以参阅[markdown 官方文档](http://daringfireball.net/projects/markdown/)

# 第七步：生成博客

在根目录下运行命令：

    jekyll build
    
运行完毕，如果没有报出错误的话，你的博客已经生成了，在{% raw %}_site{% endraw %} 目录下的 index.html 就是你的首页，jekyll 中则是文章页。

# 第八步：部署到 Github    

首先你要安装 git 工具(如果你是通过 Ruby-China 的链接来安装 ruby 的，那么你已经有了 git 工具)，并且在 [Github](https://github.com) 上注册一个账号。    
点击 github 网站上你名字右边的创建仓库按钮，创建一个名为： {% raw %}你的用户名/你的用户名.github.io{% endraw %} 的仓库，创建成功后，复制地址。    
这时需要再次修改配置文件{% raw %}_config.yml{% endraw %} ，加入下面一句代码：

    baseurl: http://你的用户名.github.io    

然后在你的博客生成系统根目录下， 依次运行：

    git init    
    git add .    
    git commit -m 'init'    
    git remote add origin 你复制的仓库地址 
    git push origin master

输入用户名密码，并 push 成功后，即可访问 http://你的用户名.github.io ，你就能看到你的博客内容了。

之后还可以直接拿来主义，使用非常酷的博客模板，以及集成评论系统之类的插件。

{{ page.date | date_to_string }}
