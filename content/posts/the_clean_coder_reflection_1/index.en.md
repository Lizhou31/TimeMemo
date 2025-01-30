---
title: "讀後感 - The Clean Coder（ㄧ）"
subtitle: "About Professionalism"
date: 2023-07-28T13:35:24+08:00
lastmod: 2023-07-28T13:35:24+08:00
draft: false
author: "Lizhou"
authorLink: "https://timememo.lizhou31.com"
description: ""
license: ""
images: []

tags: ["The Clean Coder", "讀書心得"]
categories: ["Book_Reflection"]

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
_The Clean Coder 第一章讀後感_
<!--more-->
## 前言

最近又重新把 The Clean Coder 重新拿出來讀了一遍，根據這一年工作的一些經歷，又有更多的思考和體悟（？打算來記錄一下。

因為 The Clean Coder 太多章節，我認為許多章節都很值得單獨拿出來寫，所以可能這也會是一整個系列的讀書心得。

先簡短簡介一下 The Clean Coder 這本書，中譯 ___"無瑕的程式碼番外篇-專業程式設計師的生存之道"___，作者為 Robert C. Martin，是很著名的軟體工程師，以提倡許多軟體設計原則和開發方式聞名。這本書其實也是 ___"The Clean Code"___ 的番外篇，主要是在敘述如何成為一名“專業的”程式設計師。

這本書我認為其實也不僅僅只適合工程師閱讀，其中有不少對於工作上專業態度的解釋與例子，也很適用於其他情況。

## Be careful what you ask for

第一個章節，主要就是要探討到底何謂 _Professionalism_ 以及一個追逐專業態度的人該有的表現。

但是最重要的是 __"What you ask for"__，追求專業一定不是一件簡單且輕鬆的事情，會需要承擔的責任一定會比不用追求專業來的沈重，但我認為不追求專業並不能讓自己逃避掉什麼，因為該負的責任本身就會隨著自己的年齡增長開始受到外界的期待，如果持續抱持著"不專業"的態度，僅僅只會讓自己與社會期待脫節，而到那個時候所需要付出的心理壓力並不會更小。

就如同社會期待一名父親需要做好養育孩子，教育孩子，以及與伴侶扶持家庭的責任，或許可能因為很多原因在身為父親的角色不夠“專業”，但是社會的期待如此，外界看到的結論也只會是你有沒有做好這件事情。你可以選擇在其他的部分上“專業”下心力，但所有的都是取決於 __"What you ask for"__，而你選擇的道路，就會承擔相應的責任。

稍微離題了，但總之，選擇了一項專業，隨之而來的就是相應的責任。

{{< admonition type=quote >}}
___"You can't take pride and honor in something that you can't be held accountable."___

___"Professionalism is all about taking reponsibility."___

_-- <<The Clean Coder>>_
{{< /admonition >}}

拿我自身為例，我在公司裡因為本身有一點相關背景和知識，所以時常擔任著公司在做相關決策時的諮詢討論者。從一項 Project 的功能增加，時程預估；又或是一個產品的品質控管，或是一項技術的引入與否，很常都會徵求我的意見。

對，這是我的專業，我願意這樣想，但隨之而來的是責任的沈重感。當我認為這是我的專業並給出我的建議時，我就該付出相應的責任，因為每句話都可能影響到整個公司接下來的發展，以及大家以後吃不吃得飽飯。

我很聰明嗎？並沒有；我很有經驗嗎？更不可能有。那當我決定給出我的建議，我的“專業”看法前，我就需要花很大量的時間去思考，去搜集各種資訊，去詢問各種比我更有經驗的專家，去佐證我給出的建議是有跡可循的，是可以付諸實行的。

然後更重要的是，我要有心理準備是，我如果犯錯了，我就該承擔責任。

## 所謂專業人士，就是能對自己錯誤負責的人

{{< admonition type=abstract >}}
_It is the lot of a professional to be accountable for errors even though errors are virtually certain. So, my aspiring professional, the first thing you must practice is apologizing. __Apologies are necessary, but insufficient. You cannot simply keep making the same errors over and over.__ As you mature in your profession, your error rate should rapidly decrease towards the asymptote of zero. It won't ever get to zero, but it is your reponsibility to get as close as possible to it._
{{< /admonition >}}

如同上述書中所言，人不可能完全不犯錯，沒有人永遠保證自己犯錯的機率為零，但是專業就體現在由於經驗的累積和持續不斷的修正，犯錯機率會持續下降直到趨近於零。

![Zero would be nice](Zero_would_be_nice.webp "Oppenheimer 預告中討論引爆核彈毀滅世界的機率")

然後當犯錯的時候，大方承認自己的錯誤並且找到該修正的點。如果是自己疏失的錯誤，要狠狠地記上一筆（心裡面），然後提醒自己下次需要注意。但如果不是自己疏失，可能是因為外界因素的錯誤，其實也是需要修正的。

我認為永遠不該把任何的錯誤結果 __僅僅__ 歸咎於外界因素，例如電腦當機，天氣太熱。這些可以是 __"原因"__，但不能是 __"結果"__。永遠無法完全控制外界的干擾因素，只能去適應外界的干擾。

舉個例子，曾經有次公司產品出外 Demo 時意外發生了電腦無故無法開機，最後查證是電池沒電的問題，但是我們在前一天都確認過電量和所有狀態都是 OK 的了，怎麼會有這種問題？

