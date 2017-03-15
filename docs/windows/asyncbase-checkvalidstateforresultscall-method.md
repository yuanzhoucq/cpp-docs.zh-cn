---
title: "AsyncBase::CheckValidStateForResultsCall 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForResultsCall 方法"
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::CheckValidStateForResultsCall 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

研究异步操作的结果是否可以在当前异步状态的集合。  
  
## 语法  
  
```  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## 返回值  
 S\_OK，则结果可以收集；否则，E\_ILLEGAL\_METHOD\_CALLE\_ILLEGAL\_METHOD\_CALL。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)