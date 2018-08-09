---
title: 'Srwlock:: Lockshared 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
dev_langs:
- C++
helpviewer_keywords:
- LockShared method
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fda64126709515fcf3e174a6f3cbdea22d5ee9e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011057"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared 方法
获取**SRWLock**在共享模式下的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>参数  
 *lock*  
 指向**SRWLock**对象。  
  
## <a name="return-value"></a>返回值  
 **SRWLock**在共享模式下的对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [SRWLock 类](../windows/srwlock-class.md)