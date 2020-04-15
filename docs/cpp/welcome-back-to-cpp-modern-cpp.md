---
title: 欢迎回到C++ - 现代C++
description: 描述了现代C++的新编程习语及其原理。
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369495"
---
# <a name="welcome-back-to-c---modern-c"></a>欢迎回到C++ - 现代C++

自创建以来，C++已成为世界上使用最广泛的编程语言之一。 正确编写的 C++ 程序快速、高效。 该语言比其他语言更灵活：它可以在最高抽象级别工作，在硅级别下。 C++提供高度优化的标准库。 它允许访问低级硬件功能，以最大限度地提高速度和最小化内存需求。 使用C++，您可以创建各种应用。 游戏、设备驱动程序和高性能科学软件。 嵌入式程序。 Windows 客户端应用。 甚至其他编程语言的库和编译器也以C++编写。

C++ 的原始要求之一是与 C 语言向后兼容。 因此，C++始终允许使用 C 样式编程，包括原始指针、数组、null 端接字符串和其他功能。 它们可能实现出色的性能，但也会产生错误和复杂性。 C++的演变强调了使用C型习语的需求。 旧的 C 编程设施在您需要时就在那里，但使用现代C++代码，您应该越来越需要它们。 现代C++代码更简单、更安全、更优雅，而且仍然和以往一样快。

以下各节概述了现代C++的主要特点。 除非另有说明，此处列出的功能可在 C++11 及更高版本中提供。 在 Microsoft C++编译器中，可以设置[/std](../build/reference/std-specify-language-standard-version.md)编译器选项以指定要用于项目的标准版本。

## <a name="resources-and-smart-pointers"></a>资源和智能指针

C类编程中的主要错误类之一是*内存泄漏*。 泄漏通常是由于无法调用使用**new**分配的内存的**删除**。 现代C++强调*资源获取的原则是初始化*（RAII）。 这个想法很简单。 资源（堆内存、文件句柄、套接字等）应由对象*拥有*。 该对象在其构造函数中创建或接收新分配的资源，并在其析构函数中删除它。 RAII 原则可确保当拥有的对象超出范围时，所有资源都正确返回到操作系统。

为了支持轻松采用 RAII 原则，C++标准库提供了三种智能指针类型[：std：unique_ptr、std：：shared_ptr](../standard-library/unique-ptr-class.md)和[std：：weak_ptr](../standard-library/weak-ptr-class.md)。 [std::shared_ptr](../standard-library/shared-ptr-class.md) 智能指针处理其拥有的内存的分配和删除。 下面的示例显示一个类，该类具有在调用`make_unique()`的堆上分配的数组成员。 对**新**调用和**删除**的调用由`unique_ptr`类封装。 当`widget`对象超出范围时，将调用unique_ptr析构函数，并将释放为数组分配的内存。  

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

只要有可能，在分配堆内存时使用智能指针。 如果必须显式使用新的运算符和删除运算符，请遵循 RAII 原则。 有关详细信息，请参阅[对象生存期和资源管理 （RAII）。](object-lifetime-and-resource-management-modern-cpp.md)

## <a name="stdstring-and-stdstring_view"></a>std：：字符串和 std：：string_view

C 样式字符串是 Bug 的另一个主要来源。 通过使用[std：：string 和 std：：wstring，](../standard-library/basic-string-class.md)您可以消除几乎所有与 C 样式字符串相关的错误。 您还可以从成员函数中获益，用于搜索、追加、预处理等。 两者都高度优化速度。 将字符串传递到仅需要只读访问的函数时，在 C++17 中，可以使用[std：：string_view，](../standard-library/basic-string-view-class.md)以取得更大的性能优势。

## <a name="stdvector-and-other-standard-library-containers"></a>标准：：矢量和其他标准库容器

标准库容器都遵循 RAII 的原则。 它们为元素的安全遍历提供了迭代器。 而且，它们针对性能进行了高度优化，并经过过正确的彻底测试。 通过使用这些容器，您可以消除在自定义数据结构中可能出现的错误或效率低下的可能性。 在C++中使用[矢量](../standard-library/vector-class.md)作为顺序容器，而不是原始数组。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用[映射](../standard-library/map-class.md)（而不是`unordered_map`）作为默认关联容器。 使用[集](../standard-library/set-class.md)、[多映射](../standard-library/multimap-class.md)和[多集](../standard-library/multiset-class.md)进行退化和多案例。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

当需要优化性能时，请考虑使用：

- 嵌入时的[数组](../standard-library/array-class-stl.md)类型很重要，例如，作为类成员。

- 无序关联容器，如[unordered_map](../standard-library/unordered-map-class.md)。 这些具有较低的每个元素开销和恒定时间查找，但它们可能更难正确和高效地使用。

