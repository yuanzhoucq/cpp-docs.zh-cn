---
title: timer 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: e36441f53c9b53c9826ee92b2892142a522d7243
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180116"
---
# <a name="timer-class"></a>timer 类

`timer` 消息块是单目标的 `source_block`，能够在经过指定的时间段后或在特定时间间隔向其目标发送消息。

## <a name="syntax"></a>语法

```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

#### <a name="parameters"></a>参数

*T*<br/>
此块的输出消息的负载类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[timer](#ctor)|已重载。 构造`timer`将指定的时间间隔后触发给定的消息的消息块。|
|[~ timer 析构函数](#dtor)|销毁`timer`消息块。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[pause](#pause)|停止`timer`消息块。 如果它是一个重复`timer`消息传递块，它可以重新启动具有后续`start()`调用。 对于非重复的计时器，这具有相同的效果`stop`调用。|
|[start](#start)|启动`timer`消息块。 指定超过此范围的毫秒数被调用时，将传播指定的值为下游`message`。|
|[stop](#stop)|停止`timer`消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受提供的这一条消息`timer`消息块，将所有权传递给调用方。|
|[consume_message](#consume_message)|使用以前提供的一条消息`timer`和目标，将所有权传递给调用方保留。|
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`timer`消息块。|
|[propagate_to_any_targets](#propagate_to_any_targets)|尝试提供生成的消息`timer`到所有链接的目标块。|
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留以前由此一条消息`timer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|将在保留已发布后继续传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="accept_message"></a> accept_message

接受提供的这一条消息`timer`消息块，将所有权传递给调用方。

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

##  <a name="consume_message"></a> consume_message

使用以前提供的一条消息`timer`和目标，将所有权传递给调用方保留。

```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象已使用。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

类似于`accept`，但通过调用前面始终有`reserve`。

##  <a name="link_target_notification"></a> link_target_notification

通知新的目标已链接到此回调`timer`消息块。

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

##  <a name="pause"></a> 暂停

停止`timer`消息块。 如果它是一个重复`timer`消息传递块，它可以重新启动具有后续`start()`调用。 对于非重复的计时器，这具有相同的效果`stop`调用。

```
void pause();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

尝试提供生成的消息`timer`到所有链接的目标块。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

##  <a name="release_message"></a> release_message

释放以前的消息保留。

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

##  <a name="reserve_message"></a> reserve_message

保留以前由此一条消息`timer`消息块。

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象所保留。

### <a name="return-value"></a>返回值

**true**成功保留该消息，如果**false**否则为。

### <a name="remarks"></a>备注

之后`reserve`调用时，如果它将返回**true**，而是`consume`或`release`必须调用以获取或释放消息的所有权。

##  <a name="resume_propagation"></a> resume_propagation

将在保留已发布后继续传播。

```
virtual void resume_propagation();
```

##  <a name="start"></a> 启动

启动`timer`消息块。 指定超过此范围的毫秒数被调用时，将传播指定的值为下游`message`。

```
void start();
```

##  <a name="stop"></a> stop

停止`timer`消息块。

```
void stop();
```

##  <a name="ctor"></a> 计时器

构造`timer`将指定的时间间隔后触发给定的消息的消息块。

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

*_Ms*<br/>
必须启动指定的消息传播下游的调用后经过的毫秒数。

*值*<br/>
一个值，该值将下游传播，当计时器已过期。

*_PTarget*<br/>
计时器将将其消息传播到目标。

*_Repeating*<br/>
如果为 true，指示该计时器将定期触发每个`_Ms`毫秒为单位。

*_Scheduler*<br/>
`Scheduler`对象在其中的传播任务的`timer`计划消息块计划。

*_ScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `timer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_Scheduler` 或 `_ScheduleGroup` 函数，运行时将使用默认的计划程序。

##  <a name="dtor"></a> ~timer

销毁`timer`消息块。

```
~timer();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
