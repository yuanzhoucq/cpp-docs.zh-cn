---
title: "SRWLock::LockExclusive 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LockExclusive 方法"
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SRWLock::LockExclusive 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取以独占模式的一 SRWLock 对象。  
  
## 语法  
  
```  
SyncLockExclusive LockExclusive();  
  
static SyncLockExclusive LockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### 参数  
 `lock`  
 指向SRWLock对象的指针。  
  
## 返回值  
 获取以独占模式的一 SRWLock 对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [SRWLock 类](../windows/srwlock-class.md)