---
title: "IUMSCompletionList 结构 | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSCompletionList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSCompletionList 结构"
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSCompletionList 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示 UMS 完成列表。  如果为 UMS 线程块，将分离计划程序指定的计划上下文，以决定初始线程阻塞时，在底层虚拟处理器根上计划什么。  如果初始线程未阻止，则操作系统会让之在完成列表中排队，该列表可以通过该接口访问。  计划程序可以在指定的计划上下文上或搜索工作的任意地方查询完成列表。  
  
## 语法  
  
```  
struct IUMSCompletionList;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IUMSCompletionList::GetUnblockNotifications 方法](../Topic/IUMSCompletionList::GetUnblockNotifications%20Method.md)|检索 `IUMSUnblockNotification` 接口链，表示自上次调用此方法以来其关联的线程代理已解除阻塞的执行上下文。|  
  
## 备注  
 计划程序必须非常注意使用此接口排队完成列表中的项后要执行的操作。  这些项应该放在可运行的上下文的计划程序列表中，并且通常应尽快可访问。  完全有可能已给予一个取消排队的项任意锁的所有权。  计划程序可不进行任何函数调用，该调用可在取消排队项目调用和在通常可从计划程序访问的列表上放置项目之间进行阻止。  
  
## 继承层次结构  
 `IUMSCompletionList`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 结构](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSUnblockNotification 结构](../../../parallel/concrt/reference/iumsunblocknotification-structure.md)