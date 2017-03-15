---
title: "单字节和多字节字符集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.character.multibyte"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符集 [C++], 多字节"
  - "字符集 [C++], 单字节"
  - "MBCS [C++], 关于 MBCS"
  - "SBCS（单字节字符集）"
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 单字节和多字节字符集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ASCII 字符集在 0x00 到 0x7F 的范围内定义字符。  还有其他一些字符集（主要是欧洲字符），它们在 0x00 到 0x7F 的范围内定义与 ASCII 字符集相同的字符，还在 0x80 到 0xFF 的范围内定义了扩展字符集。  因此，8 位的单字节字符集\(`SBCS`\)足以表示 ASCII 字符集以及许多欧洲语言的字符集。  但是，一些非欧洲字符集（如日文汉字）包含许多单字节代码无法表示的字符，因此要求使用多字节字符集 \(`MBCS`\) 编码。  
  
> [!NOTE]
>  许多 `SBCS` 例程在 Microsoft 运行库中处理相应的多字节字节、字符和字符串。  许多多字节字符集将 ASCII 字符集定义为子集。  在许多多字节字符集中，0x00 到 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。  例如，在`ASCII` 和`MBCS`字符串中，单字节 `NULL`字符（“\\0”）的值是 0x00 并且指示终止空字符。  
  
 多字节字符集 \(SBCS\) 可能包括单字节和双字节字符。  从而多字节字符串可以包含单字节和双字节字符混合。  两位的多字节字符有一个前导字节和尾字节。  在某个多字节字符集内，前导字节位于某个特定范围内，尾字节也一样。  当这两种范围重叠时，可能需要计算上下文以确定某个给定的字节是用作前导字节还是尾字节。  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)