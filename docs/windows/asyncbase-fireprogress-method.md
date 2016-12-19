---
title: "AsyncBase::FireProgress 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::FireProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireProgress 方法"
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::FireProgress 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用活动进程事件处理程序。  
  
## 语法  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### 参数  
 `arg`  
 要调用的事件处理方法。  
  
## 备注  
 `ProgressTraits` 是从 [ArgTraitsHelper 结构](../windows/argtraitshelper-structure.md) 中派生的。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)