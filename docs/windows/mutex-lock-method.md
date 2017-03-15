---
title: "Mutex::Lock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock 方法"
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Mutex::Lock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一直等到当前对象或与指定句柄关联的互斥体对象释放此斥锁，或指定的超时间隔已过去。  
  
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
 Mutex 对象句柄。  
  
## <a name="return-value"></a>返回值  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另请参阅
 [Mutex 类](../windows/mutex-class1.md)