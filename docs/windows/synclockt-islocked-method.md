---
title: "SyncLockT::IsLocked 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsLocked 方法"
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# SyncLockT::IsLocked 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
bool IsLocked() const;  
```  
  
## 返回值  
 如果SyncLockT对象是锁定的，则为 **true**；否则为 **false**。  
  
## 备注  
 指示当前 SyncLockT 对象是否拥有一资源；即 SyncLockT 对象已被 *锁定*。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)