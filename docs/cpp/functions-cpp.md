---
title: 函数 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 5beadbbf283a64f12dab7f0ee39a267ec1797861
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213432"
---
# <a name="functions-c"></a>函数 (C++)

函数是执行某种操作的代码块。 函数可以选择性地定义使调用方可以将实参传递到函数中的输入形参。 函数可以选择性地返回值作为输出。 函数可用于在单个可重用块中封装常用操作（理想情况是使用可清晰地描述函数行为的名称）。 以下函数接受来自调用方的两个整数并返回它们的总和;*a*和*b*是*parameters*类型的参数 **`int`** 。

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

可以在程序中的任意位置调用或*调用*函数。 传递给函数的值是*参数*，其类型必须与函数定义中的参数类型兼容。

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

对于函数长度没有实际限制，不过良好的设计应以执行单个明确定义的任务的函数为目标。 复杂算法应尽可能分解成易于理解的更简单函数。

在类范围中定义的函数称为成员函数。 在 C++ 中（与其他语言不同），函数还可以在命名空间范围中定义（包括隐式全局命名空间）。 此类函数称为*自由函数*或*非成员函数*;它们广泛用于标准库。

函数可能会*重载*，这意味着，如果函数的不同版本不同于形参的数量和/或类型，则可能会共享同一名称。 有关详细信息，请参阅[函数重载](../cpp/function-overloading.md)。

## <a name="parts-of-a-function-declaration"></a>函数声明的各个部分

最小函数*声明*包括返回类型、函数名和参数列表（可能为空），以及提供编译器附加说明的可选关键字。 下面的示例是一个函数声明：

```cpp
int sum(int a, int b);
```

函数定义包含声明和*主体*，这是大括号之间的所有代码：

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

后接分号的函数声明可以出现在程序中的多个位置处。 它必须在每个翻译单元中对该函数的任何调用之前出现。 根据单个定义规则 (ODR)，函数定义必须仅在程序中出现一次。

函数声明的必需部分有：

1. 返回类型，指定函数返回的值的类型; **`void`** 如果不返回任何值，则为。 在 c + + 11 中， **`auto`** 是有效的返回类型，它指示编译器从 return 语句推断类型。 在 c + + 14 中 `decltype(auto)` 也是允许的。 有关详细信息，请参阅下面的“返回类型中的类型推导”。

1. 函数名，必须以字母或下划线开头，不能包含空格。 一般而言，标准库函数名中的前导下划线指示私有成员函数，或不是供你的代码使用的非成员函数。

1. 参数列表（一组用大括号限定、逗号分隔的零个或多个参数），指定类型以及可以用于在函数体内访问值的可选局部变量名。

函数声明的可选部分有：

1. **`constexpr`**，指示函数的返回值是一个常数值，可以在编译时计算。

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. 其链接规范， **`extern`** 或 **`static`** 。

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   有关详细信息，请参阅[翻译单元和链接](../cpp/program-and-linkage-cpp.md)。

1. **`inline`**，指示编译器将对函数的每个调用替换为函数代码本身。 在某个函数快速执行并且在性能关键代码段中重复调用的情况下，内联可以帮助提高性能。

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   有关详细信息，请参阅[内联函数](../cpp/inline-functions-cpp.md)。

1. 一个 **`noexcept`** 表达式，指定函数是否会引发异常。 在下面的示例中，如果 `is_pod` 表达式的计算结果为，则该函数不引发异常 **`true`** 。

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   有关详细信息，请参阅 [`noexcept`](../cpp/noexcept-cpp.md)。

1. （仅限成员函数）Cv 限定符，指定该函数是 **`const`** 还是 **`volatile`** 。

1. （仅限成员函数） **`virtual`** 、 **`override`** 或 **`final`** 。 **`virtual`** 指定可以在派生类中重写函数。 **`override`** 表示派生类中的函数正在重写虚函数。 **`final`** 表示不能在任何进一步的派生类中重写函数。 有关详细信息，请参阅[虚拟函数](../cpp/virtual-functions.md)。

