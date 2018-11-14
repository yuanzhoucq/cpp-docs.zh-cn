---
title: 自动 （C++）
ms.date: 11/04/2016
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: f4d17069ed4e06a85b80d2027433ff87be6d1521
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518562"
---
# <a name="auto-c"></a>自动 （C++）

从其初始化表达式中推导声明的变量的类型。

## <a name="syntax"></a>语法

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>备注

**自动**关键字指示编译器使用的声明的变量或 lambda 表达式参数初始化表达式来推导其类型。

我们建议你使用**自动**关键字大多数情况下的，除非您确实需要转换 — 因为它提供以下优势：

- **可靠性：** 如果更改表达式的类型 — 这包括函数返回类型发生更改时，一切迎刃而解。

- **性能：** 您一定会进行任何转换。

- **可用性：** 无需担心类型名称拼写困难和拼写错误。

- **效率：** 编码可能更有效。

在其中可能不需要使用转换情况**自动**:

- 当需要特定类型且不需要执行任何其他操作时。

- 表达式模板帮助器类型 — 例如， `(valarray+valarray)`。

若要使用**自动**关键字，使用它而不是一种类型来声明变量，并指定初始化表达式。 此外，您可以修改**自动**使用说明符和声明符类似于关键字**const**，**易失性**，指针 (`*`)，引用 (`&`)，和右值引用 (`&&`)。 编译器计算初始化表达式，然后使用该信息来推断变量类型。

初始化表达式可以是赋值 （等号语法），直接初始化 （函数样式语法）、[运算符 new](new-operator-cpp.md)表达式或初始化表达式可以是*有关范围声明*中的参数[基于范围的语句 （C++）](../cpp/range-based-for-statement-cpp.md)语句。 有关详细信息，请参阅[初始值设定项](../cpp/initializers.md)和本文档后面的代码示例。

**自动**关键字是类型的占位符，但它本身不是一种类型。 因此，**自动**关键字不能使用强制转换或运算符如[sizeof](../cpp/sizeof-operator.md)并[typeid](../windows/typeid-cpp-component-extensions.md)。

## <a name="usefulness"></a>有用性

**自动**关键字是声明具有复杂的类型的变量的简单方法。 例如，可以使用**自动**来声明的变量的初始化表达式涉及模板、 指向函数的指针或指向成员的指针。

此外可以使用**自动**声明并初始化为 lambda 表达式的变量。 您不能自行声明变量的类型，因为仅编译器知道 lambda 表达式的类型。 有关详细信息，请参阅[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)。

## <a name="trailing-return-types"></a>尾部的返回类型

可以使用**自动**一起**decltype**类型说明符，以帮助编写模板库。 使用**自动**并**decltype**声明模板函数的返回类型取决于其模板自变量的类型。 或者，使用**自动**并**decltype**声明包装对其他函数的调用，然后返回任何内容是函数的返回类型的模板函数。 有关详细信息，请参阅[decltype](../cpp/decltype-cpp.md)。

## <a name="references-and-cv-qualifiers"></a>引用和 cv 限定符

请注意，使用**自动**删除引用、 const 限定符和 volatile 限定符。 请看下面的示例：

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

在上一示例中，myAuto 是 int，不是 int 引用，因此输出是`11 11`，而非`11 12`就会是这种情况，如果尚未删除引用限定符**自动**。

## <a name="type-deduction-with-braced-initializers-c14"></a>具有大括号内的初始值设定项 (C++ 14) 的类型推导

下面的代码示例演示如何初始化使用大括号的自动变量。 请注意之间 A 和 B 和 C 之间的差异和 e。

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>限制和错误消息

下表列出了对使用限制**自动**关键字和编译器发出的相应诊断错误消息。

|错误号|描述|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**自动**关键字不能与任何其他类型说明符组合。|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|使用声明的符号**自动**关键字必须具有初始值设定项。|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|你错误地使用**自动**关键字来声明类型。 例如，声明了方法返回类型或数组。|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md)， [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|不能使用声明的参数或模板参数**自动**关键字。|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|不能使用声明的方法或模板参数**自动**关键字。|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符号初始化之前无法使用。 在实践中，这意味着无法使用变量来初始化自身。|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|不能转换为与声明的类型，**自动**关键字。|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|使用声明的声明符列表中的所有符号**自动**关键字必须解析为同一类型。 有关详细信息，请参阅[声明和定义](declarations-and-definitions-cpp.md)。|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)并[typeid](../windows/typeid-cpp-component-extensions.md)运算符不能应用于使用声明的符号**自动**关键字。|

## <a name="examples"></a>示例

这些代码片段阐释了几种在其中**自动**可以使用关键字。

下面的声明等效。 在第一个语句中，变量`j`被声明为类型**int**。在第二个语句中，变量`k`推导为类型**int**由于初始化表达式 (0) 是一个整数。

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

以下声明等效，但第二个声明比第一个更简单。 若要使用的最令人信服的原因之一**自动**关键字为简单起见。

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

下面的代码片段将声明的变量类型`iter`并`elem`时**有关**和范围**为**循环启动。

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

使用下面的代码段**新**运算符和指针声明来声明指针。

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

下一个代码片段在每个声明语句中声明多个符号。 请注意，每个语句中的所有符号将解析为同一类型。

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

此代码片段使用条件运算符 (`?:`) 将变量 `x` 声明为值为 200 的整数：

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

下面的代码片段初始化变量`x`键入**int**、 可变`y`为引用类型**const int**，和变量`fp`为指向一个函数返回类型**int**。

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto & y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../cpp/auto-keyword.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[/Zc:auto（推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 运算符](../cpp/sizeof-operator.md)<br/>
[typeid](../windows/typeid-cpp-component-extensions.md)<br/>
[运算符 new](new-operator-cpp.md)<br/>
[声明和定义](declarations-and-definitions-cpp.md)<br/>
[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)<br/>
[初始值设定项](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
