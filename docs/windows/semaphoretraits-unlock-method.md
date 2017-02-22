---
title: "SemaphoreTraits::Unlock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SemaphoreTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

共享资源的版本控制。  
  
## 语法  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### 参数  
 `h`  
 到信号量对象的句柄。  
  
## 备注  
 如果解除阻塞操作不成功，Unlock\(\) 发出指示失败原因时的错误。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [SemaphoreTraits 结构](../windows/semaphoretraits-structure.md)