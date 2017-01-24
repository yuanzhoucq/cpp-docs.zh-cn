---
title: "improper_scheduler_reference 类 | Microsoft Docs"
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
  - "concrt/concurrency::improper_scheduler_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_reference 类"
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_scheduler_reference 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在 `Reference` 调用方法关闭时的一 `Scheduler` 对象，从不属于该计划程序的一部分的上下文。  
  
## 语法  
  
```  
class improper_scheduler_reference : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[improper\_scheduler\_reference::improper\_scheduler\_reference 构造函数](../Topic/improper_scheduler_reference::improper_scheduler_reference%20Constructor.md)|已重载。  构造 `improper_scheduler_reference` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `improper_scheduler_reference`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Reference 方法](../Topic/Scheduler::Reference%20Method.md)