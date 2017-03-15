---
title: "source_block 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::source_block
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 7d459d03153e95b779b8f8b19d2a68602b33acf8
ms.lasthandoff: 02/24/2017

---
# <a name="sourceblock-class"></a>source_block 类
`source_block` 是仅限于源的块的抽象基类。 该类提供基本链接管理功能和常见错误检查。  
  
## <a name="syntax"></a>语法  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>参数  
 `_TargetLinkRegistry`  
 若要用来存放目标链接的链接注册表。  
  
 `_MessageProcessorType`  
 消息处理的处理器类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`target_iterator`|用于遍历已连接的目标的迭代器。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[source_block 构造函数](#ctor)|构造 `source_block` 对象。|  
|[~ source_block 析构函数](#dtor)|销毁`source_block`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept 方法](#accept)|接受提供的这一条消息`source_block`对象，将所有权转移给调用方。|  
|[acquire_ref 方法](#acquire_ref)|获取对此的引用计数`source_block`对象，以防止删除。|  
|[consume 方法](#consume)|使用以前提供的这一条消息`source_block`对象，并成功由目标，将所有权转移给调用方保留。|  
|[link_target 方法](#link_target)|链接至该目标块`source_block`对象。|  
|[release 方法](#release)|释放以前的成功消息保留。|  
|[release_ref 方法](#release_ref)|释放此引用计数`source_block`对象。|  
|[reserve 方法](#reserve)|保留以前提供的这一条消息`source_block`对象。|  
|[unlink_target 方法](#unlink_target)|取消链接目标块与该`source_block`对象。|  
|[unlink_targets 方法](#unlink_targets)|断开所有目标块与该都链接`source_block`对象。 (重写[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[accept_message 方法](#accept_message)|当在派生类中重写，接受由源提供的消息。 消息块应重写此方法以验证`_MsgId`并返回一条消息。|  
|[async_send 方法](#async_send)|异步消息进行排队，并开始传播任务，如果这有没有已完成操作|  
|[consume_message 方法](#consume_message)|当在派生类中重写，使用先前保留的消息。|  
|[enable_batched_processing 方法](#enable_batched_processing)|启用该块的批处理。|  
|[initialize_source 方法](#initialize_source)|初始化`message_propagator`在此`source_block`。|  
|[link_target_notification 方法](#link_target_notification)|回调，以通知新的目标已链接到此`source_block`对象。|  
|[process_input_messages 方法](#process_input_messages)|处理输入消息。 这只适用于从源块派生的传播器块。|  
|[propagate_output_messages 方法](#propagate_output_messages)|将消息传播到目标。|  
|[propagate_to_any_targets 方法](#propagate_to_any_targets)|当在派生类中重写时将传播到任何或所有链接的目标将给定的消息。 这是消息块的主传播例程。|  
|[release_message 方法](#release_message)|当在派生类中重写时释放以前的消息保留。|  
|[remove_targets 方法](#remove_targets)|移除此源块的所有目标链接。 这应从析构函数调用。|  
|[reserve_message 方法](#reserve_message)|当在派生类中重写时保留以前提供的这一条消息`source_block`对象。|  
|[resume_propagation 方法](#resume_propagation)|当在派生类中重写，请在释放了保留后恢复传播。|  
|[sync_send 方法](#sync_send)|同步消息进行排队和启动传播任务，如果这有没有已完成操作。|  
|[unlink_target_notification 方法](#unlink_target_notification)|通知目标已被从此未链接的回调`source_block`对象。|  
|[wait_for_outstanding_async_sends 方法](#wait_for_outstanding_async_sends)|等待所有异步传播完成。 此传播器特定数值调节钮等待消息块的析构函数中使用，以确保所有异步传播有时间完成，然后再销毁块。|  
  
## <a name="remarks"></a>备注  
 消息块应派生自要利用链接管理和同步此类提供此块。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameaccepta-accept"></a><a name="accept"></a>接受 

 接受提供的这一条消息`source_block`对象，将所有权转移给调用方。  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`accept`方法。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
 `accept`正在由此提供一条消息时，调用目标方法`ISource`块。 消息指针返回可能不同于传递到`propagate`方法`ITarget`块，如果此源决定以使该消息的副本。  
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 当在派生类中重写，接受由源提供的消息。 消息块应重写此方法以验证`_MsgId`并返回一条消息。  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 运行时对象标识的`message`对象。  
  
### <a name="return-value"></a>返回值  
 指向调用方拥有所有权的消息的指针。  
  
### <a name="remarks"></a>备注  
 若要将所有权转移，应返回原始消息指针。 若要维护所有权，需要进行，并返回消息负载的副本。  
  
##  <a name="a-nameacquirerefa-acquireref"></a><a name="acquire_ref"></a>acquire_ref 

 获取对此的引用计数`source_block`对象，以防止删除。  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`对象被链接到此源期间`link_target`方法。  
  
##  <a name="a-nameasyncsenda-asyncsend"></a><a name="async_send"></a>async_send 

 异步消息进行排队，并开始传播任务，如果这有没有已完成操作  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一个指向`message`对象以异步方式发送。  
  
##  <a name="a-nameconsumea-consume"></a><a name="consume"></a>使用 

 使用以前提供的这一条消息`source_block`对象，并成功由目标，将所有权转移给调用方保留。  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的保留`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`consume`方法。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
 该方法将引发[bad_target](bad-target-class.md)异常如果参数`_PTarget`不表示调用目标`reserve`。  
  
 `consume`方法类似于是`accept`，但始终必须通过调用前面`reserve`返回`true`。  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 当在派生类中重写，使用先前保留的消息。  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象正在使用。  
  
### <a name="return-value"></a>返回值  
 指向调用方拥有所有权的消息的指针。  
  
### <a name="remarks"></a>备注  
 类似于`accept`，但通过调用前面始终`reserve`。  
  
##  <a name="a-nameenablebatchedprocessinga-enablebatchedprocessing"></a><a name="enable_batched_processing"></a>enable_batched_processing 

 启用该块的批处理。  
  
```
void enable_batched_processing();
```  
  
##  <a name="a-nameinitializesourcea-initializesource"></a><a name="initialize_source"></a>initialize_source 

 初始化`message_propagator`在此`source_block`。  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 要用于计划任务计划程序。  
  
 `_PScheduleGroup`  
 要用于计划任务的计划组。  
  
##  <a name="a-namelinktargeta-linktarget"></a><a name="link_target"></a>link_target 

 链接至该目标块`source_block`对象。  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向`ITarget`块要链接到此`source_block`对象。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 回调，以通知新的目标已链接到此`source_block`对象。  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="a-nameprocessinputmessagesa-processinputmessages"></a><a name="process_input_messages"></a>process_input_messages 

 处理输入消息。 这只适用于从源块派生的传播器块。  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
  
##  <a name="a-namepropagateoutputmessagesa-propagateoutputmessages"></a><a name="propagate_output_messages"></a>propagate_output_messages 

 将消息传播到目标。  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="a-namepropagatetoanytargetsa-propagatetoanytargets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 当在派生类中重写时将传播到任何或所有链接的目标将给定的消息。 这是消息块的主传播例程。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向要传播的消息的指针。  
  
##  <a name="a-namereleasea-release"></a><a name="release"></a>版本 

 释放以前的成功消息保留。  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的保留`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`release`方法。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
 该方法将引发[bad_target](bad-target-class.md)异常如果参数`_PTarget`不表示调用目标`reserve`。  
  
##  <a name="a-namereleasemessagea-releasemessage"></a><a name="release_message"></a>release_message 

 当在派生类中重写时释放以前的消息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
##  <a name="a-namereleaserefa-releaseref"></a><a name="release_ref"></a>release_ref 

 释放此引用计数`source_block`对象。  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向调用此方法的目标块的指针。  
  
### <a name="remarks"></a>备注  
 此方法由`ITarget`从此源要取消链接的对象。 源块允许释放任何资源为目标块保留。  
  
##  <a name="a-nameremovetargetsa-removetargets"></a><a name="remove_targets"></a>remove_targets 

 移除此源块的所有目标链接。 这应从析构函数调用。  
  
```
void remove_targets();
```  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>保留 

 保留以前提供的这一条消息`source_block`对象。  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
 `_PTarget`  
 正在调用的目标块的指针`reserve`方法。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。 保留可能因为众多原因失败，包括：消息已保留或已由另一目标接受，源可能拒绝保留等。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
 在您调用之后`reserve`，如果成功，必须调用`consume`或`release`才能执行或分别放弃的消息的所有权。  
  
##  <a name="a-namereservemessagea-reservemessage"></a><a name="reserve_message"></a>reserve_message 

 当在派生类中重写时保留以前提供的这一条消息`source_block`对象。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象所保留。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 之后`reserve`调用时，如果它返回`true`、 任一`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="a-nameresumepropagationa-resumepropagation"></a><a name="resume_propagation"></a>resume_propagation 

 当在派生类中重写，请在释放了保留后恢复传播。  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="a-namectora-sourceblock"></a><a name="ctor"></a>source_block 

 构造 `source_block` 对象。  
  
```
source_block();
```  
  
##  <a name="a-namedtora-sourceblock"></a><a name="dtor"></a>~ source_block 

 销毁`source_block`对象。  
  
```
virtual ~source_block();
```  
  
##  <a name="a-namesyncsenda-syncsend"></a><a name="sync_send"></a>sync_send 

 同步消息进行排队和启动传播任务，如果这有没有已完成操作。  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>参数  
 `_Msg`  
 一个指向`message`对象来同步发送。  
  
##  <a name="a-nameunlinktargeta-unlinktarget"></a><a name="unlink_target"></a>unlink_target 

 取消链接目标块与该`source_block`对象。  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 一个指向`ITarget`块取消与此链接`source_block`对象。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。  
  
##  <a name="a-nameunlinktargetnotificationa-unlinktargetnotification"></a><a name="unlink_target_notification"></a>unlink_target_notification 

 通知目标已被从此未链接的回调`source_block`对象。  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 `ITarget`被取消链接。  
  
##  <a name="a-nameunlinktargetsa-unlinktargets"></a><a name="unlink_targets"></a>unlink_targets 

 断开所有目标块与该都链接`source_block`对象。  
  
```
virtual void unlink_targets();
```  
  
##  <a name="a-namewaitforoutstandingasyncsendsa-waitforoutstandingasyncsends"></a><a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends 

 等待所有异步传播完成。 此传播器特定数值调节钮等待消息块的析构函数中使用，以确保所有异步传播有时间完成，然后再销毁块。  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ISource 类](isource-class.md)

