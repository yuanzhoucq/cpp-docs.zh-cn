---
title: "AsyncBase::Cancel 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::Cancel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Cancel 方法"
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::Cancel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是一个异步操作。  
  
## 语法  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## 返回值  
 默认情况下，总是返回 S\_OK。  
  
## 备注  
 Cancel\(\) 是 IAsyncInfo::Cancel 的默认实现，并且不执行实际工作。  实际取消异步操作，请重写 OnCancel\(\) 纯虚方法。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)