---
title: "SyncLockT::SyncLockT 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockT, 构造函数"
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# SyncLockT::SyncLockT 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
#### 参数  
 `other`  
 对另一个 SyncLockT 对象的一个 Rvalue 引用。  
  
 `sync`  
 对另一个 SyncLockWithStatusT 对象的引用。  
  
## 备注  
 初始化 SyncLockT 类的新实例。  
  
 第一构造函数初始化参数从另一 SyncLockWithStatusT 的当前 SyncLockT 对象指定的 `other`，然后 SyncLockWithStatusT 无效另一个对象。  第二个构造函数为 `protected`，并且初始化当前SyncLockT对象到无效的状态。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)