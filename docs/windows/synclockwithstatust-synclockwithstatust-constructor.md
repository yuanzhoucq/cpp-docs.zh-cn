---
title: "SyncLockWithStatusT::SyncLockWithStatusT 构造函数 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockWithStatusT, 构造函数"
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockWithStatusT::SyncLockWithStatusT 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### 参数  
 `other`  
 对另一个 SyncLockWithStatusT 对象的一个 Rvalue 引用。  
  
 `sync`  
 对另一个 SyncLockWithStatusT 对象的引用。  
  
 `status`  
 `other` 参数或 `sync` 参数的 [status\_](../windows/synclockwithstatust-status-data-member.md) 数据成员的值。  
  
## 备注  
 初始化 SyncLockWithStatusT 类的新实例。  
  
 第一构造函数初始化参数从另一 SyncLockWithStatusT 的当前 SyncLockWithStatusT 对象指定的 `other`，然后 SyncLockWithStatusT 无效另一个对象。  第二个构造函数为 `protected`，并且 SyncLockWithStatusT 初始化当前对象到无效的状态。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)