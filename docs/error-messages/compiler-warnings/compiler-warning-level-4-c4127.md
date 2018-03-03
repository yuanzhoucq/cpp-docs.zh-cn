---
title: "编译器警告 （等级 4） C4127 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1a5bbd86b6197907f043478df225dceb79679f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4127"></a>编译器警告（等级 4）C4127
条件表达式是常量  
  
 某个 `if` 语句或 `while` 循环的控制表达式的计算结果为常量。 由于其常见惯例用法，如 1 普通常量或`true`不触发此警告，除非它们是在表达式中的操作的结果。 如果的控制表达式的`while`循环是常量，因为在中间退出循环，请考虑替换`while`循环`for`循环。 可以省略的初始化、 终止测试和循环增量`for`循环，这会导致循环是无限的就像`while(1)`，并可以从的正文中退出循环`for`语句。  
  
 下面的示例演示两种方式 C4127 生成的并演示如何使用 for 循环以避免此警告：  
  
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