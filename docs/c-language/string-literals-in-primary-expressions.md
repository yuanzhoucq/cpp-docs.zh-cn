---
title: "主要表达式中的字符串文本 | Microsoft Docs"
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
  - "字符串, 在主要表达式中"
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 主要表达式中的字符串文本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“字符串”是字符、宽字符或包含在双引号内的相邻字符序列。  由于它们不是变量，因此字符串和其任一元素都不能作为赋值运算中的左操作数。  字符串的类型为 `char` 的数组（或宽字符串的 `wchar_t` 数组）。  表达式中的数组将转换为指针。  有关字符串的详细信息，请参阅[字符串](../c-language/c-string-literals.md)。  
  
## 请参阅  
 [C 主要表达式](../c-language/c-primary-expressions.md)