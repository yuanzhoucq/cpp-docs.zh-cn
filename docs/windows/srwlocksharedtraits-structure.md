---
title: "SRWLockSharedTraits 结构 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockSharedTraits 结构"
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockSharedTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

独占锁在锁定模式描述SRWLock类的常见特性。  
  
## 语法  
  
```  
struct SRWLockSharedTraits;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Type`|指针的同义词到 [SRWLOCK](../windows/srwlock-class.md) 类。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SRWLockSharedTraits::GetInvalidValue 方法](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|检索总是无效的 SRWLockSharedTraits 对象。|  
|[SRWLockSharedTraits::Unlock 方法](../windows/srwlocksharedtraits-unlock-method.md)|指定的 SRWLock 互斥对象的版本控制。|  
  
## 继承层次结构  
 `SRWLockSharedTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)