
## Blog仓库使用总结

### 分类说明

+ 若有所思：记录日常思考
+ 游记： 出行记录
+ 学术软件教程： 记录学术软件的学习过程
+ Computer: 记录不务正业的计算机鼓捣过程

### _posts目录

目录中存放着写过的所有博客内容（markdown格式文件），GitHub内嵌的jekyll会自动为你生成html页面。

markdown格式文件说明：
* 文件命名必须符合格式： year-month-day-name.markdown
* 文件内容开头以如下格式开始，注意开始与结尾处的三个短横线：  
\---  
layout: post  
title: git 小结  
author: ResonHou  
categories: GitHub  
tags: GitHub  
\---  
注：详情请查看[jekyll](http://www.jekyll.com.cn/docs/frontmatter/)
* 在头信息下面要加上如下两行内容，用于产生文章目录  
\* content  
{:toc}  
* 关键字："<\!-- more -->" 用于控制在首页上显示的内容，具体用法试一下就知道了
* 其它语法参见 [markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)

### 其他目录结构

* _config.yml: jekyll的基本设置参数（键值对），里面的参数取值可以参考[jekyll文档](https://jekyllrb.com/docs/configuration/)。

* feed.xml: 应该是站点地图信息

* _drafts: 草稿。尚未完成的博客文章，完成后可移到** /_posts **目录中。

* _includes: 将页面分块写成的片段。在** /_layouts **目录中的布局页面中使用" ** {% include xxxx.html %} ** "语法引用。

* _layouts: 布局。也就是在文章头信息中指明的布局(layout:post)。

* _sass: 经jekyll处理之前的css样式信息。

* assets: 附属材料。目前仅存放有头像图片。

* css: 里面只有一个jekyll处理之前的css主样式文件。完全可以与** /_sass ** 合并。

* js: 存放着js脚本文件。

* page: 在 **/_layouts**目录中写了四个布局，post用于撰写的文章，page就是用于这个目录中的页面。但要注意，只有在头信息里注明 ** type: page ** 项，这个页面才会显示在index.html中。
