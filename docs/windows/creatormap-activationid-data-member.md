---
title: 'Creatormap:: Activationid 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b9fd147f0821e14e825b2a8c0e8d7ad35104fe9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653009"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId 数据成员
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
### <a name="parameters"></a>参数  
 *clsid*  
 接口 ID。  
  
 *getRuntimeName*  
 用于检索对象的 Windows 运行时名称的函数。  
  
## <a name="remarks"></a>备注  
 表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [CreatorMap 结构](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)