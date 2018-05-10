---
title: 'Synclockwithstatust:: Getstatus 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03addd8d89c54eddb5deb721ab47d46e8b945edd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>返回值  
 SyncLockWithStatusT 类，如基于的对象上等待操作的结果[互斥体](../windows/mutex-class1.md)或[信号量](../windows/semaphore-class.md)。 零 (0) 指示等待操作返回发送信号的状态;否则，另一种状态发生，如超时值已用。  
  
## <a name="remarks"></a>备注  
 检索当前 SyncLockWithStatusT 对象的等待状态。  
  
 GetStatus() 函数检索的基础值[status_](../windows/synclockwithstatust-status-data-member.md)数据成员。 当基于 SyncLockWithStatusT 类的对象执行锁定操作时，该对象首先等待该对象变成可用。 该等待操作的结果存储在`status_`数据成员。 可能值`status_`数据成员是等待操作的返回值。 有关详细信息，请参阅的返回值**WaitForSingleObjectEx()** MSDN 库中的函数。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)