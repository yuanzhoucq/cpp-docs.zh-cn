---
title: 微不足道，标准布局、 POD 和文本类型 |Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9bb4a84b42cadeb2e076548a220725f1e867fe9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099692"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>微不足道，标准布局、 POD 和文本类型

术语*布局*指的是类、 结构或联合类型的对象的成员在内存中的排列方式。 在某些情况下，布局是有明确定义语言规范。 但如果类或结构包含某些 C++ 语言功能，如虚拟基类、 虚函数、 具有不同的访问控制的成员，则编译器将随意选择布局。 该布局可能会有所不同，具体取决于正在执行哪些优化，并在许多情况下对象可能不甚至占用内存的相邻区域。 例如，如果类具有虚函数，该类的所有实例可能会都共享的单个虚拟函数表。 此类类型当然非常有用，但它们也有限制。 因为布局是不确定它们不能将它传递到 C，等其他语言编写的程序，因为它们可能会不连续它们无法可靠地复制与快速低级别函数如`memcopy`或通过网络序列化。

若要启用编译器，以及 C++ 程序和有关任何给定的类型的适用性取决于特定内存布局的操作的原因的 metaprograms，C++ 14 中引入的简单的类和结构的三个类别：*普通*，*标准布局*，和*POD*或纯旧数据。 标准库具有函数模板`is_trivial<T>`，`is_standard_layout<T>`和`is_pod<T>`来确定给定的类型是否属于给定的类别。

## <a name="trivial-types"></a>普通类型

当类或结构在 C++ 编译器提供或显式默认设置特殊成员函数，则它是常用类型。 它占用的连续内存区域。 它可以具有不同的访问说明符的成员。 在 C++，编译器可以自由地选择成员排序在此情况下的方式。 因此，你可以 memcopy 此类对象，但不能从 C 程序中可靠地使用这些。 可以复制到的 char 或无符号的 char 数组并安全地复制回到 T 变量普通类型 T。 请注意，由于对齐需求、 类型成员之间可能存在填充字节。

简单类型具有普通的默认构造函数、 普通复制构造函数、 普通复制赋值运算符和普通析构函数。 每种情况下，*普通*意味着构造函数/运算符/析构函数不是用户提供，属于具有类

- 没有虚函数或虚拟基类

- 没有基类与相应非普通构造函数/运算符/析构函数

- 没有数据成员的类类型的相应非普通构造函数/运算符/析构函数

以下示例演示简单类型。 在 Trivial2，是否存在`Trivial2(int a, int b)`构造函数要求您提供默认构造函数。 对于才会被视为简单类型，您必须显式设置默认的构造函数。

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

当类或结构不包含某些 C++ 语言功能，如在 C 语言中，找不到的虚拟函数，并且所有成员都具有相同的访问控制时，这是标准布局类型。 Memcopy 可以和布局充分定义可以由 C 程序使用它。 标准布局类型可以具有用户定义的特殊成员函数。 此外，标准布局类型具有以下特征：

- 没有虚函数或虚拟基类

- 所有非静态数据成员都具有相同的访问控制

- 类类型的所有非静态成员均为标准布局

- 任何基类都是标准布局

- 具有与第一个非静态数据成员相同的类型没有基类。

- 满足这些条件之一：

  - 与非静态数据成员的派生程度最高的类和多个基类中没有非静态数据成员或

  - 具有与非静态数据成员没有基类

下面的代码演示标准布局类型的一个示例：

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

最后两个要求可能是可以更好地说明代码中。 即使在下一步的示例中，基数是标准布局`Derived`不是标准布局，因为这两个 it （派生程度最高的类） 和`Base`具有非静态数据成员：

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

在此示例中`Derived`是标准布局，因为`Base`没有非静态数据成员：

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

派生也是标准布局如果`Base`有的数据成员和`Derived`必须只有成员函数。

## <a name="pod-types"></a>POD 类型

类或结构，普通和标准布局时，POD （纯旧数据） 类型。 POD 类型的内存布局因此是连续和每个成员都有较高的地址不是可以对这些类型执行的以便复制字节之前，声明的成员和二进制 I/O。  标量类型，如 int 也是 POD 类型。 是类的 POD 类型可以作为非静态数据成员具有仅 POD 类型。

## <a name="example"></a>示例

下面的示例演示微不足道，标准布局之间的区别和 POD 类型：

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

## <a name="see-also"></a>请参阅

[基本概念](../cpp/basic-concepts-cpp.md)