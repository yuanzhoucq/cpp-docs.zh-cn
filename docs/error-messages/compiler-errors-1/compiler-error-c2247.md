---
title: 编译器错误 C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: ab1f83e2075128441cbffd2d939e3b99b45be4c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596425"
---
# <a name="compiler-error-c2247"></a>编译器错误 C2247

identifier 不可访问，因为 class 使用 specifier 继承 class

`identifier` 从声明为具有私有或受保护的访问权限的类继承。

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

此外可以为 Visual Studio.NET 2003年执行的编译器一致性工作生成此错误： 访问控制与受保护的成员。 仅可以通过类 (B) 继承的类 (A) (n) 的成员的成员函数的访问受保护的成员 (n)。

对于 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的代码，声明为友元类型的成员。 此外可以使用公共继承。

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

C2247 也生成为 Visual Studio.NET 2003年执行的编译器一致性工作： 现在无法访问私有基的类。 是一种类型的私有基类的类 (A) （B） 不应访问的类型 （C） 作为基类使用 B。

对于 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效的代码，使用范围运算符。

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