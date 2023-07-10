---
title: "Integer Promotions"
subtitle: ""
date: 2023-07-09T22:32:01+08:00
lastmod: 2023-07-09T22:32:01+08:00
draft: false
author: "Lizhou"
authorLink: "https://timememo.lizhou31.com"
description: ""
license: ""
images: []

tags: ["C","計算機概論"]
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
來討論一點整型提升
<!--more-->

## Overview

- C語言的發明人 **Dennis MacAlistair Ritchie** 與 **Kenneth Lane Thompsont** 創設以下規則：
  {{< admonition type=quote >}}
  *“A character, a short integer, or an integer bit-field, all either signed or not, or an object of enumeration type, may be used in an expression wherever an integer maybe used. **If an int can represent all the values of the original type, then the value is converted to int; otherwise the value is converted to unsigned int.** This process is called integral promotion.”*
  {{< /admonition >}}
    
  也就是所謂的 Integer Promotion （整型提升）。
    
- Wiki - 整型提升：
  {{< admonition type=quote title=Wiki >}}
  *整型提升的意義在於：表達式的整型運算要在 CPU 的相應運算器件內執行，**CPU內整型運算器 (ALU) 的操作數的字節長度一般就是 int 的字節長度**，同時也是CPU的通用暫存器的長度。因此，即使兩個 char 類型的相加，在 CPU執行時實際上也要先轉換為 CPU 內整型操作數的標準長度。通用 CPU（general-purpose CPU）是難以直接實現兩個 8比特字節直接相加運算（雖然機器指令中可能有這種字節相加指令）。所以，表達式中各種長度可能小於int長度的整型值，都必須先轉換為int或unsigned int，然後才能送入 CPU去執行運算。*
  {{< /admonition >}}

## C Standard (C99 / N1570)

C99 中有關 integer promotions 的地方分別在：__§5.1.2.3__, __§5.2.4.2.1__, __§6.3.1.1__, __§6.5.2.2__, __§6.5.3.3__, __§6.5.7__, __§6.8.4.2__
以下將不按照順序，按筆者的閱讀邏輯講解：

### _§6.3.1.1_

{{< admonition type=quote title="§6.3.1.1 / 2, 3" >}}
_The following may be used in an expression wherever an `int` or `unsigned int` may be used:_

  - _An object or expression with an integer type (other than `int` or `unsigned int`) whose integer conversion rank is less than or equal to the rank of `int` and `unsigned int`._
  - _A bit-field of type `_Bool`, `int`, `signed int`, or `unsigned int`._

_If an `int` can represent all value of the original type (as restricted by the width, for a bit-field), the value is converted to an `int`; otherwise, it is converted to an `unsigned int`. These are called the **integer promotions**. All other types are unchanged by the integer promotions._

_The integer promotions preserve value including sign. As discussed earlier, whether a “plain” `char` is treated as signed is implementation-defined._
{{< /admonition >}}

此處講明了假設一個原始的型態能夠被 `int` 表達，則會被轉換至 `int`；要不然則會被轉換至 `unsigned int`，此行為稱作 **integer promotions**。
  
前段也敘述了 integer promotions 會發生的情境：
    
  1. Integer type 且 Integer conversion rank 小於或等於 `int` 或 `unsigned int`
  2. bit-field type
    
並且 promotion 以後的數值是會保持著原本的正負。

{{< admonition type=tip >}} 
Integer conversion rank 同樣於 §6.3.1.1 / 1 有描述。
{{< /admonition >}}


### _§5.1.2.3 / 11_

{{< admonition type=quote title="§5.1.2.3 / 11" >}}
_EXAMPLE 2 In executing the fragment_

  ```c
    char c1, c2;
    /* ... */
    c1 = c1 + c2;
  ```
  _the ''integer promotions'' require that the abstract machine promote the value of each variable to int size and then add the two ints and truncate the sum. Provided the addition of two chars **can be done without overflow**, or **with overflow wrapping silently** to produce the correct result, the actual execution need only produce the same result, possibly omitting the promotions._
{{< /admonition >}}

    
這邊用了一個例子來簡單說明了 Integer promotions，在 C Standard abstract machine model中，這段運算的 `char c1`, `char c2` 都會被整型提升至 int，使其不會產生 overflow 的結果，或悄悄地 wrap overflow。
    
### _§6.5.2.2 / 6_

{{< admonition type=quote title="§6.5.2.2 / 6" >}}
*If the expression that denote the called **function has a type that does not include a prototype, the integer promotions are performed on each argument, and argument that have type float are promoted to double.** These are called the **default argument promotions.** If the number of arguments does not equal the number of parameters, the behaviors is undefined. If the function is defined with a type that includes a prototype, and either the prototype ends with an ellipsis (,...) or **the type of the arguments after promotion are are not compatible with the types of the parameters, the behavior is undefined.** If the function is defined with a type that does not include a prototype, and the types of  the arguments after promotion are not compatible with those of the parameters after promotion, the behavior is undefined, except for the following cases:*
  - *one promoted type is a signed integer type, the other promoted type is the corresponding unsigned integer type, and the value is representable in both types;*
  - *both types are pointers to qualified or unqualified versions of a character type or void.*
{{< /admonition >}}

這邊解釋了 function argument 的 promotion 情境，當：
    
  1. Function without prototype 
  2. Function has variable arguments
    
會使用 default argument promotions 。
    
參考以下解釋：
    
