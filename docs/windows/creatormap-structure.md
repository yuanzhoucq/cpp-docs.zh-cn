---
title: CreatorMap 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a622eaa40cedfd7bf22259cf81382290f20f3a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593729"
---
# <a name="creatormap-structure"></a>CreatorMap 结构

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>备注

包含有关如何初始化、 注册和注销的对象的信息。

**CreatorMap**包含以下信息：

- 如何初始化、 注册和注销的对象。

- 如何比较激活数据，具体取决于传统 COM 或 Windows 运行时的工厂。

- 有关接口的工厂缓存和服务器名称的信息。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CreatorMap::activationId 数据成员](../windows/creatormap-activationid-data-member.md)|表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。|
|[CreatorMap::factoryCache 数据成员](../windows/creatormap-factorycache-data-member.md)|存储的工厂缓存指向**CreatorMap**。|
|[CreatorMap::factoryCreator 数据成员](../windows/creatormap-factorycreator-data-member.md)|创建指定的工厂**CreatorMap**。|
|[CreatorMap::serverName 数据成员](../windows/creatormap-servername-data-member.md)|将存储的服务器名称**CreatorMap**。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`CreatorMap`

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)