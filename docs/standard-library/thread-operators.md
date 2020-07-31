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
ms.openlocfilehash: e7321831b9356fdb9ae5ce147319726def69efc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215564"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt; 运算符

||||
|-|-|-|
|[operator！ =](#op_neq)|[操作员&gt;](#op_gt)|[操作员&gt;=](#op_gt_eq)|
|[操作员&lt;](#op_lt)|[操作员&lt;&lt;](#op_lt_lt)|[操作员&lt;=](#op_lt_eq)|
|[operator = =](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作员&gt;=

确定一个 `thread::id` 对象是否大于或等于另一个。

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Left < Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorgt"></a><a name="op_gt"></a>操作员&gt;

确定一个 `thread::id` 对象是否大于另一个。

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`Right < Left`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作员&lt;=

确定一个 `thread::id` 对象是否小于或等于另一个。

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Right < Left)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorlt"></a><a name="op_lt"></a>操作员&lt;

确定一个 `thread::id` 对象是否小于另一个。

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

**`true`** 如果在合计*顺序中**靠左*，则为;否则为 **`false`** 。

### <a name="remarks"></a>备注

该运算符定义所有 `thread::id` 对象的总排序。 这些对象可以用作关联容器中的键。

此函数不引发任何异常。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

`!(Left == Right)`

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

比较两个 `thread::id` 对象是否相等。

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>参数

*左中*\
左 `thread::id` 对象。

*然后*\
正确的 `thread::id` 对象。

### <a name="return-value"></a>返回值

**`true`** 如果两个对象表示相同的执行线程，或者如果这两个对象都不表示执行线程，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

此函数不引发任何异常。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>操作员&lt;&lt;

将 `thread::id` 对象的文本表示形式插入流。

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>参数

*Ostr*\
一个 [basic_ostream](../standard-library/basic-ostream-class.md) 对象。

*识别*\
`thread::id` 对象。

### <a name="return-value"></a>返回值

*Ostr*。

### <a name="remarks"></a>备注

此函数将*Id*插入*Ostr*。

如果两个`thread::id` 对象相等，这些对象的文本表示形式相同。

## <a name="see-also"></a>另请参阅

[\<thread>](../standard-library/thread.md)
