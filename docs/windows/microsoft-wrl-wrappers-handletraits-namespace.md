---
title: "Microsoft::WRL::Wrappers::HandleTraits Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aec9ff1b4294257f692d76a96960820379116b0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits 命名空间
描述常见基于句柄的资源类型的特征。  
  
## <a name="syntax"></a>语法  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>成员  
  
### <a name="structures"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)|专用化`CriticalSection`对象以支持无效的关键部分或发布临界区的功能。|  
|[EventTraits 结构](../windows/eventtraits-structure.md)|定义的特征`Event`类句柄。|  
|[FileHandleTraits 结构](../windows/filehandletraits-structure.md)|定义的文件句柄的特征。|  
|[HANDLENullTraits 结构](../windows/handlenulltraits-structure.md)|定义未初始化句柄的共同特征。|  
|[HANDLETraits 结构](../windows/handletraits-structure.md)|定义句柄的共同的特征。|  
|[MutexTraits 结构](../windows/mutextraits-structure.md)|定义的共性[互斥体](../windows/mutex-class1.md)类。|  
|[SemaphoreTraits 结构](../windows/semaphoretraits-structure.md)|定义信号量对象的共同特征。|  
|[SRWLockExclusiveTraits 结构](../windows/srwlockexclusivetraits-structure.md)|描述常见特征`SRWLock`独占锁模式下的类。|  
|[SRWLockSharedTraits 结构](../windows/srwlocksharedtraits-structure.md)|描述常见特征`SRWLock`在共享锁定模式下的类。|  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)