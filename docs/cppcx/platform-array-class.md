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
ms.openlocfilehash: 7d9fca4de954b5ba9c7cbcb3bdfce0fe3263dbd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445796"
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

### <a name="members"></a>Members

Platform：： Array 从[platform：： WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)继承其所有方法，并实现[Platform：： IBoxArray 接口](../cppcx/platform-iboxarray-interface.md)的 `Value` 属性。

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Array 构造函数](#ctor)|初始化由类模板参数*T*指定的一维可修改类型数组。|

### <a name="methods"></a>方法

请参阅[Platform：： WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)。

### <a name="properties"></a>属性

|||
|-|-|
|[Array：： Value](#value)|检索当前数组的句柄。|

### <a name="remarks"></a>备注

Array 类是密封类，不能被继承。

Windows 运行时类型系统不支持交错数组的概念，因此不能将 IVector < Platform：： Array\<T > > 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。

有关何时以及如何使用 Platform：： Array 的详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

此类在编译器会自动包括的 vccorlib.h 标头中定义。 它可在 IntelliSense 中显示，但不会出现在对象浏览器中，因为它不是在 platform.string 中定义的公共类型。

### <a name="requirements"></a>要求

编译器选项： **/ZW**

## <a name="ctor"></a>数组构造函数

初始化由类模板参数*T*指定的一维可修改类型数组。

## <a name="syntax"></a>语法

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>参数

*T*<br/>
类模板参数。

*size*<br/>
数组中的元素数。

*data*<br/>
指向用于初始化该数组对象的类型 `T` 的数据数组的指针。

### <a name="remarks"></a>备注

有关如何创建 Platform：： Array 的实例的详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="get"></a>Array：： get 方法

检索对指定索引位置上数组元素的引用。

## <a name="syntax"></a>语法

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>参数

索引<br/>
从零开始的索引，用来标识数组元素。 最小索引为0，最大索引为[数组构造函数](#ctor)中的 `size` 参数指定的值。

### <a name="return-value"></a>返回值

`index` 参数指定的数组元素。

## <a name="value"></a>Array：： Value 属性

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
