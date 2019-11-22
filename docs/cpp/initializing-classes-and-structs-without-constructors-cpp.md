---
title: Brace initialization for classes, structs, and unions
description: Use brace initialization with any C++ class, struct or union
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 41ff38bc4bcc9ebca913b5e66b5ac2f395044222
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246505"
---
# <a name="brace-initialization"></a>Brace initialization

并不总是需要为类定义构造函数，特别是相对比较简单的类。 用户可以使用统一初始化来初始化类或结构的对象，如下面的示例所示：

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Note that when a class or struct has no constructor, you provide the list elements in the order that the members are declared in the class. If the class has a constructor, provide the elements in the order of the parameters. 如果类型具有隐式或显式声明的默认构造函数，则您可以使用默认大括号初始化（具有空大括号）。 例如，可通过使用默认和非默认大括号初始化来初始化以下类：

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

如果类具有非默认构造函数，则类成员在大括号初始值设定项中的显示顺序是对应参数在构造函数中的显示顺序，而不是成员的声明顺序（如上一示例中的 `class_a` 一样）。 否则，如果类型没有声明的构造函数，则成员在大括号初始值设定项中的显示顺序与其声明顺序一样，在这种情况下，您可初始化所需数量的公共成员，但无法跳过任何成员。 以下示例演示了在无声明的构造函数时在大括号初始化中使用的顺序：

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5("string", 'c', 2.0 }; // compiler error
}
```

如果默认构造函数已显式声明，但标记为“已删除”，则无法使用默认大括号初始化：

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

You can use brace initialization anywhere you would typically do initialization—for example, as a function parameter or a return value, or with the **new** keyword:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializer_list-constructors"></a>initializer_list constructors

The [initializer_list Class](../standard-library/initializer-list-class.md) represents a list of objects of a specified type that can be used in a constructor, and in other contexts. 您可通过使用大括号初始化构造 initializer_list：

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  To use this class, you must include the [\<initializer_list>](../standard-library/initializer-list.md) header.

可以复制 `initializer_list`。 在这种情况下，新列表的成员是对原始列表成员的引用：

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

标准库容器类以及 `string`、`wstring` 和 `regex` 具有 `initializer_list` 构造函数。 以下示例演示如何使用这些构造函数执行大括号初始化：

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```


## <a name="see-also"></a>请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)<br/>
[构造函数](../cpp/constructors-cpp.md)
