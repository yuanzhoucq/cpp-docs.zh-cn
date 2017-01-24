---
title: "编译器错误 C2694 | Microsoft Docs"
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
  - "C2694"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2694"
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2694
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“override”: 重写虚函数的限制性异常规范比基类虚成员函数“base”少  
  
 虚函数已被重写，但在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，重写的函数具有限制性较少的[异常规范](../../cpp/exception-specifications-throw-cpp.md)。  
  
 下面的示例生成 C2694：  
  
```  
// C2694.cpp  
// compile with: /Za /c  
class MyBase {  
public:  
   virtual void f(void) throw(int) {  
   }  
};  
  
class Derived : public MyBase {  
public:  
   void f(void) throw(...) {}   // C2694  
   void f2(void) throw(int) {}   // OK  
};  
```