---
title: "编译器错误 C2512 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2512
dev_langs: C++
helpviewer_keywords: C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63090bc7dac08aa87bcd68e77c076185176a7285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2512"></a>编译器错误 C2512
“identifier”：没有合适的默认构造函数可用  
  
 指定的类、结构或联合没有可用的默认构造函数。 只有在未提供用户定义的构造函数的情况下，编译器才会提供默认构造函数。  
  
 如果你提供一个使用非 void 参数的构造函数，但你想让类在没有参数的情况下创建（例如，创建为数组元素），那么还必须提供一个默认构造函数。 默认构造函数可以是一个所有参数都使用默认值的构造函数。  
  
 下面的示例生成 C2512，并演示如何修复此错误：  
  
```  
// C2512.cpp  
// C2512 expected  
struct B {  
   B (char *);  
   // Uncomment the following line to fix.  
   // B() {};  
};  
  
int main() {  
   B b;   
}  
```  
  
 下面的示例演示具有更细微差异的 C2512。 要修复此错误，请将代码重新排列为在引用类的构造函数之前定义该类：  
  
```  
// C2512b.cpp  
// compile with: /c  
struct S {  
   struct X;  
  
   void f() {  
      X *x = new X();   // C2512 X not defined yet  
   }  
  
};  
  
struct S::X {};  
  
struct T {  
   struct X;  
   void f();  
};  
  
struct T::X {};  
  
void T::f() {  
   X *x = new X();  
}  
```  
  
 调用包含常量或引用数据成员的类的默认构造函数也有可能导致 C2512。 这些成员必须在构造函数初始值设定项列表中初始化，从而导致编译器无法生成默认构造函数。  
  
 下面的示例生成 C2512，并演示如何修复此错误：  
  
```  
// C2512c.cpp  
// Compile by using: cl /c /W3 C2512c.cpp  
struct S {  
   const int i_;  
   int &r_;   
};   
  
int SumS() {  
   const int ci = 7;  
   int ir = 42;  
  
   S s1; // C2512 - no default constructor available  
   S s2{ci, ir};  // Fix - initialize const and reference members   
   return s2.i_ + s2.r_;  
}  
```