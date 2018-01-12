---
title: "Creatormap:: Activationid 数据成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs: C++
helpviewer_keywords: activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 912b18ff3e1be04913cb9345e4ac5bde25d2e039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId 数据成员
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## <a name="parameters"></a>参数  
 `clsid`  
 接口 ID。  
  
 `getRuntimeName`  
 检索对象的 Windows 运行时名称函数。  
  
## <a name="remarks"></a>备注  
 表示通过经典的 COM 类 ID 或 Windows 运行时名称标识的对象 ID。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [CreatorMap 结构](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)