---
title: "if 语句 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "else"
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "else 子句"
  - "else 关键字 [C]"
  - "if 关键字 [C]"
  - "if 关键字 [C], if 语句语法"
  - "嵌套语句"
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# if 语句 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**if** 语句控制条件分支。  如果表达式的值不为零，则执行 **if** 语句体。  **if** 语句的语法有两种形式。  
  
## 语法  
 *selection\-statement*:  
 **if \(**  *expression*  **\)**  *statement*  
  
 **if \(**  *expression*  **\)**  *statement*  **else**  *statement*  
  
 在两种形式的 **if** 语句中，将计算可具有结构之外的任何值的表达式（包括所有副作用）。  
  
 在第一种形式的语法中，如果 *expression* 为 true（非零），则执行 *statement*。  如果 *expression* 为 false，则忽略 *statement*。  在第二种形式的语法（使用了 **else**）中，如果 *expression* 为 false，则执行第二个 *statement*。  对于这两种形式，除非其中一个语句包含 **break**、**continue** 或 `goto`，否则控制随后会从程序中的 **if** 语句传递到的下一语句。  
  
 下面是 **if** 语句的示例：  
  
```  
if ( i > 0 )  
    y = x / i;  
else   
{  
    x = i;  
    y = f( x );  
}  
```  
  
 在此示例中，如果 `i` 大于 0，则执行 `y = x/i;` 语句。  如果 `i` 小于或等于 0，则将 `i` 赋给 `x`，并将 `f( x )` 赋给 `y`。  请注意，构成 **if** 子句的语句将以分号结尾。  
  
 嵌套 **if** 语句和 **else** 子句时，请使用大括号将语句和子句分组到可阐名您的意图的复合语句中。  如果大括号不存在，则编译器会通过将每个 **else** 与没有 **else** 的最近的 **if** 关联来解决二义性。  
  
```  
if ( i > 0 )           /* Without braces */  
    if ( j > i )  
        x = j;  
    else  
        x = i;  
```  
  
 在本示例中，**else** 子句与内部 **if** 语句关联。  如果 `i` 小于或等于 0，则不会将任何值赋给 `x`。  
  
```  
if ( i > 0 )   
{                      /* With braces */  
    if ( j > i )  
        x = j;  
}  
else  
    x = i;  
```  
  
 此示例中的内部 **if** 语句两边的大括号使 **else** 子句成为外部 **if** 语句的一部分。  如果 `i` 小于或等于 0，则将 `i` 赋给 `x`。  
  
## 请参阅  
 [if\-else 语句 \(C\+\+\)](../cpp/if-else-statement-cpp.md)