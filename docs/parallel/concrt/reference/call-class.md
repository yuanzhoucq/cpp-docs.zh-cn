---
title: "call 类 | Microsoft Docs"
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
  - "agents/concurrency::call"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call 类"
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# call 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`call` 消息块是多源有序的 `target_block`，可以在接收消息时调用指定的函数。  
  
## 语法  
  
```  
template<  
   class _Type,  
   class _FunctorType = std::tr1::function<void(_Type const&)>  
>  
class call : public target_block<multi_link_registry<ISource<_Type>>>;  
```  
  
#### 参数  
 `_Type`  
 传播至该块的消息的负载类型。  
  
 `_FunctorType`  
 该块可接受的函数签名。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[call::call 构造函数](../Topic/call::call%20Constructor.md)|已重载。  构造 `call` 消息块。|  
|[call::~call 析构函数](../Topic/call::~call%20Destructor.md)|销毁 `call` 消息块。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[call::process\_input\_messages 方法](../Topic/call::process_input_messages%20Method.md)|对输入消息执行调用函数。|  
|[call::process\_message 方法](../Topic/call::process_message%20Method.md)|处理此 `call` 消息块接受的消息。|  
|[call::propagate\_message 方法](../Topic/call::propagate_message%20Method.md)|将 `ISource` 块中的消息异步传递到此 `call` 消息块中。  在由源块调用时，其由 `propagate` 方法调用。|  
|[call::send\_message 方法](../Topic/call::send_message%20Method.md)|将消息从 `ISource` 块同步传递到此 `call` 消息块中。  在由源块调用时，其由 `send` 方法调用。|  
|[call::supports\_anonymous\_source 方法](../Topic/call::supports_anonymous_source%20Method.md)|重写 `supports_anonymous_source` 方法表示此块可以接受未链接的源为其提供的消息。重写 \( [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md)。\)|  
  
## 备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [target\_block](../../../parallel/concrt/reference/target-block-class.md)  
  
 `call`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [transformer 类](../../../parallel/concrt/reference/transformer-class.md)