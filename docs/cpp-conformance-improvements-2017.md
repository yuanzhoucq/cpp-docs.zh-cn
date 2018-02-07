---
title: "C++ 的一致性改进 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45f22597944084ecd2d30fe29bf4e8ab3ef80201
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-and-155improvements155"></a>Visual Studio 2017 版本 15.0、[15.3](#improvements_153) 和 [15.5](#improvements_155) 中 C++ 的一致性改进

Microsoft Visual C++ 编译器支持通用 constexpr 和用于聚合的 NSDMI，现具有 C++14 标准版中的全部新增功能。 请注意，编译器仍缺少 C++11 和 C++98 标准版中的一些功能。 请参阅 [Visual C++ 语言合规性](visual-cpp-language-conformance.md)中显示编译器当前状态的表。

## <a name="c11"></a>C++11

**在更多库中支持表达式 SFINAE**  
编译器持续改进对表达式 SFINAE 的支持，SFINAE 是模板参数推导和替换所必需的，其中 decltype 和 constexpr 表达式可能显示为模板参数。 有关详细信息，请参阅 [Visual Studio 2017 RC 中的表达式 SFINAE 改进之处](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3)。

## <a name="c-14"></a>C++ 14

**用于聚合的 NSDMI**  
聚合是一个数组或类，不包含用户提供的构造函数、专用或受保护的非静态数据成员、基类，也不包含虚拟函数。 从 C++14 开始，聚合可能包含成员初始值设定项。 有关详细信息，请参阅 [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html)（成员初始值设定项和聚合）。

**扩展的 constexpr**  
现在允许声明为 constexpr 的表达式包含某些种类的声明：if 和 switch 语句、loop 语句，以及某些对象的突变，这些对象的生命期开始时间处于 constexpr 表达式计算范围内。 此外，不再需要 constexpr 非静态成员函数为隐式 const。 有关详细信息，请参阅 [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)（放松对 constexpr 函数的约束）。

## <a name="c17"></a>C++17

**Terse static_assert**（适用于 /std:c++17）  
在 C++17 中，static_assert 的消息参数是可选的。 有关详细信息，请参阅 [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)（扩展 static_assert, v2）。

**[[fallthrough]]** 属性（适用于 /std:c++17）  
[[fallthrough]] 属性可以在 switch 语句的上下文中用作对预期发生贯穿行为的编译器的提示。 这可防止编译器在这类情况下发出警告。 有关详细信息，请参阅 [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf)（[[fallthrough]] 属性的用词）。

