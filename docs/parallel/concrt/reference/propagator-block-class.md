---
title: "propagator_block 类 | Microsoft Docs"
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
  - "agents/concurrency::propagator_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propagator_block 类"
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# propagator_block 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`propagator_block` 类是同时为源和目标的消息块的一个抽象基类。  组合了 `source_block` 和 `target_block` 类的功能。  
  
## 语法  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class propagator_block : public source_block<_TargetLinkRegistry, _MessageProcessorType>, public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### 参数  
 `_TargetLinkRegistry`  
 要用于保存目标链接的链接注册表。  
  
 `_SourceLinkRegistry`  
 要用于保存源链接的链接注册表。  
  
 `_MessageProcessorType`  
 用于消息处理的处理器类型。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`source_iterator`|该 `propagator_block` 的 `source_link_manager` 的迭代器类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[propagator\_block::propagator\_block 构造函数](../Topic/propagator_block::propagator_block%20Constructor.md)|构造 `propagator_block` 对象。|  
|[propagator\_block::~propagator\_block 析构函数](../Topic/propagator_block::~propagator_block%20Destructor.md)|销毁 `propagator_block` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[propagator\_block::propagate 方法](../Topic/propagator_block::propagate%20Method.md)|将消息从源块异步传递到此目标块中。|  
|[propagator\_block::send 方法](../Topic/propagator_block::send%20Method.md)|对此块同步发出一条消息。  由 `ISource` 块调用。  此函数完成时, 消息将已传播到块中。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[propagator\_block::decline\_incoming\_messages 方法](../Topic/propagator_block::decline_incoming_messages%20Method.md)|指示新消息应该拒绝的块。|  
|[propagator\_block::initialize\_source\_and\_target 方法](../Topic/propagator_block::initialize_source_and_target%20Method.md)|初始化基本对象。  特别地，`message_processor` 对象需要进行初始化。|  
|[propagator\_block::link\_source 方法](../Topic/propagator_block::link_source%20Method.md)|将指定源块链接到此 `propagator_block` 对象。|  
|[propagator\_block::process\_input\_messages 方法](../Topic/propagator_block::process_input_messages%20Method.md)|处理输入消息。  这用于传播器块才有用的，从 source\_block 派生\(重写 [source\_block::process\_input\_messages](../Topic/source_block::process_input_messages%20Method.md)。\)|  
|[propagator\_block::propagate\_message 方法](../Topic/propagator_block::propagate_message%20Method.md)|在派生类中重写后，该方法异步地将消息从 `ISource` 块传递至该 `propagator_block` 对象。  在由源块调用时，其由 `propagate` 方法调用。|  
|[propagator\_block::register\_filter 方法](../Topic/propagator_block::register_filter%20Method.md)|注册将在接收到的每条消息上调用的筛选器方法。|  
|[propagator\_block::remove\_network\_links 方法](../Topic/propagator_block::remove_network_links%20Method.md)|从此 `propagator_block` 对象中移除所有源和目标网络链接。|  
|[propagator\_block::send\_message 方法](../Topic/propagator_block::send_message%20Method.md)|在派生类中重写后，该方法同步地将消息从 `ISource` 块传递至该 `propagator_block` 对象。  在由源块调用时，其由 `send` 方法调用。|  
|[propagator\_block::unlink\_source 方法](../Topic/propagator_block::unlink_source%20Method.md)|与来自该 `propagator_block` 对象的指定的源块不同。|  
|[propagator\_block::unlink\_sources 方法](../Topic/propagator_block::unlink_sources%20Method.md)|与来自该 `propagator_block` 对象的所有源块取消链接。（重写 [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md)。）|  
  
## 备注  
 为避免多个继承，`propagator_block` 类继承自 `source_block` 类以及 `ITarget` 抽象类。  此处复制了 `target_block` 类中的大部分功能。  
  
## 继承层次结构  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `propagator_block`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [source\_block 类](../../../parallel/concrt/reference/source-block-class.md)   
 [ITarget 类](../../../parallel/concrt/reference/itarget-class.md)