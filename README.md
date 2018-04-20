
## Blog仓库使用总结

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

* _config.yml:

* feed.xml:

* _drafts:

* _includes:

* _layouts:

* _sass:

* assets:

* css:

* js:

* page:
