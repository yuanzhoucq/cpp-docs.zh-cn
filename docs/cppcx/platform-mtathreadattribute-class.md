---
title: Platform::MTAThreadAttribute 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 700eeae226be48c1f6659d621f2f5c0ed397bb7f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213042"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute 类

指示应用程序的线程处理模型为多线程单元 (MTA)。

## <a name="syntax"></a>语法

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[MTAThreadAttribute 构造函数 1](#ctor)构造函数|初始化此类的新实例。|

### <a name="public-methods"></a>公共方法

MTAThreadAttribute 属性继承自[Platform：： Object 类](../cppcx/platform-object-class.md)。 MTAThreadAttribute 还会重载或具有以下成员：

|名称|描述|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|确定指定对象是否等于当前对象。|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|返回此实例的哈希代码。|
|[MTAThreadAttribute::ToString](#tostring)|返回表示当前对象的字符串。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Platform`

### <a name="requirements"></a>要求

**Metadata：** platform.string

**命名空间：** Platform

## <a name="mtathreadattribute-constructor"></a><a name="ctor"></a>MTAThreadAttribute 构造函数

初始化 MTAThreadAttribute 类的新实例。

### <a name="syntax"></a>语法

```cpp
public:MTAThreadAttribute();
```

## <a name="mtathreadattributeequals"></a><a name="equals"></a>MTAThreadAttribute：： Equals

确定指定对象是否等于当前对象。

### <a name="syntax"></a>语法

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>参数

*obj*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

**`true`** 如果对象相等，则为; 否则为。否则为 **`false`** 。

## <a name="mtathreadattributegethashcode"></a><a name="gethashcode"></a>MTAThreadAttribute：： GetHashCode

返回此实例的哈希代码。

### <a name="syntax"></a>语法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>返回值

此实例的哈希代码。

## <a name="mtathreadattributetostring"></a><a name="tostring"></a>MTAThreadAttribute：： ToString

返回表示当前对象的字符串。

### <a name="syntax"></a>语法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>返回值

表示当前对象的字符串。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
