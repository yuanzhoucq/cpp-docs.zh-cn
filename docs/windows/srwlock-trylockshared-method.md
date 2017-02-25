---
title: "SRWLock::TryLockShared 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLockShared 方法"
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SRWLock::TryLockShared 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尝试获取在共享的图案 SRWLock 对象当前或指定的 SRWLock 对象。  
  
## 语法  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### 参数  
 `lock`  
 指向SRWLock对象的指针。  
  
## 返回值  
 如果成功，则共享模式的一 SRWLock 对象并调用的线程获取锁的所有权。  否则，状态无效的 SRWLock 对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [SRWLock 类](../windows/srwlock-class.md)