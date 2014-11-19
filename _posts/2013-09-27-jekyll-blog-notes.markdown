---
layout: post
title: 用Jekyll搭建博客的笔记
---
经常能够看到的syntax.css是用来高亮代码的，当然，要在\_layout目录下default.html或post.html里添加一个link，像这样`<link rel="stylesheet" href="/stylesheets/syntax.css" type="text/css" />`

添加Matlab代码的时候要用\`\`\`matlab，而不是\`\`\`Matlab，我猜其他语言也是要小写

markdown中可以用html标签来注释`<!--- comments -->` [(use triple dash to make it compatible with pandoc)](http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

rdiscount貌似在Windows上安装有问题，反正我是没成功，bundle install于是也失败了。其他平台的可以看一看[using-jekyll-with-pages](https://help.github.com/articles/using-jekyll-with-pages#troubleshooting)，应该有用。




