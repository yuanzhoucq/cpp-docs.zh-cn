---
title: '&lt;thread&gt; 运算符 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
dev_langs:
- C++
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 1f5f523b19581fe11f01266c90e6b8612da125fc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858866"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 运算符

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>  operator&gt;=

确定一个 `thread::id` 对象是否大于或等于另一个。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

`!(Left < Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="op_gt"></a>operator&gt;

确定一个 `thread::id` 对象是否大于另一个。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

`Right < Left`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="op_lt_eq"></a>  operator&lt;=

确定一个 `thread::id` 对象是否小于或等于另一个。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

`!(Right < Left)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="op_lt"></a>operator&lt;

确定一个 `thread::id` 对象是否小于另一个。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

如果在总排序中，`Left` 超过 `Right`，则为 `true`；否则为 `false`。

### <a name="remarks"></a>备注

该运算符定义所有 `thread::id` 对象的总排序。 这些对象可以用作关联容器中的键。

此函数不引发任何异常。

## <a name="op_neq"></a>operator!=

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

`!(Left == Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="op_eq_eq"></a>operator==

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

`Left` 左侧`thread::id`对象。

`Right` 右侧`thread::id`对象。

### <a name="return-value"></a>返回值

如果两个对象表示同一个执行线程或者这两个对象都不表示执行线程，则为 `true`；否则为 `false`。

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="op_lt_lt"></a>  operator&lt;&lt;

将 `thread::id` 对象的文本表示形式插入流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>参数

`Ostr` A [basic_ostream](../standard-library/basic-ostream-class.md)对象。

`Id` A`thread::id`对象。

### <a name="return-value"></a>返回值

`Ostr`。

### <a name="remarks"></a>备注

此函数会将 `Id` 插入 `Ostr`。

如果两个`thread::id` 对象相等，这些对象的文本表示形式相同。

## <a name="see-also"></a>请参阅

[\<thread>](../standard-library/thread.md)<br/>
