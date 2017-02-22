---
title: "target_block 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::target_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "target_block 类"
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# target_block 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`target_block` 类是一个抽象基类，提供基本链接管理功能和仅限于目标的块的错误检查。  
  
## 语法  
  
```  
template<  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>  
>  
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### 参数  
 `_SourceLinkRegistry`  
 要用于保存源链接的链接注册表。  
  
 `_MessageProcessorType`  
 用于消息处理的处理器类型。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`source_iterator`|用于此 `target_block` 对象的 `source_link_manager` 的迭代器类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[target\_block::target\_block 构造函数](../Topic/target_block::target_block%20Constructor.md)|构造 `target_block` 对象。|  
|[target\_block::~target\_block 析构函数](../Topic/target_block::~target_block%20Destructor.md)|销毁 `target_block` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[target\_block::propagate 方法](../Topic/target_block::propagate%20Method.md)|将消息从源块异步传递到此目标块中。|  
|[target\_block::send 方法](../Topic/target_block::send%20Method.md)|将消息从源块同步传递到此目标块中。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[target\_block::async\_send 方法](../Topic/target_block::async_send%20Method.md)|异步发送一条消息以进行处理。|  
|[target\_block::decline\_incoming\_messages 方法](../Topic/target_block::decline_incoming_messages%20Method.md)|指示新消息应该拒绝的块。|  
|[target\_block::enable\_batched\_processing 方法](../Topic/target_block::enable_batched_processing%20Method.md)|启动该块批处理。|  
|[target\_block::initialize\_target 方法](../Topic/target_block::initialize_target%20Method.md)|初始化基本对象。  特别地，`message_processor` 对象需要进行初始化。|  
|[target\_block::link\_source 方法](../Topic/target_block::link_source%20Method.md)|将指定源块链接到此 `target_block` 对象。|  
|[target\_block::process\_input\_messages 方法](../Topic/target_block::process_input_messages%20Method.md)|处理接收作为输入的消息。|  
|[target\_block::process\_message 方法](../Topic/target_block::process_message%20Method.md)|当在派生类中重写时，处理由该 `target_block` 对象接受的消息。|  
|[target\_block::propagate\_message 方法](../Topic/target_block::propagate_message%20Method.md)|在派生类中重写后，该方法异步地将消息从 `ISource` 块传递至该 `target_block` 对象。  在由源块调用时，其由 `propagate` 方法调用。|  
|[target\_block::register\_filter 方法](../Topic/target_block::register_filter%20Method.md)|注册将在接收到的每条消息上调用的筛选器方法。|  
|[target\_block::remove\_sources 方法](../Topic/target_block::remove_sources%20Method.md)|在等待未完成的异步发送操作完成后，断开所有源链接。|  
|[target\_block::send\_message 方法](../Topic/target_block::send_message%20Method.md)|在派生类中重写后，该方法同步地将消息从 `ISource` 块传递至该 `target_block` 对象。  在由源块调用时，其由 `send` 方法调用。|  
|[target\_block::sync\_send 方法](../Topic/target_block::sync_send%20Method.md)|同步发送一条消息以进行处理。|  
|[target\_block::unlink\_source 方法](../Topic/target_block::unlink_source%20Method.md)|与来自该 `target_block` 对象的指定的源块不同。|  
|[target\_block::unlink\_sources 方法](../Topic/target_block::unlink_sources%20Method.md)|与来自该 `target_block` 对象的所有源块取消链接。（重写 [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md)。）|  
|[target\_block::wait\_for\_async\_sends 方法](../Topic/target_block::wait_for_async_sends%20Method.md)|等待所有异常传播完成。|  
  
## 继承层次结构  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 `target_block`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget 类](../../../parallel/concrt/reference/itarget-class.md)