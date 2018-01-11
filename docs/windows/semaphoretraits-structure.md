---
title: "SemaphoreTraits 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs: C++
helpviewer_keywords: SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 103f02109558d9f301f9f1eec867e9379c102e17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 结构
定义信号量对象的共同特征。  
  
## <a name="syntax"></a>语法  
  
```  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SemaphoreTraits::Unlock 方法](../windows/semaphoretraits-unlock-method.md)|版本控制共享资源。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)