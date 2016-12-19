---
title: "编译器错误 C2247 | Microsoft Docs"
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
  - "C2247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2247"
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”不可访问，因为“class”使用“specifier”来从“class”继承  
  
 `identifier` 是从用私有或受保护访问权声明的类继承的。  
  
 下面的示例生成 C2247：  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 也可能由于为 Visual Studio .NET 2003 进行的编译器一致性工作生成此错误：访问具有受保护成员的控件。  受保护成员 \(n\) 只能通过类 \(B\)（该类从 \(n\) 是其成员的类 \(A\) 继承）的成员函数访问。  
  
 为使代码在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，将成员声明为该类型的友元。  还可以使用公共继承。  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 为 Visual Studio .NET 2003 进行的编译器一致性工作也可能导致 C2247：私有基类现在不可访问。  是类型 \(B\) 的私有基类的类 \(A\) 对于使用 B 作为基类的类型 \(C\) 不应是可访问的。  
  
 为使代码在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，使用范围运算符。  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```