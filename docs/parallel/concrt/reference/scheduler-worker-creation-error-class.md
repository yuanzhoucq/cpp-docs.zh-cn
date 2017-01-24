---
title: "scheduler_worker_creation_error 类 | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_worker_creation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_worker_creation_error 类"
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_worker_creation_error 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类介绍由于并发运行时未能创建辅助执行上下文而抛出异常。  
  
## 语法  
  
```  
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[scheduler\_worker\_creation\_error::scheduler\_worker\_creation\_error 构造函数](../Topic/scheduler_worker_creation_error::scheduler_worker_creation_error%20Constructor.md)|已重载。  构造 `scheduler_worker_creation_error` 对象。|  
  
## 备注  
 该异常通常在从并发运行时内调用操作系统创建运行上下文失败时引发。  执行上下文是在并发运行时任务的线程。  通常将从调用 Win32 方法 `GetLastError` 返回的错误代码转换为类型 `HRESULT` 的值，并可以通过 `get_error_code` 基类方法检索。  
  
## 继承层次结构  
 `exception`  
  
 [scheduler\_resource\_allocation\_error](../../../parallel/concrt/reference/scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)