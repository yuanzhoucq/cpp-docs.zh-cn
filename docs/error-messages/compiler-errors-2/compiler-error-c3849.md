---
title: "编译器错误 C3849 | Microsoft Docs"
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
  - "C3849"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3849"
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3849
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型“type”的表达式中的函数样式调用会丢失所有 number 个可用运算符重载的 const 和\/或 volatile 限定符  
  
 具有指定的 const\-volatile 类型的变量只能调用使用相同或更大的 const\-volatile 限定定义的函数。  
  
 若要修复此错误，请提供一个适当的成员函数。  当转换导致丢失限定时，不能对常数或易失性限定对象执行转换。  您可以获得限定符，但不能在转换中丢失限定符。  
  
 下面的示例生成 C3849：  
  
```  
// C3849.cpp  
void glbFunc3(int i, char c)  
{  
   i;  
}  
typedef void (* pFunc3)(int, char);  
  
void glbFunc2(int i)  
{  
   i;  
}  
  
typedef void (* pFunc2)(int);  
  
void glbFunc1()  
{  
}  
typedef void (* pFunc1)();  
  
struct S4  
{  
   operator ()(int i)  
   {  
      i;  
   }  
  
   operator pFunc1() const  
   {  
      return &glbFunc1;  
   }  
  
   operator pFunc2() volatile  
   {  
      return &glbFunc2;  
   }  
  
   operator pFunc3()  
   {  
      return &glbFunc3;  
   }  
  
   // operator pFunc1() const volatile  
   // {  
   //    return &glbFunc1;  
   // }  
};  
  
int main()  
{  
   // Cannot call any of the 4 overloads of "operator ()(.....)" and   
   // "operator pFunc()" because none is declared as "const volatile"  
   const volatile S4 s4;  // can only call cv member functions of S4  
   s4();   // C3849 to resolve, uncomment member function  
}  
```