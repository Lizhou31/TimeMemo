---
title: "近期關於生成式AI的一些想法"
subtitle: ""
date: 2025-02-03T12:23:52+08:00
lastmod: 2025-02-03T12:23:52+08:00
draft: false
author: "Lizhou"
authorLink: "https://timememo.lizhou31.com"
description: ""
license: ""
images: []

tags: ["AI", "雜談"]
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
_An image captured on Yugung Island at sunset._
<!--more-->
# 前言
回歸之作就獻給生成式 AI 吧。剛好也是最近使用的最多也嘗試得最多的領域。

實際上甫從 chatGPT 問世，我幾乎是馬上就去使用了，當然一開始只是圖個新鮮，畢竟可以流利對話的聊天機器人到之前幾乎都是不出現的。當然，那個時候真的就只是一個新鮮感的玩具，儘管對於他的對話能力感到新奇，但當時幾乎並沒有任何生產力的想法。

直到 OpenAI 開始發布更新，從 3.5, 3.5-turbo, 4, 4o，GPT 也從只可以文字輸入的娛樂，到現在多模態，支援圖片，語音，甚至是即時影片做為輸入的多樣化工具。

而這些進步僅僅發生在 ChatGPT 推出的兩年以內，他就從娛樂進化成了可以提供各類協助的工具，於是，也讓我開始思考，__究竟接下來人類與 AI 工具會有什麼樣的發展__（又或是 Ilya Sutskever 認為的，可能是一種全新的智能體物種），而我又該如何去面對這些幾乎是突破性的發展。

當然 AI 影響的可不僅僅是日常生活而已。

2024 諾貝爾獎應該是非常特別的一年，這年的諾獎開創性的頒給了不少 AI 相關的研究，例如諾貝爾物理學獎的得主 John J. Hopfield 和 Geoffrey E. Hinton，表彰他們在人工神經網路的基礎研究。諾貝爾化學獎也頒給了利用 AI 研究蛋白質結構與設計的學著。

這些獎項頒給了與 AI 相關的科研內容，可以說是一大震撼彈，代表在學術界的頂級榮譽，也認可了目前的 AI 科技。儘管諾獎看似離我這種普通人應該都是太遠了，但當一個人類文化智慧結晶的殿堂都開始接受這項科技的成果時，這個衝擊應該不會過很久就會席捲整個社會。

甚至其實 AI 們早就在內捲人類的生活了。根據 [Who Is AI Replacing? The Impact of Generative AI on Online Freelancing Platforms](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4602944) 調查了 Freelancer 市場在 ChatGPT 出現前後以及 AI 繪圖相關工具出現前後的工作需求佔比，而這是他們的其中一段結果摘錄：
{{< admonition type=abstract >}}
  •	Within eight months of ChatGPT’s release, job postings for __automation-prone roles (e.g., writing, coding, and automation) decreased by 20.86% more than manual-intensive jobs.__

  •	__Writing jobs__ saw the largest decline __(30.37%)__, followed by __software development (20.62%)__ and __engineering (10.42%)__.

  •	The introduction of AI-powered image-generation tools (Midjourney, Stable Diffusion, DALL-E 2) led to a __17.01% decline in job postings for graphic design (18.49%) and 3D modeling (15.57%).__
{{< /admonition >}}

也就是說，就算只是截止到目前(2024)的 AI 工具，對於人類的影響已經可以說是非常大的了。那我就在想，在這個可能是時代變革的時間點上，究竟我該拿什麼態度去對待這些工具，才能夠再好好利用工具的情況下又不會失去我原先該有的能力。

# 那些 AI 工具對我的影響

欸？失去什麼原先該有的能力？難道人會被 AI 取代？我會沒有工作？其實我並不是在擔心這個。不過如果這件事情真的發生了其實我也沒有太多的驚訝，畢竟現在任何的科技（或是說 AI）發展真的都是不斷超乎想像的。誰能想像 2022 才出現的 ChatGPT，發展了僅僅兩年就已經可以勝任原本只有真人才能做得到的工作，甚至有些還做得更好。

