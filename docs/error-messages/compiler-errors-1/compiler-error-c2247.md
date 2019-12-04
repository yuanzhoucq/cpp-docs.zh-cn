---
title: 编译器错误 C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758900"
---
# <a name="compiler-error-c2247"></a>编译器错误 C2247

"identifier" 不可访问，因为 "class" 使用 "说明符" 继承自 "class"

`identifier` 继承自使用私有或受保护访问权限声明的类。

下面的示例生成 C2247：

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

对于 Visual Studio .NET 2003：具有受保护成员的访问控制，此错误也可能是由于编译器一致性工作而生成的。 受保护的成员（n）只能通过类的成员函数（B）进行访问，该类继承自类（n）是其成员的类（n）。

对于在 Visual Studio .NET 2003 和 visual Studio .NET 版本的视觉C++对象中都有效的代码，将成员声明为类型的友元。 还可以使用公共继承。

```cpp
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

对于 Visual Studio .NET 2003 的编译器一致性工作，还可以生成 C2247：现在无法访问私有基类。 作为类型（B）的私有基类的类（A）应不能访问使用 B 作为基类的类型（C）。

对于在 Visual Studio .NET 2003 和 visual Studio .NET 版本的视觉C++对象中都有效的代码，请使用 scope 运算符。

```cpp
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
