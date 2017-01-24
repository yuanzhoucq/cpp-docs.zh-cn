---
title: "编译器警告（等级 4）C4127 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4127"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4127"
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4127
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

条件表达式是常量  
  
 某个 `if` 语句或 `while` 循环的控制表达式的计算结果为常量。 如果 `while` 循环的控制表达式是常量，因为循环将在中间退出，请考虑用 `for` 循环替换 `while` 循环。 可以省略 `for` 循环的初始化、终止测试和循环增量，这会导致无限循环（如 `while(1)`），你可以从 `for` 语句的正文中退出循环。  
  
 以下示例生成 C4127：  
  
```  
// C4127.cpp // compile with: /W4 #include <stdio.h> int main() { if (1 == 1) {}   // C4127 while (1) { break; }   // C4127 // OK for ( ; ; ) { printf("test\n"); break; } }  
```