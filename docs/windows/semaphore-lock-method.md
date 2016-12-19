---
title: "Semaphore::Lock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock 方法"
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore::Lock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一直等到当前对象或与指定句柄关联的 Semaphore 对象处于已发出信号状态或指定超时间隔已过去。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
#### <a name="parameters"></a>参数  
 `milliseconds`  
 超时间隔（以毫秒为单位）。 默认值为 INFINITE，其表示将无限期地等待。  
  
 `h`  
 Semaphore 对象的句柄。  
  
## <a name="return-value"></a>返回值  
 A Details::SyncLockWithStatusT\<HandleTraits::SemaphoreTraits>  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
[Semaphore 类](../windows/semaphore-class.md)
 