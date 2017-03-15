---
title: "AsyncBase::CurrentStatus 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::CurrentStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CurrentStatus 方法"
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::CurrentStatus 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查当前异步操作的状态。  
  
## 语法  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### 参数  
 `status`  
 此操作存储当前状态的位置。  
  
## 备注  
 此操作是线程安全的。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)   
 [AsyncStatusInternal 枚举](../windows/asyncstatusinternal-enumeration.md)