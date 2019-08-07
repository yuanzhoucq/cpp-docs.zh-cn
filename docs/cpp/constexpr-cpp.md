---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821094"
---
# <a name="constexpr-c"></a>constexpr (C++)

关键字**constexpr**已在 C++ 11 中引入的以及在 C++ 14 中改进。 它表示*常量表达式*。 与**const**类似, 它可以应用于变量, 以便在任何代码尝试修改该值时引发编译器错误。 与**const**不同, **constexpr**还可以应用于函数和类构造函数。 **constexpr**指示值 (或返回值) 是常量, 并且 (如果可能) 在编译时计算。

如果需要常数值, 例如在模板参数和数组声明中, 则可以使用**constexpr**整数值。 在编译时 (而不是在运行时) 可以计算某个值时, 它可以帮助您的程序更快地运行和使用更少的内存。

若要限制编译时常量计算的复杂性, 以及它们在编译时可能产生的影响, c + + 14 标准要求常量表达式中的类型为[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>语法

> **constexpr** *文本类型* *标识符* **=** *常量表达式* **;** 
>  **constexpr** *文本类型* *标识符* **{** *常量表达式* **}** **;** 
>  **constexpr** *文本类型* *标识符* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>参数

*params*<br/>
一个或多个参数, 每个参数必须是文本类型, 并且本身必须是常量表达式。

## <a name="return-value"></a>返回值

Constexpr 变量或函数必须返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="constexpr-variables"></a>constexpr 变量

Const 和 constexpr 变量的主要区别在于, 可以将 const 变量的初始化推迟到运行时。 Constexpr 变量必须在编译时进行初始化。  所有 constexpr 变量均为常量。

- 如果变量具有文本类型并已初始化, 则可以使用**constexpr**来声明变量。 如果初始化由构造函数执行, 则构造函数必须声明为**constexpr**。

- 如果所引用的对象已由常数表达式初始化，并且在初始化期间所调用的任何隐式转换也均是常数表达式，则可能将引用声明为 constexpr。

- **Constexpr**变量或函数的所有声明都必须具有**constexpr**说明符。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>constexpr 函数

**Constexpr**函数是指在使用代码需要时返回值可以在编译时计算的函数。 在编译时使用代码需要返回值, 例如, 初始化**constexpr**变量或提供一个非类型模板参数。 如果其参数为**constexpr**值, 则**constexpr**函数会生成编译时常量。 使用非**constexpr**参数调用时, 或在编译时不需要其值时, 它会在运行时生成一个值, 如常规函数。 (这种双重行为使你不必为同一函数编写**constexpr**和非**constexpr**版本。)

**Constexpr**函数或构造函数是隐式**内联**的。

以下规则适用于 constexpr 函数:

- **Constexpr**函数必须接受并仅返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

- **Constexpr**函数可以是递归的。

- 它不能是[虚拟](../cpp/virtual-cpp.md)的。 如果封闭类具有任何虚拟基类, 则不能将构造函数定义为 constexpr。

- 主体可以定义为 `= default` 或 `= delete`。

- 正文可以不包含**goto**语句或 try 块。

- 可以将非 constexpr 模板的显式专用化声明为**constexpr**:

- **Constexpr**模板的显式专用化还不必是**constexpr**:

以下规则适用于 Visual Studio 2017 和更高版本中的**constexpr**函数:

- 它可以包含**if**和**switch**语句以及所有循环语句, 包括、、、和等。

- 它可能包含局部变量声明, 但必须对变量进行初始化, 必须是文本类型, 不能是静态的或本地的。 本地声明的变量不需要是常量, 并且可能会改变。

- Constexpr 非静态成员函数不需要隐式常量。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 在 Visual Studio 调试器中, 调试未优化的调试版本时, 可以通过在一个**constexpr**函数中放置一个断点来判断该函数是否在编译时进行计算。 如果命中该断点，则在运行时调用该函数。  如果未命中，则在编译时调用该函数。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externConstexpr](../build/reference/zc-externconstexpr.md)编译器选项导致编译器将[外部链接](../c-language/external-linkage.md)应用到使用**extern constexpr**声明的变量。 在 Visual Studio 的早期版本中, 如果指定了 **/zc: externConstexpr** , 则 visual studio 会将内部链接应用到**constexpr**变量, 即使使用**extern**关键字也是如此。 **/Zc: externConstexpr**选项从 Visual Studio 2017 Update 15.6 开始提供, 并在默认情况下处于关闭状态。 /Permissive-选项不启用 **/zc: externConstexpr**。

## <a name="example"></a>示例

下面的示例演示**constexpr**变量、函数和用户定义类型。 在 main () 中的最后一个语句中, **constexpr**成员函数 GetValue () 是一个运行时调用, 因为在编译时不需要知道值。

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
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

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>要求

Visual Studio 2015 或更高版本。

## <a name="see-also"></a>请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
