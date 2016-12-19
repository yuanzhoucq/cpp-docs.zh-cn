---
title: "task_canceled 类 | Microsoft Docs"
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
  - "concrt/concurrency::task_canceled"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_canceled 类"
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
caps.latest.revision: 11
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_canceled 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述以强制取消当前任务由 PPL 任务层引发的异常。  它还抛出`get()`上的方法[任务](../Topic/Task%20Class%20-%20Internal%20Members.md)，已取消任务。  
  
## 语法  
  
```  
class task_canceled : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[task\_canceled::task\_canceled 构造函数](../Topic/task_canceled::task_canceled%20Constructor.md)|已重载。  构造 `task_canceled` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `task_canceled`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task::get 方法](../Topic/task::get%20Method.md)   
 [cancel\_current\_task 函数](../Topic/cancel_current_task%20Function.md)