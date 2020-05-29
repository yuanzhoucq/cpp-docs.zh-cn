---
title: integer_sequence 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: 3de64f7855b5158f1565580d305e2a6eeaf3e76f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031467"
---
# <a name="integer_sequence-class"></a>integer_sequence 类

表示整数序列。 可以用于推导并展开可变参数类型中作为自变量传递给函数的参数包（如 std::tuple\<T...>）。

## <a name="syntax"></a>语法

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>参数

*T*\
值的类型；必须是整数类型：bool、char、char16_t、char32_t、wchar_t或是带符号或无符号整数类型。

*瓦尔斯*\
非类型参数包，表示整数类型 T 的值序列。

## <a name="members"></a>成员

|||
|-|-|
|`static size_t size() noexcept`|序列中的元素数。|
|`typedef T value_type`|序列中每个元素的类型。 必须是整数类型。|

## <a name="remarks"></a>备注

直接传递给函数的参数包可以在没有任何特殊库帮助程序的进行解压缩。 当参数包属于传递给函数的类型，并且需要索引来访问元素时，对它进行解压缩的最简单方法是使用 `integer_sequence` 及其相关类型别名 `make_integer_sequence`、`index_sequence`、`make_index_sequence` 和 `index_sequence_for`。

## <a name="example"></a>示例

如下示例基于原始方案 [N3658](https://wg21.link/n3658)。 它演示如何使用 `integer_sequence` 从 `std::array<T,N>` 创建 `std::tuple`，以及如何使用 `integer_sequence` 访问元组成员。

在 `a2t` 函数中，`index_sequence` 是基于 `size_t` 整数类型的 `integer_sequence` 的别名。 `make_index_sequence` 是一个别名，会在编译时使用与调用方传入的数组相同数量的元素创建一个从零开始的 `index_sequence`。 `a2t` 通过值将 `index_sequence` 传递到 `a2t_`（其中表达式 `a[I]...` 对 `I` 进行解压缩），随后将元素提供给使用它们作为单独参数的 `make_tuple`。 例如，如果序列包含三个元素，则 `make_tuple` 称为 make_tuple(a[0], a[1], a[2])。 当然，数组元素本身可以是任何类型。

应用函数接受一个[std：：元组](../standard-library/tuple-class.md)，并使用`integer_sequence``tuple_size`帮助器类生成 。 请注意[，std：:decay_t](../standard-library/decay-class.md)是必需的[，因为tuple_size](../standard-library/tuple-size-class-tuple.md)不适用于引用类型。 `apply_` 函数对元组成员进行解压缩，并将它们作为单独参数转发到函数调用。 在此示例中，该函数是一个打印出值的简单 lambda 表达式。

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

若要为参数包创建 `index_sequence`，请使用 `index_sequence_for`\<T...>（即 `make_index_sequence`\<sizeof...(T)> 的别名）

## <a name="requirements"></a>要求

标题： \<type_traits\>

命名空间：std

## <a name="see-also"></a>请参阅

[椭圆和瓦里亚迪奇模板](../cpp/ellipses-and-variadic-templates.md)
