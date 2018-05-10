---
title: '&lt;tuple&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
dev_langs:
- C++
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: d6f921f85ffc6ef6d7985d66fe8637f044965176
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="lttuplegt-functions"></a>&lt;tuple&gt; 函数

||||
|-|-|-|
|[get](#get)|[make_tuple](#make_tuple)|[tie](#tie)|

## <a name="get"></a>  get

按索引或类型（在 C++14 中）从 `tuple` 对象获取元素。

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>参数

`Index` 要获取的元素的索引。

`Types` 在此元组，按声明顺序排列中声明类型的序列。

`T` 要获取的元素的类型。

`Tuple` Std:: tuple 包含任意数目的元素。

### <a name="remarks"></a>备注

模板函数返回对索引 `Index`处的值或 `T` 对象中类型为 `tuple` 的值的引用。

如果元组中包含的 T 类型元素的个数不为一个，则调用 `get<T>(Tuple)` 将生成编译器错误。

### <a name="example"></a>示例

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_tuple"></a>  make_tuple

从元素值中生成一个 `tuple`。

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>参数

`TN` Nth 函数参数的类型。

`tN` Nth 函数参数的值。

### <a name="remarks"></a>备注

模板函数返回 `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)`，如果对应类型 `Ti` 是 `cv` `reference_wrapper<X>`，则每个类型 `Vi` 都为 `X&`；否则为 `Ti`。

`make_tuple` 的优势之一在于要存储的对象类型由编译器自动确定，而不必显式指定。 使用 `make_tuple<int, int>(1, 2)` 时请不要使用显式模板参数（如 `make_tuple`），因为它冗长而多余并会增加复杂的右值引用问题，可能会导致编译失败。

### <a name="example"></a>示例

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="tie"></a>  平分

从元素引用中生成一个 `tuple`。

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>参数

`TN` 第 n 个元组元素的基类型。

### <a name="remarks"></a>备注

此模板函数返回 `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)`。

### <a name="example"></a>示例

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>请参阅

[\<tuple>](../standard-library/tuple.md)<br/>
