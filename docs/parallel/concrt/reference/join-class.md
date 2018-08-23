---
title: join 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a37b6d3dce5d41578999aa54c8dff2dd2271fe9e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692634"
---
# <a name="join-class"></a>join 类
`join` 消息块是单目标、多源、有序的 `propagator_block`，它可以合并来自其每个源的 `T` 类型消息。  
  
## <a name="syntax"></a>语法  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>参数  
 `T`  
 消息的负载类型加入，并传播的块。  
  
 `_Jtype`  
 类型的`join`块，此元素，也`greedy`或 `non_greedy`  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[join](#ctor)|已重载。 构造`join`消息块。|  
|[~ join 析构函数](#dtor)|销毁`join`块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受一条消息，已提供此`join`消息块，将所有权转让给调用方。|  
|[consume_message](#consume_message)|使用以前提供的消息`join`消息块，并由目标，将所有权转让给调用方保留。|  
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`join`消息块。|  
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`至此块`join`消息块。 由调用`propagate`方法，调用由源块时。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|构造输出消息时它们已传播一条消息将包含来自每个源的输入的消息。 将此输出消息发送到其每个目标。|  
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|保留以前提供的这一条消息`join`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="accept_message"></a> accept_message 

 接受一条消息，已提供此`join`消息块，将所有权转让给调用方。  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
##  <a name="consume_message"></a> consume_message 

 使用以前提供的消息`join`消息块，并由目标，将所有权转让给调用方保留。  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象正在使用。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 类似于`accept`，但始终通过调用前面`reserve`。  
  
##  <a name="ctor"></a> 联接 

 构造`join`消息块。  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>参数  
 `_NumInputs`  
 数输入此`join`将允许块。  
  
 `_Filter`  
 确定是否应接受提供的消息的筛选器函数。  
  
 `_PScheduler`  
 `Scheduler`对象在其中的传播任务`join`计划消息块。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`join`计划消息块。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 类型`filter_method`是具有签名的涵子`bool (T const &)`其调用由此`join`消息块，以确定它是否应接受提供的消息。  
  
##  <a name="dtor"></a> ~ 联接 

 销毁`join`块。  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification 

 通知新的目标已链接到此回调`join`消息块。  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message 

 以异步方式从将消息传递`ISource`至此块`join`消息块。 由调用`propagate`方法，调用由源块时。  
  
```
message_status propagate_message(
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

 构造输出消息时它们已传播一条消息将包含来自每个源的输入的消息。 将此输出消息发送到其每个目标。  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a> release_message 

 释放以前的消息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
##  <a name="reserve_message"></a> reserve_message 

 保留以前提供的这一条消息`join`消息块。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 后`reserve`调用时，如果它返回`true`，`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="resume_propagation"></a> resume_propagation 

 释放保留后恢复传播。  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [choice 类](choice-class.md)   
 [multitype_join 类](multitype-join-class.md)
