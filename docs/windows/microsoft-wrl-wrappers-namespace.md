---
title: Microsoft::WRL::Wrappers Namespace |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9667a3660f46db0a61991545108d66bf0cac9f38
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017791"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空间
定义简化对象、字符串和句柄的生存期管理的“获取资源即初始化”(RAII) 包装器类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
|[HString 类](../windows/hstring-class.md)|为处理 HSTRING 句柄提供支持。|  
|[HStringReference 类](../windows/hstringreference-class.md)|表示从现有字符串创建的 HSTRING。|  
|[Mutex 类](../windows/mutex-class1.md)|表示完全控制共享资源的同步对象。|  
|[RoInitializeWrapper 类](../windows/roinitializewrapper-class.md)|初始化 Windows 运行时。|  
|[Semaphore 类](../windows/semaphore-class.md)|表示控制可支持有限数量用户的共享资源的同步对象。|  
|[SRWLock 类](../windows/srwlock-class.md)|表示精简读取器/编写器锁定。|  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)