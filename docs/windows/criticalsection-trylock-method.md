---
title: "CriticalSection::TryLock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLock 方法"
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection::TryLock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尝试输入临界区，但不阻塞。  如果调用成功，调用线程获取临界区的所有权。  
  
## 语法  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### 参数  
 `cs`  
 一个用户指定的关键部分对象。  
  
## 返回值  
 非零值，如果关键部分成功进入或当前线程已经拥有关键部分。  零，如果其他线程已经拥有关键部分。  
  
## 备注  
 第一个函数当前 **TryLock** 影响关键部分对象。  第二个 **TryLock** 函数对用户指定的关键部分。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [CriticalSection 类](../windows/criticalsection-class.md)