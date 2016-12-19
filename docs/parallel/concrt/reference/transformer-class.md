---
title: "transformer 类 | Microsoft Docs"
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
  - "agents/concurrency::transformer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transformer 类"
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# transformer 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`transformer` 消息块是一个单目标、多源、有序的 `propagator_block`，可以接受同一类型的消息，并能够存储大量不同类型的消息。  
  
## 语法  
  
```  
template<  
   class _Input,  
   class _Output  
>  
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>, multi_link_registry<ISource<_Input>>>;  
```  
  
#### 参数  
 `_Input`  
 缓冲区接受的消息负载类型。  
  
 `_Output`  
 缓冲区存储的和传播的消息的负载类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[transformer::transformer 构造函数](../Topic/transformer::transformer%20Constructor.md)|已重载。  构造 `transformer` 消息块。|  
|[transformer::~transformer 析构函数](../Topic/transformer::~transformer%20Destructor.md)|销毁 `transformer` 消息块。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[transformer::accept\_message 方法](../Topic/transformer::accept_message%20Method.md)|接受由此 `transformer` 消息块提供的消息，将所有权转移给调用方。|  
|[transformer::consume\_message 方法](../Topic/transformer::consume_message%20Method.md)|使用先前由 `transformer` 提供并由目标保留的消息，将所有权转移给调用方。|  
|[transformer::link\_target\_notification 方法](../Topic/transformer::link_target_notification%20Method.md)|通知新的目标已链接至此 `transformer` 消息块的回调。|  
|[transformer::propagate\_message 方法](../Topic/transformer::propagate_message%20Method.md)|将 `ISource` 块中的消息异步传递到此 `transformer` 消息块中。  在由源块调用时，其由 `propagate` 方法调用。|  
|[transformer::propagate\_to\_any\_targets 方法](../Topic/transformer::propagate_to_any_targets%20Method.md)|对输入消息执行转换函数。|  
|[transformer::release\_message 方法](../Topic/transformer::release_message%20Method.md)|释放以前的消息保留。（覆盖 [source\_block::release\_message](../Topic/source_block::release_message%20Method.md)。）|  
|[transformer::reserve\_message 方法](../Topic/transformer::reserve_message%20Method.md)|保留此 `transformer` 消息块之前提供的消息。（覆盖 [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md)。）|  
|[transformer::resume\_propagation 方法](../Topic/transformer::resume_propagation%20Method.md)|释放保留后继续传播。（覆盖 [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md)。）|  
|[transformer::send\_message 方法](../Topic/transformer::send_message%20Method.md)|将消息从 `ISource` 块同步传递到此 `transformer` 消息块中。  在由源块调用时，其由 `send` 方法调用。|  
|[transformer::supports\_anonymous\_source 方法](../Topic/transformer::supports_anonymous_source%20Method.md)|重写 `supports_anonymous_source` 方法表示此块可以接受未链接的源为其提供的消息。重写 \( [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)。\)|  
  
## 备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `transformer`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [call 类](../../../parallel/concrt/reference/call-class.md)