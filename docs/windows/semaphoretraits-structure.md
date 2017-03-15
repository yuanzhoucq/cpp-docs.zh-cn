---
title: "SemaphoreTraits 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SemaphoreTraits 结构"
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SemaphoreTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义信号量对象的公共特性。  
  
## 语法  
  
```  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SemaphoreTraits::Unlock 方法](../windows/semaphoretraits-unlock-method.md)|共享资源的版本控制。|  
  
## 继承层次结构  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)