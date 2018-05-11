---
title: target_block 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 754bc6add99974ff204c977e47f35486cc830d95
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="targetblock-class"></a>target_block 类
`target_block` 类是抽象基类，它提供基本链接管理功能和针对仅限于目标的块的错误检查。  
  
## <a name="syntax"></a>语法  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>参数  
 `_SourceLinkRegistry`  
 要用于保存源链接链接注册表。  
  
 `_MessageProcessorType`  
 消息处理的处理器类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`source_iterator`|有关迭代器的类型`source_link_manager`此`target_block`对象。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[target_block](#ctor)|构造 `target_block` 对象。|  
|[~ target_block 析构函数](#dtor)|销毁`target_block`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[propagate](#propagate)|以异步方式将从源块的消息传递到此目标块中。|  
|[发送](#send)|以同步方式将从源块的消息传递到此目标块中。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[async_send](#async_send)|以异步方式发送邮件以进行处理。|  
|[decline_incoming_messages](#decline_incoming_messages)|指示到块应拒绝新消息。|  
|[enable_batched_processing](#enable_batched_processing)|启用该块的批处理。|  
|[initialize_target](#initialize_target)|初始化基对象。 具体而言，`message_processor`对象需要将其初始化。|  
|[link_source](#link_source)|将指定的源块链接到此`target_block`对象。|  
|[process_input_messages](#process_input_messages)|处理作为输入接收的消息。|  
|[process_message](#process_message)|在派生类中重写时，处理由该 `target_block` 对象接受的消息。|  
|[propagate_message](#propagate_message)|当在派生类中重写此方法以异步方式将消息传递从`ISource`至此块`target_block`对象。 由调用`propagate`方法，调用由源块时。|  
|[register_filter](#register_filter)|注册一个将在接收到每个消息调用的筛选器方法。|  
|[remove_sources](#remove_sources)|等待未完成的异步发送操作完成后，将取消链接所有源。|  
|[send_message](#send_message)|当在派生类中重写此方法以同步方式将消息传递从`ISource`至此块`target_block`对象。 由调用`send`方法，调用由源块时。|  
|[sync_send](#sync_send)|同步发送邮件以进行处理。|  
|[unlink_source](#unlink_source)|将指定的源块与该`target_block`对象。|  
|[unlink_sources](#unlink_sources)|取消链接所有源块与该`target_block`对象。 (重写[itarget:: Unlink_sources](itarget-class.md#unlink_sources)。)|  
|[wait_for_async_sends](#wait_for_async_sends)|等待所有异常传播完成。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="async_send"></a> async_send 

 以异步方式发送邮件以进行处理。  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向要发送的消息的指针。  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 指示到块应拒绝新消息。  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>备注  
 若要确保正在析构时拒绝新消息的析构函数调用此方法。  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 启用该块的批处理。  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a> initialize_target 

 初始化基对象。 具体而言，`message_processor`对象需要将其初始化。  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 要用于计划任务计划程序。  
  
 `_PScheduleGroup`  
 要用于计划任务的计划组。  
  
##  <a name="link_source"></a> link_source 

 将指定的源块链接到此`target_block`对象。  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 指向的指针`ISource`是链接的块。  
  
### <a name="remarks"></a>备注  
 不应直接在上调用此函数`target_block`对象。 应连接在一起使用的块`link_target`方法`ISource`块，将调用`link_source`相应目标上的方法。  
  
##  <a name="process_input_messages"></a> process_input_messages 

 处理作为输入接收的消息。  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
  
##  <a name="process_message"></a> process_message 

 在派生类中重写时，处理由该 `target_block` 对象接受的消息。  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a> 传播 

 以异步方式将从源块的消息传递到此目标块中。  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
##  <a name="propagate_message"></a> propagate_message 

 当在派生类中重写此方法以异步方式将消息传递从`ISource`至此块`target_block`对象。 由调用`propagate`方法，调用由源块时。  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
##  <a name="register_filter"></a> register_filter 

 注册一个将在接收到每个消息调用的筛选器方法。  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>参数  
 `_Filter`  
 筛选器方法中。  
  
##  <a name="remove_sources"></a> remove_sources 

 等待未完成的异步发送操作完成后，将取消链接所有源。  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>备注  
 所有目标块应都调用此例程以在其析构函数中删除的源。  
  
##  <a name="send"></a> 发送 

 以同步方式将从源块的消息传递到此目标块中。  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果`_PMessage`或`_PSource`参数是`NULL`。  
  
 使用`send`方法之外消息启动并传播在网络中的消息是危险的可能会导致死锁。  
  
 当`send`返回时，消息是已被接受，并传输到目标块，或它已被拒绝由目标。  
  
##  <a name="send_message"></a> send_message 

 当在派生类中重写此方法以同步方式将消息传递从`ISource`至此块`target_block`对象。 由调用`send`方法，调用由源块时。  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
### <a name="remarks"></a>备注  
 默认情况下，返回此块`declined`除非由派生类中重写。  
  
##  <a name="sync_send"></a> sync_send 

 同步发送邮件以进行处理。  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向要发送的消息的指针。  
  
##  <a name="ctor"></a> target_block 

 构造 `target_block` 对象。  
  
```
target_block();
```  
  
##  <a name="dtor"></a> ~ target_block 

 销毁`target_block`对象。  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a> unlink_source 

 将指定的源块与该`target_block`对象。  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PSource`  
 指向的指针`ISource`要取消链接的块。  
  
##  <a name="unlink_sources"></a> unlink_sources 

 取消链接所有源块与该`target_block`对象。  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a> wait_for_async_sends 

 等待所有异常传播完成。  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>备注  
 消息块析构函数使用此方法以确保所有异步操作有时间完成，然后销毁块。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ITarget 类](itarget-class.md)
