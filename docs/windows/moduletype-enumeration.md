---
title: ModuleType 枚举 |Microsoft Docs
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
ms.openlocfilehash: 831f1fbcb2da205fa08286a1fbbbf414e66075d4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019925"
---
# <a name="moduletype-enumeration"></a>ModuleType 枚举
指定模块是否应支持进程内服务器或进程外服务器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum ModuleType;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`InProc`|进程内服务器。|  
|`OutOfProc`|进程外服务器。|  
|`DisableCaching`|禁用模块上的缓存机制。|  
|`InProcDisableCaching`|组合`InProc`和`DisableCaching`。|  
|`OutOfProcDisableCaching`|组合`OutOfProc`和`DisableCaching`。|  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)