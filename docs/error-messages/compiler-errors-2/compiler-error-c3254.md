---
title: "编译器错误 C3254 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3254"
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“explicit override”: 类包含显式重写“override”，但并不从包含函数声明的接口派生  
  
 当[显式重写](../../cpp/explicit-overrides-cpp.md)（显式重写）方法时，包含该重写的类必须直接或间接从包含您要重写的函数的类型派生。  
  
 下面的示例生成 C3254：  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```