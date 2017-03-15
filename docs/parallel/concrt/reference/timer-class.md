---
title: "timer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::timer
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: 21
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
ms.openlocfilehash: 769ccd051c68f0a4d74511392f0f1a811e36e3e7
ms.lasthandoff: 02/24/2017

---
# <a name="timer-class"></a>timer 类
`timer` 消息块是单目标的 `source_block`，能够在经过指定的时间段后或在特定时间间隔向其目标发送消息。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 此块的输出消息的负载类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[计时器构造函数](#ctor)|已重载。 构造`timer`将在指定时间间隔后触发给定的消息的消息块。|  
|[~ timer 析构函数](#dtor)|销毁`timer`消息块。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[pause 方法](#pause)|停止`timer`消息块。 如果它是一个重复`timer`消息块，它可重新启动具有后续`start()`调用。 对于非重复的计时器，这有相同的效果`stop`调用。|  
|[start 方法](#start)|启动`timer`消息块。 指定的毫秒数后这被调用时，指定的值将传递作为下游`message`。|  
|[stop 方法](#stop)|停止`timer`消息块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept_message 方法](#accept_message)|接受提供的这一条消息`timer`将所有权转移给调用方的消息块。|  
|[consume_message 方法](#consume_message)|使用以前提供的消息`timer`并由该目标，将所有权转移给调用方保留。|  
|[link_target_notification 方法](#link_target_notification)|回调，以通知新的目标已链接到此`timer`消息块。|  
|[propagate_to_any_targets 方法](#propagate_to_any_targets)|尝试通过生成的消息提供`timer`到所有链接的目标块。|  
|[release_message 方法](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message 方法](#reserve_message)|保留以前提供的这一条消息`timer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation 方法](#resume_propagation)|在释放了保留后，请恢复传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 接受提供的这一条消息`timer`将所有权转移给调用方的消息块。  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 使用以前提供的消息`timer`并由该目标，将所有权转移给调用方保留。  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象正在使用。  
  
### <a name="return-value"></a>返回值  
 一个指向`message`对象时调用方现在具有的所有权。  
  
### <a name="remarks"></a>备注  
 类似于`accept`，但通过调用前面始终`reserve`。  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 回调，以通知新的目标已链接到此`timer`消息块。  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向新链接的目标的指针。  
  
##  <a name="a-namepausea-pause"></a><a name="pause"></a>暂停 

 停止`timer`消息块。 如果它是一个重复`timer`消息块，它可重新启动具有后续`start()`调用。 对于非重复的计时器，这有相同的效果`stop`调用。  
  
```
void pause();
```  
  
##  <a name="a-namepropagatetoanytargetsa-propagatetoanytargets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 尝试通过生成的消息提供`timer`到所有链接的目标块。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

 保留以前提供的这一条消息`timer`消息块。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象所保留。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 之后`reserve`调用时，如果它返回`true`、 任一`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="a-nameresumepropagationa-resumepropagation"></a><a name="resume_propagation"></a>resume_propagation 

 在释放了保留后，请恢复传播。  
  
```
virtual void resume_propagation();
```  
  
##  <a name="a-namestarta-start"></a><a name="start"></a>启动 

 启动`timer`消息块。 指定的毫秒数后这被调用时，指定的值将传递作为下游`message`。  
  
```
void start();
```  
  
##  <a name="a-namestopa-stop"></a><a name="stop"></a>停止 

 停止`timer`消息块。  
  
```
void stop();
```  
  
##  <a name="a-namectora-timer"></a><a name="ctor"></a>计时器 

 构造`timer`将在指定时间间隔后触发给定的消息的消息块。  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>参数  
 `_Ms`  
 后启动指定的消息来向下游传播的调用必须经过的毫秒数。  
  
 `value`  
 一个值，这将在计时器已过期时向下游传播。  
  
 `_PTarget`  
 计时器都将其消息传播到目标。  
  
 `_Repeating`  
 如果为 true，指示该计时器将定期触发每个`_Ms`毫秒为单位。  
  
 `_Scheduler`  
 `Scheduler`对象在其中的传播任务`timer`消息块计划安排。  
  
 `_ScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`timer`计划消息块。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定，则运行时将使用默认计划程序`_Scheduler`或`_ScheduleGroup`参数。  
  
##  <a name="a-namedtora-timer"></a><a name="dtor"></a>~ 计时器 

 销毁`timer`消息块。  
  
```
~timer();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

