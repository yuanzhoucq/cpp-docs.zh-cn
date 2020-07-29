---
title: ':::no-loc(constexpr)::: (C++)'
description: 'C + + 语言 :::no-loc(constexpr)::: 关键字指南。'
ms.date: 01/28/2020
f1_keywords:
- :::no-loc(constexpr):::_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- ':::no-loc(constexpr):::'
- ':::no-loc(const):::'
- ':::no-loc(inline):::'
- ':::no-loc(goto):::'
- ':::no-loc(try):::'
- ':::no-loc(if):::'
- ':::no-loc(switch):::'
- ':::no-loc(for):::'
- ':::no-loc(while):::'
ms.openlocfilehash: d66dc333b7ac9fba94221dc4efa723c7919ef88f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229020"
---
# <a name="no-locconstexpr-c"></a>:::no-loc(constexpr)::: (C++)

关键字 **`:::no-loc(constexpr):::`** 是在 c + + 11 中引入的，并在 c + + 14 中得到改进。 它表示* :::no-loc(const)::: ant 表达式*。 与类似 **`:::no-loc(const):::`** ，可将其应用于变量：当任何代码尝试将值进行 mod 时，将引发编译器错误 :::no-loc(if)::: 。 与不同 **`:::no-loc(const):::`** ， **`:::no-loc(constexpr):::`** 还可以应用于函数和类 :::no-loc(const)::: ructors。 **`:::no-loc(constexpr):::`** 指示值或返回值为 ant，并在 :::no-loc(const)::: 编译时计算（如果可能）。

**`:::no-loc(constexpr):::`** 整数值可用于需要整数的任何位置 :::no-loc(const)::: ，例如模板参数和数组声明中的。 在编译时（而非运行时）计算某个值时，它可帮助您的程序运行速度更快，使用更少的内存。

为了限制编译时 ant 计算的复杂性 :::no-loc(const)::: ，以及它们对编译时间的潜在影响，c + + 14 标准要求 ant 表达式中的类型为 :::no-loc(const)::: [文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>语法

> **`:::no-loc(constexpr):::`***文本类型* *ident :::no-loc(if)::: ier* **=** * :::no-loc(const)::: * **;**\
> **`:::no-loc(constexpr):::`***文本类型* *ident :::no-loc(if)::: ier* **{** * :::no-loc(const)::: ant-expression* **}** **;**\
> **`:::no-loc(constexpr):::`***文本类型* *ident :::no-loc(if)::: ier* **（** *params* **）** **;**\
> **`:::no-loc(constexpr):::`***ctor* **（** *params* **）** **;**

## <a name="parameters"></a>参数

*化*\
一个或多个参数，每个参数必须是文本类型，并且本身必须是 :::no-loc(const)::: ant 表达式。

## <a name="return-value"></a>返回值

**`:::no-loc(constexpr):::`** 变量或函数必须返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="no-locconstexpr-variables"></a>:::no-loc(constexpr)::: 变量

和变量的主要 d :::no-loc(if)::: f) **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** 是在 **`:::no-loc(const):::`** 运行时，可以将变量的初始化推迟。 **`:::no-loc(constexpr):::`** 变量必须在编译时进行初始化。  所有 **`:::no-loc(constexpr):::`** 变量都是 **`:::no-loc(const):::`** 。

- **`:::no-loc(constexpr):::`** 如果变量具有文本类型并已初始化，则可以使用声明该变量。 如果初始化 :::no-loc(for)::: 由 ructor 按 med-v 进行 :::no-loc(const)::: ，则 :::no-loc(const)::: 必须将 ructor 声明为 **`:::no-loc(constexpr):::`** 。

- **`:::no-loc(constexpr):::`** 当同时满足这两个条件时，可以声明引用：引用的对象由 :::no-loc(const)::: ant 表达式进行初始化，并且在初始化期间调用的任何隐式转换也是 :::no-loc(const)::: ant 表达式。

- 变量或函数的所有声明都 **`:::no-loc(constexpr):::`** 必须具有 **`:::no-loc(constexpr):::`** 规范 :::no-loc(if)::: ier。

```cpp
:::no-loc(constexpr)::: float x = 42.0;
:::no-loc(constexpr)::: float y{108};
:::no-loc(constexpr)::: float z = exp(5, 3);
:::no-loc(constexpr)::: int i; // Error! Not initialized
int j = 0;
:::no-loc(constexpr)::: int k = j + 1; //Error! j not a :::no-loc(const):::ant expression
```

## <a name="no-locconstexpr-functions"></a><a name=":::no-loc(constexpr):::_functions"></a>:::no-loc(constexpr):::函数

**`:::no-loc(constexpr):::`** 当使用代码需要函数时，该函数的返回值可在编译时。 使用代码要求在编译时返回值以初始化 **`:::no-loc(constexpr):::`** 变量，或提供一个非类型模板参数。 如果其参数为 **`:::no-loc(constexpr):::`** 值， **`:::no-loc(constexpr):::`** 函数将生成编译时 :::no-loc(const)::: ant。 使用非参数调用时 **`:::no-loc(constexpr):::`** ，或在编译时不需要其值时，它会在运行时生成一个值，如常规函数。 （这种双重行为使您不必编写 **`:::no-loc(constexpr):::`** 同一函数的和非 **`:::no-loc(constexpr):::`** 版本。）

