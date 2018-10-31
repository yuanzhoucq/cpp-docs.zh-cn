---
title: 'Platform:: mtathreadattribute 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2bac4ae71d98cb81eaa05bd3fd6fdf817145e22
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163746"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute 类

指示应用程序的线程处理模型为多线程单元 (MTA)。

## <a name="syntax"></a>语法

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[MTAThreadAttribute 构造函数 1](#ctor)构造函数|初始化类的新实例。|

### <a name="public-methods"></a>公共方法

MTAThreadAttribute 属性继承[platform:: object 类](../cppcx/platform-object-class.md)。 MTAThreadAttribute 还会重载或具有以下成员：

|name|描述|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|确定指定的对象是否等于当前对象。|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|返回此实例的哈希代码。|
|[MTAThreadAttribute::ToString](#tostring)|返回表示当前对象的字符串。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Platform`

### <a name="requirements"></a>要求

**元数据：** platform.winmd

**命名空间：** Platform

## <a name="ctor"></a> MTAThreadAttribute 构造函数

初始化 MTAThreadAttribute 类的新实例。

### <a name="syntax"></a>语法

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

确定指定的对象是否等于当前对象。

### <a name="syntax"></a>语法

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>参数

*obj*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

**true**如果对象相等; 否则为**false**。

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

返回此实例的哈希代码。

### <a name="syntax"></a>语法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>返回值

此实例的哈希代码。

## <a name="tostring"></a> MTAThreadAttribute::ToString

返回表示当前对象的字符串。

### <a name="syntax"></a>语法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>返回值

表示当前对象的字符串。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)