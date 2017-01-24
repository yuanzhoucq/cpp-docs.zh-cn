---
title: "MutexTraits 结构 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MutexTraits 结构"
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MutexTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[mutex](../windows/mutex-class1.md) 类定义的共同特征。  
  
## 语法  
  
```  
struct MutexTraits : HANDLENullTraits;  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[MutexTraits::Unlock 方法](../windows/mutextraits-unlock-method.md)|共享资源的版本控制。|  
  
## 继承层次结构  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)