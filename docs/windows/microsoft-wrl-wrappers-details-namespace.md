---
title: "Microsoft::WRL::Wrappers::Details Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs: C++
helpviewer_keywords: Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 520871366f02ef636eef5b2cc9c19344979c6fb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 命名空间
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## <a name="members"></a>成员  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[SyncLockT 类](../windows/synclockt-class.md)|表示可能需要独占的类型或共享资源的所有权。|  
|[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)|表示可能需要独占的类型或共享资源的所有权。|  
  
### <a name="methods"></a>方法  
  
|名称|描述|  
|----------|-----------------|  
|[CompareStringOrdinal 方法](../windows/comparestringordinal-method.md)|比较两个指定`HSTRING`对象，并返回一个整数，指示二者在排序顺序中的相对位置。|  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)