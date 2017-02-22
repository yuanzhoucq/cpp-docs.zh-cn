---
title: "AsyncStatusInternal 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::Details::AsyncStatusInternal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncStatusInternal 枚举"
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# AsyncStatusInternal 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
enum AsyncStatusInternal;  
```  
  
## 备注  
 指定要枚举异步操作的状态和 **Windows::Foundation::AsyncStatus** 枚举之间的映射。  
  
## 成员  
 `_Created`  
 为：:Windows::Foundation::AsyncStatus::Created 的等效项  
  
 `_Started`  
 为：:Windows::Foundation::AsyncStatus::Started 的等效项  
  
 `_Completed`  
 为：:Windows::Foundation::AsyncStatus::Completed 的等效项  
  
 `_Cancelled`  
 为：:Windows::Foundation::AsyncStatus::Cancelled 的等效项  
  
 `_Error`  
 为：:Windows::Foundation::AsyncStatus::Error 的等效项  
  
## 要求  
 **页眉：**async.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)