---
title: '&lt;thread&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375823"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 运算符

||||
|-|-|-|
|[操作员！](#op_neq)|[算子&gt;](#op_gt)|[算子&gt;=](#op_gt_eq)|
|[算子&lt;](#op_lt)|[算子&lt;&lt;](#op_lt_lt)|[算子&lt;=](#op_lt_eq)|
|[运算符*](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>算子&gt;=

确定一个 `thread::id` 对象是否大于或等于另一个。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Left < Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorgt"></a><a name="op_gt"></a>算子&gt;

确定一个 `thread::id` 对象是否大于另一个。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`Right < Left`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>算子&lt;=

确定一个 `thread::id` 对象是否小于或等于另一个。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Right < Left)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorlt"></a><a name="op_lt"></a>算子&lt;

确定一个 `thread::id` 对象是否小于另一个。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

如果 *"左"* 在总排序中位于*右侧*，**则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

该运算符定义所有 `thread::id` 对象的总排序。 这些对象可以用作关联容器中的键。

此函数不引发任何异常。

## <a name="operator"></a><a name="op_neq"></a>操作员！

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Left == Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operator"></a><a name="op_eq_eq"></a>运算符*

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*离开*\
左 `thread::id` 对象。

*对*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

如果两个对象表示相同的执行线程，或者两个对象都不表示执行线程，**则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>算子&lt;&lt;

将 `thread::id` 对象的文本表示形式插入流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>参数

*奥斯特*\
一个 [basic_ostream](../standard-library/basic-ostream-class.md) 对象。

*Id*\
`thread::id` 对象。

### <a name="return-value"></a>返回值

*奥斯特*.

### <a name="remarks"></a>备注

此函数将*ID*插入*到 Ostr*。

如果两个`thread::id` 对象相等，这些对象的文本表示形式相同。

## <a name="see-also"></a>另请参阅

[\<线程>](../standard-library/thread.md)
