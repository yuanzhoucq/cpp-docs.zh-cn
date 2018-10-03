---
title: SafeInt 函数 |Microsoft Docs
ms.custom: ''
ms.date: 09/28/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 504cfe0780cfb0116f59ae67937ea5f0370dc8b2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235563"
---
# <a name="safeint-functions"></a>SafeInt 函数

SafeInt 库提供若干函数，可以使用而无需创建的实例[SafeInt 类](../windows/safeint-class.md)。 如果你想要从整数溢出保护单个数学运算，可以使用这些函数。 如果你想要保护多个数学运算，则应创建`SafeInt`对象。 若要创建效率更高`SafeInt`比使用这些函数多次的对象。

这些功能，进行比较或执行两个不同类型的参数上的数学运算而无需首先将它们转换为同一类型。

每个函数有两种模板类型：`T`和`U`。 每个类型可以是一个布尔值、 字符或整数类型。 可以有符号或无符号整型类型和从 8 位到 64 位的任何大小。

## <a name="in-this-section"></a>本节内容

函数                      | 描述
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | 添加两个数字，可防止溢出。
[SafeCast](#safecast)         | 将转换为一种类型的另一种类型的参数。
[SafeDivide](#safedivide)     | 使两个数字相除，防止被零除。
[SafeEquals](#safeequals)， [SafeGreaterThan](#safegreaterthan)， [SafeGreaterThanEquals](#safegreaterthanequals)， [SafeLessThan](#safelessthan)， [SafeLessThanEquals](#safelessthanequals)， [SafeNotEquals](#safenotequals) | 比较两个数字。 这些函数，可以比较两个不同类型的数字，而不更改其类型。
[SafeModulus](#safemodulus)   | 执行取模运算对两个数字。
[SafeMultiply](#safemultiply) | 两个数字相乘，这样可以避免溢出。
[SafeSubtract](#safesubtract) | 两个数字相减，可防止溢出。

## <a name="related-sections"></a>相关章节

节                                                  | 描述
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../windows/safeint-class.md)                   | `SafeInt` 类。
[SafeIntException](../windows/safeintexception-class.md) | 特定于 SafeInt 库的异常类。

## <a name="safeadd"></a>SafeAdd

防止溢出的方式添加两个数字。

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要添加的第一个数。 其类型必须为 T。

*u*<br/>
[in]要添加的第二个数字。 其类型必须为 U。

*结果*<br/>
[out]参数其中`SafeAdd`将结果存储。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。

## <a name="safecast"></a>SafeCast

将转换为一种类型的另一种类型的数量。

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>参数

*From*<br/>
[in]要转换的源数字。 其类型必须为`T`。

*若要*<br/>
[out]对新的数字类型的引用。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。

## <a name="safedivide"></a>SafeDivide

将以一种可避免被零除两个数字相除。

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]除数。 其类型必须为 T。

*u*<br/>
[in]被除数。 其类型必须为 U。

*结果*<br/>
[out]参数其中`SafeDivide`将结果存储。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。

## <a name="safeequals"></a>SafeEquals

比较两个数字，以确定它们是否相等。

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要比较的第一个数字。 其类型必须为 T。

*u*<br/>
[in]要比较的第二个数字。 其类型必须为 U。

### <a name="return-value"></a>返回值

`true` 如果*t*并*u*相等; 否则为`false`。

### <a name="remarks"></a>备注

该方法增强了 `==`，因为 `SafeEquals` 使您能够将两个不同类型的数字作比较。

## <a name="safegreaterthan"></a>SafeGreaterThan

比较两个数字。

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要比较的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要比较的第二个数字。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果*t*大于*u*; 否则为`false`。

### <a name="remarks"></a>备注

`SafeGreaterThan` 通过它可以比较两个不同类型的数字扩展的常规比较运算符。

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

比较两个数字。

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要比较的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要比较的第二个数字。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果*t*大于或等于*u*; 否则为`false`。

### <a name="remarks"></a>备注

`SafeGreaterThanEquals` 增强了的标准比较运算符，因为它使您能够比较两个不同类型的数字。

## <a name="safelessthan"></a>SafeLessThan

确定一个数是否小于另一个。

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]第一个数字。 其类型必须为`T`。

*u*<br/>
[in]第二个号码。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果*t*是小于*u*; 否则为`false`。

### <a name="remarks"></a>备注

此方法增强了的标准比较运算符，因为`SafeLessThan`，您可以比较两个不同类型的数量。

## <a name="safelessthanequals"></a>SafeLessThanEquals

比较两个数字。

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要比较的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要比较的第二个数字。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果*t*小于或等于*u*; 否则为`false`。

### <a name="remarks"></a>备注

`SafeLessThanEquals` 通过它可以比较两个不同类型的数字扩展的常规比较运算符。

## <a name="safemodulus"></a>SafeModulus

执行取模运算对两个数字。

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]除数。 其类型必须为`T`。

*u*<br/>
[in]被除数。 其类型必须为`U`。

*结果*<br/>
[out]参数其中`SafeModulus`将结果存储。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。

## <a name="safemultiply"></a>SafeMultiply

将防止溢出的方式在一起的两个数字相乘。

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要相乘的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要相乘的第二个数字。 其类型必须为`U`。

*结果*<br/>
[out]参数其中`SafeMultiply`将结果存储。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。

## <a name="safenotequals"></a>SafeNotEquals

确定两个数字不相等。

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要比较的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要比较的第二个数字。 其类型必须为`U`。

### <a name="return-value"></a>返回值

`true` 如果*t*并*u*是否不相等; 否则为`false`。

### <a name="remarks"></a>备注

该方法增强了 `!=`，因为 `SafeNotEquals` 使您能够将两个不同类型的数字作比较。

## <a name="safesubtract"></a>SafeSubtract

防止溢出的方式的两个数字相减。

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]该减法运算中的第一号。 其类型必须为`T`。

*u*<br/>
[in]要从中减去的数字*t*。 其类型必须为`U`。

*结果*<br/>
[out]参数其中`SafeSubtract`将结果存储。

### <a name="return-value"></a>返回值

`true` 如果未发生错误;`false`如果发生错误。
