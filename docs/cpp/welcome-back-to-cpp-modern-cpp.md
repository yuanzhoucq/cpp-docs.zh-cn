---
title: 欢迎返回C++ -新式C++
description: 介绍新式C++中的新编程惯例及其基本原理。
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 9630322024e639f9e5db1888dac5a1530befc716
ms.sourcegitcommit: ba129dc55dc3ff638f3af5ac0e87ec2ca1cb2674
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869716"
---
# <a name="welcome-back-to-c---modern-c"></a>欢迎返回C++ -新式C++

自从创建以来， C++已成为世界上最广泛使用的编程语言之一。 正确编写的 C++ 程序快速、高效。 语言比其他语言更加灵活：它可以在最高的抽象级别上运行，并在硅级别下运行。 C++提供高度优化的标准库。 它支持访问低级别硬件功能，最大限度地提高速度并最大程度地减少内存需求。 使用C++，你可以创建范围广泛的应用。 游戏、设备驱动程序和高性能科学软件。 嵌入的程序。 Windows 客户端应用程序。 甚至编写适用于其他编程语言的库和编译器C++。

C++ 的原始要求之一是与 C 语言向后兼容。 因此， C++始终允许 C 样式编程，其中包含原始指针、数组、以 null 结尾的字符串和其他功能。 它们可以实现良好的性能，但也可能会产生 bug 和复杂性。 的演变C++具有强调的功能，大大减少了使用 C 样式惯例的需求。 旧的 C 编程设施在您需要它们时存在，但对于新式C++的代码，您应该需要更少的代码。 新式C++代码更简单、更安全、更优雅，而且仍能像以往一样快速。

以下部分概述了新式C++的主要功能。 除非另有说明，否则此处列出的功能在 c + + 11 和更高版本中可用。 在 Microsoft C++编译器中，可以设置[/std](../build/reference/std-specify-language-standard-version.md)编译器选项，以指定要用于项目的标准版本。

## <a name="resources-and-smart-pointers"></a>资源和智能指针

C 样式编程中的一个主要错误类是*内存泄漏*。 泄漏通常是由于对使用**new**分配的内存调用**delete**失败引起的。 新式C++强调*资源获取的原则是初始化*（RAII）。 其原理很简单。 资源（堆内存、文件句柄、套接字等）应归对象*所有*。 该对象在其构造函数中创建或接收新分配的资源，并在其析构函数中将其删除。 RAII 原则保证当所属对象超出范围时，所有资源都能正确返回到操作系统。

为了支持简单采用 RAII 原则C++ ，标准库提供了三种智能指针类型： [std：： unique_ptr](../standard-library/unique-ptr-class.md)、 [std：： shared_ptr](../standard-library/shared-ptr-class.md)和[std：： weak_ptr](../standard-library/weak-ptr-class.md)。 智能指针处理其拥有的内存分配和删除操作。 下面的示例演示一个类，其中包含一个数组成员，该成员在调用 `make_unique()`的情况下在堆上分配。 对**new**和**delete**的调用由 `unique_ptr` 类封装。 当 `widget` 对象超出范围时，将调用 unique_ptr 析构函数，并且它将释放为数组分配的内存。  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

请尽可能在分配堆内存时使用智能指针。 如果必须显式使用 new 和 delete 运算符，请遵循 RAII 原则。 有关详细信息，请参阅[对象生存期和资源管理（RAII）](object-lifetime-and-resource-management-modern-cpp.md)。

## <a name="stdstring-and-stdstring_view"></a>std：： string 和 std：： string_view

C 样式字符串是 bug 的另一个主要源。 通过使用[std：： string 和 std：： wstring](../standard-library/basic-string-class.md)，几乎可以消除与 C 样式字符串关联的所有错误。 您还可以获得用于搜索、追加、预先计算等成员函数的好处。 两者都是高度优化的速度。 将字符串传递给只需要只读访问权限的函数时，可在 c + + 17 中使用[std：： string_view](../standard-library/basic-string-view-class.md)提高性能。

## <a name="stdvector-and-other-standard-library-containers"></a>std：： vector 和其他标准库容器

标准库容器都遵循 RAII 的原则。 它们为元素的安全遍历提供迭代器。 而且，它们已针对性能进行了高度优化，并已充分测试了正确性。 通过使用这些容器，可以消除自定义数据结构中可能引入的 bug 或效率低下问题。 在中C++，使用[vector](../standard-library/vector-class.md)作为序列容器，而不是原始数组。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[map](../standard-library/map-class.md)（而不是`unordered_map`）作为默认关联容器。 对于退化和多个事例，使用[set](../standard-library/set-class.md)、[多重映射](../standard-library/multimap-class.md)和[多集。](../standard-library/multiset-class.md)

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

需要性能优化时，请考虑使用：

- [数组](../standard-library/array-class-stl.md)，前提是当嵌入很重要时，例如，作为类成员。

