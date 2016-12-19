---
title: "AsyncBase::CheckValidStateForDelegateCall 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForDelegateCall 方法"
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::CheckValidStateForDelegateCall 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试委托属性是否可在当前异步状态修改。  
  
## 语法  
  
```  
inline HRESULT CheckValidStateForDelegateCall();  
```  
  
## 返回值  
 S\_OK，如果能修改属性；委托否则，E\_ILLEGAL\_METHOD\_CALL。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)