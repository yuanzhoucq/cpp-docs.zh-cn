---
title: "AsyncBase::Start 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start 方法"
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::Start 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

开始异步操作。  
  
## 语法  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## 返回值  
 S\_OK，如果操作开始或已开始；否则，E\_ILLEGAL\_STATE\_CHANGE。  
  
## 备注  
 Start\(\) 是 IAsyncInfo::Start 的默认实现，并且不执行实际工作。  实际启动异步操作，请重写 OnStart\(\) 纯虚方法。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)