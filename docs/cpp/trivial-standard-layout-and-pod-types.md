---
title: 普通、标准布局、POD 和文本类型
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 2745302b3ebd7927e9d839e4661e884a2bd91042
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423704"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>普通、标准布局、POD 和文本类型

术语“布局”是指类、结构或联合类型的对象的成员在内存中的排列方式。 在某些情况下，布局由语言规范明确定义。 但是，当类或结构包含某些 C++ 语言功能（如虚拟基类、虚拟函数、具有不同访问控制的成员）时，编译器可以自由选择布局。 该布局可能会基于正在执行的优化而有所不同，并且在许多情况下，该对象甚至可能不会占用连续内存区域。 例如，如果某个类具有虚拟函数，则该类的所有实例可能会共享单个虚拟函数表。 此类型非常有用，但它们也有限制。 由于布局未定义，因此无法将其传递到使用其他语言（例如 C）编写的程序，并且由于它们可能是非连续的，因此无法使用快速低级函数（例如 `memcopy`）对其进行可靠复制，或者通过网络对其进行序列化。

为使编译器以及 C++ 程序和元程序能够推断出任何给定类型对于依赖于特定内存布局的操作的适用性，C++14 引入了三种类别的简单类和结构：普通、标准布局和 POD（或简单旧数据）。 标准库具有函数模板 `is_trivial<T>`、`is_standard_layout<T>` 和 `is_pod<T>`，这些模板可以确定某一给定类型是否属于某一给定类别。

## <a name="trivial-types"></a>普通类型

当 C++ 中的类或结构具有编译器提供的或显式默认设置的特殊成员函数时，该类或结构为普通类型。 它占用连续内存区域。 它可以具有含不同访问说明符的成员。 在 C++ 中，编译器可以自由选择在此情况下对成员排序的方式。 因此，你可以在内存中复制此类对象，但不能从 C 程序中可靠地使用它们。 可以将普通类型 T 复制到 char 或无符号 char 数组，并安全地复制回 T 变量。 请注意，由于对齐要求，类型成员之间可能存在填充字节。

普通类型具有普通默认构造函数、普通复制构造函数、普通复制赋值运算符和普通析构函数。 在各种情况下，“普通”意味着构造函数/运算符/析构函数并非用户提供，并且属于存在以下情况的类

- 没有虚拟函数或虚拟基类，

- 没有具有相应非普通构造函数/运算符/析构函数的基类

- 没有具有相应非普通构造函数/运算符/析构函数的类类型的数据成员

以下示例演示普通类型。 在 Trivial2 中，`Trivial2(int a, int b)` 构造函数的存在要求提供默认构造函数。 对于符合普通资格的类型，必须显式默认设置该构造函数。

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>标准布局类型

当类或结构不包含某些 C++ 语言功能（例如无法在 C 语言中找到的虚拟函数），并且所有成员都具有相同的访问控制时，该类或结构为标准布局类型。 可以在内存中对其进行复制，并且布局已经过充分定义，可以由 C 程序使用。 标准布局类型可以具有用户定义的特殊成员函数。 此外，标准布局类型还具有以下特征：

- 没有虚拟函数或虚拟基类

- 所有非静态数据成员都具有相同的访问控制

- 类类型的所有非静态成员均为标准布局

- 所有基类都为标准布局

- 没有与第一个非静态数据成员类型相同的基类。

- 满足以下条件之一：

  - 最底层派生类中没有非静态数据成员，并且具有非静态数据成员的基类不超过一个，或者

  - 没有含非静态数据成员的基类

以下代码演示标准布局类型的一个示例：

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

可能使用代码能够更好地说明最后两个要求。 在下一个示例中，即使 Base 是标准布局，`Derived` 也不是标准布局，因为它（最底层派生类）和 `Base` 都具有非静态数据成员：

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

在此示例中，`Derived` 是标准布局，因为 `Base` 没有非静态数据成员：

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

如果 `Base` 具有数据成员，并且 `Derived` 仅具有成员函数，则 Derived 也是标准布局。

## <a name="pod-types"></a>POD 类型

当某一类或结构同时为普通和标准布局时，该类或结构为 POD（简单旧数据）类型。 因此，POD 类型的内存布局是连续的，并且每个成员的地址都比在其之前声明的成员要高，以便可以对这些类型执行逐字节复制和二进制 I/O。  标量类型（例如 int）也是 POD 类型。 作为类的 POD 类型只能具有作为非静态数据成员的 POD 类型。

## <a name="example"></a>示例

以下示例演示普通、标准布局和 POD 类型之间的区别：

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal_types"></a> 文本类型

文本类型是可在编译时确定其布局的类型。 以下均为文本类型：

- void
- 标量类型
- 引用
- Void、标量类型或引用的数组
- 具有普通析构函数以及一个或多个 constexpr 构造函数且不移动或复制构造函数的类。 此外，其所有非静态数据成员和基类必须是文本类型且不可变。

## <a name="see-also"></a>另请参阅

[基本概念](../cpp/basic-concepts-cpp.md)