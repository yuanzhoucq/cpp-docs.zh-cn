---
title: "AsyncBase::TryTransitionToCompleted 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryTransitionToCompleted 方法"
ms.assetid: 8d038e0a-47ec-4cfc-8aeb-6821282df67a
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::TryTransitionToCompleted 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示当前异步操作是否已完成。  
  
## 语法  
  
```  
bool TryTransitionToCompleted(  
   void  
);  
```  
  
## 返回值  
 如果异步操作同步完成，则为 `true`；否则为 `false`。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)