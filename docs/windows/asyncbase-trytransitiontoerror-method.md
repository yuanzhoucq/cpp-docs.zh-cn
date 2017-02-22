---
title: "AsyncBase::TryTransitionToError 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::TryTransitionToError"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryTransitionToError 方法"
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::TryTransitionToError 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示指定的错误代码是否能够修改内部错误状态。  
  
## 语法  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### 参数  
 `error`  
 错误HRESULT。  
  
## 返回值  
 `true`，如果内部错误状态更改；否则，返回 `false`。  
  
## 备注  
 时，错误状态已设置为 S\_OK，此操作修改错误状态。  此操作不起作用，如果出错状态已是错误，取消，完成或关闭。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)