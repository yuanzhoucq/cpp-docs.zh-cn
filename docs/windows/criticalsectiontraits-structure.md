---
title: "CriticalSectionTraits 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs: C++
helpviewer_keywords: CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c24d8dea31a87094329276af3ebfaf9f06136adc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 结构
专用化 CriticalSection 对象，以支持无效的关键部分或发布临界区的功能。  
  
## <a name="syntax"></a>语法  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`Type`|A`typedef`到关键部分定义指针。 `Type`定义为`typedef CRITICAL_SECTION* Type;`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue 方法](../windows/criticalsectiontraits-getinvalidvalue-method.md)|专用化 CriticalSection 模板，以便始终无效的模板。|  
|[CriticalSectionTraits::Unlock 方法](../windows/criticalsectiontraits-unlock-method.md)|专用化 CriticalSection 模板，以便它支持释放指定的关键部分对象的所有权。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)