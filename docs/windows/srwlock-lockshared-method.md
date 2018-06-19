---
title: 'Srwlock:: Lockshared 方法 |Microsoft 文档'
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
ms.openlocfilehash: fccc72814ca5c4fff417e0b6221ef0f3c045a5bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33895744"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared 方法
获取在共享模式下的 SRWLock 对象。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>参数  
 `lock`  
 指向 SRWLock 对象的指针。  
  
## <a name="return-value"></a>返回值  
 在共享模式下 SRWLock 对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [SRWLock 类](../windows/srwlock-class.md)