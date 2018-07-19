---
title: 编译器错误 C2247 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed27398ea1f51ccc2ef0d3339446b422c7a503c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172308"
---
# <a name="compiler-error-c2247"></a>编译器错误 C2247
identifier 无法访问，因为 class 使用 specifier 继承 class  
  
 `identifier` 是从声明具有私有或受保护的访问权限的类继承。  
  
 下面的示例生成 C2247:  
  
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
  
 此错误还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作： 访问控制与受保护的成员。 仅可以通过从它 (n) 是其成员的类 (A) 继承的类 (B) 的成员函数的访问受保护的成员 (n)。  
  
 对于 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的代码，声明为友元的类型的成员。 此外可以使用公共继承。  
  
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
  
 C2247 还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作： 专用的基本类现在无法访问。 是一种类型的私有基类的类 (A) （B） 不应访问的类型 （C） B 用作基类。  
  
 对于 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的代码，请使用范围运算符。  
  
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