---
title: "關於工程的一些心得和看法"
subtitle: ""
date: 2023-07-01T12:23:52+08:00
lastmod: 2023-07-01T12:23:52+08:00
draft: true
author: "Lizhou"
authorLink: "https://timememo.lizhou31.com"
description: ""
license: ""
images: []

tags: []
categories: ["Tech_Experience"]

featuredImage: "featured-image.webp"
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  maxShownLines: 50
math:
  enable: false
  # ...
mapbox:
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # located in "assets/"
    # Or
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # located in "assets/"
    # Or
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
  # ...
---
_An imaginary spacecraft construction image created through stable diffusion._
<!--more-->
## 前言
我對"工程"這件事情依然是很迷惑，迷惑並不是做工程這件事情本身，而是面對工程的態度。

以一個資本主義的社會來說，"搶商機"這件事情完全沒有問題，甚至是必須的。但是很多時候效率和穩定性多少是相互受到制約的，不能說相互成反比，但是你在注重開發效率的同時，如果過份的去省略過多步驟，那開發的穩定性和後續維護性是否就會受到影響？更不要說如果開發的是一項有關人身安全的工程項目了，那從剛開始的設計，後續的驗證，應該都是要非常嚴謹的態度。

作為一個初出茅廬的小小菜鳥工程師，這段期間有幸參與了一些專案，不過因為其實是在小間的新創公司進行開發，實際上開發流程和參與開發人員都不多，很多時候都只能透過自己的到處詢問和過往經驗來 try and error，但還是多少累積了心得。

## 架構設計

工程的架構設計是一件特別難的事情。
