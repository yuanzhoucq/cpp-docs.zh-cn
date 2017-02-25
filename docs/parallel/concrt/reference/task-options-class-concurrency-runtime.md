---
title: "task_options 类（并发运行时） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::task_options"
dev_langs: 
  - "C++"
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# task_options 类（并发运行时）
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示创建任务的允许选项  
  
## 语法  
  
```  
class task_options;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[task\_options::task\_options 构造函数（并发运行时）](../Topic/task_options::task_options%20Constructor%20\(Concurrency%20Runtime\).md)|已重载。  任务创建选项的默认列表|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[task\_options::get\_cancellation\_token 方法（并发运行时）](../Topic/task_options::get_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|返回取消标记|  
|[task\_options::get\_continuation\_context 方法（并发运行时）](../Topic/task_options::get_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|返回延续内容。|  
|[task\_options::get\_scheduler 方法（并发运行时）](../Topic/task_options::get_scheduler%20Method%20\(Concurrency%20Runtime\).md)|返回计划程序|  
|[task\_options::has\_cancellation\_token 方法（并发运行时）](../Topic/task_options::has_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|指示是否已由用户指定取消标记|  
|[task\_options::has\_scheduler 方法（并发运行时）](../Topic/task_options::has_scheduler%20Method%20\(Concurrency%20Runtime\).md)|指示是否已由用户指定计划程序 n|  
|[task\_options::set\_cancellation\_token 方法（并发运行时）](../Topic/task_options::set_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|在选项中设置给定标记|  
|[task\_options::set\_continuation\_context 方法（并发运行时）](../Topic/task_options::set_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|在选项中设置给定延续上下文|  
  
## 继承层次结构  
 `task_options`  
  
## 要求  
 **标头：**ppltasks.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)