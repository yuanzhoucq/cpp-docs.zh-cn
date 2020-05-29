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
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372604"
---
# <a name="creatormap-structure"></a>CreatorMap 结构

支持 Windows 运行时C++模板库基础结构，并且不打算直接从代码中使用。

## <a name="syntax"></a>语法

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>备注

包含有关如何初始化、注册和取消注册对象的信息。

`CreatorMap` 包含下列信息：

- 如何初始化、注册和取消注册对象。

- 如何根据经典 COM 或 Windows 运行时工厂比较激活数据。

- 有关接口的工厂缓存和服务器名称的信息。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                                          | 说明
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[创建者映射：：激活 Id](#activationid)     | 表示由经典 COM 类 ID 或 Windows 运行时名称标识的对象 ID。
[创建者映射：：工厂缓存](#factorycache)     | 存储指向 工厂缓存的指针`CreatorMap`。
[创作者地图：：工厂创造者](#factorycreator) | 为指定的`CreatorMap`创建工厂。
[创建者映射：：服务器名称](#servername)         | 存储 的`CreatorMap`服务器名称。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CreatorMap`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** 微软：：WRL：:D

## <a name="creatormapactivationid"></a><a name="activationid"></a>创建者映射：：激活 Id

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>参数

*Clsid*<br/>
接口 ID。

*获取 Runtime 名称*<br/>
检索对象的 Windows 运行时名称的函数。

### <a name="remarks"></a>备注

表示由经典 COM 类 ID 或 Windows 运行时名称标识的对象 ID。

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>创建者映射：：工厂缓存

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>备注

存储指向 工厂缓存的指针`CreatorMap`。

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>创作者地图：：工厂创造者

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>参数

*电流标志*<br/>
[运行时类类型](runtimeclasstype-enumeration.md)枚举器之一。

*进入*<br/>
创建者地图。

*iidClass工厂*<br/>
类工厂的接口 ID。

*工厂*<br/>
操作完成后，类工厂的地址。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

为指定的创建者映射创建工厂。

## <a name="creatormapservername"></a><a name="servername"></a>创建者映射：：服务器名称

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>备注

存储创建者映射的服务器名称。
