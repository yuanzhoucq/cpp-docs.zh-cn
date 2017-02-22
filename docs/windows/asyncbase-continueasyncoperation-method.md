---
title: "AsyncBase::ContinueAsyncOperation 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ContinueAsyncOperation 方法"
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::ContinueAsyncOperation 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定异步操作是否应继续处理还是应暂停。  
  
## 语法  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## 返回值  
 `true`，如果没有异步操作的当前状态是 *started*，表示操作应继续。  否则，`false`，表示操作应暂停。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)