---
title: SafeInt 函数
ms.date: 10/22/2018
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
ms.openlocfilehash: c1c5593aee19254d4348d4e8658ffe9c3f0cf1b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368248"
---
# <a name="safeint-functions"></a>SafeInt 函数

SafeInt 库提供了多个无需创建 [SafeInt 类](../safeint/safeint-class.md)实例即可使用的函数。 若要防止一个数学运算出现整数溢出，可使用这些函数。 若要保护多个数学运算，应创建 `SafeInt` 对象。 创建 `SafeInt` 对象比多次使用这些函数更高效。

使用这些函数，可以对两个不同类型的参数进行比较或执行数学运算，无需先将它们转换为相同类型。

所有这些函数都有两种模板类型：`T` 和 `U`。 每种模板类型都可以是布尔类型、字符类型或整型类型。 整型类型可以有符号，也可以无符号，且大小介于 8 位和 64 位之间。

> [!NOTE]
> 此库的最新版本位于[https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)。

## <a name="in-this-section"></a>本节内容

函数                      | 说明
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | 将两个数字相加，并防止溢出。
[安全广播](#safecast)         | 将一种类型的参数强制转换为另一种类型。
[安全分流](#safedivide)     | 将两个数字相除，并防止除以零。
[SafeEquals](#safeequals)、[SafeGreaterThan](#safegreaterthan)、[SafeGreaterThanEquals](#safegreaterthanequals)、[SafeLessThan](#safelessthan)、[SafeLessThanEquals](#safelessthanequals)、[SafeNotEquals](#safenotequals) | 比较两个数字。 使用这些函数，可以比较两个不同类型的数字，而不更改它们的类型。
[SafeModulus](#safemodulus)   | 对两个数字执行取模运算。
[SafeMultiply](#safemultiply) | 将两个数字相乘，并防止溢出。
[SafeSubtract](#safesubtract) | 将两个数字相减，并防止溢出。

## <a name="related-sections"></a>相关章节

部分                                                  | 说明
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | `SafeInt` 类。
[SafeIntException](../safeint/safeintexception-class.md) | SafeInt 库专用的异常类。

## <a name="safeadd"></a><a name="safeadd"></a>安全添加

以防止溢出的方式将两个数字相加。

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
[输入] 要相加的第一个数字。 其类型必须为 T。

*美国*<br/>
[输入] 要相加的第二个数字。 其类型必须为 U。

*结果*<br/>
[输出] `SafeAdd` 在其中存储结果的参数。

### <a name="return-value"></a>返回值

如果未出错，返回 true****；否则，返回 false****。

## <a name="safecast"></a><a name="safecast"></a>安全广播

将一种类型的数字转换为另一种类型。

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>参数

*从*<br/>
[输入] 要转换的源数字。 这必须是 `T` 类型。

*自*<br/>
[输出] 对新数字类型的引用。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果未出错，返回 true****；否则，返回 false****。

## <a name="safedivide"></a><a name="safedivide"></a>安全分流

以防止除以零的方式将两个数字相除。

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
[输入] 除数。 其类型必须为 T。

*美国*<br/>
[输入] 被除数。 其类型必须为 U。

*结果*<br/>
[输出] `SafeDivide` 在其中存储结果的参数。

### <a name="return-value"></a>返回值

如果未出错，返回 true****；否则，返回 false****。

## <a name="safeequals"></a><a name="safeequals"></a>安全平等

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
[输入] 要比较的第一个数字。 其类型必须为 T。

*美国*<br/>
[输入] 要比较的第二个数字。 其类型必须为 U。

### <a name="return-value"></a>返回值

如果 t** 和 u** 相等，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

该方法增强了 `==`，因为 `SafeEquals` 使您能够将两个不同类型的数字作比较。

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>安全大于

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
[输入] 要比较的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要比较的第二个数字。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果 t** 大于 u**，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

`SafeGreaterThan` 扩展了常规比较运算符，因为它可便于比较两个不同类型的数字。

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>安全大于均等

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
[输入] 要比较的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要比较的第二个数字。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果 t** 大于或等于 u**，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

`SafeGreaterThanEquals` 增强了标准比较运算符，因为它可便于比较两个不同类型的数字。

## <a name="safelessthan"></a><a name="safelessthan"></a>安全不点

确定一个数字是否小于另一个数字。

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[输入] 第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 第二个数字。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果 t** 小于 u**，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

这种方法增强了标准比较运算符，因为 `SafeLessThan` 可便于比较两个不同类型的数字。

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>安全不相等

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
[输入] 要比较的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要比较的第二个数字。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果 t** 小于或等于 u**，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

`SafeLessThanEquals` 扩展了常规比较运算符，因为它可便于比较两个不同类型的数字。

## <a name="safemodulus"></a><a name="safemodulus"></a>安全Modulus

对两个数字执行取模运算。

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
[输入] 除数。 这必须是 `T` 类型。

*美国*<br/>
[输入] 被除数。 这必须是 `U` 类型。

*结果*<br/>
[输出] `SafeModulus` 在其中存储结果的参数。

### <a name="return-value"></a>返回值

如果未出错，返回 true****；否则，返回 false****。

## <a name="safemultiply"></a><a name="safemultiply"></a>安全乘法

以防止溢出的方式将两个数字相乘。

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
[输入] 要相乘的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要相乘的第二个数字。 这必须是 `U` 类型。

*结果*<br/>
[输出] `SafeMultiply` 在其中存储结果的参数。

### <a name="return-value"></a>返回值

如果未出错，返回 `true`；否则，返回 `false`。

## <a name="safenotequals"></a><a name="safenotequals"></a>安全不相等

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
[输入] 要比较的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要比较的第二个数字。 这必须是 `U` 类型。

### <a name="return-value"></a>返回值

如果 t** 和 u** 不相等，返回 true****；否则，返回 false****。

### <a name="remarks"></a>备注

该方法增强了 `!=`，因为 `SafeNotEquals` 使您能够将两个不同类型的数字作比较。

## <a name="safesubtract"></a><a name="safesubtract"></a>安全减法

以防止溢出的方式将两个数字相减。

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
[输入] 减法运算中的第一个数字。 这必须是 `T` 类型。

*美国*<br/>
[输入] 要从 t** 中减去的数字。 这必须是 `U` 类型。

*结果*<br/>
[输出] `SafeSubtract` 在其中存储结果的参数。

### <a name="return-value"></a>返回值

如果未出错，返回 true****；否则，返回 false****。