後來才發現可能是有其他同事改過電腦設定導致關機程序改變，因而並沒有完全進入關機，只是休眠狀態，我們也沒有注意到，就造成了錯誤的結果。

這是我們犯下的錯誤嗎？不完全是。但是這是我們應該負起的責任，因此我們馬上重新審視了外出工作的前置作業檢查，把有可能的出錯情況降到最低。

那要應對不同的錯誤進行改正，需要的就是不斷的學習。

## 了解自己的領域並堅持學習

學習很重要，尤其對追求專業來說，更為重要。除了理解新知識，也需要去回顧歷史。

{{< admonition type=quote >}}
_Remember Santayana's curse: __"Those who cannot remember the past are condemned to repeat it."__ -- <<The Clean Code>>_
{{< /admonition >}}

過去的知識並不是一文不值，更多的是能夠讓我們理解到知識發展的脈絡，讓以後的路更加清晰。

當然更重要的是需要在自己的領域深耕並堅持學習，其中包含兩個方面：

### 理解自己的領域

專業就是在自己的領域有著一定程度深耕，就如書中建議軟體工程師需要理解的內容：

{{< admonition type=abstract >}}
_Here is a __minimal__ list of the things that every software professional should be conversant with:_

* _Design patterns. You ought to be able to decribe all 24 patterns in the GOF book and have a working knoledge of many of the patterns in the POSA books._
* _Design principles. You should know the SOLID principles and have a good undersatanding of the component principle._
* _Methods. You should understand XP, Scrum, Lean, Kanban, Waterfall, Structured Analysis, and Structured Designed._ 
* _Disclilines. You should pratice TDD, Object-Oriented design, Structured Programming, Continous Integration, and Pair Programming._
* _Artifacts. You should know how to use: UML, DFDs, Structure Charts, PetriNets, State Transition Diagrams and Tables, flow charts, and decision tables._
{{< /admonition >}}

真的慚愧，我上述有很多都很不了解，看來需要認真惡補惡補。

另外，除了 __“自己的領域”__，書中也有提到需要了解 __“業務領域”__，開發什麼，就必須了解相對應的業務領域。

我今天想開發一個工業應用上的自動化設備，除了理解本身軟體開發的領域，也需要去理解到底工業自動化都是怎麼設計的，需要怎麼樣的連接接口，應用設備。我不需要成為那個領域的專業人士，但我一定需要具備能與相關領域專業人士溝通的能力。

{{< admonition type=quote >}}
_"It is worst kind of unprofessional behavior to simply code from a spec without understanding why that spec makes sense to the business. Rather, you should know enough about the domain to be able to recognize and challenge specification errors." -- <<The Clean Coder>>_
{{< /admonition >}}

好像可以參考領域驅動開發 (Domain-Driven Design,DDD) 的相關知識。因為很多時候問題並不是寫寫程式就能夠簡單解決的，會需要更多的專業知識支持，僅僅只是固守自己的專業是沒有用的，還需要具備與其他專業溝通的能力。

### 堅持學習

{{< admonition type=quote >}}
_"Would you visit a doctor who did not keep current with medical journals? Would you hire a tax lawyer who did not keep current wth the tax laws and precedents? Why should employers hire developers who don't keep current?" -- <<The Clean Coder>>_
{{< /admonition >}}

堅持學習除了學習新知識以外，還需要堅持反覆練習。本書作者有提到他會使用一種 "kata" 來持續反覆練習已有的技巧，保持技巧成熟。並非使用難以解決的問題，而是使用已知解決但疏於練習的問題，來增加熟練度。

{{< admonition type=abstract >}}
_The point of doing the kata is not of figure out how to solve the problem you know how to do that already. The point of the kata is to train your finger and your brain_
{{< /admonition >}}

這也是我目前需要增進的地方，很多東西我儘管都知道要怎麼做，但是真正上手的時候也都會需要卡一陣子才能夠真的寫出來。

## 修改與測試

好的程式碼應該保持靈活可維護的軟體結構，而如果想要讓程式碼靈活，則必須時常去修改它。

{{< admonition type=quote >}}
_"If you want your software to be flexible, you have to flex it!" -- <<The Clean Code>>_
{{< /admonition >}}

而能保證修改後不會破壞整個程式的運行結構，就需要建立良好的測試環境以及流程。書中建議，不，是要求要做到覆蓋 100% 的單元測試，去測試每行程式碼，這樣才能保證每次修改後不會產生預期外的錯誤。

而要有辦法做到覆蓋率如此高的測試，就需要在設計階段就要有良好的模組化思考和測試驅動開發思維（Test-Driven Developement, TDD）

## 謙遜

書中提到，程式設計是一門及其自負的行為，畢竟程式設計師們是本質上是一名創作者，透過自己的程式去構成相應的結果。

我認為的確如此，我們需要對自己寫出的每行程式極度自信，因為花了時間去理解了到底寫了什麼東西，並且經過的大量測試，那是應該要對自己的程式抱持著十分的自信。而這種自信的確也是一種自負的狀態。

但這種自負是建立在，因為需要謙遜地去對待過去的所有錯誤，以及小心的去看待每一行自己寫出來的程式，所以才會有這種心態。而每當發生錯誤時，更要毫不保留的去承認自己的錯誤，然後去找出問題。

專業人士是謙遜且自信的，對待所有未知謙遜且小心，而在已知的地方則自信並大膽。

>_"我保證這部分可行"_

這是我很常對我的組員說的:rofl:，儘管我離真正的專業人士還差得遠呢！