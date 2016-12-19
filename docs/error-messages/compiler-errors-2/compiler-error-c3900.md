---
title: "编译器错误 C3900 | Microsoft Docs"
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
  - "C3900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3900"
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 不允许在当前范围中使用  
  
 属性块只能包含函数声明和内联函数定义。  在属性块中除了函数之外不允许使用其他成员。  不允许使用 typedef、运算符或友元函数。  有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  
  
 事件定义只能包含访问方法和函数。  
  
 下面的示例生成 C3900：  
  
```  
// C3900.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void set(int);   // OK  
      int i;   // C3900 variable declaration  
   };  
};  
```  
  
 下面的示例生成 C3900：  
  
```  
// C3900b.cpp  
// compile with: /clr  
using namespace System;  
delegate void H();  
ref class X {  
   event H^ E {  
      int m;   // C3900  
  
      // OK  
      void Test() {}  
  
      void add( H^ h ) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```