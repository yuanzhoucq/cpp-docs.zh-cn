---
title: if-else 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee04052a0088ff95a41ccb6083abc334287ea2b
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820641"
---
# <a name="if-else-statement-c"></a>if-else 语句 (C++)

控制条件分支。 中的语句*if 块*仅当执行*if 表达式*的计算结果为非零值 （或 TRUE）。 如果的值*表达式*为非零值，*语句 1*和块中的任何其他语句执行和其他的块，如果存在，则跳过。 如果的值*表达式*是零，则跳过 if 块，并且执行其他的块，（如果存在）。 表达式的计算结果为非零值。

- true
- 非 null 指针，
- 任何非零值的算术值，或
- 类定义明确转换为算术、 布尔值或指针类型。 (有关转换的信息，请参阅[标准转换](../cpp/standard-conversions.md)。)

## <a name="syntax"></a>语法

```cpp
if ( expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
}
```

## <a name="example"></a>示例

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if_with_init"></a> 如果语句具有初始值设定项

**Visual Studio 2017 15.3 及更高版本**(适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)):**如果**语句还可能包含声明和初始化命名的变量的表达式。 该变量时，才需要 if 块的作用域内时，请使用这种形式的 if 语句。

## <a name="example"></a>示例

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

中的所有窗体**如果**语句*表达式*，它可以具有结构之外的任何值计算，包括所有副作用。 控制权将传递从**如果**语句在程序中的下一个语句除非之一*语句*s 包含[中断](../cpp/break-statement-cpp.md)，[继续](../cpp/continue-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)。

**Else**子句`if...else`语句是与最接近以前**如果**不具有相应的同一范围中的语句**其他**语句。

## <a name="a-nameifconstexpr-if-constexpr-statements"></a><a name="if_constexpr"> 如果 constexpr 语句

**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 在函数模板，你可以使用**如果 constexpr**语句进行编译时分支决策，而无需不必使用多个函数重载。 例如，可以编写单个函数的句柄参数解包 （需要零参数重载均没有）：

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[switch 语句 (C++)](../cpp/switch-statement-cpp.md)