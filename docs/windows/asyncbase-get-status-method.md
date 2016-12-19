---
title: "AsyncBase::get_Status 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::get_Status"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_Status 方法"
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::get_Status 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索一个枚举值，它指示工作流同步操作的状态。  
  
## 语法  
  
```  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
#### 参数  
 `status`  
 句柄中的存储位置 。  有关更多信息，请参见 Windows Workflow Foundation:AsyncStatus enumeration 概述。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_ILLEGAL\_METHOD\_CALL。  
  
## 备注  
 此方法实现 IAsyncInfo::get\_Status。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)