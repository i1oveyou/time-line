---
layout: post
title:  "关于本站搭建"
date:   2021-09-01 12:00:00 +0800
categories: [others] 
---



>  Quick Start



tools

base58: https://www.metools.info/code/c74.html

mp4 -> gif : https://www.freeconvert.com/zh/convert/mp4-to-gif



# 本站配置



博客框架 [jekyll](http://jekyllthemes.org/)

采用主题： [agusmakmun](https://github.com/agusmakmun/agusmakmun.github.io) ， 通过博主**enovella_**发现的这个简洁主题

其它主题推荐 [huxpro](https://github.com/Huxpro/huxpro.github.io), [chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/)

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







## 页脚的GitHub



> _layouts\default.html





```
<div class="btn-github" style="float:right;">
<iframe src="https://ghbtns.com/github-btn.html?user=enovella&repo=enovella.github.io&type=star&count=true" frameborder="0" scrolling="0" width="85" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=enovella&repo=enovella.github.io&type=fork&count=true" frameborder="0" scrolling="0" width="85" height="20px"></iframe>

===>改为   
<div class="btn-github" style="float:right;">
<iframe src="https://ghbtns.com/github-btn.html?user=i1oveyou&repo=i1oveyou.github.io&type=star&count=true" frameborder="0" scrolling="0" width="85" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=i1oveyou&repo=i1oveyou.github.io&type=fork&count=true" frameborder="0" scrolling="0" width="85" height="20px"></iframe>
</div>
```



## 字体



在 `/index.html`

```
---
layout: default
---

<div id="home">
  <h1>{{ site.title }}</h1>
  <link rel="stylesheet" href="https://npm.elemecdn.com/lxgw-wenkai-screen-webfont/style.css" media="print" onload="this.media='all'"> //添加部分
  <hr />
```

ps: 图床使用的是他人的cdn加速，可能会挂掉



在 `static\css\main.css`

```css

body {
  font-family: "LXGW WenKai Screen","Roboto Condensed", Arial, sans-serif;
  background: url("/static/img/subtle_dots.png");
  line-height: 1.5em;
  font-weight: 300;
  font-size: 16px;
  color: #666;
}
```

