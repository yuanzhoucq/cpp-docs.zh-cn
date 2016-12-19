---
title: "scheduler_not_attached 类 | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_not_attached"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_not_attached 类"
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_not_attached 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在需要一个计划程序附加到当前上下文的操作时，将会显示一个不是。  
  
## 语法  
  
```  
class scheduler_not_attached : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[scheduler\_not\_attached::scheduler\_not\_attached 构造函数](../Topic/scheduler_not_attached::scheduler_not_attached%20Constructor.md)|已重载。  构造 `scheduler_not_attached` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `scheduler_not_attached`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)