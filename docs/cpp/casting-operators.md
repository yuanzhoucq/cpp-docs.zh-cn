---
title: "强制转换运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "强制转换运算符"
  - "运算符 [C++], 强制转换"
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 强制转换运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有几种特定于 C\+\+ 语言的转换运算符。  这些运算符用于删除旧式 C 语言转换中的一些多义性和危险继承。  这些运算符是：  
  
-   [dynamic\_cast](../cpp/dynamic-cast-operator.md) 用于多态类型的转换。  
  
-   [static\_cast](../cpp/static-cast-operator.md) 用于非多态类型的转换。  
  
-   [const\_cast](../cpp/const-cast-operator.md) 用于删除 `const`、`volatile` 和 `__unaligned` 特性。  
  
-   [reinterpret\_cast](../cpp/reinterpret-cast-operator.md) 用于位的简单重新解释。  
  
-   [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 用于生成可验证的 MSIL。  
  
 在万不得已时使用 `const_cast` 和 `reinterpret_cast`，因为这些运算符与旧的样式转换带来的危险相同。  但是，若要完全替换旧的样式转换，仍必须使用它们。  
  
## 请参阅  
 [强制转换](../cpp/casting.md)