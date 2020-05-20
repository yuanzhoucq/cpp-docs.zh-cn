---
title: 欢迎回到 c + +-新式 c + +
description: 介绍新式 c + + 中的新编程惯例及其原理。
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 76ac17e71368cdeee669b98505778838ef0dfee7
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550792"
---
# <a name="welcome-back-to-c---modern-c"></a>欢迎回到 c + +-新式 c + +

自创建后，c + + 已成为世界上最广泛使用的编程语言之一。 正确编写的 C++ 程序快速、高效。 语言比其他语言更加灵活：它可以在最高的抽象级别上运行，并在硅级别下运行。 C + + 提供高度优化的标准库。 它支持访问低级别硬件功能，最大限度地提高速度并最大程度地减少内存需求。 使用 c + +，可以创建各种应用。 游戏、设备驱动程序和高性能科学软件。 嵌入的程序。 Windows 客户端应用程序。 甚至其他编程语言的库和编译器都是用 c + + 编写的。

C++ 的原始要求之一是与 C 语言向后兼容。 因此，c + + 始终允许 C 样式编程，其中包含原始指针、数组、以 null 结尾的字符串和其他功能。 它们可以实现良好的性能，但也可能会产生 bug 和复杂性。 C + + 的发展重点强调了一些功能，大大减少了使用 C 样式惯例的需求。 旧的 C 编程设施在您需要它们时存在，但对于新式 c + + 代码，您应该需要更少且更少的代码。 新式 c + + 代码更简单、更安全、更优雅，并与以往一样快。

以下部分概述了新式 c + + 的主要功能。 除非另有说明，否则此处列出的功能在 c + + 11 和更高版本中可用。 在 Microsoft c + + 编译器中，可以设置 [`/std`](../build/reference/std-specify-language-standard-version.md) 编译器选项来指定要用于项目的标准版本。

## <a name="resources-and-smart-pointers"></a>资源和智能指针

C 样式编程中的一个主要错误类是*内存泄漏*。 泄漏通常是由于为分配的内存的调用失败引起的 **`delete`** **`new`** 。 新式 c + + 强调*了资源获取的原则是初始化*（RAII）的。 思路非常简单。 资源（堆内存、文件句柄、套接字等）应归对象*所有*。 该对象在其构造函数中创建或接收新分配的资源，并在其析构函数中将其删除。 RAII 原则保证当所属对象超出范围时，所有资源都能正确返回到操作系统。

为了支持简单采用 RAII 原则，c + + 标准库提供了三种智能指针类型： [`std::unique_ptr`](../standard-library/unique-ptr-class.md) 、 [`std::shared_ptr`](../standard-library/shared-ptr-class.md) 和 [`std::weak_ptr`](../standard-library/weak-ptr-class.md) 。 智能指针处理其拥有的内存分配和删除操作。 下面的示例演示一个类，其中包含一个数组成员，该成员在对的调用中的堆上分配 `make_unique()` 。 对和的 **`new`** 调用 **`delete`** 由 `unique_ptr` 类封装。 当 `widget` 对象超出范围时，将调用 unique_ptr 析构函数，并且它将释放为数组分配的内存。  

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

## <a name="stdstring-and-stdstring_view"></a>`std::string` 和 `std::string_view`

C 样式字符串是 bug 的另一个主要源。 通过使用[ `std::string` 和 `std::wstring` ](../standard-library/basic-string-class.md)，几乎可以消除与 C 样式字符串关联的所有错误。 您还可以获得用于搜索、追加、预先计算等成员函数的好处。 两者都是高度优化的速度。 将字符串传递给只需要只读访问权限的函数时，可以使用在 c + + 17 中 [`std::string_view`](../standard-library/basic-string-view-class.md) 提高性能。

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector`和其他标准库容器

标准库容器都遵循 RAII 的原则。 它们为元素的安全遍历提供迭代器。 而且，它们已针对性能进行了高度优化，并已充分测试了正确性。 通过使用这些容器，可以消除自定义数据结构中可能引入的 bug 或效率低下问题。 使用 [`vector`](../standard-library/vector-class.md) 作为 c + + 中的顺序容器，而不是原始数组。

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

使用 [`map`](../standard-library/map-class.md) （而不是 `unordered_map` ）作为默认关联容器。 [`set`](../standard-library/set-class.md) [`multimap`](../standard-library/multimap-class.md) [`multiset`](../standard-library/multiset-class.md) 对于退化和多个事例，使用、和。

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

需要性能优化时，请考虑使用：

- [`array`](../standard-library/array-class-stl.md)嵌入时的类型很重要，例如，作为类成员。

- 未排序的关联容器，如 [`unordered_map`](../standard-library/unordered-map-class.md) 。 这些开销较低，每个元素的开销和持续时间的查找都较低，但它们可能更难以正确有效地使用。

- 已排序 `vector` 。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。

不要使用 C 样式数组。 对于需要直接访问数据的旧 Api，请改用访问器方法，如 `f(vec.data(), vec.size());` 。 有关容器的详细信息，请参阅[c + + 标准库容器](../standard-library/stl-containers.md)。

## <a name="standard-library-algorithms"></a>标准库算法

在假设需要为程序编写自定义算法之前，请先查看 c + + 标准库[算法](../standard-library/algorithm.md)。 标准库包含许多常见操作（如搜索、排序、筛选和随机化进程）的不断增长的算法。 数学库很广泛。 从 c + + 17 开始，提供了许多算法的并行版本。

以下是一些重要示例：

- `for_each`，默认遍历算法（以及基于范围的 `for` 循环）。

- `transform`，用于不就地修改容器元素

- `find_if`，默认搜索算法。

- `sort`、 `lower_bound` 和其他默认排序和搜索算法。

若要编写比较运算符，请 **`<`** 在可以时使用 strict 并使用*命名 lambda* 。

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto`而不是显式类型名称

