---
title: "join 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::join
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
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
ms.openlocfilehash: b9671e6c9d29fb5f93977fe080e90dd087429460
ms.lasthandoff: 02/24/2017

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
 消息的负载类型的联接和传播块。  
  
 `_Jtype`  
 类型的`join`块，此元素，也`greedy`或`non_greedy`  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[加入构造函数](#ctor)|已重载。 构造`join`消息块。|  
|[~ join 析构函数](#dtor)|销毁`join`块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[accept_message 方法](#accept_message)|接受提供的这一条消息`join`将所有权转移给调用方的消息块。|  
|[consume_message 方法](#consume_message)|使用以前提供的消息`join`消息块并由该目标，将所有权转移给调用方保留。|  
|[link_target_notification 方法](#link_target_notification)|回调，以通知新的目标已链接到此`join`消息块。|  
|[propagate_message 方法](#propagate_message)|以异步方式从将消息传递`ISource`至此块`join`消息块。 由调用`propagate`方法时由源块调用。|  
|[propagate_to_any_targets 方法](#propagate_to_any_targets)|构造输出消息时均传播一条消息将包含来自每个源的输入的消息。 将此输出消息发送到其每个目标。|  
|[release_message 方法](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message 方法](#reserve_message)|保留以前提供的这一条消息`join`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation 方法](#resume_propagation)|在释放了保留后，请恢复传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
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
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 接受提供的这一条消息`join`将所有权转移给调用方的消息块。  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 使用以前提供的消息`join`消息块并由该目标，将所有权转移给调用方保留。  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象正在使用。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 类似于`accept`，但通过调用前面始终`reserve`。  
  
##  <a name="a-namectora-join"></a><a name="ctor"></a>联接 

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
 `Scheduler`对象在其中的传播任务`join`消息块计划。  
  
 `_PScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`join`消息块计划。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。  
  
 类型`filter_method`是具有签名的伪函数`bool (T const &)`其调用此`join`消息块，以确定它是否应接受提供的消息。  
  
##  <a name="a-namedtora-join"></a><a name="dtor"></a>~ 联接 

 销毁`join`块。  
  
```
~join();
```  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 回调，以通知新的目标已链接到此`join`消息块。  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 以异步方式从将消息传递`ISource`至此块`join`消息块。 由调用`propagate`方法时由源块调用。  
  
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
 一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。  
  
##  <a name="a-namepropagatetoanytargetsa-propagatetoanytargets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 构造输出消息时均传播一条消息将包含来自每个源的输入的消息。 将此输出消息发送到其每个目标。  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="a-namereleasemessagea-releasemessage"></a><a name="release_message"></a>release_message 

 释放以前的消息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
##  <a name="a-namereservemessagea-reservemessage"></a><a name="reserve_message"></a>reserve_message 

 保留以前提供的这一条消息`join`消息块。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 之后`reserve`调用时，如果它返回`true`、 任一`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="a-nameresumepropagationa-resumepropagation"></a><a name="resume_propagation"></a>resume_propagation 

 在释放了保留后，请恢复传播。  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [choice 类](choice-class.md)   
 [multitype_join 类](multitype-join-class.md)

