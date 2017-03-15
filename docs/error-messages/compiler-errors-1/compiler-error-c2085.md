---
title: "编译器错误 C2085 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2085"
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 不在形参表中  
  
 该标识符在函数定义中声明而未在形参表中声明。（仅用于 ANSI C）  
  
 下面的示例生成 C2085：  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 可能的解决方案：  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 如果缺少分号，`func1()` 看起来就像是函数定义，而不是原型，所以 `main` 定义在 `func1()` 中，从而对标识符 `main` 生成错误 C2085。