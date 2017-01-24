---
title: "task 类（并发运行时） | Microsoft Docs"
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
  - "ppltasks/concurrency::task"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task 类"
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task 类（并发运行时）
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

并行模式库 \(PPL\) `task` 类。  `task` 对象表示可异步且可与其他任务同时执行的工作，以及由并发运行时中的并行算法生成的并行工作。  它在成功完成时生成 `_ResultType` 类型结果。  类型为 `task<void>` 的任务不产生结果。  任务可以等待以及独立于其他任务取消。  它还可能由使用继续 \(`then`\)、联接 \(`when_all`\) 和选项 \(`when_any`\) 模式的其他任务构成。  
  
## 语法  
  
```  
template <  
   typename _Type  
>  
class task;  
  
template <>  
class task<void>;  
  
template<  
   typename _ReturnType  
>  
class task;  
```  
  
#### 参数  
 `_Type`  
 `T`  
 `_ReturnType`  
 此任务的结果类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|`result_type`|此类对象生成的结果的类型。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[task::task 构造函数](../Topic/task::task%20Constructor.md)|已重载。  构造 `task` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[task::get 方法](../Topic/task::get%20Method.md)|已重载。  返回此任务产生的结果。  如果任务不处于最终状态，则对 `get` 的调用会等待任务完成。  在调用带 `void` 的`result_type` 的任务时，此方法不返回值。|  
|[task::is\_apartment\_aware 方法](../Topic/task::is_apartment_aware%20Method.md)|确定任务是否解包 Windows 运行时 `IAsyncInfo` 接口或源自此任务。|  
|[task::is\_done 方法（并发运行时）](../Topic/task::is_done%20Method%20\(Concurrency%20Runtime\).md)|确定任务是否已完成。|  
|[task::scheduler 方法（并发运行时）](../Topic/task::scheduler%20Method%20\(Concurrency%20Runtime\).md)|返回此任务的计划程序|  
|[task::then 方法](../Topic/task::then%20Method.md)|已重载。  添加延续任务到此任务。|  
|[task::wait 方法](../Topic/task::wait%20Method.md)|等待此任务到达最终状态。  `wait` 可执行内联任务，前提是所有任务依赖项得到满足并且后台辅助线程没有将其选出执行。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[task::operator\!\= 运算符](../Topic/task::operator!=%20Operator.md)|已重载。  确定是否两个 `task` 对象表示不同的内部任务。|  
|[task::operator\= 运算符](../Topic/task::operator=%20Operator.md)|已重载。  将一个 `task` 对象的内容替换为另一个对象的内容。|  
|[task::operator\=\= 运算符](../Topic/task::operator==%20Operator.md)|已重载。  确定是否两个 `task` 对象表示相同的内部任务。|  
  
## 备注  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 继承层次结构  
 `task`  
  
## 要求  
 **标头：**ppltasks.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)