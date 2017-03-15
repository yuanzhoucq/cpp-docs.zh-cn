---
title: "编译器错误 C3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3190"
ms.assetid: 7c701afa-85a7-4f7a-8881-0662436ac244
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有提供的模板参数的“instantiation”不是“type”的任何成员函数的显式实例化  
  
 编译器检测出尝试进行显式函数实例化；但是，提供的类型参数不与任何的可能函数匹配。  
  
 下面的示例生成 C3190：  
  
```  
// C3190.cpp  
// compile with: /LD  
template<class T>  
struct A {  
   A(int x = 0) {  
   }  
   A(int x, int y) {  
   }  
};  
  
template A<float>::A();   // C3190  
// try the following line instead  
// template A<int>::A(int);  
  
struct Y {  
   template<class T> void f(T);  
};  
  
template<class T> void Y::f(T) { }  
  
template void Y::f(int,int);   // C3190  
  
template<class OT> class X {  
   template<class T> void f2(T,OT);  
};  
  
template<class OT> template<class T> void X<OT>::f2(T,OT) {}  
  
template void X<float>::f2<int>(int,char);   // C3190  
// try one of the following lines instead  
// template void X<char>::f2(int, char);  
// template void X<char>::f2<int>(int,char);  
// template void X<char>::f2<>(int,char);  
```