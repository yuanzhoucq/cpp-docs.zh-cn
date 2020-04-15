---
title: Platform::WriteOnlyArray 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374643"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray 类

表示一个一维数组，当调用方为要填充的方法传递数组时，可将此一维数组用作输入参数。

此 ref 类在 vccorlib.h 中声明为私有；因此，它不是通过元数据发出的，只能通过 C++ 使用它。 此类仅用作输入参数，用于接收调用方分配的数组。 此类无法通过用户代码构造。 它允许 C++ 方法直接写入到该数组中，这种模式称为“FillArray” ** 模式。 有关详细信息，请参阅[数组和写入唯一数组](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="syntax"></a>语法

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

这些方法具有内部可访问性，即，只能在 C++ 应用或组件中访问这些方法。

|名称|说明|
|----------|-----------------|
|[只写数组：：开始](#begin)|指向数组中第一个元素的迭代器。|
|[写唯一的Array：:D](#data)|指向数据缓冲区的指针。|
|[只写入数组：结束](#end)|指向数组中最后一个元素的下一位置的迭代器。|
|[只写：：快速通过](#fastpass)|指示数组能否使用 FastPass 机制，此机制是系统透明执行的优化。 请勿在你的代码中使用此机制|
|[只写入数组：长度](#length)|返回数组中的元素数目。|
|[只写入数组：：设置](#set)|将指定元素设置为指定值。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`WriteOnlyArray`

### <a name="requirements"></a>要求

编译器选项： **/ZW**

**元数据：** Platform.winmd

**命名空间：** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>只写入数组：：开始方法

返回一个指向数组中第一个元素的指针。

### <a name="syntax"></a>语法

```cpp
T* begin() const;
```

### <a name="return-value"></a>返回值

指向数组中第一个元素的指针。

### <a name="remarks"></a>备注

此迭代器可与 STL 算法（如 `std::sort`）一起使用以操作数组中的元素。

## <a name="writeonlyarraydata-property"></a><a name="data"></a>写唯一数组：:D

指向数据缓冲区的指针。

### <a name="syntax"></a>语法

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>返回值

指向原始数组字节的指针。

## <a name="writeonlyarrayend-method"></a><a name="end"></a>只写入数组：结束方法

返回一个指向数组中最后一个元素的下一位置的指针。

### <a name="syntax"></a>语法

```cpp
T* end() const;
```

### <a name="return-value"></a>返回值

指向数组中最后一个元素的下一位置的指针迭代器。

### <a name="remarks"></a>备注

此迭代器可与 STL 算法（如 `std::sort`）一起使用以对数组元素执行操作。

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>只写入数组：：快速通道属性

指示能否执行内部 FastPass 优化。 不用于用户代码。

### <a name="syntax"></a>语法

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>返回值

指示数组是否为 FastPass 的布尔值。

## <a name="writeonlyarrayget-method"></a><a name="get"></a>只写入数组：：获取方法

返回指定索引处的元素。

### <a name="syntax"></a>语法

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>参数

*指数阿格*<br/>
要使用的索引。

### <a name="return-value"></a>返回值

## <a name="writeonlyarraylength-property"></a><a name="length"></a>只写入数组：长度属性

返回调用方分配的数组中的元素数目。

### <a name="syntax"></a>语法

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>返回值

数组中的元素数。

## <a name="writeonlyarrayset-function"></a><a name="set"></a>只写入数组：：设置函数

在数组中指定索引处设置指定值。

### <a name="syntax"></a>语法

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>参数

*指数阿格*<br/>
要设置的元素的索引。

*值阿格*<br/>
要在 `indexArg` 设置的值。

### <a name="return-value"></a>返回值

对刚刚设置的元素的引用。

### <a name="remarks"></a>备注

有关如何解释 HRESULT 值的详细信息，请参阅 COM[错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
