---
title: 并发命名空间运算符 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376290"
---
# <a name="concurrency-namespace-operators-amp"></a>并发命名空间运算符 (AMP)

||||
|-|-|-|
|[操作员！](#operator_neq)|[操作员百分比](#operator_mod)|[运算符*](#operator_star)|
|[运算符*](#operator_add)|[操作员-](#operator-)|[操作员/](#operator_div)|
|[运算符*](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>运算符*

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
元组参数的排名。

*_Lhs*<br/>
要比较的元数之一。

*_Rhs*<br/>
要比较的元数之一。

### <a name="return-value"></a>返回值

如果元数相等，**则为 true;** 否则，**假**。

## <a name="operator"></a><a name="operator_neq"></a>操作员！

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
元组参数的排名。

*_Lhs*<br/>
要比较的元数之一。

*_Rhs*<br/>
要比较的元数之一。

### <a name="return-value"></a>返回值

如果元结不相等，**则为 true;** 否则，**假**。

## <a name="operator"></a><a name="operator_add"></a>运算符*

计算指定参数的组件级总和。

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
元组参数的排名。

*_Lhs*<br/>
要添加的参数之一。

*_Rhs*<br/>
要添加的参数之一。

### <a name="return-value"></a>返回值

指定参数的组件和

## <a name="operator-"></a><a name="operator-"></a>操作员-

计算指定参数之间的组件差异。

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
元组参数的排名。

*_Lhs*<br/>
要从中减去的参数。

*_Rhs*<br/>
要减去的参数。

### <a name="return-value"></a>返回值

指定参数之间的组件差异。

## <a name="operator"></a><a name="operator_star"></a>运算符*

计算指定参数的组件级积。

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
元组参数的排名。

*_Lhs*<br/>
要乘法的元数之一。

*_Rhs*<br/>
要乘法的元数之一。

### <a name="return-value"></a>返回值

指定参数的组件级积。

## <a name="operator"></a><a name="operator_div"></a>操作员/

计算指定参数的按组件商。

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
元组参数的排名。

*_Lhs*<br/>
要分割的元组。

*_Rhs*<br/>
要除以的元组。

### <a name="return-value"></a>返回值

指定参数的组件商。

## <a name="operator"></a><a name="operator_mod"></a>操作员百分比

计算第二个指定参数的第一个指定参数的模数。

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
元组参数的排名。

*_Lhs*<br/>
计算莫杜洛的元组。

*_Rhs*<br/>
元组通过。

### <a name="return-value"></a>返回值

第一个指定参数的结果调制第二个指定的参数。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace-cpp-amp.md)
