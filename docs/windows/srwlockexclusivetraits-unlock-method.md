---
title: "SRWLockExclusiveTraits::Unlock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 7fd6b0fb-8b88-4a43-aa74-0d7fe47a0da6
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SRWLockExclusiveTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的 SRWLock 互斥对象的版本控制。  
  
## 语法  
  
```  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
#### 参数  
 `srwlock`  
 为 SRWLock 对象的句柄。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [SRWLockExclusiveTraits 结构](../windows/srwlockexclusivetraits-structure.md)