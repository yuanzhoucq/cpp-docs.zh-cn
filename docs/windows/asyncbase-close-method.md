---
title: "AsyncBase::Close 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::Close 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

结束异步操作。  
  
## 语法  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## 返回值  
 S\_OK，如果操作关闭或已关闭；否则，E\_ILLEGAL\_STATE\_CHANGE。  
  
## 备注  
 Close\(\) 是 IAsyncInfo::Close 的默认实现，并且不执行实际工作。  实际取消异步操作，请重写 OnClose\(\) 纯虚方法。  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)