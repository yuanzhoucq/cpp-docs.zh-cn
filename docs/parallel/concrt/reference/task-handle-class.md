---
title: "task_handle 类 | Microsoft Docs"
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
  - "ppl/concurrency::task_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_handle 类"
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: 23
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_handle 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_handle` 类表示单个并行工作项目。  它封装了说明和执行一段工作所需的数据。  
  
## 语法  
  
```  
template<  
   typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### 参数  
 `_Function`  
 将调用的函数对象类型，以执行 `task_handle` 对象表示的工作。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[task\_handle::task\_handle 构造函数](../Topic/task_handle::task_handle%20Constructor.md)|构造新的 `task_handle` 对象。  任务的工作通过调用指定为构造函数的参数的函数来执行。|  
|[task\_handle::~task\_handle 析构函数](../Topic/task_handle::~task_handle%20Destructor.md)|销毁 `task_handle` 对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[task\_handle::operator\(\) 运算符](../Topic/task_handle::operator\(\)%20Operator.md)|函数调用运算符，运行时调用该运算符来执行任务句柄的工作。|  
  
## 备注  
 `task_handle` 对象可与 `structured_task_group` 或更常规的 `task_group` 对象结合使用来将工作分解为并行任务。  有关更多信息，请参见 [任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 请注意，`task_handle` 对象的创建者负责维护创建的 `task_handle` 对象的生存期，直到并发运行时不再需要它为止。  通常，这意味着 `task_handle` 对象不得销毁，直到其排队的 `task_group` 或 `structured_task_group` 的 `wait` 或 `run_and_wait` 方法被调用。  
  
 `task_handle` 对象通常与 C\+\+ lambda 结合使用。  因为您不知道 lambda 的真实类型，所以 [make\_task](../Topic/make_task%20Function.md) 函数通常用于创建 `task_handle` 对象。  
  
 运行时创建您传递给 `task_handle` 对象的工作函数副本。  因此，您传递给 `task_handle` 对象的函数对象中发生的任何状态变更均不会出现在该函数对象的副本中。  
  
## 继承层次结构  
 `task_handle`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 类](../Topic/task_group%20Class.md)   
 [structured\_task\_group 类](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [make\_task 函数](../Topic/make_task%20Function.md)   
 [task\_group::run 方法](../Topic/task_group::run%20Method.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)