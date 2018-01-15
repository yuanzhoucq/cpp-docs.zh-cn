---
title: "SRWLockSharedTraits 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs: C++
helpviewer_keywords: SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cadf94f1d336de7bac13572a045e7ac8487013cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 结构
描述中共享的锁模式的 SRWLock 类的共同特征。  
  
## <a name="syntax"></a>语法  
  
```  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`Type`|同义词指向的指针[SRWLOCK](../windows/srwlock-class.md)类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue 方法](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|检索始终无效的 SRWLockSharedTraits 对象。|  
|[SRWLockSharedTraits::Unlock 方法](../windows/srwlocksharedtraits-unlock-method.md)|释放指定 SRWLock 对象的独有控制。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)