---
title: 并发命名空间运算符 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 03079f8899f3b13c8509e1affd10a82191b1817c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228474"
---
# <a name="concurrency-namespace-operators-amp"></a>并发命名空间运算符 (AMP)

||||
|-|-|-|
|[operator！ =](#operator_neq)|[操作员](#operator_mod)|[操作员](#operator_star)|
|[operator +](#operator_add)|[操作员](#operator-)|[操作员](#operator_div)|
|[operator = =](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

确定指定的参数是否相等。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要比较的元组之一。

*_Rhs*<br/>
要比较的元组之一。

### <a name="return-value"></a>返回值

**`true`** 如果元组相同，则为;否则为 **`false`** 。

## <a name="operator"></a><a name="operator_neq"></a>operator！ =

确定指定的参数是否不相等。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要比较的元组之一。

*_Rhs*<br/>
要比较的元组之一。

### <a name="return-value"></a>返回值

**`true`** 如果元组不相等，则为;否则为 **`false`** 。

## <a name="operator"></a><a name="operator_add"></a>operator +

计算指定参数的按组件的和。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要添加的参数之一。

*_Rhs*<br/>
要添加的参数之一。

### <a name="return-value"></a>返回值

指定参数的按组件的和。

## <a name="operator-"></a><a name="operator-"></a>操作员

计算指定参数之间的以组件为的差。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要从中减去的参数。

*_Rhs*<br/>
要减去的参数。

### <a name="return-value"></a>返回值

指定参数之间的以组件为方差。

## <a name="operator"></a><a name="operator_star"></a>操作员

计算指定参数的按组件的积。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要相乘的元组之一。

*_Rhs*<br/>
要相乘的元组之一。

### <a name="return-value"></a>返回值

指定参数的按组件的积。

## <a name="operator"></a><a name="operator_div"></a>操作员

计算指定参数的按分量的商。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
要划分的元组。

*_Rhs*<br/>
要作为除数的元组。

### <a name="return-value"></a>返回值

指定参数的按组件的商。

## <a name="operator"></a><a name="operator_mod"></a>操作员

按指定的第二个参数计算第一个指定参数的模数。

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
元组参数的秩。

*_Lhs*<br/>
从中计算模的元组。

*_Rhs*<br/>
要作为模的元组。

### <a name="return-value"></a>返回值

第一个指定参数的结果将指定第二个指定的参数。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace-cpp-amp.md)
