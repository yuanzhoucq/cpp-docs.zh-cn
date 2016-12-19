---
title: "AsyncBase::PutOnComplete 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::PutOnComplete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PutOnComplete 方法"
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::PutOnComplete 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置完成事件处理程序的地址为指定值。  
  
## 语法  
  
```  
STDMETHOD(  
   PutOnComplete  
)(TComplete* completeHandler);  
```  
  
#### 参数  
 `completeHandler`  
 完成事件处理程序中设置的地址。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_ILLEGAL\_METHOD\_CALL。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)