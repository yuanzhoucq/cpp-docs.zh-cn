---
title: CreatorMap 结构 |Microsoft 文档
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
ms.openlocfilehash: a6113737d7463354ffa273ced61b190246f63a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="creatormap-structure"></a>CreatorMap 结构
支持的 Windows 运行时 c + + 模板库基础结构，不宜在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>备注  
 包含有关如何初始化、 注册和注销对象的信息。  
  
 CreatorMap 包含以下信息：  
  
-   如何初始化、 注册和注销对象。  
  
-   如何比较具体取决于经典 COM 或 Windows 运行时工厂激活数据。  
  
-   有关接口的工厂缓存和服务器名称的信息。  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CreatorMap::activationId 数据成员](../windows/creatormap-activationid-data-member.md)|表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。|  
|[CreatorMap::factoryCache 数据成员](../windows/creatormap-factorycache-data-member.md)|CreatorMap，将存储指向工厂缓存的指针。|  
|[CreatorMap::factoryCreator 数据成员](../windows/creatormap-factorycreator-data-member.md)|指定 CreatorMap 创建一个工厂。|  
|[CreatorMap::serverName 数据成员](../windows/creatormap-servername-data-member.md)|存储 CreatorMap 的服务器名称。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CreatorMap`  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)