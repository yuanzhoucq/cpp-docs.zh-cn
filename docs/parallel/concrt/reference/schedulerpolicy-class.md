---
title: "SchedulerPolicy 类 | Microsoft Docs"
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
  - "concrt/concurrency::SchedulerPolicy"
  - "concrtrm/concurrency::SchedulerPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SchedulerPolicy 类"
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SchedulerPolicy 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`SchedulerPolicy` 类包含一组键\/值对，一个用于每个策略元素，其控制计划程序实例的行为。  
  
## 语法  
  
```  
class SchedulerPolicy;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[SchedulerPolicy::SchedulerPolicy 构造函数](../Topic/SchedulerPolicy::SchedulerPolicy%20Constructor.md)|已重载。  构造新的计划程序策略并用并发运行时和资源管理器支持的 [策略密钥](../Topic/PolicyElementKey%20Enumeration.md) 值填充。|  
|[SchedulerPolicy::~SchedulerPolicy 析构函数](../Topic/SchedulerPolicy::~SchedulerPolicy%20Destructor.md)|销毁计划程序策略。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[SchedulerPolicy::GetPolicyValue 方法](../Topic/SchedulerPolicy::GetPolicyValue%20Method.md)|检索作为 `_Key` 形参提供的策略键的值。|  
|[SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)|同时在 `SchedulerPolicy` 对象上设置 `MinConcurrency` 和 `MaxConcurrency` 策略。|  
|[SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)|设置 `_Key` 形参提供的策略键的值，并返回旧值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[SchedulerPolicy::operator\= 运算符](../Topic/SchedulerPolicy::operator=%20Operator.md)|从另一个计划程序策略分配计划程序策略。|  
  
## 备注  
 有关可通过 `SchedulerPolicy` 类控制的策略的更多信息，请参见 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)。  
  
## 继承层次结构  
 `SchedulerPolicy`  
  
## 要求  
 **页眉：**concrt.h，concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [CurrentScheduler 类](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)