1. （仅限成员函数） **`static`** 应用于成员函数意味着该函数不与类的任何对象实例相关联。

1. （仅限非静态成员函数）引用限定符，用于指定当隐式对象参数（ `*this` ）为右值引用与左值引用时，编译器要选择的函数的重载。 有关详细信息，请参阅[函数重载](function-overloading.md#ref-qualifiers)。

下图显示了函数定义的各个部分。 灰色区域是函数体。

![函数定义部分](../cpp/media/vc38ru1.gif "函数定义部分") <br/>
函数定义部分

## <a name="function-definitions"></a>函数定义

*函数定义*包含声明和函数体，括在大括号中，其中包含变量声明、语句和表达式。 下面的示例演示了一个完整的函数定义：

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

函数体内声明的变量称为局部变量。 它们会在函数退出时超出范围；因此，函数应永远不返回对局部变量的引用！

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>const 和 constexpr 函数

可以将成员函数声明为 **`const`** ，以指定不允许函数更改类中任何数据成员的值。 通过将成员函数声明为 **`const`** ，可以帮助编译器强制实施*const 正确性*。 如果有人错误地尝试使用声明为的函数修改对象 **`const`** ，则会引发编译器错误。 有关详细信息，请参阅[const](const-cpp.md)。

将函数声明为，在 **`constexpr`** 编译时可能会确定它生成的值。 Constexpr 函数的执行速度通常比常规函数快。 有关详细信息，请参阅 [`constexpr`](constexpr-cpp.md)。

## <a name="function-templates"></a>函数模板

函数模板类似于类模板；它基于模板自变量生成具体功能。 在许多情况下，模板能够推断类型参数，因此无需显式指定它们。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

有关详细信息，请参阅[函数模板](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>函数形参和实参

函数具有零种或多种类型的逗号分隔参数列表，其中每个参数都具有可以用于在函数体内访问它的名称。 函数模板可以指定其他类型或值参数。 调用方传递实参（其类型与形参列表兼容的具体值）。

默认情况下，参数通过值传递给函数，这意味着函数会收到所传递的对象的副本。 对于大型对象，创建副本可能成本高昂，并非始终必要。 若要使参数按引用传递（特别是左值引用），请将引用限定符添加到参数中：

```cpp
void DoSomething(std::string& input){...}
```

当函数修改通过引用传递的参数时，它会修改原始对象，而不是本地副本。 若要防止函数修改此类参数，请将参数限定为 const&：

```cpp
void DoSomething(const std::string& input){...}
```

**C + + 11：** 若要显式处理通过右值引用或左值引用传递的参数，请在参数上使用双与号以指示通用引用：

```cpp
void DoSomething(const std::string&& input){...}
```

在参数声明列表中使用单个关键字声明的函数 **`void`** 不采用任何参数，前提是该关键字 **`void`** 是自变量声明列表中的第一个和唯一一个成员。 **`void`** 列表中其他位置的类型参数会产生错误。 例如：

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

请注意，尽管指定参数是非法的 **`void`** ，但此处所述的除外，派生自类型的类型 **`void`** （如指向 **`void`** 的指针和的数组 **`void`** ）可以出现在参数声明列表的任何位置。

### <a name="default-arguments"></a>默认自变量

函数签名中的最后一个或几个参数可能会分配有默认自变量，这意味着调用方可能会在调用函数时省略自变量（除非要指定某个其他值）。

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

有关详细信息，请参阅[默认参数](../cpp/default-arguments.md)。

## <a name="function-return-types"></a>函数返回类型

函数不能返回其他函数或内置数组;但是，它可以返回指向这些类型的指针，或返回生成函数对象的*lambda*。 除了这些情况外，函数可能返回范围内的任何类型的值，或者它可能不返回值，在这种情况下，返回类型为 **`void`** 。

### <a name="trailing-return-types"></a>结尾返回类型

“普通”返回类型位于函数签名左侧。 *尾随返回类型*位于签名的最右侧，前面是 **`->`** 运算符。 当返回值的类型取决于模板参数时，结尾返回类型在函数模板中尤其有用。

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

当与 **`auto`** 尾随返回类型一起使用时，它只用作 decltype 表达式生成的任何一个占位符，而不是自身执行类型推导。

## <a name="function-local-variables"></a>函数局部变量

在函数体中声明的变量称为局部变量或只是一个*本地**变量*。 非静态局部变量仅在函数体中可见，如果它们在堆栈上声明，则会在函数退出时超出范围。 构造局部变量并按值返回它时，编译器通常可以执行*命名的返回值优化*，以避免不必要的复制操作。 如果通过引用返回局部变量，则编译器会发出警告，因为调用方为使用该引用而进行的任何尝试会在局部变量已销毁之后进行。

在 C++ 中，局部变量可以声明为静态。 变量仅在函数体中可见，但是对于函数的所有实例，存在变量的单个副本。 局部静态对象将在 `atexit` 指定的终止期间销毁。 如果某个静态对象由于程序的控制流跳过了其声明而未构造，则不会尝试销毁该对象。

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>返回类型中的类型推导（c + + 14）

在 c + + 14 中，可以使用 **`auto`** 指示编译器从函数体推断返回类型，而不必提供尾随返回类型。 请注意， **`auto`** 始终推导为值返回值。 使用 `auto&&` 可指示编译器推导引用。

在此示例中， **`auto`** 将推断为 lhs 和 rhs 之和的非常量值副本。

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

请注意，不 **`auto`** 会保留它推导的类型的常量类型。 对于返回值需要保留其参数的常量性或引用性的转发函数，可以使用 **`decltype(auto)`** 关键字，该关键字使用 **`decltype`** 类型推断规则并保留所有类型信息。 **`decltype(auto)`** 可用作左侧的普通返回值或作为尾随返回值。

下面的示例（基于[N3493](https://wg21.link/n3493)中的代码）显示 **`decltype(auto)`** 用于启用在实例化模板之前不知道的返回类型中的函数自变量的完美转发。

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>从函数返回多个值

有多种方法可从函数返回多个值：

1. 封装命名类或结构对象中的值。 要求类或结构定义对调用方可见：

    ```cpp
    #include <string>
    #include <iostream>

    using namespace std;

    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```

1. 返回 std：：元组或 std：:p air 对象：

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }

    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;

        // --or--

        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;

        return 0;
    }
    ```

1. **Visual Studio 2017 版本15.3 及更高版本**（适用于 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ）：使用结构化绑定。 结构化绑定的优点是，存储返回值的变量在声明时将进行初始化，在某些情况下，这两个变量的效率会大大提高。 在语句中， `auto[x, y, z] = f();` 括号会引入和初始化整个函数块范围内的名称。

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;

        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```

1. 除了使用返回值本身以外，您还可以通过定义任意数量的参数以使用传递引用来返回值，以便函数可以修改或初始化调用方提供的对象的值。 有关详细信息，请参阅[引用类型函数自变量](reference-type-function-arguments.md)。

## <a name="function-pointers"></a>函数指针

C++ 通过与 C 语言相同的方式支持函数指针。 但是更加类型安全的替代方法通常是使用函数对象。

**`typedef`** 如果声明返回函数指针类型的函数，则建议使用来声明函数指针类型的别名。  例如：

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

如果不执行此操作，则函数声明的正确语法可以通过用函数名称和自变量列表替换标识符（上例中为 `fp`）来从函数指针的声明符语法推导出，如下所示：

```cpp
int (*myFunction(char* s))(int);
```

前面的声明等效于上面使用的声明 **`typedef`** 。

## <a name="see-also"></a>另请参阅

[函数重载](../cpp/function-overloading.md)<br/>
[带有变量参数列表的函数](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[显式默认的和已删除的函数](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[函数的参数相关名称（Koenig）查找](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[默认参数](../cpp/default-arguments.md)<br/>
[内联函数](../cpp/inline-functions-cpp.md)
