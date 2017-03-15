---
title: "SyncLockWithStatusT::GetStatus 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetStatus 方法"
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SyncLockWithStatusT::GetStatus 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>返回值  
 根据 SyncLockWithStatusT 类，如对象的等待操作的结果 [互斥体](../windows/mutex-class1.md) 或 [信号量](../windows/semaphore-class.md)。 零 (0) 指示等待操作返回已发出信号的状态;否则，另一种状态出现，如所经过的超时值。  
  
## <a name="remarks"></a>备注  
 检索当前 SyncLockWithStatusT 对象的等待状态。  
  
 GetStatus() 函数用于检索基础 [status_](../windows/synclockwithstatust-status-data-member.md) 数据成员。 当基于 SyncLockWithStatusT 类的对象执行锁定操作时，该对象第一次等待发出对象变得可用。 这一等待操作的结果存储在 `status_` 数据成员。 可能值 `status_` 数据成员是等待操作的返回值。 有关详细信息，请参阅的返回值 **WaitForSingleObjectEx()** MSDN 库中的函数。  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)