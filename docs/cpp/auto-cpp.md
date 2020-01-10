---
title: 自动 （C++）
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 0991c836d1ade663be3e1b734ec4745796b91abd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301647"
---
# <a name="auto-c"></a>自动 （C++）

从其初始化表达式中推导声明的变量的类型。

> [!NOTE]
> C++标准为此关键字定义原始和修订的含义。 在 Visual Studio 2010 之前， **auto**关键字在*自动*存储类中声明变量;即具有本地生存期的变量。 从 Visual Studio 2010 开始， **auto**关键字声明一个变量，该变量的类型是从其声明中的初始化表达式推导出来的。 [/Zc： auto&#91;&#93; ](../build/reference/zc-auto-deduce-variable-type.md)编译器选项控制**auto**关键字的含义。

## <a name="syntax"></a>语法

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>备注

**Auto**关键字指示编译器使用已声明变量的初始化表达式或 lambda 表达式参数来推导其类型。

在大多数情况下，我们建议你使用**auto**关键字，除非你确实需要转换，因为它具有以下优势：

- **可靠性：** 如果表达式的类型发生更改（这包括在函数返回类型发生更改时），则它将正常工作。

- **性能：** 您可以保证不会进行任何转换。

- **可用性：** 无需担心类型名称拼写错误和拼写错误。

- **效率：** 你的编码可能更高效。

可能不希望使用**auto**的转换情况：

- 当需要特定类型且不需要执行任何其他操作时。

- 表达式模板帮助程序类型，例如 `(valarray+valarray)`。

若要使用**auto**关键字，请使用它（而不是类型）来声明变量，并指定初始化表达式。 此外，还可以使用说明符和声明符（如**const**、 **volatile**、指针（`*`）、引用（`&`）和右值引用（`&&`）修改**auto**关键字。 编译器计算初始化表达式，然后使用该信息来推断变量类型。

初始化表达式可以是赋值 （等号语法），直接初始化 （函数样式语法）、[运算符 new](new-operator-cpp.md)表达式或初始化表达式可以是*有关范围声明*中的参数[基于范围的语句 （C++）](../cpp/range-based-for-statement-cpp.md)语句。 有关详细信息，请参阅本文档后面的[初始值设定项](../cpp/initializers.md)和代码示例。

**Auto**关键字是类型的占位符，但它本身不是类型。 因此， **auto**关键字不能用于转换或运算符，例如[sizeof](../cpp/sizeof-operator.md)和（对于C++/cli） [typeid](../extensions/typeid-cpp-component-extensions.md)。

## <a name="usefulness"></a>有用性

**Auto**关键字是声明具有复杂类型的变量的一种简单方法。 例如，您可以使用**auto**声明一个变量，其中的初始化表达式包含模板、指向函数的指针或指向成员的指针。

还可以使用**auto**来声明变量并将其初始化为 lambda 表达式。 您不能自行声明变量的类型，因为仅编译器知道 lambda 表达式的类型。 有关详细信息，请参阅[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)。

## <a name="trailing-return-types"></a>尾部的返回类型

可以结合使用**auto**和**decltype**类型说明符来帮助编写模板库。 使用**auto**和**decltype**声明其返回类型依赖于其模板参数类型的模板函数。 或者，使用**auto**和**decltype**声明一个模板函数，该函数包装对其他函数的调用，然后返回该函数的返回类型的任何内容。 有关详细信息，请参阅[decltype](../cpp/decltype-cpp.md)。

## <a name="references-and-cv-qualifiers"></a>引用和 cv 限定符

请注意，使用**自动**删除引用、常量限定符和可变限定符。 请看下面的示例：

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

在上面的示例中，myAuto 是一个 int，而不是一个 int 引用，因此 `11 11`输出，而不是在不是由**auto**删除引用限定符的情况下 `11 12`。

## <a name="type-deduction-with-braced-initializers-c14"></a>具有大括号内的初始值设定项 (C++ 14) 的类型推导

下面的代码示例演示如何使用大括号初始化自动变量。 请注意 B 和 C 之间的差异以及 A 和 E 之间的差异。

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

下表列出了对**auto**关键字的使用限制以及编译器发出的相应诊断错误消息。

|错误号|描述|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**Auto**关键字不能与任何其他类型说明符组合。|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|使用**auto**关键字声明的符号必须具有初始值设定项。|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|错误地使用了**auto**关键字声明类型。 例如，声明了方法返回类型或数组。|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md)、 [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|不能使用**auto**关键字声明参数或模板参数。|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|不能使用**auto**关键字声明方法或模板参数。|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符号初始化之前无法使用。 在实践中，这意味着无法使用变量来初始化自身。|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|不能强制转换为使用**auto**关键字声明的类型。|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|声明符列表中使用**auto**关键字声明的所有符号都必须解析为相同的类型。 有关详细信息，请参阅[声明和定义](declarations-and-definitions-cpp.md)。|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)和[typeid](../extensions/typeid-cpp-component-extensions.md)运算符不能应用于使用**auto**关键字声明的符号。|

## <a name="examples"></a>示例

这些代码片段说明了可以使用**auto**关键字的一些方式。

下面的声明等效。 在第一个语句中，变量 `j` 声明为**int**类型。在第二个语句中，将变量 `k` 推导为类型**int** ，因为初始化表达式（0）是整数。

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

以下声明等效，但第二个声明比第一个更简单。 使用**auto**关键字的最有说服力的原因之一是简单。

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

以下代码片段**在循环的** **for**和 range 开始时声明 `iter` 和 `elem` 的变量类型。

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

下面的代码片段使用**new**运算符和指针声明来声明指针。

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

下面的代码片段将变量 `x` 初始化为**int**类型的变量 `y`，对类型**const int**的引用进行变量 `fp`，并将变量为指向返回**int**类型的函数的指针。

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>另请参阅

[auto 关键字](../cpp/auto-keyword.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[/Zc:auto（推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 运算符](../cpp/sizeof-operator.md)<br/>
[typeid](../extensions/typeid-cpp-component-extensions.md)<br/>
[运算符 new](new-operator-cpp.md)<br/>
[声明和定义](declarations-and-definitions-cpp.md)<br/>
[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)<br/>
[初始值设定项](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
