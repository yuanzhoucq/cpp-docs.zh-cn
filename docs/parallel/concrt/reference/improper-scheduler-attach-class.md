---
title: "improper_scheduler_attach 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_scheduler_attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_attach 类"
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_scheduler_attach 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在 `Attach` 调用方法已经附加到当前上下文的 `Scheduler` 对象时。  
  
## 语法  
  
```  
class improper_scheduler_attach : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[improper\_scheduler\_attach::improper\_scheduler\_attach 构造函数](../Topic/improper_scheduler_attach::improper_scheduler_attach%20Constructor.md)|已重载。  构造 `improper_scheduler_attach` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `improper_scheduler_attach`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)