---
title: "scheduler_ptr 结构（并发运行时） | Microsoft Docs"
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
  - "pplinterface/concurrency::scheduler_ptr"
dev_langs: 
  - "C++"
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 8
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_ptr 结构（并发运行时）
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示指向计划程序的指针。  此类存在是为了通过使用 shared\_ptr 允许共享生存期的规范，或通过使用原始指针允许无格式引用的规范。  
  
## 语法  
  
```  
struct scheduler_ptr;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[scheduler\_ptr::scheduler\_ptr 构造函数（并发运行时）](../Topic/scheduler_ptr::scheduler_ptr%20Constructor%20\(Concurrency%20Runtime\).md)|已重载。  创建一个从 shared\_ptr 到计划程序的计划程序指针|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[scheduler\_ptr::get 方法（并发运行时）](../Topic/scheduler_ptr::get%20Method%20\(Concurrency%20Runtime\).md)|返回指向计划程序的原始指针|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[scheduler\_ptr::operator bool 运算符（并发运行时）](../Topic/scheduler_ptr::operator%20bool%20Operator%20\(Concurrency%20Runtime\).md)|测试计划程序指针是否为非 null|  
|[scheduler\_ptr::operator\-\> 运算符（并发运行时）](../Topic/scheduler_ptr::operator-%3E%20Operator%20\(Concurrency%20Runtime\).md)|行为类似于指针|  
  
## 继承层次结构  
 `scheduler_ptr`  
  
## 要求  
 **标头：**pplinterface.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)