- 已`vector`排序 。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的旧 API，请使用访问器方法，例如`f(vec.data(), vec.size());`。 有关容器的详细信息，请参阅[C++标准库容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>标准库算法

在假定需要为程序编写自定义算法之前，请先查看C++标准库[算法](../standard-library/algorithm.md)。 标准库包含越来越多的算法，用于许多常见操作，如搜索、排序、筛选和随机化。 数学库很广泛。 从 C++17 开始，提供了许多算法的并行版本。

下面是一些重要示例：

- **for_each**，默认遍历算法（以及基于范围的循环）。

- **转换**，用于容器元素的不到位修改

- **find_if**，默认搜索算法。

- **排序****、lower_bound**和其他默认排序和搜索算法。

要编写比较器，请使用严格**<**，并尽可能使用名为*lambdas。*

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>自动而不是显式类型名称

C++11 引入了[用于](auto-cpp.md)变量、函数和模板声明的自动关键字。 **自动**告诉编译器推断对象的类型，这样您就不必显式键入它。 当推算类型是嵌套模板时，**自动**特别有用：

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>基于范围的循环

数组和容器的 C 样式迭代容易出现索引错误，而且键入也十分繁琐。 为了消除这些错误并使代码更具可读性，请使用基于范围的用于标准库容器和原始数组的循环。 有关详细信息，请参阅[基于范围的语句](../cpp/range-based-for-statement-cpp.md)。

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

## <a name="constexpr-expressions-instead-of-macros"></a>缺点表达式而不是宏

C 和 C++ 中的宏是预处理器在编译前处理的令牌。 在编译文件之前，宏令牌的每个实例都将替换为其定义的值或表达式。 宏通常用于 C 样式编程，用于定义编译时常量值。 但是，宏容易出错且难以调试。 在现代C++中，您应该更喜欢编译时间常量的[constexpr](constexpr-cpp.md)变量：

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>统一初始化

在现代C++中，可以为任何类型的大括号初始化使用大括号初始化。 这种初始化形式在初始化数组、矢量或其他容器时特别方便。 在下面的示例中，`v2`使用 的三个`S`实例初始化。 `v3`使用使用大括号初始化的`S`三个实例进行初始化。 编译器根据 声明的类型推断每个元素的类型`v3`。

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

有关详细信息，请参阅[Brace 初始化](initializing-classes-and-structs-without-constructors-cpp.md)。

## <a name="move-semantics"></a>移动语义

现代C++提供*移动语义*，从而可以消除不必要的内存副本。 在语言的早期版本中，在某些情况下，副本是不可避免的。 *移动*操作将资源的所有权从一个对象转移到下一个对象，而不进行复制。 实现拥有资源的类（如堆内存、文件句柄等）时，可以为其定义*移动构造函数*和*移动赋值运算符*。 在不需要副本的情况下，编译器将在重载解析期间选择这些特殊成员。 标准库容器类型在对象上调用移动构造函数（如果定义了。 有关详细信息，请参阅[移动构造函数和移动分配运算符 （C++）。](move-constructors-and-move-assignment-operators-cpp.md)

## <a name="lambda-expressions"></a>Lambda 表达式

在 C 样式编程中，可以使用*函数指针*将函数传递给另一个函数。 函数指针在维护和理解方面不方便。 它们引用的函数可以在源代码的其他地方定义，远离调用它的点。 此外，它们不是类型安全的。 现代C++提供*函数对象*，类重写[（）](function-call-operator-parens.md)运算符，这使得它们可以像函数一样调用。 创建函数对象的最方便方法是使用内联[lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。 下面的示例演示如何使用 lambda 表达式传递函数对象，`for_each`该函数将在矢量中的每个元素上调用该函数：

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

lambda 表达式`[=](int i) { return i > x && i < y; }`可以读取为"函数，该函数采用单个类型的`int`参数，并返回一个布尔，指示参数是否大于`x`和 小于 。 `y` 请注意，变量`x`和`y`来自周围上下文的变量可以在 lambda 中使用。 指定`[=]`这些变量由值捕获;但是，这些变量的*用值捕获*。换句话说，lambda 表达式具有这些值的自身副本。

## <a name="exceptions"></a>例外

现代C++强调异常，而不是错误代码，这是报告和处理错误条件的最佳方式。 有关详细信息，请参阅[有关异常和错误处理的现代C++最佳做法](errors-and-exception-handling-modern-cpp.md)。

## <a name="stdatomic"></a>std：：原子

使用C++标准库[（标准库）：原子](../standard-library/atomic-structure.md)结构和相关类型，用于线程间通信机制。

## <a name="stdvariant-c17"></a>分值：变数 （C++17）

联合通常用于 C 样式编程，通过使不同类型的成员占用相同的内存位置来节省内存。 但是，联合类型不安全，并且容易出现编程错误。 C++17 引入了[std：：变型](../standard-library/variant-class.md)类，作为联合的更强大、更安全的替代。 [std：：访问](../standard-library/variant-functions.md#visit)函数可用于以类型安全的方式访问`variant`类型的成员。

## <a name="see-also"></a>另请参阅

[C++语言参考](../cpp/cpp-language-reference.md)\
[兰姆达表达式](../cpp/lambda-expressions-in-cpp.md)\
[C++标准库](../standard-library/cpp-standard-library-reference.md)\
[微软C++语言一致性表](../overview/visual-cpp-language-conformance.md)
