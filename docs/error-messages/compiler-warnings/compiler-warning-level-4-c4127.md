---
title: "编译器警告 （等级 4） C4127 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 3e9fb4ed25e51311ec4f6b1d71a249c21d466069
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4127"></a>编译器警告（等级 4）C4127
条件表达式是常量  
  
 某个 `if` 语句或 `while` 循环的控制表达式的计算结果为常量。 由于其常见惯例用法，如 1 普通常量或`true`不触发此警告，除非它们是在表达式中的操作的结果。 如果的控制表达式的`while`循环是常量，因为在中间退出循环，请考虑替换`while`循环`for`循环。 可以省略的初始化、 终止测试和循环增量`for`循环，这会导致循环是无限的就像`while(1)`，并可以从的正文中退出循环`for`语句。  
  
 下面的示例演示两种方式 C4127 生成的并演示如何使用 for 循环以避免此警告︰  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```
