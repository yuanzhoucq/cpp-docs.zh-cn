---
title: "编译器错误 C2563 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2563"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2563"
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2563
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在形参表中不匹配  
  
 函数的形参表（或指向函数的指针）与另一个函数的形参表（或指向成员函数的指针）不匹配。  因此，无法进行函数或指针的分配。  
  
 下面的示例生成 C2563：  
  
```  
// C2563.cpp  
void func( int );  
void func( int, int );  
int main() {  
   void *fp();  
   fp = func;   // C2563  
}  
```