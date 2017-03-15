---
title: "编译器警告（等级 2）C4250 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4250"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4250"
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器警告（等级 2）C4250
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class1”: 通过域控制继承“class2::member”  
  
 两个或更多的成员同名。  `class2` 中的成员是继承的成员，因为该类是包含该成员的其他类的基类。  
  
 若要禁止 C4250，请使用 [警告](../../preprocessor/warning.md) 杂注。  
  
 因为虚拟基类在多个派生类间共享，因此派生类中的名称决定基类中的名称。  例如，假定存在以下类层次结构，在菱形内有两个继承 func 的定义：通过弱类继承的 vbc::func\(\) 实例和通过主导类继承的 dominant::func\(\)。  通过菱形类对象继承的非限定 func\(\) 调用始终调用 dominate::func\(\) 实例。如果弱类要引入 func\(\) 实例，这两个定义都不起主控作用，而调用则被标记为不明确。  
  
```  
// C4250.cpp  
// compile with: /c /W2  
#include <stdio.h>  
struct vbc {  
   virtual void func() { printf("vbc::func\n"); }  
};  
  
struct weak : public virtual vbc {};  
  
struct dominant : public virtual vbc {  
   void func() { printf("dominant::func\n"); }  
};  
  
struct diamond : public weak, public dominant {};  
  
int main() {  
   diamond d;  
   d.func();   // C4250  
}  
```  
  
## 示例  
 下面的示例生成 C4250。  
  
```  
// C4250_b.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
class A {  
public:  
   virtual operator int () {  
      return 2;  
   }  
};  
  
class B : virtual public A {  
public:  
   virtual operator int () {  
      return 3;  
   }  
};  
  
class C : virtual public A {};  
  
class E : public B, public C {};   // C4250  
  
int main() {  
   E eObject;  
   cout << eObject.operator int() << endl;  
}  
```  
  
## 示例  
 此示例演示更为复杂的情况。  下面的示例生成 C4250。  
  
```  
// C4250_c.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
  
class V {  
public:  
   virtual int f() {  
      return 1024;  
   }  
};  
  
class B : virtual public V {  
public:  
   int b() {  
      return f(); // B::b() calls V::f()  
   }  
};  
  
class M : virtual public V {  
public:  
   int f() {  
      return 7;  
   }  
};  
  
// because of dominance, f() is M::f() inside D,  
// changing the meaning of B::b's f() call inside a D  
class D : public B, public M {};   // C4250  
  
int main() {  
   D d;  
   cout << "value is: " << d.b();   // invokes M::f()  
}  
```