---
title: "AsyncBase::OnClose 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::OnClose"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnClose 方法"
ms.assetid: 96766450-c262-4611-8534-7d190b799142
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::OnClose 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在派生类中重写时，结束异步刷新操作。  
  
## 语法  
  
```  
virtual void OnClose(  
   void  
) = 0;  
```  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)   
 [AsyncBase::Close 方法](../windows/asyncbase-close-method.md)