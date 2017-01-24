---
title: "task_continuation_context 类 | Microsoft Docs"
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
  - "ppltasks/concurrency::task_continuation_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_continuation_context 类"
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 15
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_continuation_context 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_continuation_context` 类允许你指定要在何处执行继续。  它仅在从 Windows 应用商店应用程序使用此类时才有用。  对于非 Windows 应用商店应用程序，任务延续执行上下文通过运行时确定，并且不可配置。  
  
## 语法  
  
```  
class task_continuation_context : public details::_ContextCallback;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[task\_continuation\_context::use\_arbitrary 方法](../Topic/task_continuation_context::use_arbitrary%20Method.md)|创建任务延续上下文，以便运行时选择延续的执行上下文。|  
|[task\_continuation\_context::use\_current 方法](../Topic/task_continuation_context::use_current%20Method.md)|返回表示当前执行上下文的任务延续上下文对象。|  
|[task\_continuation\_context::use\_default 方法](../Topic/task_continuation_context::use_default%20Method.md)|创建默认任务延续上下文。|  
  
## 继承层次结构  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## 要求  
 **标头：**ppltasks.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/zh-cn/5389e8a5-5038-40b6-844a-55e9b58ad35f)