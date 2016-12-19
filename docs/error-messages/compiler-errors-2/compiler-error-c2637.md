---
title: "编译器错误 C2637 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2637"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2637"
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2637
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 无法修改指向数据成员的指针  
  
 指向数据成员的指针不能具有调用约定。  若要解决此问题，请移除调用约定或声明指向成员函数的指针。  
  
 下面的示例生成 C2637：  
  
```  
// C2637.cpp  
// compile with: /c  
struct S {};  
int __stdcall S::*pms1;   // C2637  
  
// OK  
int S::*pms2;  
int (__stdcall S::*pms3)(...);  
```