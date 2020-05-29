---
title: Platform::Box 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354761"
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

|成员|说明|
|------------|-----------------|
|[箱](#ctor) | 创建可以封装指定类型的值的 `Box`。 |
|[运算符盒&lt;形 T&gt;^](#box-const-t) | 实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。 |
|[运算符&lt;盒收缩挥发 T&gt;^](#box-const-volatile-t) | 启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。 |
|[操作员盒&lt;T&gt;^](#box-t) | 实现从值类 `T` 到 `Box<T>` 的装箱转换。 |
|[运算符&lt;盒挥发 T&gt;^](#box-volatile-t) | 启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。 |
|[框：：运算符 T](#t) | 实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。 |
|[值属性](#value) | 返回在 `Box` 对象中封装的值。 |

## <a name="boxbox-constructor"></a><a name="ctor"></a>框：：框构造函数

创建可以封装指定类型的值的 `Box`。

### <a name="syntax"></a>语法

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>参数

*值阿格*<br/>
要进行装箱的值的类型（例如 `int`、`bool`、`float64`、`DateTime`）。

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>框：：运算符盒&lt;同 T&gt;= 运算符

实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何值类、值结构或枚举类型。 在[默认命名空间](../cppcx/default-namespace.md)中包括内置类型。

### <a name="return-value"></a>返回值

表示`Platform::Box<T>^`在 ref 类中装箱的原始值的实例。

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>框：：运算符盒&lt;收缩挥发性&gt;T = 运算符

启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 在[默认命名空间](../cppcx/default-namespace.md)中包括内置类型。

### <a name="return-value"></a>返回值

表示`Platform::Box<T>^`在 ref 类中装箱的原始值的实例。

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>框：：运算符框&lt;&gt;T = 运算符

实现从值类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 在[默认命名空间](../cppcx/default-namespace.md)中包括内置类型。

### <a name="return-value"></a>返回值

表示`Platform::Box<T>^`在 ref 类中装箱的原始值的实例。

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>框：：运算符框&lt;挥发&gt;T = 运算符

启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 在[默认命名空间](../cppcx/default-namespace.md)中包括内置类型。

### <a name="return-value"></a>返回值

表示`Platform::Box<T>^`在 ref 类中装箱的原始值的实例。

## <a name="boxoperator-t-operator"></a><a name="t"></a>框：：运算符 T 运算符

实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。

### <a name="syntax"></a>语法

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>参数

*T*<br/>
任何枚举类型、值类或值结构。 在[默认命名空间](../cppcx/default-namespace.md)中包括内置类型。

### <a name="return-value"></a>返回值

表示`Platform::Box<T>^`在 ref 类中装箱的原始值的实例。

## <a name="boxvalue-property"></a><a name="value"></a>框：：值属性

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
