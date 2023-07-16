---
title: "RT_Thread 學習紀錄（一）"
subtitle: "Overview"
date: 2023-07-16T20:44:24+08:00
lastmod: 2023-07-16T20:44:24+08:00
draft: true
author: "Lizhou"
authorLink: "https://timememo.lizhou31.com"
description: ""
license: ""
images: []

tags: ["C", "RT-Thread"]
categories: ["Technical_Note"]

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
初探 RT-Thread
<!--more-->

## 緣起

從大學上過作業系統（OS）課程以後，對於整個系統運作就一直抱有一種很不明的情愫（？

透過一段程式調度整個硬體設備，包括邏輯運算中樞，各種通訊界面，還有控制外部週邊單元，還要應付~~毛病一堆~~的使用者，如果把作業系統放在現實生活根本就是神一般的人物吧？

總之，在學到作業系統以後對於運用和編寫作業系統這件事一直都抱有憧憬。

![Kira](Kira.webp "我絕對不會說其實最早啟發我作業系統幻想的是他")

後來大學開始使用 Linux 系統，並因緣際會的學到了一些 Kernel 知識和 Kernel module 開發，對作業系統更加著迷了，但受限於 Linux 這種大型且複雜的作業系統，我也只能在旁邊摸摸皮毛過過乾癮，但總覺得參與感不夠。

後來大學專題因為主題是 BLE Mesh，為了能夠良好的移植 Bluetooth 的協議層，接觸到了 Linux Foundation 底下的 [Zephyr Project](https://zephyrproject.org/)，開始接觸並使用 RTOS，不過這時還是以應用為主。但是心底一直有個想法，應該真正的去摸清楚整個 RTOS 的實做，並且透過自己重新實現來加深理解整個作業系統的概念。但是可以說自己懶，或是一直找不到很合適的專題或機會去真正實現這個想法。

