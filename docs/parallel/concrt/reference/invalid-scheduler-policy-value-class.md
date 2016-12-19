---
title: "invalid_scheduler_policy_value 类 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_scheduler_policy_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_value 类"
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_scheduler_policy_value 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当 `SchedulerPolicy` 对象的策略键设置为该键时，一个无效值介绍异常引发此类。  
  
## 语法  
  
```  
class invalid_scheduler_policy_value : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_scheduler\_policy\_value::invalid\_scheduler\_policy\_value 构造函数](../Topic/invalid_scheduler_policy_value::invalid_scheduler_policy_value%20Constructor.md)|已重载。  构造 `invalid_scheduler_policy_value` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 类](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)