C + + 11 引入了用于 [`auto`](auto-cpp.md) 变量、函数和模板声明中的关键字。 **`auto`** 告诉编译器推断对象的类型，这样就无需显式键入。 **`auto`** 当推导出的类型是嵌套模板时，尤其有用：

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>基于范围的 `for` 循环

数组和容器上的 C 样式迭代容易导致索引错误，而且键入单调乏味。 若要消除这些错误，并使代码更具可读性，请将基于范围的 `for` 循环用于标准库容器和原始阵列。 有关详细信息，请参阅[基于范围的 `for` 语句](../cpp/range-based-for-statement-cpp.md)。

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

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr`表达式而非宏

C 和 c + + 中的宏是在编译之前由预处理器处理的标记。 在编译文件之前，宏标记的每个实例都将替换为其定义的值或表达式。 通常在 C 样式编程中使用宏来定义编译时常量值。 但宏容易出错且难以调试。 在现代 c + + 中，你应首选 [`constexpr`](constexpr-cpp.md) 用于编译时常量的变量：

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>统一初始化

在现代 c + + 中，可以对任何类型使用大括号初始化。 初始化数组、矢量或其他容器时，这种形式的初始化非常方便。 在下面的示例中， `v2` 用的三个实例进行了初始化 `S` 。 `v3`使用大括号初始化的三个实例 `S` 来初始化。 编译器基于声明的类型推断每个元素的类型 `v3` 。

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

有关详细信息，请参阅[大括号初始化](initializing-classes-and-structs-without-constructors-cpp.md)。

## <a name="move-semantics"></a>移动语义

新式 c + + 提供了*移动语义*，从而可以消除不必要的内存副本。 在早期版本的语言中，在某些情况下无法避免复制。 *移动*操作将资源的所有权从一个对象转移到下一个对象，而不创建副本。 某些类拥有诸如堆内存、文件句柄等资源。 实现资源所属类时，可以为其定义*移动构造函数*和*移动赋值运算符*。 编译器在不需要复制的情况下，在重载解析期间选择这些特殊成员。 标准库容器类型调用对象的移动构造函数（如果已定义）。 有关详细信息，请参阅[移动构造函数和移动赋值运算符（c + +）](move-constructors-and-move-assignment-operators-cpp.md)。

## <a name="lambda-expressions"></a>Lambda 表达式

在 C 样式编程中，可以通过使用*函数指针*将函数传递到其他函数。 函数指针不太方便维护和理解。 它们引用的函数可以在源代码中的其他位置定义，而不是从调用它的位置定义。 而且，它们不是类型安全的。 现代 c + + 提供*函数对象*、重写 [`operator()`](function-call-operator-parens.md) 运算符的类，从而使它们可以像函数一样进行调用。 创建函数对象的最简便方法是采用内联[lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。 下面的示例演示如何使用 lambda 表达式传递函数对象，该函数 `for_each` 将在向量中的每个元素上调用：

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Lambda 表达式 `[=](int i) { return i > x && i < y; }` 可以读取为 "函数，该函数采用类型的单个自变量 `int` ，并返回一个布尔值，指示该参数是否大于 `x` 且小于 `y` 。" 请注意， `x` `y` 可在 lambda 中使用来自周围上下文的变量和。 `[=]`指定这些变量是通过值*捕获*的; 换言之，lambda 表达式具有其自己的这些值的副本。

## <a name="exceptions"></a>例外

新式 c + + 强调异常，而不是错误代码，作为报告和处理错误条件的最佳方式。 有关详细信息，请参阅[异常和错误处理的新式 c + + 最佳实践](errors-and-exception-handling-modern-cpp.md)。

## `std::atomic`

对于线程间通信机制，请使用 c + + 标准库 [`std::atomic`](../standard-library/atomic-structure.md) 结构和相关类型。

## <a name="stdvariant-c17"></a>`std::variant`（C + + 17）

联合通常在 C 样式编程中使用，以通过使不同类型的成员占用相同的内存位置来节省内存。 但是，联合不是类型安全的，很容易出错。 C + + 17 引入了 [`std::variant`](../standard-library/variant-class.md) 类，作为联合的更可靠、更安全的替代方法。 [`std::visit`](../standard-library/variant-functions.md#visit)函数可用于以 `variant` 类型安全的方式访问类型的成员。

## <a name="see-also"></a>另请参阅

[C + + 语言参考](../cpp/cpp-language-reference.md)\
[Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)\
[C + + 标准库](../standard-library/cpp-standard-library-reference.md)\
[Microsoft c + + 语言一致性表](../overview/visual-cpp-language-conformance.md)
