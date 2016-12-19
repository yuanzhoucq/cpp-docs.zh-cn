---
title: "编译器错误 C2675 | Microsoft Docs"
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
  - "C2675"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2675"
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2675
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一元“operator”:“type”不定义该运算符或到预定义运算符可接受的类型的转换  
  
 如果使用一元运算符，并且类型不定义运算符或到预定义运算符可接受的类型的转换，也会发生 C2675。  若要使用该运算符，必须针对指定类型将其重载，或者定义一个到某个类型（该运算符已针对此类型进行了定义）的转换。  
  
## 示例  
 下面的示例生成 C2675。  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```