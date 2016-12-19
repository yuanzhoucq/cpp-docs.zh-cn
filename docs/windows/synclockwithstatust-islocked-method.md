---
title: "SyncLockWithStatusT::IsLocked 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsLocked 方法"
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockWithStatusT::IsLocked 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
bool IsLocked() const;  
```  
  
## 备注  
 指示当前 SyncLockWithStatusT 对象是否拥有一资源；即 SyncLockWithStatusT 对象已被 *锁定*。  
  
## 返回值  
 如果SyncLockWithStatusT对象是锁定的，则为 **true**；否则为 **false**。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)