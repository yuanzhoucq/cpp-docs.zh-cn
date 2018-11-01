---
title: 编译器警告（等级 2）C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 8baf3c03c87dc70a80b785d7f81cbee4e1d828f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454855"
---
# <a name="compiler-warning-level-2-c4250"></a>编译器警告（等级 2）C4250

class1： 继承 class2::member 通过域控制

两个或多个成员具有相同的名称。 中的一个`class2`因为它是包含此成员的其他类的基类继承。

若要禁止 C4250，请使用[警告](../../preprocessor/warning.md)杂注。

因为在多个派生类之间共享虚拟基类，派生类中的名称决定在基类中的名称。 例如，给定以下类层次结构，有两个定义的菱形中可以继承 func： 通过弱类，并通过主导类基准:: func() vbc::func() 实例。 通过菱形类对象，func() 的非限定的调用始终调用主要:: func() 实例。  如果弱类要引入 func() 的实例，既不会控制定义，并且调用将会被标记为不明确。

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