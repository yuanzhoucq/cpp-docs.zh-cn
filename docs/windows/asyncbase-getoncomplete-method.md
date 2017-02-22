---
title: "AsyncBase::GetOnComplete 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::GetOnComplete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOnComplete 方法"
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::GetOnComplete 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制当前进度事件处理程序的地址为指定的变量。  
  
## 语法  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### 参数  
 `completeHandler`  
 当前完成事件处理程序地址存储的位置。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_ILLEGAL\_METHOD\_CALL。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)