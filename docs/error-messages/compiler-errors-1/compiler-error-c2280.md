---
title: 编译器错误 C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 9ee5b8105241ee347812a0dcc083a4f1cc7dca49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208403"
---
# <a name="compiler-error-c2280"></a>编译器错误 C2280

"*声明*"：尝试引用已删除的函数

编译器检测到引用函数的尝试 `deleted` 。 此错误的原因可能是调用了在源代码中显式标记为的成员函数 `= deleted` 。 此错误还可能由编译器调用自动声明并标记为的结构或类的隐式特殊成员函数引起 `deleted` 。 有关编译器自动生成或特殊成员函数的时间的详细信息 **`default`** `deleted` ，请参阅[特殊成员函数](../../cpp/special-member-functions.md)。

## <a name="example-explicitly-deleted-functions"></a>示例：显式删除的函数

调用显式 `deleted` 函数会导致此错误。 显式 `deleted` 成员函数意味着该类或结构特意设计为防止其使用，因此，若要解决此问题，应更改代码以避免此问题。

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

## <a name="example-uninitialized-data-members"></a>示例：未初始化的数据成员

未初始化的引用类型数据成员或 **`const`** 数据成员将导致编译器隐式声明 `deleted` 默认构造函数。 若要解决此问题，请在声明数据成员时对其进行初始化。

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

## <a name="example-reference-and-const-data-members"></a>示例： Reference 和 const 数据成员

**`const`** 或引用类型的数据成员导致编译器声明 `deleted` 复制赋值运算符。 初始化后，不能将这些成员分配到，因此无法使用简单的复制或移动操作。 若要解决此问题，我们建议您更改逻辑以删除导致错误的赋值运算。

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

## <a name="example-movable-deletes-implicit-copy"></a>示例：可移动删除隐式复制

如果类声明了移动构造函数或移动赋值运算符，但没有显式声明复制构造函数，则编译器会隐式声明一个复制构造函数，并将其定义为 `deleted` 。 同样，如果某个类声明了移动构造函数或移动赋值运算符，但没有显式声明复制赋值运算符，则编译器会隐式声明一个复制赋值运算符，并将其定义为 `deleted` 。 若要解决此问题，必须显式声明这些成员。

当你看到 "将错误 C2280 与 a 连接 `unique_ptr` " 时，几乎肯定是因为你尝试调用其复制构造函数，该构造函数是一个 `deleted` 函数。 按照设计， `unique_ptr` 无法复制。 改为使用移动构造函数转移所有权。

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

## <a name="example-variant-and-volatile-members"></a>示例： Variant 和 volatile 成员

Visual Studio 2015 Update 2 之前的编译器版本是不一致的，并且生成了匿名联合的默认构造函数和析构函数。 它们现在隐式声明为 `deleted` 。 这些版本还允许 **`default`** **`default`** 在具有成员变量的类和结构中进行复制和移动构造函数的非一致性隐式定义，以及复制和移动赋值运算符 **`volatile`** 。 编译器现在将其视为具有不重要的构造函数和赋值运算符，并且不生成 **`default`** 实现。 如果此类是联合的成员或类内的匿名联合，则联合或类的复制和移动构造函数和复制和移动赋值运算符将隐式定义为 `deleted` 。 若要解决此问题，必须显式声明必需的特殊成员函数。

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

## <a name="example-indirect-base-members-deleted"></a>示例：已删除的间接基成员

Visual Studio 2015 Update 2 之前的编译器版本不一致，并且允许派生类调用间接派生基类的特殊成员函数 `private virtual` 。 发出此类调用时，编译器现在会发出编译器错误 C2280。

在此示例中，类 `top` 间接派生自私有虚拟 `base` 。 在一致的代码中，这使得的成员无法 `base` 访问 `top` ; 无法对类型的对象 `top` 进行默认构造或销毁。 若要在依赖旧编译器行为的代码中解决此问题，请将中间类更改为使用 `protected virtual` 派生，或将 `top` 类更改为使用直接派生：

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