**`:::no-loc(constexpr):::`** 函数或 :::no-loc(const)::: ructor 是隐式的 **`:::no-loc(inline):::`** 。

以下规则适用于 :::no-loc(constexpr)::: 函数：

- **`:::no-loc(constexpr):::`** 函数必须接受并仅返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

- **`:::no-loc(constexpr):::`** 函数可以是递归的。

- 它不能是[虚拟](../cpp/virtual-cpp.md)的。 :::no-loc(const):::不能定义 ructor，因为 **`:::no-loc(constexpr):::`** 封闭类具有任何虚拟基类。

- 主体可以定义为 `= default` 或 `= delete`。

- 主体不能包含任何 **`:::no-loc(goto):::`** 语句或 **`:::no-loc(try):::`** 块。

- 非模板的显式专用化 **`:::no-loc(constexpr):::`** 可以声明为 **`:::no-loc(constexpr):::`** ：

- 模板的显式专用化 **`:::no-loc(constexpr):::`** 还不一定要 **`:::no-loc(constexpr):::`** ：

以下规则适用于 **`:::no-loc(constexpr):::`** Visual Studio 2017 和更高版本中的函数：

- 它可以包含 **`:::no-loc(if):::`** 和 **`:::no-loc(switch):::`** 语句以及所有循环语句，包括 **`:::no-loc(for):::`** 、基于范围的 **`:::no-loc(for):::`** 、 **`:::no-loc(while):::`** 和。 ** :::no-loc(while)::: **

- 它可能包含局部变量声明，但必须对变量进行初始化。 它必须是文本类型，不能是 **`static`** 或线程本地类型。 本地声明的变量不需要为 **`:::no-loc(const):::`** ，并且可能会改变。

- **`:::no-loc(constexpr):::`** 非 **`static`** 成员函数不需要是隐式的 **`:::no-loc(const):::`** 。

```cpp
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 在 Visual Studio 调试器中，调试未优化的调试版本时，可以 **`:::no-loc(constexpr):::`** 通过在函数内放置一个断点来确定是否在编译时计算该函数。 如果命中该断点，则在运行时调用该函数。  如果未命中，则在编译时调用该函数。

## <a name="extern-no-locconstexpr"></a>部:::no-loc(constexpr):::

[/Zc： externConstexpr](../build/reference/zc-extern:::no-loc(constexpr):::.md)编译器选项导致编译器将[外部链接](../c-language/external-linkage.md)应用到使用**extern :::no-loc(constexpr)::: **声明的变量。 在 Visual Studio 的早期版本中，默认情况下或在 **/zc： externConstexpr-** 为 spec :::no-loc(if)::: i 时， **`:::no-loc(constexpr):::`** 即使使用关键字，visual studio 也会对变量应用内部链接 **`extern`** 。 **/Zc： externConstexpr**选项从 Visual Studio 2017 Update 15.6 开始提供，并在默认情况下处于关闭状态。 [/Permissive-](../build/reference/permissive-standards-con:::no-loc(for):::mance.md)选项不启用 **/zc： externConstexpr**。

## <a name="example"></a>示例

下面的示例演示 **`:::no-loc(constexpr):::`** 变量、函数和用户定义类型。 在中的最后一个语句中 `main()` ， **`:::no-loc(constexpr):::`** 成员函数 `GetValue()` 是一个运行时调用，因为在编译时不需要知道值。

```cpp
// :::no-loc(constexpr):::.cpp
// Compile with: cl /EHsc /W4 :::no-loc(constexpr):::.cpp
#include <iostream>

using namespace std;

// Pass by value
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
:::no-loc(constexpr)::: float exp2(:::no-loc(const)::: float& x, :::no-loc(const)::: int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
:::no-loc(constexpr)::: int length(:::no-loc(const)::: T(&)[N])
{
    return N;
}

// Recursive :::no-loc(constexpr)::: function
:::no-loc(constexpr)::: int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    :::no-loc(constexpr)::: explicit Foo(int i) : _i(i) {}
    :::no-loc(constexpr)::: int GetValue() :::no-loc(const):::
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is :::no-loc(const)::::
    :::no-loc(constexpr)::: Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    :::no-loc(constexpr)::: float x = exp(5, 3);
    :::no-loc(constexpr)::: float y { exp(2, 5) };
    :::no-loc(constexpr)::: int val = foo.GetValue();
    :::no-loc(constexpr)::: int f5 = fac(5);
    :::no-loc(const)::: int nums[] { 1, 2, 3, 4 };
    :::no-loc(const)::: int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>要求

Visual Studio 2015 或更高版本。

## <a name="see-also"></a>另请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)\
[:::no-loc(const):::](../cpp/:::no-loc(const):::-cpp.md)
