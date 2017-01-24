---
title: "AsyncBase::OnCancel 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::OnCancel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnCancel 方法"
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::OnCancel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在派生类中重写时，取消同步操作。  
  
## 语法  
  
```  
virtual void OnCancel(  
   void  
) = 0;  
```  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)   
 [AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)