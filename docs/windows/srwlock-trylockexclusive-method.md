---
title: "Srwlock:: Trylockexclusive 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs: C++
helpviewer_keywords: TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebeaae465bd387d3939f9588be3c4a8e5eaf507b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive 方法
尝试获取当前或指定 SRWLock 对象的排他模式的 SRWLock 对象。 如果调用成功，则调用线程将获得的锁定所有权。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>参数  
 `lock`  
 指向 SRWLock 对象的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，独占模式和调用的线程中的 SRWLock 对象采用锁的所有权。 否则为其状态无效的 SRWLock 对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [SRWLock 类](../windows/srwlock-class.md)