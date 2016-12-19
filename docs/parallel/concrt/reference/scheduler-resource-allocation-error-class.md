---
title: "scheduler_resource_allocation_error 类 | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_resource_allocation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_resource_allocation_error 类"
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_resource_allocation_error 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述由于无法在并发运行时中获取关键资源而抛出的异常。  
  
## 语法  
  
```  
class scheduler_resource_allocation_error : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[scheduler\_resource\_allocation\_error::scheduler\_resource\_allocation\_error 构造函数](../Topic/scheduler_resource_allocation_error::scheduler_resource_allocation_error%20Constructor.md)|已重载。  构造 `scheduler_resource_allocation_error` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[scheduler\_resource\_allocation\_error::get\_error\_code 方法](../Topic/scheduler_resource_allocation_error::get_error_code%20Method.md)|返回导致异常的错误代码。|  
  
## 备注  
 该异常通常在从并发运行时内调用操作系统失败时引发。  通常将从调用 Win32 方法 `GetLastError` 返回的错误代码转换为类型 `HRESULT` 的值，并可以用 `get_error_code` 方法检索。  
  
## 继承层次结构  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)