- 无序的关联容器，例如[unordered_map](../standard-library/unordered-map-class.md)。 这些容器具有较低的元素开销和定时查找特性，但可能很难正确有效地使用它们。

- 经过排序的`vector`。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的较旧的 Api，请使用访问器方法，如`f(vec.data(), vec.size());`。 有关容器的详细信息，请参阅[C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>标准库算法

在假设需要为程序编写自定义算法之前，请先查看C++标准库[算法](../standard-library/algorithm.md)。 标准库包含许多常见操作（如搜索、排序、筛选和随机化进程）的不断增长的算法。 The math library is extensive. Starting in C++17, parallel versions of many algorithms are provided.

Here are some important examples:

- **for_each**, the default traversal algorithm (along with range-based for loops).

- **transform**, for not-in-place modification of container elements

- **find_if**, the default search algorithm.

- **sort**, **lower_bound**, and the other default sorting and searching algorithms.

若要写入一个比较运算符，请使用格式精确的 **<** 并在可行时使用*命名的 lambda*。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto instead of explicit type names

C++11 introduced the [auto](auto-cpp.md) keyword for use in variable, function, and template declarations. **auto** tells the compiler to deduce the type of the object so that you don't have to type it explicitly. **auto** is especially useful when the deduced type is a nested template:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>基于范围的 for 循环

C-style iteration over arrays and containers is prone to indexing errors and is also tedious to type. To eliminate these errors, and make your code more readable, use range-based for loops with both Standard Library containers and raw arrays. For more information, see [Range-based for statement](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>constexpr expressions instead of macros

Macros in C and C++ are tokens that are processed by the preprocessor before compilation. Each instance of a macro token is replaced with its defined value or expression before the file is compiled. Macros are commonly used in C-style programming to define compile-time constant values. However, macros are error-prone and difficult to debug. In modern C++, you should prefer [constexpr](constexpr-cpp.md) variables for compile-time constants:

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Uniform initialization

In modern C++, you can use brace initialization for any type. This form of initialization is especially convenient when initializing arrays, vectors, or other containers. In the following example, `v2` is initialized with three instances of `S`. `v3` is initialized with three instances of `S` that are themselves initialized using braces. The compiler infers the type of each element based on the declared type of `v3`.

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

For more information, see [Brace initialization](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Move semantics

Modern C++ provides *move semantics*, which make it possible to eliminate unnecessary memory copies. In earlier versions of the language, copies were unavoidable in certain situations. A *move* operation transfers ownership of a resource from one object to the next without making a copy. When implementing a class that owns a resource (such as heap memory, file handles, and so on), you can define a *move constructor* and *move assignment operator* for it. The compiler will choose these special members during overload resolution in situations where a copy isn't needed. The Standard Library container types invoke the move constructor on objects if one is defined. For more information, see [Move Constructors and Move Assignment Operators (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Lambda 表达式

In C-style programming, a function can be passed to another function by using a *function pointer*. Function pointers are inconvenient to maintain and understand. The function they refer to may be defined elsewhere in the source code, far away from the point at which it's invoked. Also, they're not type-safe. Modern C++ provides *function objects*, classes that override the [()](function-call-operator-parens.md) operator, which enables them to be called like a function. The most convenient way to create function objects is with inline [lambda expressions](../cpp/lambda-expressions-in-cpp.md). The following example shows how to use a lambda expression to pass a function object, that the `for_each` function will invoke on each element in the vector:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

The lambda expression `[=](int i) { return i > x && i < y; }` can be read as "function that takes a single argument of type `int` and returns a boolean that indicates whether the argument is greater than `x` and less than `y`." Notice that the variables `x` and `y` from the surrounding context can be used in the lambda. `[=]` 指定这些变量是通过值*捕获*的;换言之，lambda 表达式具有其自己的这些值的副本。

## <a name="exceptions"></a>异常

新式C++强调异常，而不是错误代码，作为报告和处理错误条件的最佳方式。 有关详细信息，请[参阅C++异常和错误处理的新式最佳实践](errors-and-exception-handling-modern-cpp.md)。

## <a name="stdatomic"></a>std：：原子

对于线程C++间通信机制，使用标准库[std：：原子](../standard-library/atomic-structure.md)结构和相关类型。

## <a name="stdvariant-c17"></a>std：： variant （c + + 17）

联合通常在 C 样式编程中使用，以通过使不同类型的成员占用相同的内存位置来节省内存。 但是，联合不是类型安全的，很容易出错。 C + + 17 引入了[std：： variant](../standard-library/variant-class.md)类作为联合的更可靠、更安全的替代类。 [Std：：就诊](../standard-library/variant-functions.md#visit)函数可用于以类型安全的方式访问 `variant` 类型的成员。

## <a name="see-also"></a>另请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)\
[Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)\
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++ 语言一致性表](../overview/visual-cpp-language-conformance.md)
