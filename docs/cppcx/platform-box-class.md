---
title: Platform::Box 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 6afc12dbc3f6980bb7fd42d7f0a8fdc9e6d0e284
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232165"
---
# <a name="platformbox-class"></a>Platform::Box 类

使值类型（例如） `Windows::Foundation::DateTime` 或标量类型（例如）能够 **`int`** 存储在类型中 `Platform::Object` 。 通常没有必要显式使用 `Box` ，因为当你将值类型强制转换为 `Object^`时会发生隐式装箱：

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
|[operator Box &lt; Const T&gt;^](#box-const-t) | 启用从 **`const`** 值类 `T` 或 **`enum`** 类 `T` 到的装箱转换 `Box<T>` 。 |
|[操作框 &lt; const Volatile T&gt;^](#box-const-volatile-t) | 启用从 **`const volatile`** 值类 `T` 或 **`enum`** 类型 `T` 到的装箱转换 `Box<T>` 。 |
|[运算符框 &lt; T&gt;^](#box-t) | 实现从值类 `T` 到 `Box<T>` 的装箱转换。 |
|[不可变的运算符 &lt;&gt;^](#box-volatile-t) | 启用从 **`volatile`** 值类 `T` 或 **`enum`** 类型 `T` 到的装箱转换 `Box<T>` 。 |
|[Box：： operator T](#t) | 启用从值类 `T` 或 **`enum`** 类到的装箱 `T` 转换 `Box<T>` 。 |
|[Value 属性](#value) | 返回在 `Box` 对象中封装的值。 |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box：： Box 构造函数

创建可以封装指定类型的值的 `Box`。

### <a name="syntax"></a>语法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>参数

*valueArg*<br/>
要装箱的值的类型，例如、、、 **`int`** **`bool`** `float64` `DateTime` 。

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box：： operator Box &lt; Const T &gt; ^ 运算符

启用从 **`const`** 值类 `T` 或 **`enum`** 类 `T` 到的装箱转换 `Box<T>` 。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何值类、值结构或枚举类型。 包括[默认命名空间](../cppcx/default-namespace.md)中的内置类型。

### <a name="return-value"></a>返回值

一个 `Platform::Box<T>^` 实例，表示 ref 类中装箱的原始值。

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box：： operator Box &lt; const Volatile T &gt; ^ 运算符

启用从 **`const volatile`** 值类 `T` 或 **`enum`** 类型 `T` 到的装箱转换 `Box<T>` 。

### <a name="syntax"></a>语法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括[默认命名空间](../cppcx/default-namespace.md)中的内置类型。

### <a name="return-value"></a>返回值

一个 `Platform::Box<T>^` 实例，表示 ref 类中装箱的原始值。

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box：： operator Box &lt; T &gt; ^ 运算符

实现从值类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括[默认命名空间](../cppcx/default-namespace.md)中的内置类型。

### <a name="return-value"></a>返回值

一个 `Platform::Box<T>^` 实例，表示 ref 类中装箱的原始值。

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box：： operator Box &lt; Volatile T &gt; ^ 运算符

启用从 **`volatile`** 值类 `T` 或 **`enum`** 类型 `T` 到的装箱转换 `Box<T>` 。

### <a name="syntax"></a>语法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括[默认命名空间](../cppcx/default-namespace.md)中的内置类型。

### <a name="return-value"></a>返回值

一个 `Platform::Box<T>^` 实例，表示 ref 类中装箱的原始值。

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box：： operator T 运算符

启用从值类 `T` 或 **`enum`** 类到的装箱 `T` 转换 `Box<T>` 。

### <a name="syntax"></a>语法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 包括[默认命名空间](../cppcx/default-namespace.md)中的内置类型。

### <a name="return-value"></a>返回值

一个 `Platform::Box<T>^` 实例，表示 ref 类中装箱的原始值。

## <a name="boxvalue-property"></a><a name="value"></a>Box：： Value 属性

返回在 `Box` 对象中封装的值。

### <a name="syntax"></a>语法

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>返回值

返回具有和其装箱前最初具有的类型相同类型的装箱值。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)<br/>
[装箱](../cppcx/boxing-c-cx.md)
