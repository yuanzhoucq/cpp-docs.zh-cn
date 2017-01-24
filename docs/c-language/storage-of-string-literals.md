---
title: "字符串文本的存储 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符串, 存储"
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字符串文本的存储
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文本字符串的字符将按顺序存储在连续内存位置。  字符串中的转义序列（例如，**\\\\** 或 **\\"**）将作为单个字符进行计数。  null 字符（由 **\\0** 转义序列表示）自动追加到每个字符串并标记该字符串的末尾。（这会在[转换阶段](../preprocessor/phases-of-translation.md) 7 出现。）请注意，编译器无法在两个不同的地址存储两个相同的字符串。  [\/GF](../build/reference/gf-eliminate-duplicate-strings.md) 强制编译器将相同字符串的单个副本置于可执行文件中。  
  
## 备注  
 **Microsoft 专用**  
  
 字符串具有静态存储持续时间。  有关存储持续时间的信息，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C 字符串文本](../c-language/c-string-literals.md)