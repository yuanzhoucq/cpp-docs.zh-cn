---
title: "编译器错误 C2450 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2450"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2450"
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2450
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”类型的 switch 表达式是非法的  
  
 `switch` 表达式计算为无效类型。  它必须计算为 integer 类型，或具有到 integer 类型的明确转换的类类型。  如果它计算为用户定义的类型，则必须提供转换运算符。  
  
 下面的示例生成 C2450：  
  
```  
// C2450.cpp  
class X {  
public:  
   int i;  
} x;  
  
class Y {  
public:  
   int i;  
   operator int() { return i; }   // conversion operator  
} y;  
  
int main() {  
   int j = 1;  
   switch ( x ) {   // C2450, x is not type int  
   // try the following line instead  
   // switch ( y ) {  
      default:  ;  
   }  
}  
```