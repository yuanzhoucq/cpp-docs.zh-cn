---
title: "编译器错误 C3203 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3203"
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C3203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“类型”：未专用化的类模板或泛型不能用作模板或模板的泛型参数或泛型参数“param”，应为 real 类型  
  
 你传递了一个无效的参数到类模板或泛型。  类模板或泛型需要一种类型作为参数。  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作可以导致此错误：专用的类模板不能用作基类列表中的模板参数。  若要解决 C3203，则当将模板类型参数用作基类列表中的模板参数时，将其显式添加到模板类名称。  
  
```  
// C3203.cpp  
template< typename T >  
struct X {  
   void f(X) {}  
};  
  
template< typename T >  
struct Y : public X<Y> {   // C3203  
// try the following line instead  
// struct Y : public X<Y<T> > {  
   void f(Y) {}  
};  
  
int main() {  
   Y<int> y;  
}  
```  
  
 以下示例将生成 C3203，并演示如何修复此错误：  
  
```  
// C3203_b.cpp  
// compile with: /c  
template <class T>  
struct S1 {};  
  
template <class T>  
class C1 {};  
  
typedef C1<S1> MyC1;   // C3203  
  
// OK  
template <template <class> class T>  
class C2 {};  
  
typedef C2<S1> MyC1;  
  
template <class T>  
class C3 {};  
  
typedef C3<S1<int> > MyC12;  
```  
  
 当使用泛型时，也可能发生 C3203：  
  
```  
// C3203_c.cpp  
// compile with: /clr /c  
generic <class T>  
value struct GS1 {};  
  
generic <class T>  
value struct GC1 {};  
  
typedef GC1<GS1> MyGC1;   // C3203  
typedef GC1<GS1<int> > MyGC2;   // OK  
```