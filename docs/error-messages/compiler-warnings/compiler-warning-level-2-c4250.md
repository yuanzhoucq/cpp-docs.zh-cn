---
title: "编译器警告 （等级 2） C4250 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4250
dev_langs: C++
helpviewer_keywords: C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d92a337e3ded4b958bb9d1dbb7359d21f28d619c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4250"></a>编译器警告（等级 2）C4250
class1： 继承 class2::member 通过域控制  
  
 两个或多个成员具有相同的名称。 中的一个`class2`因为它是包含此成员的其他类的基类继承。  
  
 若要禁止 C4250，请使用[警告](../../preprocessor/warning.md)杂注。  
  
 虚拟基类多个派生类之间共享的因为派生类中的名称可控制在基类中的名称。 例如，给定以下类层次结构，有两个定义的在菱形中继承的 func： 通过弱的类中和大多数:: func() 通过主导类 vbc::func() 实例。 通过菱形类对象，func() 的非限定的调用始终调用主要:: func() 实例。  如果弱类引入 func() 的实例，既不定义将控制，并调用将会被标记为不明确。  
  
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
  
## <a name="example"></a>示例  
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
  
## <a name="example"></a>示例  
 此示例演示更复杂的情况。 下面的示例生成 C4250。  
  
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