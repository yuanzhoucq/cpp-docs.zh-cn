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
ms.openlocfilehash: c39afc565a7ec775600b9c9fb6f15a89acdef57b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142531"
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

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[记](#ctor)|已重载。 构造一个 `timer` 消息块，它将在指定的时间间隔后激发给定的消息。|
|[~ 计时器析构函数](#dtor)|销毁 `timer` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[播放](#pause)|停止 `timer` 消息块。 如果它是重复的 `timer` 消息块，则可以使用后续的 `start()` 调用来重新启动它。 对于非重复计时器，这与 `stop` 调用的效果相同。|
|[start](#start)|启动 `timer` 消息块。 调用此后指定的毫秒数后，指定的值将作为 `message`传播到下游。|
|[stop](#stop)|停止 `timer` 消息块。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `timer` 消息块提供的消息，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由 `timer` 提供的消息，并由目标保留，将所有权转移给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `timer` 消息块。|
|[propagate_to_any_targets](#propagate_to_any_targets)|尝试将 `timer` 块生成的消息提供给所有链接目标。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `timer` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
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

## <a name="accept_message"></a>accept_message

接受此 `timer` 消息块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

## <a name="consume_message"></a>consume_message

使用之前由 `timer` 提供的消息，并由目标保留，将所有权转移给调用方。

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
所使用的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

与 `accept`类似，但前面总是调用 `reserve`。

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `timer` 消息块。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="pause"></a>播放

停止 `timer` 消息块。 如果它是重复的 `timer` 消息块，则可以使用后续的 `start()` 调用来重新启动它。 对于非重复计时器，这与 `stop` 调用的效果相同。

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

尝试将 `timer` 块生成的消息提供给所有链接目标。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

## <a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `timer` 消息块之前提供的消息。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。

### <a name="remarks"></a>备注

调用 `reserve` 后，如果返回**true**，则必须调用 `consume` 或 `release`，才能获取或释放消息的所有权。

## <a name="resume_propagation"></a>resume_propagation

释放保留后恢复传播。

```cpp
virtual void resume_propagation();
```

## <a name="start"></a>start

启动 `timer` 消息块。 调用此后指定的毫秒数后，指定的值将作为 `message`传播到下游。

```cpp
void start();
```

## <a name="stop"></a>stop

停止 `timer` 消息块。

```cpp
void stop();
```

## <a name="ctor"></a>记

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
如果为 true，则指示计时器将每隔 `_Ms` 毫秒定期触发一次。

*_Scheduler*<br/>
计划 `timer` 消息块的传播任务的 `Scheduler` 对象。

*_ScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `timer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_Scheduler` 或 `_ScheduleGroup` 函数，运行时将使用默认的计划程序。

## <a name="dtor"></a>~ 计时器

销毁 `timer` 消息块。

```cpp
~timer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
