---
title: '&lt;functional&gt; 函数'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
ms.openlocfilehash: 93b61f1d0342d7d4b7ddfc7fce4d64ea5e10a2eb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305154"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; 函数

||||
|-|-|-|
| [bind](#bind) | [bit_and](#bit_and) | [bit_not](#bit_not) |
| [bit_or](#bit_or) | [bit_xor](#bit_xor) | [cref](#cref) |
| [invoke](#invoke) | [mem_fn](#mem_fn) | [not_fn](#not_fn) |
| [ref](#ref) | [swap](#swap) | |

这些函数在 C + + 11 中已过时，在 C + + 17 中删除：

||||
|-|-|-|
| [bind1st](#bind1st) | [bind2nd](#bind2nd) | [mem_fun](#mem_fun) |
| [mem_fun_ref](#mem_fun_ref) | [ptr_fun](#ptr_fun) | |

在 C + + 17 中已弃用这些函数：

|||
|-|-|
| [not1](#not1) | [not2](#not2) |

## <a name="bind"></a> bind

将自变量绑定到可调用对象。

```cpp
template <class FT, class T1, class T2, ..., class TN>
unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>参数

*Fey*<br/>
要调用的对象的类型。

*TN*<br/>
第 N 个调用参数的类型。

*fn*<br/>
要调用的对象。

*tN*<br/>
第 N 个调用参数。

### <a name="remarks"></a>备注

类型`FT, T1, T2, ..., TN`必须是复制构造的并`INVOKE(fn, t1, ..., tN)`必须是有效的表达式对于某些值`w1, w2, ..., wN`。

第一个模板函数返回具有弱结果类型的转发调用包装器 `g`。 效果`g(u1, u2, ..., uM)`是`INVOKE(f, v1, v2, ..., vN, ` [invoke_result](../standard-library/invoke-result-class.md)`<FT cv (V1, V2, ..., VN)>::type)`，其中`cv`是 cv 限定符`g`的值和类型的绑定参数`v1, v2, ..., vN`确定按下面的指定。 你可以使用它将参数绑定到可调用的对象，从而使可调用对象具有定制的参数列表。

第二个模板函数返回转移调用包装器 `g`，该包装器具有作为 `RTy` 的同义词的嵌套类型 `result_type`。 `g(u1, u2, ..., uM)` 产生的作用是 `INVOKE(f, v1, v2, ..., vN, RTy)`，其中 `cv` 是 `g` 的 cv 限定符，绑定参数 `v1, v2, ..., vN` 的值和类型按以下指定内容确定。 你可以使用它将参数绑定到可调用的对象，从而使可调用对象具有定制的参数列表和指定的返回类型。

绑定参数 `v1, v2, ..., vN` 及其对应类型 `V1, V2, ..., VN` 的值取决于在对调用包装器 `g` 的 `bind` 和 cv 限定符 `cv` 调用过程中的类型 `Ti` 的对应参数 `ti` 的类型，如下所示：

如果 `ti` 类型为 `reference_wrapper<T>`，则参数 `vi` 为 `ti.get()`，其类型 `Vi` 为 `T&`；

如果的值`std::is_bind_expression<Ti>::value`是**true**自变量`vi`是`ti(u1, u2, ..., uM)`及其类型`Vi`是`result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

如果该值`j`的`std::is_placeholder<Ti>::value`参数不为零`vi`是`uj`及其类型`Vi`是`Uj&`;

否则参数 `vi` 为 `ti`，其类型 `Vi` 为 `Ti` `cv` `&`。

例如，给定函数 `f(int, int)` 后，表达式 `bind(f, _1, 0)` 返回转移调用包装器 `cw`，使得 `cw(x)` 调用 `f(x, 0)`。 表达式 `bind(f, 0, _1)` 返回转移调用包装器 `cw`，使得 `cw(x)` 调用 `f(0, x)`。

对的调用中的参数数目`bind`和参数`fn`必须等于可传递给可调用对象的参数数目`fn`。 例如，`bind(cos, 1.0)`正确无误，且两`bind(cos)`和`bind(cos, _1, 0.0)`不正确。

函数调用由 `bind` 返回的调用包装器的过程中的参数数量必须至少与对 `bind` 调用过程中的所有占位符参数的 `is_placeholder<PH>::value` 的最大编号值一样大。 例如，`bind(cos, _2)(0.0, 1.0)`是否正确 (并返回`cos(1.0)`)，和`bind(cos, _2)(0.0)`不正确。

### <a name="example"></a>示例

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a> bind1st

创建适配器，将二元函数对象转换为一元函数对象的一个帮助程序模板函数。 它将二元函数的第一个参数绑定到指定的值。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>参数

*func*<br/>
要转换为一元函数对象的二元函数对象。

*left*<br/>
要将二元函数对象的第一个参数绑定到的值。

### <a name="return-value"></a>返回值

将二元函数对象的第一个参数绑定到值而得出的一元函数对象*左*。

### <a name="remarks"></a>备注

函数绑定器是一种函数适配器。 因为它们返回的函数对象，它们可在某些类型的函数组合来构造更复杂和强大的表达式。

如果*func*是类型的对象`Operation`并`c`是常量，则`bind1st( func, c )`等同于[binder1st](../standard-library/binder1st-class.md)类构造函数`binder1st<Operation>( func, c )`，并更方便使用。

### <a name="example"></a>示例

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a> bind2nd

创建适配器，将二元函数对象转换为一元函数对象的一个帮助程序模板函数。 它将二元函数的第二个参数绑定到指定的值。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>参数

*func*<br/>
要转换为一元函数对象的二元函数对象。

*right*<br/>
要将二元函数对象的第二个参数绑定到的值。

### <a name="return-value"></a>返回值

绑定到的二元函数对象的第二个参数的一元函数对象结果*右*。

### <a name="remarks"></a>备注

函数绑定器是一种函数适配器。 因为它们返回的函数对象，它们可在某些类型的函数组合来构造更复杂和强大的表达式。

如果*func*是类型的对象`Operation`并`c`是常量，则`bind2nd( func, c )`等同于[binder2nd](../standard-library/binder2nd-class.md)类构造函数`binder2nd<Operation>( func, c )`，并更方便地使用。

### <a name="example"></a>示例

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a> bit_and

预定义的函数对象执行按位 AND 运算 (二元`operator&`) 对其自变量。

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

*类型*， *T*， *U*支持任何类型`operator&`接受指定或推断类型的操作数。

左侧<br/>
按位 AND 运算的左操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*T*。

右侧<br/>
按位 AND 运算的右操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*U*。

### <a name="return-value"></a>返回值

`Left & Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator&` 返回的类型。

### <a name="remarks"></a>备注

`bit_and` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator&` 的用户定义的类型。

## <a name="bit_not"></a> bit_not

预定义的函数对象执行按位求补 (NOT) 运算 (一元`operator~`) 对其自变量。 在 C + + 14 中添加。

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
{
    Type operator()(const Type& Right) const;
};

// specialized transparent functor for operator~
template <>
struct bit_not<void>
{
    template <class Type>
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>参数

*Type*<br/>
支持一元 `operator~` 的类型。

右侧<br/>
按位求补运算的操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移推断类型的左值或右值引用参数*类型*。

### <a name="return-value"></a>返回值

`~ Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator~` 返回的类型。

### <a name="remarks"></a>备注

`bit_not` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator~` 的用户定义的类型。

## <a name="bit_or"></a> bit_or

预定义的函数对象执行位或运算 (`operator|`) 对其自变量。

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

*类型*， *T*， *U*支持任何类型`operator|`接受指定或推断类型的操作数。

左侧<br/>
按位或运算的左操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*T*。

右侧<br/>
按位或运算的右操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*U*。

### <a name="return-value"></a>返回值

`Left | Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator|` 返回的类型。

### <a name="remarks"></a>备注

`bit_or` 函子被限制为基本数据类型的整型类型，或限制为实现 `operator|` 的用户定义的类型。

## <a name="bit_xor"></a> bit_xor

预定义的函数对象执行按位 XOR 运算 (二元`operator^`) 对其自变量。

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>参数

*类型*， *T*， *U*支持任何类型`operator^`接受指定或推断类型的操作数。

左侧<br/>
按位 XOR 运算的左操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*T*。

右侧<br/>
按位 XOR 运算的右操作数。 专用化的模板采用类型的左值引用参数*类型*。 专用化的模板可完美转移左值和右值引用参数的类型推断*U*。

### <a name="return-value"></a>返回值

`Left ^ Right` 的结果。 专专用化模板可完美转移结果，该结果具有由 `operator^` 返回的类型。

### <a name="remarks"></a>备注

`bit_xor` 函子被限制为基本数据类型的整型类型，或限制为实现二元 `operator^` 的用户定义的类型。

## <a name="cref"></a> cref

从变量构造常量 `reference_wrapper`。

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>参数

*Ty*<br/>
要包装的参数的类型。

*arg*<br/>
要包装的参数。

### <a name="remarks"></a>备注

第一个函数返回 `reference_wrapper<const Ty>(arg.get())`。 可以使用它来包装常量引用。 第二个函数返回 `reference_wrapper<const Ty>(arg)`。 可以使用它将包装的引用重新包装为常量引用。

### <a name="example"></a>示例

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }
```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="invoke"></a> invoke

调用具有给定参数的任何可调用对象。 添加 C + + 17 中。

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>参数

*Callable*<br/>
要调用的对象的类型。

*参数*<br/>
调用参数的类型。

*fn*<br/>
要调用的对象。

*args*<br/>
调用参数。

*specification*<br/>
**Noexcept**规范`std::is_nothrow_invocable_v<Callable, Args>)`。

### <a name="remarks"></a>备注

调用可调用对象*fn*使用的参数*args*。 有效地`INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)`，其中伪函数`INVOKE(f, t1, t2, ..., tN)`意味着以下操作之一：

- 当 `f` 是指向类 `T` 的成员函数的指针，且 `t1` 是类型 `T` 的对象、对类型 `T` 的对象的引用或对派生自 `T` 的类型的对象的引用时，它表示 `(t1.*f)(t2, ..., tN)`。 也就是说，当`std::is_base_of<T, std::decay_t<decltype(t1)>>::value`为 true。

- `(t1.get().*f)(t2, ..., tN)` 当`f`是指向类成员函数`T`并`std::decay_t<decltype(t1)>`专用化的`std::reference_wrapper`。

- `((*t1).*f)(t2, ..., tN)` 当`f`是指向类成员函数`T`和`t1`不是上述类型之一。

- 当 N == 1，且 `f` 是指向类 `T` 的成员数据的指针，`t1` 是类型 `T` 的对象、对类型 `T` 的对象的引用或对派生自 `T` 的类型的对象的引用时，它表示 `t1.*f`。  也就是说，当`std::is_base_of<T, std::decay_t<decltype(t1)>>::value`为 true。

- `t1.get().*f` 当 N = = 1 和`f`是指向成员数据的类`T`并`std::decay_t<decltype(t1)>`专用化的`std::reference_wrapper`。

- `(*t1).*f` 当 N = = 1 和`f`是指向成员数据的类`T`和`t1`不是上述类型之一。

- 在所有其他情况下，它表示 `f(t1, t2, ..., tN)`。

可调用对象的结果类型的信息，请参阅[invoke_result](invoke-result-class.md)。 可调用类型的谓词，请参阅[is_invocable，is_invocable_r，is_nothrow_invocable，is_nothrow_invocable_r 类](is-invocable-classes.md)。

### <a name="example"></a>示例

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a> mem_fn

生成一个简单的调用包装器。

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>参数

*RTy*<br/>
包装函数的返回类型。

*Ty*<br/>
成员函数指针的类型。

### <a name="remarks"></a>备注

模板函数返回一个简单的调用包装器`cw`，具有弱结果类型，以便在表达式`cw(t, a2, ..., aN)`等同于`INVOKE(pm, t, a2, ..., aN)`。 它不会引发任何异常。

返回的调用包装器派生自`std::unary_function<cv Ty*, RTy>`(和定义嵌套的类型`result_type`的同义词*RTy*嵌套类型`argument_type`的同义词`cv Ty*`) 仅当类型*Ty*是指向成员函数具有 cv 限定符`cv`不采用任何参数。

返回的调用包装器派生自`std::binary_function<cv Ty*, T2, RTy>`(和定义嵌套的类型`result_type`的同义词*RTy*，则嵌套类型`first argument_type`的同义词`cv Ty*`，以及将嵌套的类型`second argument_type`同义词`T2`) 仅当类型*Ty*是指向成员函数具有 cv 限定符`cv`采用一种参数，类型`T2`。

### <a name="example"></a>示例

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }
```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a> mem_fun

帮助程序模板函数，在使用指针自变量进行初始化的情况下，用来构造成员函数的函数对象适配器。 在 C + + 11 中已过时[mem_fn](#mem_fn)并[绑定](#bind)，并在 C + + 17 中移除。

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>参数

*pMem*<br/>
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

### <a name="return-value"></a>返回值

类型 `mem_fun_t` 或 `mem_fun1_t` 的 **const** 或 **non_const** 函数对象。

### <a name="example"></a>示例

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a> mem_fun_ref

帮助程序模板函数，在使用引用参数进行初始化的情况下，用来构造成员函数的函数对象适配器。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>参数

*pMem*<br/>
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

### <a name="return-value"></a>返回值

一个**const**或`non_const`类型的函数对象`mem_fun_ref_t`或`mem_fun1_ref_t`。

### <a name="example"></a>示例

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a> not1

返回一元谓词的补集。 弃用的项[not_fn](#not_fn)在 C + + 17 中。

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>参数

*predicate*<br/>
要求反的一元谓词。

### <a name="return-value"></a>返回值

已修改的一元谓词的求反的一元谓词。

### <a name="remarks"></a>备注

如果`unary_negate`一个一元谓词，从构造`predicate( x )`，则会返回`!predicate( x )`。

### <a name="example"></a>示例

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a> not2

返回二元谓词的补集。 弃用的项[not_fn](#not_fn)在 C + + 17 中。

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>参数

*func*<br/>
要进行求反的二元谓词。

### <a name="return-value"></a>返回值

已修改的二元谓词的求反的二元谓词。

### <a name="remarks"></a>备注

如果`binary_negate`从二元谓词构造`binary_predicate( x, y )`，则会返回`!binary_predicate( x, y )`。

### <a name="example"></a>示例

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="not_fn"></a> not_fn

`not_fn`函数模板采用可调用对象并返回可调用对象。 返回可调用对象更高版本调用带有某些参数，它将其传递给原始的可调用对象，并以逻辑方式对结果取反。 它将保留已包装可调用对象的常量限定和值类别行为。 `not_fn` 是 C + + 17 中的新增功能，并替换已弃用`std::not1`， `std::not2`， `std::unary_negate`，和`std::binary_negate`。

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>参数

*func*<br/>
可调用对象用于构造转发调用包装器。

### <a name="remarks"></a>备注

模板函数返回类似的调用包装器`return call_wrapper(std::forward<Callable>(func))`根据此仅限阐述的类：

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

可调用对象上的显式构造函数*func*需要类型`std::decay_t<Callable>`若要满足的要求`MoveConstructible`，和`is_constructible_v<FD, Callable>`必须为 true。 初始化已包装可调用对象`fd`从`std::forward<Callable>(func)`，并引发任何异常的构造由引发`fd`。

包装公开调用运算符按左值或右值引用类别和常量限定来区分，如下所示：

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

前两个相同`return !std::invoke(fd, std::forward<Args>(args)...)`。 第二个两个都作为相同`return !std::invoke(std::move(fd), std::forward<Args>(args)...)`。

### <a name="example"></a>示例

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a> ptr_fun

帮助程序模板函数，用于将一元和二元函数指针分别转换为一元和二元自适应函数。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>参数

*pfunc*<br/>
要转换为自适应函数的一元或二元函数指针。

### <a name="return-value"></a>返回值

第一个模板函数返回一元函数[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`，**结果**> (\* `pfunc`)。

第二个模板函数返回二元函数[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**， **Arg2**，**结果**> (\* `pfunc`)。

### <a name="remarks"></a>备注

函数指针是一个函数对象。 它可能会传递到的任何算法都需要函数作为参数，但它不是自适应。 需要使用与适配器，例如，将值绑定到它或对其求反其嵌套类型的信息。 通过 `ptr_fun` 帮助程序函数转换一元和二元函数指针可允许函数适配器使用一元和二元函数指针。

### <a name="example"></a>示例

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a> ref

从变量构造常量 `reference_wrapper` 。

```cpp
template <class Ty>
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>返回值

对 `arg`的引用；具体而言，是指对 `reference_wrapper<Ty>(arg)`的引用。

### <a name="example"></a>示例

下面的示例定义了两个函数：一个绑定到字符串变量，另一个绑定到通过调用 `ref`计算的字符串变量的引用。 当变量的值发生更改时，第一个函数将继续使用旧值，而第二个函数将使用新值。

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a> swap

交换两个 `function` 对象。

```cpp
template <class FT>
void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>参数

*FT*<br/>
由函数对象控制的类型。

*f1*<br/>
第一个函数对象。

*f2*<br/>
第二个函数对象。

### <a name="remarks"></a>备注

该函数返回 `f1.swap(f2)`。

### <a name="example"></a>示例

```cpp
// std__functional__swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    swap(fn0, fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```

## <a name="see-also"></a>请参阅

[\<functional>](../standard-library/functional.md)<br/>
