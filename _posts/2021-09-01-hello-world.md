---
layout: post
title:  "关于本站搭建"
---



>  Quick Start



免费api接口： https://apis.whyta.cn/

今日诗词：https://www.jinrishici.com/

天气接口：https://v2.jinrishici.com/info



# 本站配置



博客框架 [jekyll](http://jekyllthemes.org/)

采用主题： [no-style-please](https://github.com/riggraz/no-style-please) 

直接去[jekyll](http://jekyllthemes.org/)下载博客模板 , 之后只需要在模板修改内容, git上传即可



图床问题？

使用 public repository +  page + raw.githubusercontent.com

图片链接替换

```
./img/ 
==>
https://raw.githubusercontent.com/i1oveyou/time-machine/master/_posts/img/ 
```



test img show 图床测试



![avatar-13](./img/20240906_134035.jpg)



![lsp](https://raw.githubusercontent.com/redqx/redqx.github.io/master/_posts/img/20240906_134035.jpg)



> ssh上传

为什么不用https,这个老是出现问题.

好吧也不能这样说,应该说 ssh出现问题就用https

```
git remote set-url origin git@github.com:i1oveyou/i1oveyou.github.io.git
```



>  upload

```
git add .
git commit -m "happy every day"
git push -u origin master
```



## 今日诗词

`_layouts\home.html`

```
---
layout: default
---
<header>
  <h1>{{ site.title }}</h1>
  <p><b> 
    <span>今日诗词: </span>
    <span id="jinrishici-sentence">正在加载今日诗词....</span>
    <script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
  </b></p>
  {%-if site.theme_config.show_description-%}
    <p>{{ site.description }}</p>
  {%-endif-%}
</header>

{%-include menu_item.html collection=site.data.menu.entries-%}

{{ content }}
```



优化版 [javascript简单应用——今日诗词 ](https://www.cnblogs.com/lfri/p/12213043.html)



## 去掉日期显示（日记网站不需要）



地方1 `_includes\post_list.html`

```
{%-if include.category-%}
  {%-assign posts = site.categories[include.category]-%}  
{%-else-%}
  {%-assign posts = site.posts-%}
{%-endif-%}

{%-if include.limit and posts.size > include.limit-%}
  {%-assign limit_exceeded = true-%}
{%-else-%}
  {%-assign limit_exceeded = false-%}
{%-endif-%}

{%- if posts.size > 0 -%}
  <ul>
    {%- for post in posts limit: include.limit -%}
        <li>
          <span>{{- post.date | date: site.theme_config.date_format -}}</span>
          <a href="{{ post.url | relative_url }}">{{ post.title | downcase }}</a>
          //删除downcase小写显示
          //删除post.date那一行
        </li>
    {%- endfor -%}
    {%- if include.show_more and limit_exceeded -%}
      <li><a href="{{ include.show_more_url }}">{{ include.show_more_text | default: "Show more..." }}</a></li>
    {%- endif -%}
  </ul>
{%- endif -%}
```



地方2

```
---
layout: default
---

{%-include back_link.html-%}

<article>
  <p class="post-meta">//删除这个
    <time datetime="{{ page.date }}">{{ page.date | date: site.theme_config.date_format }}</time>
    
  </p>
  
  <h1>{{ page.title }}</h1>

  {{ content }}
</article>
```



## _config.yml



### remote_theme

```

#theme: no-style-please # if you are using GitHub Pages, change it to remote_theme: riggraz/no-style-please
remote_theme: riggraz/no-style-please
```

把theme修改为remote_theme



### permalink

原来的permalink有问题

修改如下

```
permalink: /:month/:day/:title
```



### theme_config

修改回退键样式

```
# back_home_text: ".." 
back_home_text: "<= back to home" 
```



## 字体



在 `_includes\head.html`

```
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link rel="stylesheet" href="https://npm.elemecdn.com/lxgw-wenkai-screen-webfont/style.css" media="print" onload="this.media='all'"> //添加部分
  <title>
    {%- if page.title -%}
      {{ page.title }}
    {%- else -%}
      {{ site.title }}
    {%- endif -%}
  </title>

  {%-seo title=false-%}
  {%-feed_meta-%}

  <link rel="shortcut icon" type="image/x-icon" href="{{ site.favicon | relative_url }}" />
  <link rel="stylesheet" href="{{ "/assets/css/main.css" | relative_url }}" />
</head>
```

ps: 图床使用的是他人的cdn加速，可能会挂掉



在 `\_sass\no-style-please.scss`

```css
body {
  color: black;
  font-family: "LXGW WenKai Screen","monospace", Arial, sans-serif;
  font-size: 16px;
  line-height: 1.4;
  margin: 0;
  min-height: 100%;
  overflow-wrap: break-word;
}
```

