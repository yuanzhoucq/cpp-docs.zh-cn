---
title: "AsyncBase::ErrorCode 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::ErrorCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorCode 方法"
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::ErrorCode 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索当前异步操作中的错误代码。  
  
## 语法  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### 参数  
 `error`  
 此操作存储当前错误代码的位置。  
  
## 备注  
 此操作是线程安全的。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)