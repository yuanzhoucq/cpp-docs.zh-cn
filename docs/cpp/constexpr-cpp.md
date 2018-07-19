---
title: constexpr （C++） |Microsoft 文档
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f95f6c98138ff1eb52750c1b8593795ca28c784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417992"
---
# <a name="constexpr-c"></a>constexpr (C++)

关键字**constexpr**已在 C++ 11 中引入的以及在 C++ 14 中改进。 这意味着*常量表达式*。 如**const**，它可以应用于变量，以便如果任何代码试图修改的值，则将引发编译器错误。 与不同**const**， **constexpr**还可以应用于函数和类构造函数。 **constexpr**指示的值或返回值是常数，并且如果可能，将在编译时计算。

A **constexpr**每当 const 整数时必需的如在模板自变量和数组声明，则可以使用整数值。 并且时可以在编译时，而不是运行时计算某个值，它可以帮助你更快地运行，并使用较少的内存的程序。

若要限制计算编译时常量的复杂度以及它们的编译时间的潜在影响，C++ 14 标准要求在常量表达式中涉及的类型是限于[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>语法

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>参数

 *params*  
一个或多个参数必须是文本类型并且其本身必须是常量表达式。

## <a name="return-value"></a>返回值


 Constexpr 变量或函数必须返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="constexpr-variables"></a>constexpr 变量

 Const 和 constexpr 变量之间的主要区别在于：const 变量的初始化可以延迟到运行时，而 constexpr 变量必须在编译时进行初始化。  所有 constexpr 变量均为常量。

- 可使用声明变量**constexpr**，如果它具有文本类型并且未被初始化。 如果由构造函数执行初始化，则构造函数必须声明为**constexpr**。

- 如果所引用的对象已由常数表达式初始化，并且在初始化期间所调用的任何隐式转换也均是常数表达式，则可能将引用声明为 constexpr。

- 所有声明**constexpr**变量或函数必须具有**constexpr**说明符。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> constexpr 函数

A **constexpr**函数是使用代码需要它时，可以在编译计算其返回值。  当其自变量为**constexpr**值，并且使用代码需要返回值在编译时，例如，初始化**constexpr**变量或提供一个非类型模板自变量，它会生成编译时常量。 当调用使用非**constexpr**自变量，或不需要在编译时其值时，它将与正则函数一样运行时生成一个值。  (此双重行为使你无需编写**constexpr**和非-**constexpr**同一函数的版本。)

A **constexpr**函数或构造函数是隐式**内联**。

以下规则适用于 constexpr 函数：

- A **constexpr**函数必须接受并仅返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

- A **constexpr**函数可以是递归。

- 它不能是[虚拟](../cpp/virtual-cpp.md)。 A 不能定义为 constexpr 构造函数，如果封闭类具有任何虚拟基类。

- 正文可以定义为 **= 默认**或 **= 删除**。

- 不能包含正文**goto**语句或的 try 块。

- 可以将非 constexpr 模板的显式专用化声明为**constexpr**:

- 显式专用化**constexpr**模板没有也显示为**constexpr**:

以下规则适用于**constexpr** Visual Studio 2017 及更高版本的函数：

- 它可能包含**如果**和**切换**语句以及所有循环语句包括**为**、 基于范围的 for，**时**，和**执行-时**。
 
- 它可能包含局部变量声明，但该变量必须进行初始化，必须文本的类型，并且不能为静态或线程本地。 本地声明变量不需要是常量，且可能会发生变化。

- Constexpr 非静态成员函数不需要是隐式常量。


```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 注意： 在 Visual Studio 调试器中，当调试非优化调试生成，你可以判断是否**constexpr**函数正在评估在编译时通过将放在其内部断点。 如果命中该断点，则在运行时调用该函数。  如果未命中，则在编译时调用该函数。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)编译器选项使编译器将[外部链接]()对使用声明的变量**extern constexpr**。 在早期版本的 Visual Studio 中，并按默认或如果 **/Zc:externConstexpr-** 指定，则 Visual Studio 将应用到的内部链接**constexpr**变量即使**extern**使用关键字。 **/Zc:externConstexpr**选项是在 Visual Studio 2017 更新 15.6 中开始提供。 和默认处于关闭状态。 /Permissive-option 不会启用 /Zc:externConstexpr。

## <a name="example"></a>示例

 下面的示例演示**constexpr**变量、 函数和用户定义的类型。 请注意，在 main （） 中的最后一个语句**constexpr**成员函数 getvalue （） 是运行时调用，因为不需要在编译时已知该值。

```cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    //foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    //Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    //Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}

```

## <a name="requirements"></a>要求

Visual Studio 2015

## <a name="see-also"></a>请参阅

- [声明和定义](../cpp/declarations-and-definitions-cpp.md)
- [const](../cpp/const-cpp.md)
