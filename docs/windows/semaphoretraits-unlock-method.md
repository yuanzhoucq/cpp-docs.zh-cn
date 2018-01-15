---
title: "Semaphoretraits:: Unlock 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs: C++
helpviewer_keywords: Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 819f7d7e4e4d5b6182da6172bd91a1e799379b52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock 方法
版本控制共享资源。  
  
## <a name="syntax"></a>语法  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 信号量对象的句柄。  
  
## <a name="remarks"></a>备注  
 如果解除锁定操作不成功，Unlock() 会发出一个错误，指示失败的原因。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [SemaphoreTraits 结构](../windows/semaphoretraits-structure.md)