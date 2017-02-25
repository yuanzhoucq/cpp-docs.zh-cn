---
title: "structured_task_group 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::structured_task_group"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "structured_task_group 类"
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# structured_task_group 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`structured_task_group` 类表示并行工作的高度结构化集合。  可以使用 `task_handle` 对象将各个任务排队至 `structured_task_group` 中，并等待它们完成，或在它们完成执行之前取消任务组，这将中止尚未开始执行的所有任务。  
  
## 语法  
  
```  
class structured_task_group;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[structured\_task\_group::structured\_task\_group 构造函数](../Topic/structured_task_group::structured_task_group%20Constructor.md)|已重载。  构造新的 `structured_task_group` 对象。|  
|[structured\_task\_group::~structured\_task\_group 析构函数](../Topic/structured_task_group::~structured_task_group%20Destructor.md)|销毁 `structured_task_group` 对象。  在析构函数执行之前，期望在对象上调用 `wait` 或 `run_and_wait` 方法，除非由于异常析构函数作为堆栈展开的结果执行。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[structured\_task\_group::cancel 方法](../Topic/structured_task_group::cancel%20Method.md)|尽最大努力尝试取消位于该任务组的工作的子树。  如果可能，任务组上每个计划的任务将传递性取消。|  
|[structured\_task\_group::is\_canceling 方法](../Topic/structured_task_group::is_canceling%20Method.md)|通知调用方任务组当前是否正在取消中。  这不一定表示 `cancel` 方法会在 `structured_task_group` 对象上调用（尽管这样肯定会让该方法返回 `true`）。  它可能是这种情况：`structured_task_group` 对象正在执行内联，而工作树上部的任务组已被取消。  例如，在运行时可以提前确定取消将流过 `structured_task_group` 对象的情况下，也将返回 `true`。|  
|[structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)|已重载。  在 `structured_task_group` 对象上安排轻量任务。  调用方管理 `_Task_handle` 形参中传递的 `task_handle` 对象的生存期。  带 `_Placement` 参数的版本导致任务偏向执行由该参数指定的位置。|  
|[structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)|已重载。  在 `structured_task_group` 对象的帮助下安排任务在调用上下文上运行内联来获取完全取消支持。  如果将 `task_handle` 对象作为参数传递给 `run_and_wait`，则调用方将负责管理 `task_handle` 对象的生存期。  该函数等待直到在 `structured_task_group` 对象上的所有工作都已完成或取消。|  
|[structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)|一直等待到 `structured_task_group` 上的所有工作完成或取消。|  
  
## 备注  
 在使用 `structured_task_group` 对象上有诸多严格限制，以获取性能：  
  
-   多个线程不能使用一个 `structured_task_group` 对象。  `structured_task_group` 对象上的所有操作必须由创建该对象的线程都执行。  该规则的两个例外为成员函数 `cancel` 和 `is_canceling`。  该对象可能未在 lambda 表达式的捕获列表中，并在某个任务中使用，除非该任务使用其中一个取消操作。  
  
-   计划到 `structured_task_group` 对象的所有任务均通过使用 `task_handle` 对象（您必须显示管理其生存期）进行计划。  
  
-   多个组可能只能按绝对嵌套顺序使用。  如果声明了两个 `structured_task_group` 对象，声明的第二个（内侧的）必须在任何方法之前析构，除非在第一个（外侧的）上调用了 `cancel` 或 `is_canceling`。  在相同或功能嵌套的范围内声明多个 `structured_task_group` 对象的情况以及任务通过 `run` 或 `run_and_wait` 方法排队至 `structured_task_group` 时的情况下，该条件均为 true。  
  
-   与一般 `task_group` 类不同，`structured_task_group` 类中的所有状态都是最终的。  在已将任务排队到组并等待它们完成后，您可能不会再次使用同一个组。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 继承层次结构  
 `structured_task_group`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 类](../Topic/task_group%20Class.md)   
 [task\_handle 类](../../../parallel/concrt/reference/task-handle-class.md)