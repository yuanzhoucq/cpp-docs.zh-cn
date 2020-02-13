---
title: unbounded_buffer 类
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142338"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer 类

`unbounded_buffer` 消息块是多目标、多源、有序的 `propagator_block`，能够存储不限数量的消息。

## <a name="syntax"></a>语法

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>参数

*_Type*<br/>
缓冲区存储和传播的消息的负载类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[unbounded_buffer](#ctor)|已重载。 构造 `unbounded_buffer` 消息块。|
|[~ unbounded_buffer 析构函数](#dtor)|销毁 `unbounded_buffer` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[去除](#dequeue)|删除 `unbounded_buffer` 消息块中的项。|
|[排队](#enqueue)|将一个项添加到 `unbounded_buffer` 消息块。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `unbounded_buffer` 消息块提供的消息，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由 `unbounded_buffer` 消息块提供并由目标保留的消息，将所有权转移给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `unbounded_buffer` 消息块。|
|[process_input_messages](#process_input_messages)|将 `message` `_PMessage` 置于此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。|
|[propagate_message](#propagate_message)|将消息从 `ISource` 块异步传递到此 `unbounded_buffer` 消息块。 它由源块调用时由 `propagate` 方法调用。|
|[propagate_output_messages](#propagate_output_messages)|将 `message` `_PMessage` 置于此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。 （重写[source_block：:p ropagate_output_messages](source-block-class.md#propagate_output_messages)。）|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `unbounded_buffer` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从 `ISource` 块同步传递到此 `unbounded_buffer` 消息块。 它由源块调用时由 `send` 方法调用。|
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 （重写[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

有关详细信息，请参阅[异步消息块](../asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept_message"></a>accept_message

接受此 `unbounded_buffer` 消息块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

## <a name="consume_message"></a>consume_message

使用之前由 `unbounded_buffer` 消息块提供并由目标保留的消息，将所有权转移给调用方。

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
所使用的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

与 `accept`类似，但前面总是调用 `reserve`。

## <a name="dequeue"></a>去除

删除 `unbounded_buffer` 消息块中的项。

```cpp
_Type dequeue();
```

### <a name="return-value"></a>返回值

从 `unbounded_buffer`中移除的消息的有效负载。

## <a name="enqueue"></a>排队

将一个项添加到 `unbounded_buffer` 消息块。

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>参数

*_Item*<br/>
要添加的项。

### <a name="return-value"></a>返回值

如果接受该项，**则为 true** ; 否则为**false** 。

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `unbounded_buffer` 消息块。

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="propagate_message"></a>propagate_message

将消息从 `ISource` 块异步传递到此 `unbounded_buffer` 消息块。 它由源块调用时由 `propagate` 方法调用。

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md#message_status)指示目标决定对消息执行的操作。

## <a name="propagate_output_messages"></a>propagate_output_messages

将 `message` `_PMessage` 置于此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>备注

如果在 `unbounded_buffer`中，另一条消息已在此消息之前，将不会发生传播到已接受或使用之前的消息。 成功 `accept` 或 `consume` 消息的第一个链接目标取得所有权，而其他目标则无法获取该消息。

## <a name="process_input_messages"></a>process_input_messages

将 `message` `_PMessage` 置于此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

## <a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `unbounded_buffer` 消息块之前提供的消息。

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

## <a name="send_message"></a>send_message

将消息从 `ISource` 块同步传递到此 `unbounded_buffer` 消息块。 它由源块调用时由 `send` 方法调用。

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md#message_status)指示目标决定对消息执行的操作。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**true** ，因为块不会推迟所提供的消息。

## <a name="ctor"></a>unbounded_buffer

构造 `unbounded_buffer` 消息块。

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>参数

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `unbounded_buffer` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `unbounded_buffer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型 `filter_method` 是具有签名 `bool (_Type const &)` 的函子，此 `unbounded_buffer` 消息块调用此方法来确定它是否应接受提供的消息。

## <a name="dtor"></a>~ unbounded_buffer

销毁 `unbounded_buffer` 消息块。

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[single_assignment 类](single-assignment-class.md)
