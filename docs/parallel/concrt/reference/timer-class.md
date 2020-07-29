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
ms.openlocfilehash: 026aef03bb813585decb206c1691835330a4dd05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224937"
---
# <a name="timer-class"></a>timer 类

`timer` 消息块是单目标的 `source_block`，能够在经过指定的时间段后或在特定时间间隔向其目标发送消息。

## <a name="syntax"></a>语法

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>参数

*T*<br/>
此块的输出消息的负载类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[记](#ctor)|已重载。 构造一个 `timer` 消息块，它将在指定的时间间隔后激发给定的消息。|
|[~ 计时器析构函数](#dtor)|销毁 `timer` 消息块。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[pause](#pause)|停止 `timer` 消息块。 如果它是重复 `timer` 消息块，则可以通过后续调用重新启动它 `start()` 。 对于非重复计时器，这与调用的效果相同 `stop` 。|
|[start](#start)|启动 `timer` 消息块。 调用此后指定的毫秒数后，指定的值将作为向后传播 `message` 。|
|[stop](#stop)|停止 `timer` 消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此消息块提供的消息 `timer` ，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由提供 `timer` 并由目标保留的消息，将所有权转移到调用方。|
|[link_target_notification](#link_target_notification)|通知新目标已链接到此 `timer` 消息块的回调。|
|[propagate_to_any_targets](#propagate_to_any_targets)|尝试向 `timer` 所有链接目标提供块生成的消息。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此消息块先前提供的消息 `timer` 。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此消息块提供的消息 `timer` ，并将所有权转移到调用方。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

使用之前由提供 `timer` 并由目标保留的消息，将所有权转移到调用方。

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 所使用的对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

类似于 `accept` ，但后面始终是对的调用 `reserve` 。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

通知新目标已链接到此 `timer` 消息块的回调。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="pause"></a><a name="pause"></a>播放

停止 `timer` 消息块。 如果它是重复 `timer` 消息块，则可以通过后续调用重新启动它 `start()` 。 对于非重复计时器，这与调用的效果相同 `stop` 。

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

尝试向 `timer` 所有链接目标提供块生成的消息。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 要释放的对象的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此消息块先前提供的消息 `timer` 。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 保留的对象的。

### <a name="return-value"></a>返回值

**`true`** 如果消息已成功保留，则 **`false`** 为; 否则为。

### <a name="remarks"></a>备注

`reserve`调用后，如果它返回 **`true`** ，则 `consume` 或 `release` 必须调用以获取或释放消息的所有权。

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

释放保留后恢复传播。

```cpp
virtual void resume_propagation();
```

## <a name="start"></a><a name="start"></a>start

启动 `timer` 消息块。 调用此后指定的毫秒数后，指定的值将作为向后传播 `message` 。

```cpp
void start();
```

## <a name="stop"></a><a name="stop"></a>stop

停止 `timer` 消息块。

```cpp
void stop();
```

## <a name="timer"></a><a name="ctor"></a>记

构造一个 `timer` 消息块，它将在指定的时间间隔后激发给定的消息。

```cpp
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
在调用开始后，要向下游传播指定的消息所需的毫秒数。

*value*<br/>
在计时器过期时将传播到下游的值。

*_PTarget*<br/>
计时器将消息传播到的目标。

*_Repeating*<br/>
如果为 true，则指示计时器将每毫秒定期触发一次 `_Ms` 。

*_Scheduler*<br/>
计划 `Scheduler` 消息块的传播任务的对象 `timer` 。

*_ScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `timer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_Scheduler` 或 `_ScheduleGroup` 函数，运行时将使用默认的计划程序。

## <a name="timer"></a><a name="dtor"></a>~ 计时器

销毁 `timer` 消息块。

```cpp
~timer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
