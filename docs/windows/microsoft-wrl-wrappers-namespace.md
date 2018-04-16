---
title: "Microsoft::WRL::Wrappers Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7633bcd784fa7b9b5f7255e25e8ddc52c5b93db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空间
定义简化对象、字符串和句柄的生存期管理的“获取资源即初始化”(RAII) 包装器类型。  
  
## <a name="syntax"></a>语法  
  
```  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>成员  
  
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSection 类](../windows/criticalsection-class.md)|表示关键部分对象。|  
|[Event 类（Windows 运行时 C++ 模板库）](../windows/event-class-windows-runtime-cpp-template-library.md)|表示一个事件。|  
|[HandleT 类](../windows/handlet-class.md)|表示对象的句柄。|  
|[HString 类](../windows/hstring-class.md)|为操作 HSTRING 句柄提供支持。|  
|[HStringReference 类](../windows/hstringreference-class.md)|表示 HSTRING 创建从现有字符串。|  
|[Mutex 类](../windows/mutex-class1.md)|表示完全控制共享资源的同步对象。|  
|[RoInitializeWrapper 类](../windows/roinitializewrapper-class.md)|初始化 Windows 运行时。|  
|[Semaphore 类](../windows/semaphore-class.md)|表示控制可支持有限数量用户的共享资源的同步对象。|  
|[SRWLock 类](../windows/srwlock-class.md)|表示精简读取器/编写器锁定。|  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)