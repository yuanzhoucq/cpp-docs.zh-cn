---
title: "DeferrableEventArgs::InvokeAllFinished 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# DeferrableEventArgs::InvokeAllFinished 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用以指示处理延迟事件的全部过程都已完成。  
  
## 语法  
  
```cpp  
void InvokeAllFinished()  
```  
  
## 备注  
 事件源调用 [InvokeAll](../windows/eventsource-invokeall-method.md) 后，你应调用此方法。  调用此方法将阻止发生进一步的延迟，并且如果没有发生延迟将强制完成处理程序来执行。  
  
 有关代码示例，请参阅 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。  
  
## 要求  
 **标头：**event.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)