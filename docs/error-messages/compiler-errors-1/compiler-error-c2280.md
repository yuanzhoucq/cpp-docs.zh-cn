---
title: 编译器错误 C2280 |Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
dev_langs:
- C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b401ba3755113a71dd401efa8da1fe46adfe6a45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108661"
---
# <a name="compiler-error-c2280"></a>编译器错误 C2280

'*声明*： 尝试引用已删除的函数

编译器检测到尝试引用`deleted`函数。 此错误可能引起对显式标记为成员函数的调用`= deleted`的源代码中。 此错误还可能引起对结构或类，该类是自动声明并标记为的隐式的特殊成员函数的调用`deleted`编译器。 有关编译器自动生成详细信息`default`或`deleted`特殊成员函数，请参阅[特殊成员函数](../../cpp/special-member-functions.md)。

## <a name="example-explicitly-deleted-functions"></a>示例： 显式删除函数

调用显式`deleted`函数会导致此错误。 显式`deleted`成员函数表示类或结构有意设计是为了防止其使用，因此，若要解决此问题，则应更改代码时，避免它。

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>示例： 未初始化的数据成员

未初始化的引用类型的数据成员或`const`数据成员将使编译器隐式声明`deleted`默认构造函数。 若要解决此问题，请声明时初始化数据成员。

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>示例： 引用和 const 数据成员

一个`const`或引用类型的数据成员将使编译器声明`deleted`复制赋值运算符。 初始化后，这些成员不能分配到，因此，简单的复制或移动不能正常运行。 若要解决此问题，我们建议您更改自己的逻辑来删除导致错误的赋值操作。

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>示例： 可移动删除隐式的副本

如果一个类声明了移动构造函数或移动赋值运算符，但未显式声明复制构造函数，编译器隐式声明复制构造函数，其定义为`deleted`。 同样，如果一个类声明了移动构造函数或移动赋值运算符，但未显式声明复制赋值运算符，编译器隐式声明复制赋值运算符和其定义为`deleted`。 若要解决此问题，必须显式声明这些成员。

当看到门户中的错误 C2280 `unique_ptr`，它几乎可以肯定是因为你尝试调用其复制构造函数，这是`deleted`函数。 根据设计，`unique_ptr`无法复制。 使用移动构造函数以改为转让所有权。

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>示例： 变体和易失性成员

Visual Studio 2015 Update 2 之前的编译器版本是不符合要求和生成默认构造函数和匿名联合的析构函数。 这些现在隐式声明为`deleted`。 这些版本还允许使用的不符合要求的隐式定义`default`复制和移动构造函数和`default`复制和移动赋值运算符中类和结构具有`volatile`成员变量。 编译器现在会考虑这些具有非普通构造函数和赋值运算符，不会生成`default`实现。 如果这样的类，联合或在类内部匿名联合的成员的复制和移动构造函数和联合或类的复制和移动赋值运算符隐式定义为`deleted`。 若要解决此问题，必须显式声明所需的特殊成员函数。

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>删除示例： 间接基成员

Visual Studio 2015 Update 2 之前的编译器版本是不符合要求和允许派生的类调用的特殊成员函数的间接派生`private virtual`基类。 当进行此类调用时，编译器现将发出编译器错误 C2280。

在此示例中，类`top`间接派生自专用虚拟`base`。 在符合标准代码中，这使得的成员`base`无法访问`top`; 类型的对象`top`不能为默认构造或销毁。 若要解决此问题在依赖旧的编译器行为的代码中，更改要使用的中间类`protected virtual`派生或更改`top`以使用直接派生的类：

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
