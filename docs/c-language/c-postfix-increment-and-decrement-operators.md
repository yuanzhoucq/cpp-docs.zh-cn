---
title: "C 后缀增量和减量运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "增量运算符, 语法"
  - "标量运算符"
  - "类型 [C], 标量"
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# C 后缀增量和减量运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

后缀递增和递减运算符的操作数是可修改的左值的标量类型。  
  
## 语法  
 *postfix\-expression*:  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 后缀递增或递减运算的结果是操作数的值。  获取结果后，操作数的值将增加（或减少）。  以下代码演示了后缀递增运算符。  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 在本示例中，变量 `var` 先与 0 进行比较，然后增加。  如果 `var` 在增加之前为正数，则执行下一条语句。  首先，`q` 所指向的对象的值赋给 `p`所指向的对象。  然后，`q` 和 `p` 增加。  
  
## 请参阅  
 [后缀增量和减量运算符：\+\+ 和 \-\-](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)