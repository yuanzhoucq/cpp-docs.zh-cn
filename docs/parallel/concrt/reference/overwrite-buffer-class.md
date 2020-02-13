---
title: overwrite_buffer 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 5b222170112f43ae9700054f42e1368545612d00
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138791"
---
# <a name="overwrite_buffer-class"></a>overwrite_buffer 类

`overwrite_buffer` 消息块是多目标、多源、有序的 `propagator_block`，一次能够存储一条消息。 新消息覆盖之前保存的消息。

## <a name="syntax"></a>语法

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>参数

*T*<br/>
缓冲区存储和传播的消息的负载类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[overwrite_buffer](#ctor)|已重载。 构造 `overwrite_buffer` 消息块。|
|[~ overwrite_buffer 析构函数](#dtor)|销毁 `overwrite_buffer` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[has_value](#has_value)|检查此 `overwrite_buffer` 消息块是否还具有值。|
|[value](#value)|获取对 `overwrite_buffer` 消息块中所存储消息的当前有效负载的引用。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `overwrite_buffer` 消息块提供的消息，并将消息的副本返回到调用方。|
|[consume_message](#consume_message)|使用之前由 `overwrite_buffer` 消息块提供的消息并由目标保留，并将消息的副本返回给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `overwrite_buffer` 消息块。|
|[propagate_message](#propagate_message)|将消息从 `ISource` 块异步传递到此 `overwrite_buffer` 消息块。 它由源块调用时由 `propagate` 方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|将 `message _PMessage` 放置在此 `overwrite_buffer` 消息块中，并将其提供给所有链接目标。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `overwrite_buffer` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从 `ISource` 块同步传递到此 `overwrite_buffer` 消息块。 它由源块调用时由 `send` 方法调用。|
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 （重写[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

## <a name="remarks"></a>备注

`overwrite_buffer` 消息块会将其存储消息的副本传播到其每个目标。

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

## <a name="accept_message"></a>accept_message

接受此 `overwrite_buffer` 消息块提供的消息，并将消息的副本返回到调用方。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

`overwrite_buffer` 消息块将消息的副本返回到其目标，而不是转让当前保存的消息的所有权。

## <a name="consume_message"></a>consume_message

使用之前由 `overwrite_buffer` 消息块提供的消息并由目标保留，并将消息的副本返回给调用方。

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

## <a name="has_value"></a>has_value

检查此 `overwrite_buffer` 消息块是否还具有值。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>返回值

如果块接收到值，**则为 true** ; 否则为**false** 。

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `overwrite_buffer` 消息块。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="dtor"></a>~ overwrite_buffer

销毁 `overwrite_buffer` 消息块。

```cpp
~overwrite_buffer();
```

## <a name="ctor"></a>overwrite_buffer

构造 `overwrite_buffer` 消息块。

```cpp
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

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `overwrite_buffer` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `overwrite_buffer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型 `filter_method` 是具有签名 `bool (T const &)` 的函子，此 `overwrite_buffer` 消息块调用此方法来确定它是否应接受提供的消息。

## <a name="propagate_message"></a>propagate_message

将消息从 `ISource` 块异步传递到此 `overwrite_buffer` 消息块。 它由源块调用时由 `propagate` 方法调用。

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

将 `message _PMessage` 放置在此 `overwrite_buffer` 消息块中，并将其提供给所有链接目标。

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向此 `overwrite_buffer` 已取得所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

此方法用新接受的消息 `_PMessage`覆盖 `overwrite_buffer` 中的当前消息。

## <a name="send_message"></a>send_message

将消息从 `ISource` 块同步传递到此 `overwrite_buffer` 消息块。 它由源块调用时由 `send` 方法调用。

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**true** ，因为块不会推迟所提供的消息。

## <a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `overwrite_buffer` 消息块之前提供的消息。

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

## <a name="value"></a>负值

获取对 `overwrite_buffer` 消息块中所存储消息的当前有效负载的引用。

```cpp
T value();
```

### <a name="return-value"></a>返回值

当前存储的消息的负载。

### <a name="remarks"></a>备注

此方法返回后，存储在 `overwrite_buffer` 中的值可能会立即更改。 如果 `overwrite_buffer`中当前没有消息存储，则此方法将等待消息到达。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[unbounded_buffer 类](unbounded-buffer-class.md)<br/>
[single_assignment 类](single-assignment-class.md)
