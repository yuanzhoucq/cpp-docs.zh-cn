---
title: overwrite_buffer 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dccde651898bf5ff0986dc2e577a1d2ee5765e3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="overwritebuffer-class"></a>overwrite_buffer 类
`overwrite_buffer` 消息块是多目标、多源、有序的 `propagator_block`，一次能够存储一条消息。 新消息覆盖之前保存的消息。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 存储和传播的缓冲区的消息负载类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[overwrite_buffer](#ctor)|已重载。 构造`overwrite_buffer`消息块。|  
|[~ overwrite_buffer 析构函数](#dtor)|销毁`overwrite_buffer`消息块。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[has_value](#has_value)|检查是否这`overwrite_buffer`消息块尚未具有值。|  
|[value](#value)|获取存储在消息的当前负载的引用`overwrite_buffer`消息块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受一条消息，已提供此`overwrite_buffer`消息块，返回到调用方的消息的副本。|  
|[consume_message](#consume_message)|使用以前提供的消息`overwrite_buffer`消息块，并由目标，将消息的消息副本返还给调用方保留。|  
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`overwrite_buffer`消息块。|  
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`至此块`overwrite_buffer`消息块。 由调用`propagate`方法，调用由源块时。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|位置`message _PMessage`在此`overwrite_buffer`消息块和它提供给所有链接的目标。|  
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|保留以前提供的这一条消息`overwrite_buffer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
|[send_message](#send_message)|以同步方式从将消息传递`ISource`至此块`overwrite_buffer`消息块。 由调用`send`方法，调用由源块时。|  
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 (重写[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|  
  
## <a name="remarks"></a>备注  
 `overwrite_buffer`消息块传播到其每个目标其存储消息的副本。  
  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="accept_message"></a> accept_message 

 接受一条消息，已提供此`overwrite_buffer`消息块，返回到调用方的消息的副本。  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 `overwrite_buffer`消息传送到其目标，消息的块返回副本，而不是将当前持有的消息的所有权转让。  
  
##  <a name="consume_message"></a> consume_message 

 使用以前提供的消息`overwrite_buffer`消息块，并由目标，将消息的消息副本返还给调用方保留。  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象正在使用。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 类似于`accept`，但始终通过调用前面`reserve`。  
  
##  <a name="has_value"></a> has_value 

 检查是否这`overwrite_buffer`消息块尚未具有值。  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果块已接收一个值，`false`否则为。  
  
##  <a name="link_target_notification"></a> link_target_notification 

 通知新的目标已链接到此回调`overwrite_buffer`消息块。  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向新链接的目标的指针。  
  
##  <a name="dtor"></a> ~ overwrite_buffer 

 销毁`overwrite_buffer`消息块。  
  
```
~overwrite_buffer();
```  
  
##  <a name="ctor"></a> overwrite_buffer 

 构造`overwrite_buffer`消息块。  
  
```
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>参数  
 `_Filter`  
 确定是否应接受提供的消息的筛选器函数。  
  
 `_PScheduler`  
 `Scheduler`对象在其中的传播任务`overwrite_buffer`计划消息块。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`overwrite_buffer`计划消息块。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 类型`filter_method`是具有签名的涵子`bool (T const &)`其调用由此`overwrite_buffer`消息块，以确定它是否应接受提供的消息。  
  
##  <a name="propagate_message"></a> propagate_message 

 以异步方式从将消息传递`ISource`至此块`overwrite_buffer`消息块。 由调用`propagate`方法，调用由源块时。  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 位置`message _PMessage`在此`overwrite_buffer`消息块和它提供给所有链接的目标。  
  
```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向的指针`message`对象此`overwrite_buffer`取得了的所有权。  
  
### <a name="remarks"></a>备注  
 此方法会覆盖中的当前消息`overwrite_buffer`新接受的消息与`_PMessage`。  
  
##  <a name="send_message"></a> send_message 

 以同步方式从将消息传递`ISource`至此块`overwrite_buffer`消息块。 由调用`send`方法，调用由源块时。  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>参数  
 `_PMessage`  
 指向 `message` 对象的指针。  
  
 `_PSource`  
 指向提供消息的源块的指针。  
  
### <a name="return-value"></a>返回值  
 A [message_status](concurrency-namespace-enums.md)目标决定如何处理消息的指示。  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>返回值  
 `true` 因为该块没有推迟所提供的消息。  
  
##  <a name="release_message"></a> release_message 

 释放以前的消息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
##  <a name="reserve_message"></a> reserve_message 

 保留以前提供的这一条消息`overwrite_buffer`消息块。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被保留。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 后`reserve`调用时，如果它返回`true`，`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 释放保留后恢复传播。  
  
```
virtual void resume_propagation();
```  
  
##  <a name="value"></a> 值 

 获取存储在消息的当前负载的引用`overwrite_buffer`消息块。  
  
```
T value();
```  
  
### <a name="return-value"></a>返回值  
 当前存储的消息的负载。  
  
### <a name="remarks"></a>备注  
 中存储的值`overwrite_buffer`无法更改此方法返回后立即。 此方法将等待消息到达时，如果没有消息将当前存储在`overwrite_buffer`。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [unbounded_buffer 类](unbounded-buffer-class.md)   
 [single_assignment 类](single-assignment-class.md)
