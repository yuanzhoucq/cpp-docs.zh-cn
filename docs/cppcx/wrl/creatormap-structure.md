---
title: CreatorMap 结构
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784099"
---
# <a name="creatormap-structure"></a>CreatorMap 结构

支持 Windows 运行时C++模板库基础结构，不应在代码中直接使用。

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
[CreatorMap::activationId](#activationid)     | 表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。
[CreatorMap::factoryCache](#factorycache)     | 存储的工厂缓存指向`CreatorMap`。
[CreatorMap::factoryCreator](#factorycreator) | 创建指定的工厂`CreatorMap`。
[CreatorMap::serverName](#servername)         | 将存储的服务器名称`CreatorMap`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CreatorMap`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL::Details

## <a name="activationid"></a>CreatorMap::activationId

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

## <a name="factorycache"></a>CreatorMap::factoryCache

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>备注

存储的工厂缓存指向`CreatorMap`。

## <a name="factorycreator"></a>CreatorMap::factoryCreator

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
之一[RuntimeClassType](runtimeclasstype-enumeration.md)枚举器。

*entry*<br/>
CreatorMap。

*iidClassFactory*<br/>
类工厂的接口 ID。

*factory*<br/>
操作完成后，类工厂的地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

为指定 CreatorMap 创建的工厂。

## <a name="servername"></a>CreatorMap::serverName

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>备注

存储 CreatorMap 的服务器名称。
