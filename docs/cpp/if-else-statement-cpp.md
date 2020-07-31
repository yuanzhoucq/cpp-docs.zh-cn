---
title: if-else 语句 (C++)
ms.date: 07/20/2019
description: 使用 c + + 中的 if 语句控制条件分支。
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: a9256e32c89890635c5473a85b4bb3b56bec26d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187564"
---
# <a name="if-else-statement-c"></a>if-else 语句 (C++)

控制条件分支。 仅当*if 表达式*的计算结果为非零值（或）时，才会执行*if 块*中的语句 **`true`** 。 如果*expression*的值为非零值，则将执行*语句 1*中的任何其他语句，并跳过 else 块（如果存在）。 如果*expression*的值为零，则跳过 if 块，并执行 else 块（如果存在）。 计算结果为非零值的表达式为

- **`true`**
- 非 null 指针，
- 任何非零算术值，或
- 一种类类型，该类型定义到算术、布尔或指针类型的明确转换。 （有关转换的信息，请参阅[标准转换](../cpp/standard-conversions.md)。）

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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

// C++17 - Visual Studio 2017 version 15.3 and later:
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

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a>带有初始值设定项的 if 语句

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： **`if`** 语句还可以包含声明和初始化命名变量的表达式。 如果只需要在 if 块范围内使用变量，请使用以下形式的 if 语句。

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

在语句的所有形式中， **`if`** 将计算除结构之外的任何值的*表达式*（包括所有副作用）。 Control 从语句传递 **`if`** 到程序中的下一条语句，除非其中一个*语句*包含[break](../cpp/break-statement-cpp.md)、 [continue](../cpp/continue-statement-cpp.md)或[goto](../cpp/goto-statement-cpp.md)。

**`else`** 语句的子句 `if...else` 与 **`if`** 同一作用域中不具有相应语句的最近一个语句相关联 **`else`** 。

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr">如果 constexpr 语句

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）：在函数模板中，可以使用**if constexpr**语句进行编译时分支决策，而无需使用多个函数重载。 例如，可以编写处理参数解包的单个函数（不需要零参数重载）：

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

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[switch 语句（c + +）](../cpp/switch-statement-cpp.md)
