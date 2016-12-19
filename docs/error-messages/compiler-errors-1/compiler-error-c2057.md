---
title: "编译器错误 C2057 | Microsoft Docs"
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
  - "C2057"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2057"
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2057
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应输入常量表达式  
  
 该上下文要求输入常数表达式，即其值在编译时已知的表达式。  
  
 编译器在编译时必须知道类型的大小，以便为该类型的实例分配空间。  
  
## 示例  
 下面的示例生成 C2057，并演示如何修复此错误：  
  
```  
// C2057.cpp  
int i;  
int b[i];   // C2057 - value of i is unknown at compile time  
int main() {  
   const int i = 8;  
   int b[i]; // OK - value of i is fixed and known to compiler  
}  
```  
  
## 示例  
 C 对常数表达式有限制性更强的规则。  下面的示例生成 C2057，并演示如何修复此错误：  
  
```  
// C2057b.c  
#define ArraySize1 10  
int main() {   
   const int ArraySize2 = 10;   
   int h[ArraySize2];   // C2057 - C does not allow variables here  
   int h[ArraySize1];   // OK - uses preprocessor constant  
}  
```