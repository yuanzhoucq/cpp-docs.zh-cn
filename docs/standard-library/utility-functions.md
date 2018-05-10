---
title: '&lt;utility&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: a26a4a0cab0bdea8a7a642cc760da0f3fc79b471
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltutilitygt-functions"></a>&lt;utility&gt; 函数

||||
|-|-|-|
|[exchange](#exchange)|[forward](#forward)|[get 函数 &lt;utility&gt;](#get)|
|[make_pair](#make_pair)|[move](#move)|[swap](#swap)|

## <a name="exchange"></a>  exchange

**(C++14)** 向对象赋予新值并返回其旧值。

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>参数

`val` 将接收 new_val 的值的对象。

`new_val` 其值被复制或移到 val 对象。

### <a name="remarks"></a>备注

对于复杂类型，`exchange` 可避免在移动构造函数可用时复制旧值、避免在新值是临时对象或进行移动时复制新值，并且可使用任何可用的转换赋值运算符接受任何类型作为新值。 Exchange 函数不同于 [std::swap](../standard-library/algorithm-functions.md#swap)，后者的左参数不会移动或复制到右参数。

### <a name="example"></a>示例

下面的示例说明如何使用 `exchange`。 在实际情况下，`exchange` 对难以复制的大型对象非常有用：

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a>  forward

如果自变量是右值或右值引用，则有条件地将其自变量强制转换为右值引用。 这会将自变量的右值状态还原到转发函数，以支持完美转发。

```cpp
template <class Type>    // accepts lvalues
constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Type`|传入 `Arg` 的值的类型，可能不同于 `Arg` 的类型。 通常由转发函数的模板自变量决定。|
|`Arg`|要强制转换的自变量。|

### <a name="return-value"></a>返回值

如果传入 `Arg` 的值最初为右值或右值引用，则返回对 `Arg` 的右值引用；否则，返回 `Arg`，而不修改其类型。

### <a name="remarks"></a>备注

你必须指定显式模板参数来调用 `forward`。

`forward` 不转发其参数。 而是在其参数最初为右值或右值引用时，通过有条件地将参数强制转换为右值引用，`forward` 使得编译器能够在得知转发的参数的原始类型后执行重载决策。 转发函数的实参的表面类型可能不同于其原始类型，例如，当右值用作函数的实参并绑定到形参名称时；拥有名称可使其成为左值，而无论该值是否作为右值实际存在，`forward` 将还原实参的右值状态。

还原参数原始值的右值状态以执行重载决策被称为“完美转发”。 通过完美转发，模板函数可接受任一引用类型的自变量，并在必要时还原其右值状态以执行正确的重载决策。 通过使用完美转发，你可以保留右值的移动语义，而且无需提供仅根据其自变量的引用类型而变化的函数的重载。

## <a name="get"></a>get

按索引位置或类型从 `pair` 对象获取元素。

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&
get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr const tuple_element_t<Index, pair<T1, T2>>&
get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
constexpr tuple_element_t<Index, pair<T1, T2>>&&
get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>参数

`Index` 指定元素的从 0 开始的索引。

`T1` 第一个 pair 元素的类型。

`T2` 第二个 pair 元素的类型。

`pr` 要从选择的对。

### <a name="remarks"></a>备注

每个模板函数都返回对其 `pair` 参数的元素的引用。

对于索引重载，如果 `Index` 的值为 0，则这些函数返回 `pr.first` ；如果 `Index` 的值为 1，则这些函数返回 `pr.second`。 类型 `RI` 是返回的元素的类型。

对于不具有索引参数的重载，要返回的元素由类型参数推导。 如果 `get<T>(Tuple)` 中包含的 T 类型元素的个数不为一个，则调用 `pr` 将生成编译器错误。

### <a name="example"></a>示例

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```

## <a name="make_pair"></a>  make_pair

一种可用来构造 `pair` 类型对象的模板函数，其中，组件类型将根据作为参数传递的数据类型自动进行选择。

```cpp
template <class T, class U>
pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>参数

`Val1` 初始化的第一个元素的值`pair`。

`Val2` 初始化的第二个元素的值`pair`。

### <a name="return-value"></a>返回值

所构造的配对对象：`pair`< `T`，`U`>( `Val1`, `Val2`)。

### <a name="remarks"></a>备注

`make_pair` 可以将 [reference_wrapper 类](../standard-library/reference-wrapper-class.md)类型的对象转换为引用类型，将衰减数组和函数转换为指针。

在返回的 `pair` 对象中，`T` 通过以下方式确定：

- 如果输入类型 `T` 为 `reference_wrapper<X>`，则返回的类型 `T` 为 `X&`。

- 否则，返回的类型 `T` 为 `decay<T>::type`。 如果不支持 [decay 类](../standard-library/decay-class.md)，则返回的类型 `T` 与输入类型 `T` 相同。

返回的类型 `U` 以类似的方式通过输入类型 `U` 来确定。

`make_pair` 的优势之一在于要存储的对象类型由编译器自动确定，而不必显式指定。 使用 `make_pair<int, int>(1, 2)` 时请不要使用显式模板参数（如 `make_pair`），因为它冗长而多余并会增加复杂的右值引用问题，可能会导致编译失败。 就此示例来说，正确的语法应该是 `make_pair(1, 2)`

利用 `make_pair` 帮助程序函数，还可以实现向需要一个配对作为输入参数的函数传递两个值。

### <a name="example"></a>示例

有关如何使用 helper 函数 `make_pair` 声明和初始化对的示例，请参阅 [pair 结构](../standard-library/pair-structure.md)。

## <a name="move"></a>  move

无条件将其自变量强制转换为右值引用，从而表示其可以移动（如果其类型支持移动）。

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Type`|一种从 `Arg` 中传递的参数类型推导出的类型（与引用折叠规则一起）。|
|`Arg`|要强制转换的自变量。 虽然 `Arg` 的类型看起来指定为右值引用，但 `move` 也接受左值参数，原因是左值引用可以绑定到右值引用。|

### <a name="return-value"></a>返回值

作为右值引用 `Arg`，无论其类型是否是引用类型。

### <a name="remarks"></a>备注

模板参数 `Type` 不应显式指定，而应从 `Arg` 中传递的值类型进行推导。 `Type` 的类型将根据引用折叠规则进行进一步调整。

`move` 不会移动其参数。 相反，通过无条件将其参数（可能是左值）强制转换为右值引用，它使得编译器随后能够移动（而不是复制）在 `Arg` 中传递的值（如果其类型支持移动）。 如果其类型不支持移动，则将进行复制。

如果 `Arg` 中传递的值为左值（也就是说，它具有名称或可以采用其地址），则它在发生移动时将会失效。 在移动 `Arg` 中传递的值后，请勿按照其名称或地址来引用它。

## <a name="swap"></a>  swap

交换两个 [pair 结构](../standard-library/pair-structure.md)对象的元素。

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`left`|一个 `pair` 类型的对象。|
|`right`|一个 `pair` 类型的对象。|

### <a name="remarks"></a>备注

`swap` 的优势之一在于要存储的对象类型由编译器自动确定，而不必显式指定。 使用 `swap<int, int>(1, 2)` 时请不要使用显式模板参数（如 `swap`），因为它冗长而多余并会增加复杂的右值引用问题，可能会导致编译失败。

## <a name="see-also"></a>请参阅

[\<utility>](../standard-library/utility.md)<br/>
