---
layout: default
title: 直接在 github 上写文章
category: Jekyll
---

## {{ page.title }}

怎么才能像其他博客一样，打开网页就能写呢？直接用 github 就可以啦。

进入你博客项目的仓库，到 _posts 目录下新建文件，文件名仍然是日期加名称，后缀名为 .md 的文件。

写进内容，保存即可。

当然，要想在博客中显示，还得 git pull 到本地仓库进行 jekyll build，再 git add . git commit git push 才行……
