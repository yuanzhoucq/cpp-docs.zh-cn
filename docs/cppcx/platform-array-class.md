---
title: Platform::Array 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318658"
---
# <a name="platformarray-class"></a>Platform::Array 类

表示可以跨应用程序二进制接口 (ABI) 接收和传递的一维可修改数组。

## <a name="syntax"></a>语法

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>成员

平台：：Array从平台继承其所有方法[：：WriteOnlyArray类](../cppcx/platform-writeonlyarray-class.md)，实现`Value`[平台的属性：：：iBoxArray接口](../cppcx/platform-iboxarray-interface.md)。

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Array 构造函数](#ctor)|初始化类模板参数*T*指定的一维、可修改的类型数组。|

### <a name="methods"></a>方法

请参阅[平台：：编写"只写数组"类](../cppcx/platform-writeonlyarray-class.md)。

### <a name="properties"></a>属性

|||
|-|-|
|[数组：值](#value)|检索当前数组的句柄。|

### <a name="remarks"></a>备注

Array 类是密封类，不能被继承。

Windows 运行时类型系统不支持锯齿数组的概念，因此不能将 IVector<Platform：：array\<T>> 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。

有关何时以及如何使用 Platform：：Array 的详细信息，请参阅[数组和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

此类在编译器会自动包括的 vccorlib.h 标头中定义。 它在 IntelliSense 中可见，但在对象浏览器中不可见，因为它不是在 platform.winmd 中定义的公共类型。

### <a name="requirements"></a>要求

编译器选项： **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>数组构造函数

初始化类模板参数*T*指定的一维、可修改的类型数组。

## <a name="syntax"></a>语法

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>参数

*T*<br/>
类模板参数。

*大小*<br/>
数组中的元素数。

*数据*<br/>
指向用于初始化该数组对象的类型 `T` 的数据数组的指针。

### <a name="remarks"></a>备注

有关如何创建平台实例的详细信息：数组，请参阅[数组和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="arrayget-method"></a><a name="get"></a>数组：：获取方法

检索对指定索引位置上数组元素的引用。

## <a name="syntax"></a>语法

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>参数

*index*<br/>
从零开始的索引，用来标识数组元素。 最小索引为 0，最大值索引是`size`[数组构造函数](#ctor)中参数指定的值。

### <a name="return-value"></a>返回值

`index` 参数指定的数组元素。

## <a name="arrayvalue-property"></a><a name="value"></a>数组：值属性

检索当前数组的句柄。

## <a name="syntax"></a>语法

```cpp
property Array^ Value;
```

### <a name="return-value"></a>返回值

当前数组的句柄。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)<br/>
[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
