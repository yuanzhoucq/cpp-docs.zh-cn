---
title: "timer 类 | Microsoft Docs"
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
  - "agents/concurrency::timer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "timer 类"
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# timer 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`timer` 消息块是一个单目标 `source_block`，能够在经过指定的时间段后或在特定时间间隔向其目标发送消息。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<_Type>>>;  
```  
  
#### 参数  
 `_Type`  
 该块输出消息的负载类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[timer::timer 构造函数](../Topic/timer::timer%20Constructor.md)|已重载。  构造将在指定的时间间隔后触发指定消息的 `timer` 消息块。|  
|[timer::~timer 析构函数](../Topic/timer::~timer%20Destructor.md)|销毁 `timer` 消息块。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[timer::pause 方法](../Topic/timer::pause%20Method.md)|停止 `timer` 消息块。  如果它是一个重复的 `timer` 消息块，则可以通过后续 `start()` 调用重启。  对于非重复计时器，这与 `stop` 调用有相同的效果。|  
|[timer::start 方法](../Topic/timer::start%20Method.md)|启动 `timer` 消息块。  对此调用之后指定的毫秒数，指定的值将作为 `message` 向下传播。|  
|[timer::stop 方法](../Topic/timer::stop%20Method.md)|停止 `timer` 消息块。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[timer::accept\_message 方法](../Topic/timer::accept_message%20Method.md)|接受由此 `timer` 消息块提供的消息，将所有权转移给调用方。|  
|[timer::consume\_message 方法](../Topic/timer::consume_message%20Method.md)|使用先前由 `timer` 提供并由目标保留的消息，将所有权转移给调用方。|  
|[timer::link\_target\_notification 方法](../Topic/timer::link_target_notification%20Method.md)|通知新的目标已链接至此 `timer` 消息块的回调。|  
|[timer::propagate\_to\_any\_targets 方法](../Topic/timer::propagate_to_any_targets%20Method.md)|尝试将 `timer` 块生成的消息提供给所有链接的目标。|  
|[timer::release\_message 方法](../Topic/timer::release_message%20Method.md)|释放以前的消息保留。（覆盖 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)。）|  
|[timer::reserve\_message 方法](../Topic/timer::reserve_message%20Method.md)|保留此 `timer` 消息块之前提供的消息。（覆盖 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)。）|  
|[timer::resume\_propagation 方法](../Topic/timer::resume_propagation%20Method.md)|释放保留后继续传播。（覆盖 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)。）|  
  
## 备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `timer`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)