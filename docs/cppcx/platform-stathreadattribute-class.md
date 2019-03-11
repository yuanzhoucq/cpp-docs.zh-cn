---
title: Platform::STAThreadAttribute 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 05fb2879839c504f49f56e25ffe28329aa969c69
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743574"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute 类

指示应用程序的线程模型是单线程单元 (STA)。

## <a name="syntax"></a>语法

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[STAThreadAttribute 构造函数 1](#ctor)|初始化类的新实例。|

### <a name="public-methods"></a>公共方法

STAThreadAttribute 属性继承[platform:: object 类](../cppcx/platform-object-class.md)。 STAThreadAttribute 还会重载或具有以下成员：

|name|描述|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|确定指定的对象是否等于当前对象。|
|[STAThreadAttribute::GetHashCode](#gethashcode)|返回此实例的哈希代码。|
|[STAThreadAttribute::ToString](#tostring)|返回表示当前对象的字符串。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`Platform`

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** 平台

## <a name="ctor"></a> STAThreadAttribute constructor

初始化 STAThreadAttribute 类的新实例。

### <a name="syntax"></a>语法

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

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

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

返回此实例的哈希代码。

### <a name="syntax"></a>语法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>返回值

此实例的哈希代码。

## <a name="tostring"></a> STAThreadAttribute::ToString

返回表示当前对象的字符串。

### <a name="syntax"></a>语法

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>返回值

表示当前对象的字符串。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)
