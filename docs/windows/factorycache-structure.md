---
title: "FactoryCache 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0fc48c9a3651e8c5a6609886862c2f73c5707638
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="factorycache-structure"></a>FactoryCache 结构
支持的 Windows 运行时 c + + 模板库基础结构，不宜在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>备注  
 包含的类工厂和值，该值标识已注册 wrt 或 COM 类对象的位置。  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[FactoryCache::cookie 数据成员](../windows/factorycache-cookie-data-member.md)|包含一个值，用于标识已注册的 Windows 运行时或 COM 类对象，以及更高版本用于注销对象。|  
|[FactoryCache::factory 数据成员](../windows/factorycache-factory-data-member.md)|指向 Windows 运行时或 COM 类工厂。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `FactoryCache`  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)