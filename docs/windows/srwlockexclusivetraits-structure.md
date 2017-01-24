---
title: "SRWLockExclusiveTraits 结构 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockExclusiveTraits 结构"
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockExclusiveTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

独占锁在锁定模式描述SRWLock类的常见特性。  
  
## 语法  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Type`|指针的同义词到 [SRWLOCK](../windows/srwlock-class.md) 类。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SRWLockExclusiveTraits::GetInvalidValue 方法](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|检索总是无效的 SRWLockExclusiveTraits 对象。|  
|[SRWLockExclusiveTraits::Unlock 方法](../windows/srwlockexclusivetraits-unlock-method.md)|指定的 SRWLock 互斥对象的版本控制。|  
  
## 继承层次结构  
 `SRWLockExclusiveTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)