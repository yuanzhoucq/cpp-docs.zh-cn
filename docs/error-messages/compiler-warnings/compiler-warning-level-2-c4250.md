---
title: 编译器警告（等级 2）C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: e0feb1cb7131b4388c87213a85ff1c921f636e1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162031"
---
# <a name="compiler-warning-level-2-c4250"></a>编译器警告（等级 2）C4250

"class1"：通过控制继承 "class2：： member"

两个或多个成员具有相同的名称。 `class2` 中的一个是继承的，因为它是包含此成员的其他类的基类。

若要取消 C4250，请使用[警告](../../preprocessor/warning.md)杂注。

由于虚拟基类在多个派生类之间共享，因此派生类中的名称支配基类中的名称。 例如，假设有以下类层次结构，则在菱形中继承了两个 func 定义： vbc：： func （）实例通过弱类，并通过主导类实现了主导：： func （）。 通过菱形类对象的 func （）的非限定调用始终调用主导：： func （）实例。  如果弱类要引入 func （）的实例，则这两个定义都不会成为主导的，并且调用会被标记为不明确。

```cpp
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

```cpp
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

此示例显示了更复杂的情况。 下面的示例生成 C4250。

```cpp
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
