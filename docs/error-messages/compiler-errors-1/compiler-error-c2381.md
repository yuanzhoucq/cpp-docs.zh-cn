---
title: "编译器错误 C2381 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2381"
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 重定义；\_\_declspec\(noreturn\) 不同  
  
 声明并定义了函数，但定义使用的是 [noreturn](../../cpp/noreturn.md) `__declspec` 修饰符。  `noreturn` 的使用构成该函数的重定义；声明和定义需要遵守 `noreturn` 的用法。  
  
 下面的示例生成 C2381：  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```