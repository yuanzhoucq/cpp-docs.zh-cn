---
title: "invalid_scheduler_policy_key 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_key"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_key 类"
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_scheduler_policy_key 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在无效或未知键传递给 `SchedulerPolicy` 对象构造函数时，也 `SchedulerPolicy` 对象的 `SetPolicyValue` 方法通过必须更改使用其他方式例如 `SetConcurrencyLimits` 方法，的键。  
  
## 语法  
  
```  
class invalid_scheduler_policy_key : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_scheduler\_policy\_key::invalid\_scheduler\_policy\_key 构造函数](../Topic/invalid_scheduler_policy_key::invalid_scheduler_policy_key%20Constructor.md)|已重载。  构造 `invalid_scheduler_policy_key` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 类](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)