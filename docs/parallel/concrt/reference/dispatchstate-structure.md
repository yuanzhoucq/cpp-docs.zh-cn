---
title: "DispatchState 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::DispatchState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DispatchState 结构"
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DispatchState 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`DispatchState` 结构用于将状态传递给 `IExecutionContext::Dispatch` 方法。  它描述了一些情形，即调用 `IExecutionContext` 接口上的 `Dispatch` 方法的情形。  
  
## 语法  
  
```  
struct DispatchState;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[DispatchState::DispatchState 构造函数](../Topic/DispatchState::DispatchState%20Constructor.md)|构造新的 `DispatchState` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[DispatchState::m\_dispatchStateSize 数据成员](../Topic/DispatchState::m_dispatchStateSize%20Data%20Member.md)|此结构的大小，用于版本控制。|  
|[DispatchState::m\_fIsPreviousContextAsynchronouslyBlocked 数据成员](../Topic/DispatchState::m_fIsPreviousContextAsynchronouslyBlocked%20Data%20Member.md)|通知此上下文是否因为前一个上下文被异步阻塞而输入了 `Dispatch` 方法。  这只能在 UMS 计划上下文上使用，并对其他所有执行上下文设置为值 `0`。|  
|[DispatchState::m\_reserved 数据成员](../Topic/DispatchState::m_reserved%20Data%20Member.md)|保留用于将来信息传递的位。|  
  
## 继承层次结构  
 `DispatchState`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext::Dispatch 方法](../Topic/IExecutionContext::Dispatch%20Method.md)