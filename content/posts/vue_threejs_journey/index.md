---
title: "週末的一點前端小旅程"
subtitle: "Vuejs + Threejs 的小嘗試"
date: 2023-08-13T21:20:55+08:00
lastmod: 2023-08-13T21:20:55+08:00
draft: true
author: ""
authorLink: ""
description: ""
license: ""
images: []

tags: ["網頁","Vuejs","Threejs"]
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
*從零開始的一點前端小旅程*
<!--more-->
## 前言
週五下班前和同事聊到公司的某個系統功能開發的想法，聊著聊著就突然來了興趣，想著坐而言不如起而行，直接上手試試看最不熟練的前端。

由於公司是用 [Vue](https://vuejs.org/) 當作開發框架，然後我想試試看 Typescript 進行開發，因此整個開發便是在 Vue.js + [Three.js](https://threejs.org/) + Typescript 底下完成。

## 開發功能描述
先簡略描述一下系統狀態，有個 3D 模型，上面會有數個測量點顯示在模型上，如下圖所示：
![Demo1](demo1.webp "模型示意圖")
然後每個點上都會有個針對這個模型的一些數值，主要就是想開發一個功能，如果點擊/搜尋到畫面上的任意測量點，會把視角移動到最適合使用者看到點的位置，如下圖所示：
![Demo2](demo2.webp "功能示意圖")
那對我來說會有幾個難點：

1. 前端網頁以及框架的不熟悉，由於本身並不是主要寫前端的人，所以幾乎需要從零開始學習這次所需要的 Vue 框架，前端 3D 套件 Three.js，以及 Typescript 。
2. 由於模型多少還是有一定的複雜度，因此在移動相機視角的時候必須根據測量點在模型上的哪個位置進行視角改變，如果測量點在模型傾斜 45 度角的位置，就必須讓視角也跟著傾斜 45 度角，才能達到最好的視角角度。
3. 因為希望能夠讓這份程式有重用性，以及希望嘗試一點設計方法，因此會需要在一開始就規劃一下程式架構。

## 程式架構講解
### 架構簡述
{{< mermaid >}}
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
{{< /mermaid >}}
### 模型分類

### Interface 

### 計算相機座標

## 結語