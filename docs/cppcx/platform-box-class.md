---
title: Platform::Box 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: ca8c9229d0ef5fa654f462282f257b1684984102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404645"
---
# <a name="platformbox-class"></a>Platform::Box 类

使值类型（例如 `Windows::Foundation::DateTime` ）或标量类型（例如 `int` ）能够存储在 `Platform::Object` 类型中。 通常没有必要显式使用 `Box` ，因为当你将值类型强制转换为 `Object^`时会发生隐式装箱：

### <a name="syntax"></a>语法

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>要求

**标头：** vccorlib.h

**命名空间：** Platform

### <a name="members"></a>成员

|成员|描述|
|------------|-----------------|
|[Box](#ctor) | 创建可以封装指定类型的值的 `Box`。 |
|[运算符框&lt;const T&gt;^](#box-const-t) | 实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。 |
|[运算符框&lt;const 易失性 T&gt;^](#box-const-volatile-t) | 启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。 |
|[operator Box&lt;T&gt;^](#box-t) | 实现从值类 `T` 到 `Box<T>` 的装箱转换。 |
|[operator Box&lt;volatile T&gt;^](#box-volatile-t) | 启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。 |
|[Box:: operator T](#t) | 实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。 |
|[Value 属性](#value) | 返回在 `Box` 对象中封装的值。 |

## <a name="ctor"></a> Box:: box 构造函数

创建可以封装指定类型的值的 `Box`。

### <a name="syntax"></a>语法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>参数

*valueArg*<br/>
要进行装箱的值的类型（例如 `int`、`bool`、`float64`、`DateTime`）。

## <a name="box-const-t"></a> Box:: operator 框&lt;const T&gt;^ 运算符

实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何值类、值结构或枚举类型。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。

### <a name="return-value"></a>返回值

一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。

## <a name="box-const-volatile-t"></a> Box:: operator 框&lt;const 易失性 T&gt;^ 运算符

启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。

### <a name="return-value"></a>返回值

一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。

## <a name="box-t"></a> Box:: operator 框&lt;T&gt;^ 运算符

实现从值类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。

### <a name="return-value"></a>返回值

一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。

## <a name="box-volatile-t"></a> Box:: operator 框&lt;易失性 T&gt;^ 运算符

启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。

### <a name="return-value"></a>返回值

一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。

## <a name="t"></a>  Box:: operator T 运算符

实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。

### <a name="return-value"></a>返回值

一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。

## <a name="value"></a> Box:: value 属性

返回在 `Box` 对象中封装的值。

### <a name="syntax"></a>语法

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>返回值

返回具有和其装箱前最初具有的类型相同类型的装箱值。

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)<br/>
[装箱](../cppcx/boxing-c-cx.md)
