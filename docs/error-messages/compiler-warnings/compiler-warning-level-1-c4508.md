---
title: "编译器警告（等级 1）C4508 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4508"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4508"
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4508
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数应返回一个值；假定“void”返回类型  
  
 函数没有指定返回类型。  在此情况下，也应激发 C4430，且编译器实现 C4430 报告的修复（默认值为 int）。  
  
 若要解决此警告，请显式声明函数的返回类型。  
  
 下面的示例生成 C4508：  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```