實際上我一邊使用這些工具並享受著這些東西帶給我的便利性時，我一邊也開始有點惶恐，當我對這些好用的工具產生依賴性時，是否會失去什麼原先我該具備的能力。

舉個例子，之前有段時間我在與朋友討論相機的成像原理時，對於 __CoC (Circle of confusion)__ 這個名詞感到陌生，於是我很順手的就直接丟給了 ChatGPT 請他解釋，但當時為了方便直接是使用中文問的（一般在使用時我還是覺得英文的問答品質會比中文高很多），於是 ChatGPT 給我了一個似是而非的解答，而當時我也沒有太在意，就把他的回答當作我的理解給記了下來。

結果大概是中文語意的問題，實際上 ChatGPT 上的解釋是具有誤導性的，而這個誤導讓我後續對於整個模糊圈（CoC）的判斷又出現了問題，後面跟朋友的討論就出現了雞同鴨講的情況。

後來我回想一下整件事情的發生，我才突然驚覺自己好像因為太過於依賴 ChatGPT 的回答導致我喪失了當初多方求證的能力。儘管每個在教你使用任何大語言模型工具的課程，大多都會提到所有的 AI 工具都會有一定程度的錯誤，使用者都必需自己花時間去審慎評估。

但是當看似高品質的資訊越來越易於取得時，求證的過程就會漸漸的被省略，至少我是如此。

當然影響也不僅僅只有這樣，還有包括自己在寫程式的習慣漸漸的在改變，也越來越倚靠 AI 快速先幫我打底，我再去慢慢精修的結果。又或是碰到問題，直接習慣性地先丟給 ChatGPT 的語言模型幫我做一次 Survey，這樣得到答案的效率更高。

這樣不好嗎？很好，老實說。無論是我工作上或是生活中，效率都有提高。只是似乎，倚靠著自己“思考“的過程在慢慢地減少。

{{< figure src="Kazz_stopThinking.webp" alt="Description" width="100%" caption="卡茲停止了思考" >}}

# 關於 AI 工具應用的一些小結

其實這篇真的就比較偏向一些 MurMur，怕越寫焦點會越模糊掉。（其實是太久沒寫文章開始詞窮了Ｘ）之後或許會根據某些主題再多 MurMur 一點？

儘管 AI 工具帶來了非常多的方便，但當我們有許多能力漸漸的因為這些方便而疏於使用後，究竟會帶來哪些副作用目前仍是沒有肯定的。至少對我自己來說我已經受到些許的負面的副作用影響了。

曾經在聽了某個跟 AI 工具相關的演講，當時的講師表示:

{{< admonition type=quote >}}
在接下來的的 AI 時代，你必須找到自己真正熱忱的事情，才能夠讓自己更能夠面對這些衝擊。
{{< /admonition >}}

更進一步地說，AI 工具已經能夠滿足不少工作及格分左右的需求，剩下的就是需要靠自己的熱忱去完成更多的分數。但也可以說，當你對某些事情有熱忱時，能夠擋住實現這些熱忱的門檻已經越來越少了。例如一個毫無程式能力基礎的，甚至連 Python 要去哪裡執行都不知道的財務統計專業人員，可以通過不斷地詢問 ChatGPT 在僅僅一天之內來完成一個功能非常完整，能夠自己搜尋到各類財務資料並且自己出報告的程式。沒有繪畫能力的我，也能非常簡單地透過幾句指令，就能在我的投影片裡面加入有意義且精美的插圖。

達成目標的門檻越來越低，但“及格”的標準也會越來越高了。我認為在接下來的時代，把握自己熱忱相關的技能，透過 AI 帶來的方便性工具來弭平可能的困難，並且用來持續精境支持自己熱忱的那些能力，不要讓輕易的讓自己的這些能力退化成能夠被輕易取代。

這大概是，我認為接下來艱難的時代我需要學習的內容。
