---
title: "message_processor 类 | Microsoft Docs"
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
  - "agents/concurrency::message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_processor 类"
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 16
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# message_processor 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`message_processor` 类是用于处理 `message` 对象的抽象基类。  信息的顺序无法确保固定。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class message_processor;  
```  
  
#### 参数  
 `_Type`  
 由此 `message_processor` 对象处理的消息内负载的数据类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`type`|`_Type` 的类型别名。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[message\_processor::async\_send 方法](../Topic/message_processor::async_send%20Method.md)|在派生类中重写时，异步将消息放置到块中。|  
|[message\_processor::sync\_send 方法](../Topic/message_processor::sync_send%20Method.md)|在派生类中重写时，同步将消息放置到块中。|  
|[message\_processor::wait 方法](../Topic/message_processor::wait%20Method.md)|当在派生类中重写时，等待所有异步操作完成。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[message\_processor::process\_incoming\_message 方法](../Topic/message_processor::process_incoming_message%20Method.md)|在派生类中重写时，执行到块中的消息转发处理。  每调用一次则添加一则新消息，并且发现队列为空。|  
  
## 继承层次结构  
 `message_processor`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ordered\_message\_processor 类](../../../parallel/concrt/reference/ordered-message-processor-class.md)