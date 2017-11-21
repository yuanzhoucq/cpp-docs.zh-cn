---
title: "timer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs: C++
helpviewer_keywords: timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9a7771afe4a93c6c4dafcd090276202732d1ad8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
 此块的输出消息负载类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[计时器](#ctor)|已重载。 构造`timer`将在指定时间间隔后激发给定的消息的消息块。|  
|[~ timer 析构函数](#dtor)|销毁`timer`消息块。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[暂停](#pause)|停止`timer`消息块。 如果它是一个重复`timer`消息块，它可以重新启动通过后续`start()`调用。 对于非重复计时器，这具有相同的效果`stop`调用。|  
|[start](#start)|启动`timer`消息块。 指定的此之后的毫秒数被调用时，指定的值将传播下游作为`message`。|  
|[停止](#stop)|停止`timer`消息块。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[accept_message](#accept_message)|接受一条消息，已提供此`timer`消息块，将所有权转让给调用方。|  
|[consume_message](#consume_message)|使用以前提供的消息`timer`并由目标，将所有权转让给调用方保留。|  
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`timer`消息块。|  
|[propagate_to_any_targets](#propagate_to_any_targets)|尝试通过生成的消息提供`timer`到所有的链接目标的块。|  
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|  
|[reserve_message](#reserve_message)|保留以前提供的这一条消息`timer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|  
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [ISource](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="accept_message"></a>accept_message 

 接受一条消息，已提供此`timer`消息块，将所有权转让给调用方。  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的提供`message`对象。  
  
### <a name="return-value"></a>返回值  
 指向的指针`message`对象调用方现在具有的所有权。  
  
##  <a name="consume_message"></a>consume_message 

 使用以前提供的消息`timer`并由目标，将所有权转让给调用方保留。  
  
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
  
##  <a name="link_target_notification"></a>link_target_notification 

 通知新的目标已链接到此回调`timer`消息块。  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 指向新链接的目标的指针。  
  
##  <a name="pause"></a>暂停 

 停止`timer`消息块。 如果它是一个重复`timer`消息块，它可以重新启动通过后续`start()`调用。 对于非重复计时器，这具有相同的效果`stop`调用。  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 尝试通过生成的消息提供`timer`到所有的链接目标的块。  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```  
  
##  <a name="release_message"></a>release_message 

 释放以前的消息保留。  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被释放。  
  
##  <a name="reserve_message"></a>reserve_message 

 保留以前提供的这一条消息`timer`消息块。  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>参数  
 `_MsgId`  
 `runtime_object_identity`的`message`对象被保留。  
  
### <a name="return-value"></a>返回值  
 `true`如果消息已成功保留，`false`否则为。  
  
### <a name="remarks"></a>备注  
 后`reserve`调用时，如果它返回`true`，`consume`或`release`必须调用来获取或释放消息的所有权。  
  
##  <a name="resume_propagation"></a>resume_propagation 

 释放保留后恢复传播。  
  
```
virtual void resume_propagation();
```  
  
##  <a name="start"></a>启动 

 启动`timer`消息块。 指定的此之后的毫秒数被调用时，指定的值将传播下游作为`message`。  
  
```
void start();
```  
  
##  <a name="stop"></a>停止 

 停止`timer`消息块。  
  
```
void stop();
```  
  
##  <a name="ctor"></a>计时器 

 构造`timer`将在指定时间间隔后激发给定的消息的消息块。  
  
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
 若要启动指定的消息，下游传播的调用后必须等待的毫秒数。  
  
 `value`  
 一个值，此计时器已过期时下游传播。  
  
 `_PTarget`  
 计时器将将其消息传播到目标。  
  
 `_Repeating`  
 如果为 true，指示计时器将触发定期每个`_Ms`毫秒。  
  
 `_Scheduler`  
 `Scheduler`对象在其中的传播任务`timer`计划消息块计划。  
  
 `_ScheduleGroup`  
 `ScheduleGroup`对象在其中的传播任务`timer`计划消息块。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定，运行时将使用默认计划程序`_Scheduler`或`_ScheduleGroup`参数。  
  
##  <a name="dtor"></a>~ 计时器 

 销毁`timer`消息块。  
  
```
~timer();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)
