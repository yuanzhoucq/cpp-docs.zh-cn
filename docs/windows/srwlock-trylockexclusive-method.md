---
title: 'Srwlock:: Trylockexclusive 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 993031604469aa09608f936f260869a3b53dbc9c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652765"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive 方法
尝试获取**SRWLock**对象中的当前或指定的排他模式**SRWLock**对象。 如果调用成功，则调用线程采用锁的所有权。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>参数  
 *lock*  
 指向**SRWLock**对象。  
  
## <a name="return-value"></a>返回值  
 如果成功， **SRWLock**排他模式和调用线程中的对象采用锁的所有权。 否则为**SRWLock**对象，其状态为无效。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [SRWLock 类](../windows/srwlock-class.md)