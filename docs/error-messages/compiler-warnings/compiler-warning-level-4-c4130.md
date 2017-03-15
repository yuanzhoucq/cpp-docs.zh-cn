---
title: "编译器警告（等级 4）C4130 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4130"
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”：字符串常量地址的逻辑操作  
  
 使用具有字符串文本地址的运算符会产生意外的代码。  
  
 下面的示例生成 C4130：  
  
```  
// C4130.cpp // compile with: /W4 int main() { char *pc; pc = "Hello"; if (pc == "Hello") // C4130 { } }  
```  
  
 **if** 语句会将指针 `pc` 中存储的值与字符串“Hello”的地址进行比较，每次代码中出现该字符串时，都将单独分配该值。**if** 语句不会将 `pc` 所指向的字符串与字符串“Hello”进行比较。  
  
 若要比较字符串，请使用 `strcmp` 函数。