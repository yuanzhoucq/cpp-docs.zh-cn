---
title: "event 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event 类"
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# event 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

一个明确知道并发运行时的手动重置事件。  
  
## 语法  
  
```  
class event;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[event::~event 析构函数](../Topic/event::~event%20Destructor.md)|销毁事件。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[event::reset 方法](../Topic/event::reset%20Method.md)|将事件重置为非终止状态。|  
|[event::set 方法](../Topic/event::set%20Method.md)|发出事件信号。|  
|[event::wait 方法](../Topic/event::wait%20Method.md)|等待事件变为终止状态。|  
|[event::wait\_for\_multiple 方法](../Topic/event::wait_for_multiple%20Method.md)|等待多个事件变为终止状态。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[event::timeout\_infinite 常量](../Topic/event::timeout_infinite%20Constant.md)|表示等待永远不应超时的值。|  
  
## 备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 继承层次结构  
 `event`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)