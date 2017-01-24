---
title: "ordered_message_processor 类 | Microsoft Docs"
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
  - "agents/concurrency::ordered_message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered_message_processor 类"
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ordered_message_processor 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ordered_message_processor` 是允许消息块按接受的顺序处理消息的 `message_processor`。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class ordered_message_processor : public message_processor<_Type>;  
```  
  
#### 参数  
 `_Type`  
 处理器处理的消息的负载类型。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`type`|`_Type` 的类型别名。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ordered\_message\_processor::ordered\_message\_processor 构造函数](../Topic/ordered_message_processor::ordered_message_processor%20Constructor.md)|构造 `ordered_message_processor` 对象。|  
|[ordered\_message\_processor::~ordered\_message\_processor 析构函数](../Topic/ordered_message_processor::~ordered_message_processor%20Destructor.md)|销毁 `ordered_message_processor` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ordered\_message\_processor::async\_send 方法](../Topic/ordered_message_processor::async_send%20Method.md)|如果尚未异步对消息进行排队和开始处理任务，则完成此操作。（重写 [message\_processor::async\_send](../Topic/message_processor::async_send%20Method.md)。）|  
|[ordered\_message\_processor::initialize 方法](../Topic/ordered_message_processor::initialize%20Method.md)|使用相应的回调函数、计划程序和计划组初始化 `ordered_message_processor` 对象。|  
|[ordered\_message\_processor::initialize\_batched\_processing 方法](../Topic/ordered_message_processor::initialize_batched_processing%20Method.md)|Initialize 批消息处理|  
|[ordered\_message\_processor::sync\_send 方法](../Topic/ordered_message_processor::sync_send%20Method.md)|如果尚未同步对消息进行排队和开始处理任务，那么完成此操作。（重写 [message\_processor::sync\_send](../Topic/message_processor::sync_send%20Method.md)。）|  
|[ordered\_message\_processor::wait 方法](../Topic/ordered_message_processor::wait%20Method.md)|特定于处理器的自旋等待，在消息块的析构函数中使用以确保在销毁块之前有时间完成所有异步方法处理任务。（重写 [message\_processor::wait](../Topic/message_processor::wait%20Method.md)。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[ordered\_message\_processor::process\_incoming\_message 方法](../Topic/ordered_message_processor::process_incoming_message%20Method.md)|异步调用的处理函数。  它将消息取消排队，并开始处理它们。（重写 [message\_processor::process\_incoming\_message](../Topic/message_processor::process_incoming_message%20Method.md)。）|  
  
## 继承层次结构  
 [message\_processor](../../../parallel/concrt/reference/message-processor-class.md)  
  
 `ordered_message_processor`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)