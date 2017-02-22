---
title: "default_scheduler_exists 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::default_scheduler_exists"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default_scheduler_exists 类"
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# default_scheduler_exists 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在 `Scheduler::SetDefaultSchedulerPolicy` 调用方法时，默认计划程序在进程中已存在。  
  
## 语法  
  
```  
class default_scheduler_exists : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[default\_scheduler\_exists::default\_scheduler\_exists 构造函数](../Topic/default_scheduler_exists::default_scheduler_exists%20Constructor.md)|已重载。  构造 `default_scheduler_exists` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `default_scheduler_exists`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler::SetDefaultSchedulerPolicy 方法](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)