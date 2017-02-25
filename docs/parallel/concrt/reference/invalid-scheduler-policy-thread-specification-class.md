---
title: "invalid_scheduler_policy_thread_specification 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_thread_specification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_thread_specification 类"
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_scheduler_policy_thread_specification 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，当尝试设置 `SchedulerPolicy` 对象的并发限制此类时 `MinConcurrency` 键的值大于 `MaxConcurrency` 键的值小于。  
  
## 语法  
  
```  
class invalid_scheduler_policy_thread_specification : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_scheduler\_policy\_thread\_specification::invalid\_scheduler\_policy\_thread\_specification 构造函数](../Topic/invalid_scheduler_policy_thread_specification::invalid_scheduler_policy_thread_specification%20Constructor.md)|已重载。  构造 `invalid_scheduler_policy_value` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 类](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)