---
title: "source_block 类 | Microsoft Docs"
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
  - "agents/concurrency::source_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_block 类"
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# source_block 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`source_block` 是仅限于源的块的抽象基类。  该类提供了基本的链接管理功能，还提供了常见的错误检查。  
  
## 语法  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;  
```  
  
#### 参数  
 `_TargetLinkRegistry`  
 要用于保存目标链接的链接注册表。  
  
 `_MessageProcessorType`  
 用于消息处理的处理器类型。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`target_iterator`|要遍历已连接的目标的迭代器。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[source\_block::source\_block 构造函数](../Topic/source_block::source_block%20Constructor.md)|构造 `source_block` 对象。|  
|[source\_block::~source\_block 析构函数](../Topic/source_block::~source_block%20Destructor.md)|销毁 `source_block` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[source\_block::accept 方法](../Topic/source_block::accept%20Method.md)|接受由此 `source_block` 对象提供的消息，将所有权转移给调用方。|  
|[source\_block::acquire\_ref 方法](../Topic/source_block::acquire_ref%20Method.md)|获取此 `source_block` 对象上的引用计数，以防止删除。|  
|[source\_block::consume 方法](../Topic/source_block::consume%20Method.md)|使用先前由 `source_block` 对象提供并由目标成功保留的消息，将所有权转移给调用方。|  
|[source\_block::link\_target 方法](../Topic/source_block::link_target%20Method.md)|将目标块链接到此 `source_block` 对象。|  
|[source\_block::release 方法](../Topic/source_block::release%20Method.md)|释放以前成功的消息保留。|  
|[source\_block::release\_ref 方法](../Topic/source_block::release_ref%20Method.md)|释放此 `source_block` 对象上的引用数。|  
|[source\_block::reserve 方法](../Topic/source_block::reserve%20Method.md)|保留此 `source_block` 对象之前提供的消息。|  
|[source\_block::unlink\_target 方法](../Topic/source_block::unlink_target%20Method.md)|从此 `source_block` 对象取消目标块的链接。|  
|[source\_block::unlink\_targets 方法](../Topic/source_block::unlink_targets%20Method.md)|从该 `source_block` 对象断开所有目标块的链接。（重写 [ISource::unlink\_targets](../Topic/ISource::unlink_targets%20Method.md)。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[source\_block::accept\_message 方法](../Topic/source_block::accept_message%20Method.md)|当在派生类中重写时，接受源提供的消息。  消息块应重写此方法以验证 `_MsgId` 并返回一条消息。|  
|[source\_block::async\_send 方法](../Topic/source_block::async_send%20Method.md)|如果尚未异步对消息进行排队和开始传播任务，则完成此操作。|  
|[source\_block::consume\_message 方法](../Topic/source_block::consume_message%20Method.md)|当在派生类中重写时，使用之前保留的消息。|  
|[source\_block::enable\_batched\_processing 方法](../Topic/source_block::enable_batched_processing%20Method.md)|启动该块批处理。|  
|[source\_block::initialize\_source 方法](../Topic/source_block::initialize_source%20Method.md)|初始化此 `source_block` 内的 `message_propagator`。|  
|[source\_block::link\_target\_notification 方法](../Topic/source_block::link_target_notification%20Method.md)|通知新的目标已链接至此 `source_block` 对象的回调。|  
|[source\_block::process\_input\_messages 方法](../Topic/source_block::process_input_messages%20Method.md)|处理输入消息。  这用于传播器块才有用的，从source\_block 派生|  
|[source\_block::propagate\_output\_messages 方法](../Topic/source_block::propagate_output_messages%20Method.md)|传播消息到目标。|  
|[source\_block::propagate\_to\_any\_targets 方法](../Topic/source_block::propagate_to_any_targets%20Method.md)|当在派生类中重写，将给定消息传播至任何或所有链接的目标。  这是消息块的主传播例程。|  
|[source\_block::release\_message 方法](../Topic/source_block::release_message%20Method.md)|当在派生类中被重写时，释放之前的消息保留。|  
|[source\_block::remove\_targets 方法](../Topic/source_block::remove_targets%20Method.md)|移除此源块的所有目标链接。  这应从析构函数调用。|  
|[source\_block::reserve\_message 方法](../Topic/source_block::reserve_message%20Method.md)|当在派生类中重写时，保留之前由该 `source_block` 对象提供的消息。|  
|[source\_block::resume\_propagation 方法](../Topic/source_block::resume_propagation%20Method.md)|在派生类中重写时，在释放保留后恢复传播。|  
|[source\_block::sync\_send 方法](../Topic/source_block::sync_send%20Method.md)|如果尚未同步对消息进行排队和开始传播任务，那么完成此操作。|  
|[source\_block::unlink\_target\_notification 方法](../Topic/source_block::unlink_target_notification%20Method.md)|通知目标已在此 `source_block` 对象中取消链接的回调。|  
|[source\_block::wait\_for\_outstanding\_async\_sends 方法](../Topic/source_block::wait_for_outstanding_async_sends%20Method.md)|等待所有异常传播完成。  该特定于传播函数的自旋等待，在消息块的析构函数中使用以确保在销毁块之前有时间完成所有异步传播。|  
  
## 备注  
 消息块应从此块派生，以利用此类提供的链接管理和同步。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `source_block`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource 类](../../../parallel/concrt/reference/isource-class.md)