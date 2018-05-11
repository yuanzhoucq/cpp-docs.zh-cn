---
title: ModuleType 枚举 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d36355c9f64f9f5c827ef8c4d5b3cb6a77d17b65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="moduletype-enumeration"></a>ModuleType 枚举
指定模块是否应支持进程内服务器或进程外服务器。  
  
## <a name="syntax"></a>语法  
  
```  
enum ModuleType;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`InProc`|进程内服务器。|  
|`OutOfProc`|进程外服务器。|  
|`DisableCaching`|禁用在模块上的缓存机制。|  
|`InProcDisableCaching`|组合`InProc`和`DisableCaching`。|  
|`OutOfProcDisableCaching`|组合`OutOfProc`和`DisableCaching`。|  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)