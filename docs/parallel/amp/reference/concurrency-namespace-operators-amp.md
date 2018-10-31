---
title: 并发命名空间运算符 (AMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1e313dbda3dfc75f291310818d593b9a4daf90b
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162173"
---
# <a name="concurrency-namespace-operators-amp"></a>并发命名空间运算符 (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>operator==

确定指定的参数是否相等。

```
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

**true**如果元组相等; 否则为**false**。

##  <a name="operator_neq"></a>operator!=

确定指定的参数是否不相等。

```
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

**true**如果元组不相等; 否则为**false**。

##  <a name="operator_add"></a>  operator+

计算指定的参数的按分量逐位的总和。

```
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

指定的参数的按分量逐位之和。

##  <a name="operator-"></a>operator-

计算指定参数间的按分量逐位差异。

```
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
要被减数的参数。

*_Rhs*<br/>
要减去的参数。

### <a name="return-value"></a>返回值

指定的参数之间的按分量逐位差异。

##  <a name="operator_star"></a>  operator*

计算指定的参数的乘积。

```
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

指定的参数的乘积。

##  <a name="operator_div"></a>  operator/

计算指定的参数的按分量逐位的商。

```
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
要作为被除数的元组。

*_Rhs*<br/>
要除以的元组。

### <a name="return-value"></a>返回值

指定的参数的商数。

##  <a name="operator_mod"></a>operator%

计算第二个指定参数的第一个指定参数的模数。

```
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
从该元组计算模块数目。

*_Rhs*<br/>
取模的元组，到。

### <a name="return-value"></a>返回值

第一个指定的参数取模第二个指定参数的结果。

## <a name="see-also"></a>请参阅

[并发 Namespace ](concurrency-namespace-cpp-amp.md)
