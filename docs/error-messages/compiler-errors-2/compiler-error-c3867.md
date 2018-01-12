---
title: "编译器错误 C3867 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3867
dev_langs: C++
helpviewer_keywords: C3867
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c5fdcdfed8393402d9514a286469d0cbe4f0e7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3867"></a>编译器错误 C3867
“func”: 函数调用缺少自变量列表；请使用“&func”创建指向成员的指针  
  
 你曾尝试在不使用成员函数的类名称和 address-of 运算符限定成员函数的情况下采用其地址。  
  
 此错误还可能来自于为 Visual C++ 2005 执行的编译器一致性工作：增强了指针到成员一致性。 使用 Visual C++ 2005 之前的版本编译的代码现在将生成 C3867。  
  
## <a name="example"></a>示例  
 C3867 可能会从带有误导性的建议解决方案的编译器发出。 如可能，请使用派生程度最高的类。  
  
 下面的示例生成 C3867，并演示如何修复此错误：  
  
```  
// C3867_1.cpp  
// compile with: /c  
struct Base {   
protected:   
   void Test() {}  
};  
  
class Derived : public Base {   
   virtual void Bar();  
};  
  
void Derived::Bar() {  
   void (Base::*p1)() = Test;   // C3867  
   &Derived::Test;   // OK  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3867，并演示如何修复此错误：  
  
```  
// C3867_2.cpp  
#include<stdio.h>  
  
struct S {  
   char *func() {  
      return "message";  
   }  
};  
  
class X {  
public:  
   void f() {}  
};  
  
int main() {  
   X::f;   // C3867  
  
   // OK  
   X * myX = new X;  
   myX->f();  
  
   S s;  
   printf_s("test %s", s.func);   // C3867  
   printf_s("test %s", s.func());   // OK  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3867，并演示如何修复此错误：  
  
```  
// C3867_3.cpp  
class X {  
public:  
   void mf(){}  
};  
  
int main() {  
   void (X::*pmf)() = X::mf;   // C3867  
  
   // try the following line instead  
   void (X::*pmf2)() = &X::mf;  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3867。  
  
```  
// C3867_4.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b1;  
      b1.p = f;   // C3867  
   }  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3867。  
  
```  
// C3867_5.cpp  
// compile with: /EHsc  
#include <iostream>  
  
class Testpm {  
public:  
   void m_func1() {  
      std::cout << m_num << "\tm_func1\n";   
    }  
  
   int m_num;  
   typedef void (Testpm::*pmfn1)();  
   void func(Testpm* p);  
};  
  
void Testpm::func(Testpm* p) {  
   pmfn1 s = m_func1;   // C3867  
   pmfn1 s2 = &Testpm::m_func1;   // OK  
   (p->*s2)();  
}  
  
int main() {  
   Testpm *pTestpm = new Testpm;  
   pTestpm->m_num = 10;  
  
   pTestpm->func(pTestpm);  
}  
```