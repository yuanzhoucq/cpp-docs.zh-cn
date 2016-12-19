---
title: "编译器警告（等级 4）C4764 | Microsoft Docs"
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
  - "C4764"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4764"
ms.assetid: 7bd4296f-966b-484c-bf73-8dbc8e85b4a9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4764
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法对齐大于 16 个字节的捕获对象  
  
 指定了大于 16 字节的对齐，但是在某些平台上，如果函数引发异常，堆栈将强制实现不大于 16 字节的对齐。  
  
## 示例  
 下面的示例生成 C4764：  
  
```  
// C4764.cpp // compile with: /W4 /EHsc // processor: x64 IPF #include <stdio.h> class A { public: int x; }; typedef __declspec(align(32)) A ALIGNEDA; int main() { ALIGNEDA a; try { a.x = 15; throw a; } catch (ALIGNEDA b) // can’t align b to > 16 bytes { printf_s("%d\n", b.x); } }   // C4764  
```