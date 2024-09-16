---
layout: post
title:  "关于本站搭建"
---



>  Quick Start



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
https://raw.githubusercontent.com/redqx/redqx.github.io/master/_posts/img/ 
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

