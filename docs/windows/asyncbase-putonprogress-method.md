---
title: "AsyncBase::PutOnProgress 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::PutOnProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PutOnProgress 方法"
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::PutOnProgress 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置完成事件处理程序的地址为指定值。  
  
## 语法  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### 参数  
 `progressHandler`  
 发展事件处理程序中设置的地址。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_ILLEGAL\_METHOD\_CALL。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)