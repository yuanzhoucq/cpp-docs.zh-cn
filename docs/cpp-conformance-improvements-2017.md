---
title: "C++ 编译器一致性改进 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: b26df320266a1465e214c70c29c7077d04ffb4b9
ms.lasthandoff: 03/06/2017

---
   
# <a name="c-conformance-improvements-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] 中的 C++ 一致性改进

## <a name="new-language-features"></a>新语言功能  
编译器支持通用 constexpr 和聚合的 NSDMI，现具有 C++14 标准版中的全部新增功能。 请注意，编译器仍缺少 C++11 和 C++98 标准版中的一些功能。

### <a name="c11"></a>C++11：
**在更多库中支持表达式 SFINAE** - Visual C++ 编译器持续改进对表达式 SFINAE 的支持，SFINAE 是模板参数推导和替换所必需的，其中 decltype 和 constexpr 表达式可能显示为模板参数。 有关详细信息，请参阅 [Visual Studio 2017 RC 中的表达式 SFINAE 改进之处](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3)。 


### <a name="c-14"></a>C++ 14：
**用于聚合的 NSDMI** - 聚合是一个数组或类，不具有用户提供的构造函数、专用或受保护的非静态数据成员、基类，也不具有虚拟函数。 从 C++14 开始，聚合可能包含成员初始值设定项。 有关详细信息，请参阅 [Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html)（成员初始值设定项和聚合）。

**constexpr** - 现在允许声明为 constexpr 的表达式包含某些种类的声明：if 和 switch 语句、loop 语句，以及某些对象的突变，这些对象的生命期开始时间处于 constexpr 表达式计算范围内。 此外，不再需要 constexpr 非静态成员函数为隐式 const。 有关详细信息，请参阅 [Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)（放松对 constexpr 函数的约束）。 

### <a name="c17"></a>C++17：
**Terse static_assert**（适用于 /std:c++latest）在 C++17 中，static_assert 的消息参数是可选的。 有关详细信息，请参阅 [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)（扩展 static_assert, v2）。 

**[[fallthrough]] 属性**（适用于 /std:c++latest）[[fallthrough]] 属性可以在 switch 语句的上下文中用作对预期发生贯穿行为的编译器的提示。 这可防止编译器在这类情况下发出警告。 有关详细信息，请参阅 [Wording for [[fallthrough]] attribute](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf)（[[fallthrough]] 属性的用词）。 

**通用的基于范围的 for 循环**（不需要编译器开关）基于范围的 for 循环不再需要 begin() 和 end() 返回相同类型的对象。 这使得 end() 能够返回类似于 Ranges-V3 方案中定义的 ranges 所使用的那种 sentinel 对象。 有关详细信息，请参阅 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)（通用化基于范围的 for 循环）和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3)（GitHub 上的 range-v3 库）。 


有关 Visual Studio 2015 Update 3 中一致性改进的完整列表，请参阅 [Visual C++ What's New 2003 through 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx)（Visual C++ 2003 至 2015 中的新增功能）。

## <a name="bug-fixes"></a>Bug 修复
### <a name="copy-list-initialization"></a>复制列表初始化
Visual Studio 2017 使用并非在 Visual Studio 2015 中捕获的初始值设定项列表正确引发与对象创建相关的编译器错误，并可能导致故障或未定义的运行时行为。  根据 N4594 13.3.1.7p1，在复制列表初始化中，编译器需要考虑用于重载决策的显式构造函数，但是如果实际选择了该重载，则必须引发错误。 

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
struct MyList {
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
当条件性运算的左侧操作数在 constexpr 上下文中无效时，Visual Studio 2017 会正确引发错误。 下列代码在 Visual Studio 2015 中进行编译，但不在 Visual Studio 2017 中进行编译：

```cpp  
template<int N>
struct array 
{
       int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
       return arr.size() == 10 || arr.size() == 11; // error starting in Visual Studio 2017
}
```
要更正错误，可将 array::size() 函数声明为 constexpr 或从 f 中删除 constexpr 限定符。 

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
                        // as an argument to a variadic function
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
对于使用 CStringW 生成和管理的字符串，提供的 ‘operator LPCWSTR()’ 应该用来将 CStringW 对象强制转换为格式字符串所需的 C 指针。

```cpp  
CStringW str1;
CStringW str2;
str1.Format(… , static_cast<LPCWSTR>(str2));
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
若要更正此错误，将运算符 int() 声明为 const。 

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
为了支持表达式 SFINAE，编译器现在会在声明模板而不是实例化模板时分析 decltype 参数。 因此，如果在 decltype 参数中找到非依赖专用化，则它不会被推迟到实例化时间，而会被立即处理，并且将在此时诊断产生的所有错误。  

以下示例显示了在声明时引发的这类编译器错误：

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
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

### <a name="default-initializers-for-value-class-members-ccli"></a>值类成员的默认初始值设定项 (C++/CLI)
在 Visual Studio 2015 及更早版本中，编译器允许（但会忽略）值类成员的默认成员初始值设定项。  值类的默认初始化始终对成员执行零初始化；不允许使用默认构造函数。  在 Visual Studio 2017 中，默认成员初始值设定项引发编译器错误，如下例所示：

```cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>默认索引器 (C++/CLI)
在 Visual Studio 2015 及更早版本中，编译器在某些情况下将默认属性误识别为默认索引器。 有可能通过使用标识符“default”访问该属性来解决这个问题。 在 C++11 中将默认值引入为关键字后，解决方法本身会出现问题。 因此，在 Visual Studio 2017 中，需要解决方法的 Bug 都已修复，现在将“default”用于访问类的默认属性时，编译器会引发错误。

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

## <a name="see-also"></a>另请参阅  
[Visual C/C++ 语言一致性](visual-cpp-language-conformance.md)  

