---
title: '&lt;ostream&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: d8b6f4e0f0b5bca41f8d895415fff4003231ad1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373607"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 运算符

||
|-|
|[算子&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>算子&lt;&lt;

将各种类型写入流。

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>参数

*_Ch*\
一个字符。

*_Elem*\
元素类型。

*_Ostr*\
`basic_ostream` 对象。

*Str*\
字符串。

*_Tr*\
字符特征。

*瓦尔*\
类型

### <a name="return-value"></a>返回值

流。

### <a name="remarks"></a>备注

`basic_ostream` 类还定义了多个插入运算符。 有关详细信息，请参阅[basic_ostream：运算符&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)。

模板函数

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

确定序列的长度 N `traits_type::`=`str`[长度](../standard-library/char-traits-struct.md#length)（ ）， 从*str*开始，然后插入序列。 如果 N < `_Ostr.`[width](../standard-library/ios-base-class.md#width)，则该函数还将插入 `_Ostr.width` 的重复项 - N 个填充字符。 如果 （），`_Ostr`重复在序列之前。 [flags](../standard-library/ios-base-class.md#flags) & 标志`adjustfield`！=[左](../standard-library/ios-functions.md#left)。 否则，重复项在该序列后。 函数返回 *_Ostr*。

模板函数

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

插入元素 `_Ch`。 如果 1 < `_Ostr.width`，则该函数还将插入 `_Ostr.width` 的重复项 - 1 个填充字符。 如果 `_Ostr.flags & adjustfield != left`，则该重复项在序列前。 否则，重复项在该序列后。 它返回 *_Ostr*。

模板函数

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

行为等同于

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

只不过，序列从*str*开始的每个元素 *_Ch*通过`_Ostr.`调用[put（](../standard-library/basic-ostream-class.md#put)`_Ostr.`[加宽](../standard-library/basic-ios-class.md#widen)（`_Ch`） ） 转换为类型`Elem`的对象。

模板函数

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

行为等同于

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

除非 *_Ch*通过`Elem`调用`_Ostr.put`（ ）`_Ostr.widen``_Ch`转换为类型的对象。

模板函数

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

行为等同于

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

（在插入元素之前，无需将其加宽。）

模板函数

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

行为等同于

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

（在插入 *_Ch*之前，它不必加宽。

模板函数

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

返回`_Ostr` << （`const char *` `str`）

模板函数

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

返回`_Ostr` << （`char` `_Ch`）

模板函数：

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

返回`_Ostr` << （`const char *` `str`）

模板函数：

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

返回`_Ostr` << （`char` `_Ch`）

模板函数：

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

返回 `_Ostr` `<<` `val`（并将[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)转换为进程中左值的 `_Ostr`）。

### <a name="example"></a>示例

有关使用 `operator<<` 的示例，请参阅 [flush](../standard-library/ostream-functions.md#flush)。

## <a name="see-also"></a>另请参阅

[\<流>](../standard-library/ostream.md)