[stack overflow - I want default argument promotion’s example](https://stackoverflow.com/a/60225225)
    
可以得知 default function prototype 的使用情境。

{{< admonition type=tip >}} 
另，在 [stack overflow - Function without prototype called with non-compatible type](https://stackoverflow.com/a/55419261) 之中有說到了 function declare without prototype 的講解，底下的 comment 也有提到 function without prototype is old syntax you should not use in new code.
{{< /admonition >}}

針對 function 的 parameters 和 arguments 的 integer promotion，有幾個會造成 UB (Undefined Behavior)：
  * 如果 function 的 prototype 是 defined，但經過 promotion 之後的 arguments 和 parameters 是無法匹配起來的，會造成 UB。
  * 如果 function 的 prototype 是 not defined，parameters 和 arguments 雙邊進行 promotion 之後是無法匹配的，也會造成 UB。
  
{{< admonition type=tip >}}
也可以參考以下資訊 [stack overflow - Default argument and parameter promotions in C](https://stackoverflow.com/a/61836943)
{{< /admonition >}}

### _§6.5.3.3_

{{< admonition type=quote title="§6.5.3.3" >}}
*The result of the unary + operator is the value of its (promoted) operand. The integer promotions are performed on the operand, and **the result has the promoted type**.*

*The result of the unary - operator is the negative of its (promoted) operand. The integer promotions are performed on the operand, and **the result has the promoted type**.*

*The result of the ~ operator is the bitwise complement of its (promoted) operand (that is, each bit in the result is set if and only if the corresponding bit in the converted operand is not set). The integer promotions are performed on the operand, and **the result has the promoted type**. If the promoted type is an unsigned type, the expression ~E is equivalent to the maximum value representable in that type minus E.*
  
_The result of the logical negation operator ! is 0 if the value of its operand compares unequal to 0, 1 if the value of its operand compares equal to 0. The result has type int. The expression !E is equivalent to (0 == E)._
{{< /admonition >}}
    
此段講解了 unary arithmetic operator 使用上的 integer promotions 場景：
  * Unary `+` operator
  * Unary `-` operator
  * Unary `~` operator

此三個 unary operator 都會表現出 promoted result，`+E` 甚至可以當作主動觸發 Integer Promotion 的方法。
    
### _§6.5.7 / 3_

{{< admonition type=quote title="§6.5.7 / 3" >}}
_The integer promotions are performed on each of the operands. The type of the result is that of the promoted left operand. ***If the value of the right operand is negative or is greater than or equal to the width of the promoted left operand, the behavior is undefined.***_
{{< /admonition >}}

此段是對於 Bitwise shift operators 的更多說明，當使用 Bitwise shift operators 時，兩邊的 operands 都會 integer promotions，並且若右側的 operand 是負數或其 shift 的位數 (bits) 大於等於左側 promoted 以後的位數 (bits)，則是 undefined behavior。

{{< admonition type=tip >}}
在 jserv 老師的 <2021年「Linux核心」暑期課程> 中的 <[位元旋轉實做和Linux核心案例](https://hackmd.io/@sysprog/bitwise-rotation)> 中有講解到關於 Linux 核心在實做位元旋轉時因應 integer promotions 所做出的不同實做。
  {{< admonition type=quote title="節錄位元旋轉實作和 Linux 核心案例" >}}
  Linux Kernel 曾經的 32 位元旋轉實作如下：

  ```c
    static inline __u32 rol32(__u32 word, unsigned int shift) 
    {
      return (word << shift) | (word >> (32 - shift));
    }
  ```

  但上述實作當 shift 為 0 時，其中 >> 32 對於 32 位元整數來說，會遇到 C 語言中規範的 undefined behavior（如上述規格書所述）

  因此後續進行改善為如下實作：

  ```c
    static inline __u32 rol32(__u32 word, unsigned int shift)
    {
      return (word << (shift & 31)) | (word >> ((-shift) & 31));
    }
  ```

  但上述主要是因為 32 位元的 integer promotion 的結果造成 UB，如果是 8 位元的實作則並不會有問題：

  ```c
    static inline __u8 rol8(__u8 word, unsigned int shift)
    {
      return (word << shift) | (word >> (8 - shift));
    }
  ```

  {{< /admonition >}}
{{< /admonition >}}

### _§6.8.4.2 / 5_

{{< admonition type=quote title="§6.8.4.2 / 5" >}}
_**The integer promotions are performed on the controlling expression**. The constant expression in each case label is converted to the promoted type of the controlling expression. If a converted value matches that of the promoted controlling expression, control jumps to the statement following the matched case label. Otherwise, if there is a default label, control jumps to the labeled statement. If no converted case constant expression matches and there is no default label, no part of the switch body is executed._
{{< /admonition >}}

此段是對於 switch statement 的附加敘述，switch statement 的 controlling expression 會先經過 promote，然後各個 Label 在進行 convert 進行比對。


## 關於 Integer Promotions 的一些想法與延伸

- 實際上關於 Integer Promotions 的發生可以說是必然的，就如同 Wiki 上所說的，任何值要送入 ALU 運算時都會需要把數值存進某個 register 中，而這個 register 大小通常等於 `int` 的大小。當送入 register 的情況發生以後，實際上就等同於發生了 Integer Promotions 。
- 機器（硬體）上的“必然”在軟體是由規格書特別規範出來，這樣似乎可以針對語言的 Abstract machine 進行討論了...（下集待續？）

其他參考資料來源

- ***[ISO/IEC 9899:201X (N1570)](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)***