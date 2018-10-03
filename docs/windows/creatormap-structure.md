---
title: CreatorMap 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a7bf4ec2132e19989c5f1ae7c47003056928d0fd
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234926"
---
# <a name="creatormap-structure"></a>CreatorMap 结构

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>备注

包含有关如何初始化、 注册和注销的对象的信息。

`CreatorMap` 包含下列信息：

- 如何初始化、 注册和注销的对象。

- 如何比较激活数据，具体取决于传统 COM 或 Windows 运行时的工厂。

- 有关接口的工厂缓存和服务器名称的信息。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                                          | 描述
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[Creatormap:: Activationid](#activationid)     | 表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。
[Creatormap:: Factorycache](#factorycache)     | 存储的工厂缓存指向`CreatorMap`。
[Creatormap:: Factorycreator](#factorycreator) | 创建指定的工厂`CreatorMap`。
[Creatormap:: Servername](#servername)         | 将存储的服务器名称`CreatorMap`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CreatorMap`

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="activationid"></a>Creatormap:: Activationid

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>参数

*clsid*<br/>
接口 ID。

*getRuntimeName*<br/>
用于检索对象的 Windows 运行时名称的函数。

### <a name="remarks"></a>备注

表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。

## <a name="factorycache"></a>Creatormap:: Factorycache

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>备注

存储的工厂缓存指向`CreatorMap`。

## <a name="factorycreator"></a>Creatormap:: Factorycreator

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>参数

*currentflags*<br/>
之一[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。

*entry*<br/>
CreatorMap。

*iidClassFactory*<br/>
类工厂的接口 ID。

*工厂*<br/>
操作完成后，类工厂的地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

为指定 CreatorMap 创建的工厂。

## <a name="servername"></a>Creatormap:: Servername

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>备注

存储 CreatorMap 的服务器名称。