**基于范围的通用 for 循环**（无需编译器开关）  
基于范围的 for 循环不再需要 begin() 和 end() 返回相同类型的对象。 这使 end() 能够返回 [range-v3](https://github.com/ericniebler/range-v3) 中的范围和完成但尚未发布的范围技术规范使用的 sentinel。 有关详细信息，请参阅 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)（通用化基于范围的 for 循环）。

## <a name="improvements_153"></a>Visual Studio 2017 版本 15.3 中的改进

**constexpr lambda**  
现在可以在常数表达式中使用 Lambda 表达式。 有关详细信息，请参阅 [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf)。

**函数模板中的 if constexpr**  
函数模板可能包含 `if constexpr` 语句，用于启用编译时创建分支。 有关详细信息，请参阅 [if constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html)。

**具有初始化表达式的选择语句**  
`if` 语句可以包括在该语句本身所含块范围中引入变量的初始化表达式。 有关详细信息，请参阅[具有初始化表达式的选择语句](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html)。

**[[maybe_unused]] 和 [[nodiscard]] 属性**  
不使用实体时不提示警告的新属性，或在放弃函数调用的返回值时创建一个警告的新属性。 有关详细信息，请参阅 [maybe_unused 属性的用词](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf)和 [unused、nodiscard 和 fallthrough 属性的建议](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf)。

**不重复使用属性命名空间**  
仅在属性列表中启用单个命名空间标识符的新语法。 有关详细信息，请参阅 [C++ 中的属性](cpp/attributes2.md)。

**结构化绑定**  
现在可以在单个声明中存储具有其各组件名称的值，前提是该值是数组、std::tuple 或 std::pair 或者具有所有公共的非静态数据成员。 有关详细信息，请参阅[结构化绑定](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf)。

**枚举类值的构造规则**  
现在有一种从作用域内枚举的基础类型到该枚举本身的隐式/非收缩转换，前提是它的定义不引入枚举器，并且源使用列表初始化语法。 有关详细信息，请参阅[枚举类值的构造规则](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)。

**按值捕获 *this**  
Lambda 表达式中的 `*this` 对象现在可按值捕获。 这样可以在并行和异步操作中实现调用 lambda 的情况，特别是在较新的计算机体系结构中。 有关详细信息，请参阅[通过值执行的 \*this 的 Lambda 捕获为 [=,\*this]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)。

**删除 bool 的 operator++**  
`bool` 类型上不再支持 `operator++`。 有关详细信息，请参阅[删除弃用的 operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)。

**删除弃用的“register”关键字**  
之前弃用（且被编译器忽略的）`register` 关键字现已从语言中删除。 有关详细信息，请参阅[删除弃用的 register 关键字](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)。

有关 Visual Studio 2015 Update 3 及之前的版本中一致性改进的完整列表，请参阅 [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx)（Visual C++ 2003 至 2015 中的新增功能）。

## <a name="improvements_155"></a>Visual Studio 2017 版本 15.5 中的改进

标有 [14] 的功能即使是在 /std:c++14 模式中也无条件提供。

**extern constexpr 的新编译器开关**  
在早期版本的 Visual Studio 中，编译器常常提供 `constexpr` 变量内部链接，甚至是在变量标记为 `extern` 的时候。 在 Visual Studio 2017 版本 15.5 中，新编译器开关 [/Zc:externConstexpr](build/reference/zc-externconstexpr.md) 启用符合标准的正确行为。 有关详细信息，请参阅 [extern constexpr 链接](#extern_linkage)。

**删除动态异常规范**  
[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) C++11 已弃用动态异常规范。 C++17 中已删除此功能，但是弃用的 `throw()` 规范（仍然）作为 `noexcept(true)` 的别名严格保留。 有关详细信息，请参阅[动态异常规范的删除和 noexcept](#noexcept_removal)。 

**not_fn()**  
[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` 替换了 `not1` 和 `not2`。

**重新组织 enable_shared_from_this**  
在 C++11 中添加 [P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this`。 C++17 标准更新规范以更好地处理某些特殊情况。 [14]

**拼接映射和集**  
[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) 此功能从关联容器（例如 map、set、unordered\_map、unordered\_set）中提取节点，然后可修改这些节点，并插入回同一容器或使用相同节点类型的不同容器中。 （常见用例是从 `std::map` 提取节点、更改密钥并重新插入。）

**弃用残留库部分**  
[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) 这些年来，C++ 标准库的多个功能已被更新的功能取代，或者已变得不太有用或存在问题。 C++17 中正式弃用了这些功能。 

**删除 std::function 中的分配器支持**  
[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) 在 C++17 之前，经典模板 `std::function` 有多个采用分配器参数的构造函数。 但是，在此上下文中，分配器的使用出现了问题并且语义不明。 所以，删除了这些构造函数。

**对 not_fn() 的修复**  
[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) `std::not_fn` 的新措词提供对在调用包装器时传播值类别的支持。

**shared_ptr\<T[]>, shared_ptr\<T[N]>**  
[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) 将库基础知识中的 `shared_ptr` 更改合并到 C++17。 [14]

**修复数组的 shared_ptr**  
[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) 修复数组的 shared_ptr 支持。 [14]

**阐明 insert_return_type**  
[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) 有唯一键的关联容器和有唯一键的无序容器均有一个返回嵌套类型 `insert_return_type` 的成员函数 `insert`。 该返回类型现在定义为在容器 Iterator 和 NodeType 上参数化的类型的专用化。

**STL 的内联变量**  
[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

**弃用的 Annex D 功能**  
C++ 标准的 Annex D 包含所有已弃用的功能，包括 `shared_ptr::unique()`、`<codecvt>` 和 `namespace std::tr1`。 设置 /std:c++17 编译器开关时，Annex D 中几乎所有的标准库功能都被标记为已弃用。 有关详细信息，请参阅 [Annex D 中的标准库功能被标记为已弃用](#annex_d)。

现在，`<experimental/filesystem>` 中的 `std::tr2::sys` 命名空间在 /std:c++14 下默认发出弃用警告，在 /std:c++17 下默认删除。

通过避免非标准扩展（类内显式专用化）改进了 iostreams 中的一致性。

标准库现在在内部使用变量模板。

标准库已随 C++17 编译器的更改更新，包括在类型系统中添加 noexcept 和删除动态异常规范。

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-and-155update155"></a>Visual Studio 版本 15.0、[15.3](#update_153) 和 [15.5](#update_155) 中的 Bug 修复

### <a name="copy-list-initialization"></a>复制列表初始化

Visual Studio 2017 使用并非在 Visual Studio 2015 中捕获的初始值设定项列表正确引发与对象创建相关的编译器错误，并可能导致故障或未定义的运行时行为。 根据 N4594 13.3.1.7p1，在复制列表初始化中，编译器需要考虑用于重载决策的显式构造函数，但是如果实际选择了该重载，则必须引发错误。

以下两个示例在 Visual Studio 2015 中编译，但在 Visual Studio 2017 中不编译。

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

为更正此错误，应使用直接初始化：

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

在 Visual Studio 2015 中，编译器以与常规复制初始化相同的方式错误地处理复制列表初始化；它只考虑将转换构造函数用于重载决策。 在以下示例中，Visual Studio 2015 选择 MyInt(23)，但 Visual Studio 2017 正确引发错误。

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

此示例与上一个示例类似，但引发了不同的错误。 它在 Visual Studio 2015 中成功，在 Visual Studio 2017 中失败 (C2668)。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>弃用的的 Typedef

Visual Studio 2017 现在针对在类或结构中声明的已弃用 Typedef 发出正确警告。 下面的示例在 Visual Studio 2015 中编译，且未收到警告，但在 Visual Studio 2017 中则引发 C4996。

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>constexpr

当条件性运算的左侧操作数在 constexpr 上下文中无效时，Visual Studio 2017 会正确引发错误。 以下代码在 Visual Studio 2015 中编译，但在 Visual Studio 2017 中不编译（C3615 constexpr 函数 “f” 无法得出常数表达式）：

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```
要更正此错误，请将 `array::size()` 函数声明为 `constexpr`，或者从 `f` 中删除 `constexpr` 限定符。

### <a name="class-types-passed-to-variadic-functions"></a>传递给 variadic 函数的类类型

在 Visual Studio 2017 中，传递给 variadic 函数（如 printf）的类或结构必须完全可复制。 传递此类对象时，编译器只是执行按位复制，不会调用构造函数或析构函数。

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

若要更正错误，可调用一种成员函数，该函数返回可完全复制的类型， 

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

或者执行静态强制转换，以在传递对象之前将其进行转换：

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

对于使用 CStringW 生成和管理的字符串，提供的 `operator LPCWSTR()` 应用来将 CStringW 对象强制转换为格式字符串所需的 C 指针。

```cpp
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>类构造中的 cv 限定符

在 Visual Studio 2015 中，编译器有时会在通过构造函数调用生成类对象时错误地忽略 cv 限定符。 这可能会导致故障或意外的运行时行为。 以下示例在 Visual Studio 2015 中编译，但在 Visual Studio 2017 中引发了编译器错误：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

要更正此错误，请将 `operator int()` 声明为 `const`。

### <a name="access-checking-on-qualified-names-in-templates"></a>对模板中限定名称的访问检查

早期版本的编译器不对某些模板上下文中的限定名称执行访问检查。 这可能会干扰预期的 SFINAE 行为，在这一行为中，预期由于名称的不可访问性，替换会失败。 这可能会导致在运行时发生故障或意外行为，因为编译器错误地调用了运算符的错误重载。 在 Visual Studio 2017 中，引发了编译器错误。 具体错误可能会有所不同，但通常是“C2672 找不到匹配的重载函数”。 下列代码在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中引发错误：

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>缺少的模板参数列表

在 Visual Studio 2015 及更早版本中，当模板出现在模板参数列表中（例如作为默认模板参数或非类型模板参数的一部分）时，编译器不会诊断缺少的模板参数列表。 这可能导致不可预知的行为，包括编译器故障或意外的运行时行为。 下列代码在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中引发错误。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>表达式 SFINAE

为了支持表达式 SFINAE，编译器现在会在声明模板而不是实例化模板时分析 decltype 参数。 因此，如果在 decltype 参数中找到非依赖专用化，则它不会被推迟到实例化时间，而是被立即处理，并且在当时诊断产生的所有错误。

以下示例显示了在声明时引发的这类编译器错误：

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>在匿名命名空间内声明的类

根据 C++ 标准，在匿名命名空间内部声明的类具有内部链接，因此不能导出。 在 Visual Studio 2015 及更早版本中，此规则不是强制执行的。 在 Visual Studio 2017 中，部分强制执行此规则。 下面的示例在 Visual Studio 2017 中引发错误：“错误 C2201: const anonymous namespace::S1::vftable: 必须具有外部链接才能导出/导入。”

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>值类成员的默认初始值设定项 (C++/CLI)

在 Visual Studio 2015 及更早版本中，编译器允许（但会忽略）值类成员的默认成员初始值设定项。 值类的默认初始化始终对成员执行零初始化；不允许使用默认构造函数。 在 Visual Studio 2017 中，默认成员初始值设定项引发编译器错误，如下例所示：

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>默认索引器 (C++/CLI)

在 Visual Studio 2015 及更早版本中，编译器在某些情况下将默认属性误识别为默认索引器。 可通过使用标识符 `default` 访问该属性来解决这个问题。 在 C++11 中将 `default` 引入为关键字后，解决方法本身会出现问题。 因此，在 Visual Studio 2017 中，需要解决方法的 Bug 都已修复，现在将 `default` 用于访问类的默认属性时，编译器会引发错误。

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

在 Visual Studio 2017 中，可以通过属性名称同时访问两个值属性：

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Visual Studio 2017 版本 15.3 中的 Bug 修复

### <a name="calls-to-deleted-member-templates"></a>调用的成员模板已遭删除

在旧版 Visual Studio 中，在某些情况下，编译器可能无法在对已删除的成员模板执行格式错误的调用时发出错误，这可能会导致运行时故障发生。 下面的代码现在生成错误 C2280“"int S\<int>::f\<int>(void)": 正在尝试引用已删除的函数”：

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

若要修复此错误，请将 i 声明为 `int`。

### <a name="pre-condition-checks-for-type-traits"></a>类型特征的前提条件检查

为了更严格地遵循标准，Visual Studio 2017 版本 15.3 改进了类型特征的前提条件检查。 此类检查验证的是类型是否可赋值。 以下代码在 Visual Studio 2017 版本 15.3 中生成错误 C2139：

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>有关从本机到托管的封送的新编译器警告和运行时检查

从托管函数到本机函数的调用需要执行封送。 虽然 CLR 会执行封送，但并不理解 C++ 语义。 如果通过值传递本机对象，CLR 要么调用对象的复制构造函数，要么使用 BitBlt，而这可能会导致未定义的运行时行为发生。

现在，如果编译器能够在编译时知晓含有已删除的复制构造函数的本机对象通过值在本机和托管边界之间传递，则会发出警告。 如果编译器在编译时不知晓，则插入运行时检查，以便在出现格式错误的封送时，程序能够立即调用 `std::terminate`。 在 Visual Studio 2017 版本 15.3 中，以下代码生成警告 C4606: "A": 跨本机和托管边界按值传递参数要求有效的复制构造函数。 否则会发生未定义的运行时行为。

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

若要修复此错误，请删除 `#pragma managed` 指令以将调用方标记为本机，并避免执行封送。

### <a name="experimental-api-warning-for-winrt"></a>WinRT 的实验性 API 警告

为了获取反馈而发布的实验性 WinRT API 使用 `Windows.Foundation.Metadata.ExperimentalAttribute` 进行修饰。 在 Visual Studio 2017 版本 15.3 中，编译器会在遇到此特性时生成警告 C4698。 旧版 Windows SDK 中的一些 API 已使用此特性进行修饰，调用这些 API 现在会触发这一编译器警告。 更高版本的 Windows SDK 会从所有已发布的类型中删除此特性。不过，如果使用的是更低版本 SDK，需要对已发布类型的所有调用禁用这些警告。

下面的代码生成警告 C4698："Windows::Storage::IApplicationDataStatics2::GetForUserAsync" 仅供评估使用，可能会在今后推出的版本中发生变更或遭到删除。

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

若要禁用此警告，请添加 #pragma：

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>模板成员函数的外部定义

Visual Studio 2017 版本 15.3 在遇到未在类中声明的模板成员函数的外部定义时生成错误。 下面的代码现在生成错误 C2039："f":不是 "S" 的成员。

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

若要修复此错误，请在类中添加声明：

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>尝试使用“this”指针的地址

在 C++ 中，`this` 是指向 X 的类型指针的 prvalue。不能使用 `this` 的地址，也不能将其绑定到左值引用。 在旧版 Visual Studio 中，编译器允许通过执行转换来规避此限制。 在 Visual Studio 2017 版本 15.3 中，编译器会生成错误 C2664。

### <a name="conversion-to-an-inaccessible-base-class"></a>转换成不可访问的基类

如果尝试将类型转换成不可访问的基类，Visual Studio 2017 版本 15.3 会生成错误。 现在，编译器引发“错误 C2243:‘类型转换’: 存在从‘D *’到‘B *’的转换，但不可访问。” 下面的代码格式错误，可能会导致运行时故障发生。 现在，编译器在遇到如下代码时生成错误 C2243：

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>不允许对成员函数的外部定义使用默认自变量

不允许对模板类中成员函数的外部定义使用默认参数。编译器将在 /permissive 下发出警告，并在 /permissive- 下发出硬错误。

在以前版本的 Visual Studio 中，以下格式错误的代码可能会导致发生运行时故障。 Visual Studio 2017 版本 15.3 生成警告 C5034: "A\<T>::f": 类模板成员的外部定义不能包含默认参数：

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

若要修复此错误，请删除 `= false` 默认自变量。

### <a name="use-of-offsetof-with-compound-member-designator"></a>将 offsetof 与复合成员指示符结合使用

在 Visual Studio 2017 版本 15.3 中，使用 /Wall 选项进行编译时，如果使用 `offsetof(T, m)`（其中 m 是“复合成员指示符”），会生成警告。 下面的代码格式错误，可能会导致运行时发生故障。 Visual Studio 2017 版本 15.3 生成“警告 C4841: 使用了非标准扩展: offsetof 中的复合成员指示符”：

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

若要修复此代码，请使用 pragma 禁用此警告，或将此代码更改为不使用 `offsetof`：

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>将 offsetof 与静态数据成员或成员函数结合使用

在 Visual Studio 2017 版本 15.3 中，使用 `offsetof(T, m)`（其中 m 表示静态数据成员或成员函数）会导致出现错误。 下面的代码生成错误 C4597：未定义的行为: offsetof 应用于成员函数 "foo"。同时，还生成错误 C4597：未定义的行为: offsetof 应用于静态数据成员 "bar"。

```cpp
#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);
```

此代码格式错误，可能会导致运行时发生故障。 若要修复此错误，请将此代码更改为不再调用未定义的行为。 这是 C++ 标准不允许使用的不可移植代码。

### <a name="declspec"></a>有关 declspec 属性的新警告

在 Visual Studio 2017 版本 15.3 中，如果在 `extern "C"` 链接规范前应用了 `__declspec(...)`，则编译器不再忽略此特性。 以前，编译器会忽略此特性，进而可能会产生运行时影响。 设置 /Wall 和 /WX 选项后，下面的代码生成“警告 C4768: 已忽略链接规范前的 __declspec 特性”：

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

若要修复此警告，请将 extern "C" 前置:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

此警告在 15.3 中默认关闭，但在 15.5 中默认打开，只影响使用 /Wall 和 /WX 编译的代码。

### <a name="decltype-and-calls-to-deleted-destructors"></a>decltype 和调用的析构函数已遭删除

在旧版 Visual Studio 中，在“decltype”相关表达式的上下文中，编译器无法检测对已删除析构函数的调用。 在 Visual Studio 2017 版本 15.3 中，下面的代码生成“错误 C2280: "A\<T>::~A(void)": 正在尝试引用已删除的函数”：

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>未初始化的 const 变量

Visual Studio 2017 RTW 版本包含一个回归，即如果未初始化“const”变量，C++ 编译器不会发出诊断提醒。 Visual Studio 2017 版本 15.3 修复了此回归。 下面的代码现在生成警告 C4132：“值”:应初始化 const 对象。

```cpp
const int Value; //C4132
```

若要修复此错误，请向 `Value` 赋值。

### <a name="empty-declarations"></a>空声明

现在，Visual Studio 2017 版本 15.3 不仅会对内置类型发出警告，还会对所有类型的空声明发出警告。 下面的代码现在对所有四种声明生成第 2 级 C4091 警告：

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

若要移除这些警告，只需注释掉或删除空声明即可。 如果未命名的对象会造成副作用（如 RAII），应命名对象。

在 /Wv:18 下此警告被排除在外，而在警告等级 W2 下此警告默认启用。

### <a name="stdisconvertible-for-array-types"></a>std::is_convertible 用于数组类型

早期版本的编译器为数组类型提供了不正确的 [std::is_convertible](standard-library/is-convertible-class.md) 结果。 这要求库编写者在使用 `std::is_convertible<...>` 类型特征时，要特殊处理 Microsoft Visual C++ 编译器。 在以下示例中，静态断言在早期版本的 Visual Studio 中是通过的，但在 Visual Studio 2017 版本 15.3 中不通过：

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` 是通过检查虚函数定义是否完整计算而得：

```cpp 
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>私有析构函数和 std::is_constructible

在决定 [std::is_constructible](standard-library/is-constructible-class.md) 的结果时，早期版本的编译器忽略了析构函数是否是私有的。 现在会考虑这一点。 在以下示例中，静态断言在早期版本的 Visual Studio 中是通过的，但在 Visual Studio 2017 版本 15.3 中不通过：

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

私有析构函数导致类型不可构造。 `std::is_constructible<T, Args...>` 的计算方式类似编写以下声明：

```cpp
   T obj(std::declval<Args>()...)
```

此调用表示一个析构函数调用。

### <a name="c2668-ambiguous-overload-resolution"></a>C2668：重载决策不明确

当发现多个候选项（都使用声明和参数依赖查找）时，早期版本的编译器有时无法检测到多义性。 这可能导致选择错误的重载并出现异常的运行时行为。 在以下示例中，Visual Studio 2017 版本 15.3 正确引发 C2668“f”：对重载函数的调用不确定：

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f; 

   S s1, s2;
   f(s1, s2); // C2668
}
```

要修复代码，请在打算调用 `::f()` 时删除正在使用的 `N::f` 语句。

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660：局部函数声明与参数依赖查找

局部函数声明将函数声明隐藏在封闭作用域中，并禁用参数依赖查找。 但在这种情况中，早期版本的编译器会执行参数依赖查找，这有可能导致选择错误的重载，并出现异常的运行时行为。 出现此错误，通常是因为局部函数声明的签名不正确。 在下例中，Visual Studio 2017 版本 15.3 正确引发 C2660“f”：函数不具有 2 个参数：

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

要修改此问题，请更改或删除 `f(S)` 签名。

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038：初始值设定项列表中的初始化顺序

类成员按它们声明的顺序，而非按它们在初始值设定项列表中出现的顺序进行初始化。 如果初始值设定项列表的顺序不同于声明顺序，早期版本的编译器不会发出警告。 如果列表中为另一成员初始化所依赖的某成员已被初始化，则可能会造成未定义的运行时行为。 在以下示例中，Visual Studio 2017 版本 15.3（具有 /Wall）引发了“警告 C5038: 数据成员 "A::y" 将在数据成员 "A::x" 之后被初始化”：

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

要修复此问题，请将初始值设定项列表的顺序设置为与声明顺序相同。 如果一个或两个初始化表达式同时引用基类成员，则会引发类似警告。

请注意，警告默认为关闭，它仅会影响通过 /Wall 编译的代码。

## <a name="update_155"></a>Visual Studio 2017 版本 15.5 中的 Bug 修复和其他行为更改

### <a name="partial-ordering-change"></a>部分排序更改

现在，编译器正确拒绝以下代码，并提供正确的错误消息：

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

上面的示例中的问题是类型中有两种差异（const 和 non-const 以及 pack 和 non-pack）。 要消除编译器错误，请删除其中一种差异。 这使得编译器能明确地对函数进行排序。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>异常处理程序

对数组或函数类型的引用的处理程序从不匹配任意异常对象。 现在，编译器正确遵循此规则并引发第 4 级警告。 使用 /Zc:strictStrings 时，它也不再将 `char*` 或 `wchar_t*` 的处理程序与字符串文本相匹配。

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```
以下代码可避免此错误：

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>std::tr1 命名空间已弃用

现在，非标准 `std::tr1` 命名空间在 C++14 和 C++17 这两种模式中均标记为已弃用。 在 Visual Studio 2017 版本 15.5 中，以下代码引发错误 C4996：

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

若要修复此错误，请删除对 `tr1` 命名空间的引用：

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="annex_d"></a>Annex D 中的标准库功能标记为已弃用

设置 /std:c++17 模式编译器开关时，Annex D 中几乎所有的标准库功能都标记为已弃用。

在 Visual Studio 2017 版本 15.5 中，以下代码引发错误 C4996：

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

若要修复此错误，请按警告文本中的说明操作，如以下代码所示：

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>未引用的本地变量

在 Visual Studio 15.5 中，会在较多的情况下发出警告 C4189，如以下代码所示：

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}

```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

若要修复此错误，请删除未使用的变量。

### <a name="single-line-comments"></a>单行注释

在 Visual Studio 2017 版本 15.5 中，警告 C4001 和 C4179 不再由 C 编译器发出。 以前，仅在 /Za 编译器开关下发出这两个警告。  因为单行注释自 C99 开始已经是 C 标准的一部分，所以不再需要这些警告。

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

如果代码不需要向后兼容，则可以通过删除对 C4001/C4179 的禁止显示来避免警告。 如果代码不需要向后兼容，则仅禁止显示 C4619。

```C
/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>有外部“C”链接的 __declspec 属性 

在 Visual Studio 的早期版本中，在 `extern "C"` 链接规范之前应用 `__declspec(...)` 时，编译器会忽略 `__declspec(...)` 属性。 此行为导致生成用户意料之外的代码并且可能产生运行时影响。 Visual Studio 版本 15.3 中添加了此警告，但是默认关闭。 Visual Studio 2017 版本 15.5 默认启用此警告。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

要修复此错误，请将链接规范放在 __declspec 属性之前：

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

在 Visual Studio 2017 15.3 或更低版本（例如版本 10.0.15063.0，也称为 RS2 SDK）附带的某些 Windows SDK 标头上会有 C4768 这一个新警告。 但是，已修复更高版本 Windows SDK 标头（尤其是 ShlObj.h 和 ShlObj_core.h），所以它们不生成此警告。 看见来自 Windows SDK 标头的这一警告时，可以采取以下措施：

1. 切换到 Visual Studio 2017 版本 15.5 附带的最新 Windows SDK。
2. 关闭 Windows SDK 标头声明 #include 附近的警告：

   ```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>extern constexpr 链接 

在早期版本的 Visual Studio 中，编译器常常提供 `constexpr` 变量内部链接，甚至是在变量标记为 `extern` 的时候。 在 Visual Studio 2017 版本 15.5 中，新编译器开关 (/Zc:externConstexpr) 启用符合标准的正确行为。 这最终将成为默认设置。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

如果头文件包含声明 `extern constexpr` 的变量，需将它标记为 `__declspec(selectany)`以便正确组合其重复声明：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>不能在不完整的类类型上使用 typeid

在早期版本的 Visual Studio 中，编译器不正确地允许以下代码，导致可能不正确的类型信息。 在 Visual Studio 2017 版本 15.5 中，编译器正确引发错误：

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>std::is_convertible 目标类型

`std::is_convertible` 要求目标类型为有效返回类型。 在早期版本的 Visual Studio 中，编译器不正确地允许抽象类型，这可能导致不正确的重载决策和意外的运行时行为。  现在，以下代码正确引发错误 C2338：

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

若要避免此错误，使用 `is_convertible` 时应该比较指针类型，因为如果有一个类型是抽象的，那么非指针类型的比较可能会失败：

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a>动态异常规范的删除和 noexcept

在 C++17 中，`throw()` 是 `noexcept` 的别名，删除了 `throw(<type list>)` 和 `throw(...)`，并且某些类型可能包含 `noexcept`。 这可能导致符合 C++14 或更低版本的代码的源兼容性问题。 通常，使用 C++17 模式时，可以使用“/Zc:noexceptTypes-”开关还原为 `noexcept` 的 C++14 版本。 这样可以将源代码更新为符合 C++17，而无需在同时重写所有 `throw()` 代码。

现在，编译器还诊断 C++17 模式声明中或者带有新警告 C5043 的“/permissive-”所具有的更多不匹配的异常规范。

应用 /std:c++17 开关时，以下代码在 Visual Studio 2017 版本 15.5 中生成 C5043 和 C5040：

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```
要在使用“/std:c++17”的同时删除错误，请将“/Zc:noexceptTypes-”开关添加到命令行，或者更新代码以使用 `noexcept`，如以下示例中所示：

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>内联变量

现在，静态 constexpr 数据成员是隐式内联的，这意味着它们在类中的声明现在是它们的定义。 使用静态 constexpr 数据成员的外部定义是冗余的，现已弃用。 在 Visual Studio 2017 版本 15.5 中应用 /std:c++17 开关时，以下代码现在生成警告 C5041: "size": 不需要对 constexpr 静态数据成员进行外部定义，且在 C + + 17 中弃用了该类定义：

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>现在默认打开 extern "C" __declspec(...) 警告 C4768

Visual Studio 2017 版本 15.3 中添加了此警告，但是默认关闭。 在 Visual Studio 2017 版本 15.5 中，它默认打开。 有关详细信息，请参阅[有关 declspec 属性的新警告](#declspec)。

### <a name="defaulted-functions-and-declspecnothrow"></a>默认函数和 __declspec(nothrow)

以前，当相应基/成员函数允许异常时，编译器允许使用 `__declspec(nothrow)` 声明默认函数。 此行为与 C++ 标准冲突，可能导致在运行时发生未定义的行为。 如果有异常规范不匹配，标准要求此类函数定义为已删除。  在 /std:c++17 下，以下代码引发错误 C2280: 尝试引用已删除的函数*。*因为显式异常规范与隐式声明的异常规范不兼容，所以已隐式删除函数：


```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

要更正此代码，请从默认函数删除 __declspec(nothrow)，或者删除 `= default` 并提供函数定义以及任何所需异常处理：

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```
### <a name="noexcept-and-partial-specializations"></a>noexcept 和部分专用化
由于类型系统中有 noexcept，由于缺少 noexcept 函数指针的部分专用化，所以匹配特定“可调用”类型的部分专业化可能无法编译或选择主模板。

在这种情况下，可能需要添加额外的部分专用化以处理 noexcept 函数指针和成员函数的 noexcept 指针。 这些重载仅在 /std:c++17 模式中合规。 如果必须维持与 C++14 的向后兼容性，并且正在编写他人将使用的代码，那么应该保证这些新重载位于 `#ifdef` 指令内。 如果在自包含模块中工作，那么可以仅使用“/Zc:noexceptTypes-”开关进行编译，而不是使用 `#ifdef` 临界子句。

以下代码在 /std:c++14 下编译；但不能在 /std:c++17 下编译，会出现“错误 C2027: 使用了未定义的类型 "A\<T>"”：

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

以下代码在 /std:c++17 下成功，因为编译器选择新的部分专用化 `A<void (*)() noexcept>`：

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="see-also"></a>请参阅

[Visual C/C++ 语言一致性](visual-cpp-language-conformance.md)  
