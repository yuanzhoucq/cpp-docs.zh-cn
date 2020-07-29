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
ms.openlocfilehash: e02fa1ffbf4c3e2c7d17dfe2d6ae66758945d9de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219513"
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

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unbounded_buffer](#ctor)|已重载。 构造 `unbounded_buffer` 消息块。|
|[~ unbounded_buffer 析构函数](#dtor)|销毁 `unbounded_buffer` 消息块。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[去除](#dequeue)|从消息块中删除一项 `unbounded_buffer` 。|
|[排队](#enqueue)|向消息块添加一个项 `unbounded_buffer` 。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此消息块提供的消息 `unbounded_buffer` ，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用消息块先前提供的消息 `unbounded_buffer` 并由目标保留，将所有权转移给调用方。|
|[link_target_notification](#link_target_notification)|通知新目标已链接到此 `unbounded_buffer` 消息块的回调。|
|[process_input_messages](#process_input_messages)|将放置 `message` `_PMessage` 在此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。|
|[propagate_message](#propagate_message)|将消息从块异步传递 `ISource` 到此 `unbounded_buffer` 消息块。 此 `propagate` 方法由源块调用时由方法调用。|
|[propagate_output_messages](#propagate_output_messages)|将放置 `message` `_PMessage` 在此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。 （重写[source_block：:p ropagate_output_messages](source-block-class.md#propagate_output_messages)。）|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此消息块先前提供的消息 `unbounded_buffer` 。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从块同步传递 `ISource` 到此 `unbounded_buffer` 消息块。 此 `send` 方法由源块调用时由方法调用。|
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

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此消息块提供的消息 `unbounded_buffer` ，并将所有权转移到调用方。

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

使用消息块先前提供的消息 `unbounded_buffer` 并由目标保留，将所有权转移给调用方。

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 所使用的对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

类似于 `accept` ，但后面始终是对的调用 `reserve` 。

## <a name="dequeue"></a><a name="dequeue"></a>去除

从消息块中删除一项 `unbounded_buffer` 。

```cpp
_Type dequeue();
```

### <a name="return-value"></a>返回值

从中移除的消息的负载 `unbounded_buffer` 。

## <a name="enqueue"></a><a name="enqueue"></a>排队

向消息块添加一个项 `unbounded_buffer` 。

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>参数

*_Item*<br/>
要添加的项。

### <a name="return-value"></a>返回值

**`true`** 如果此项已被接受，则 **`false`** 为; 否则为。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

通知新目标已链接到此 `unbounded_buffer` 消息块的回调。

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

将消息从块异步传递 `ISource` 到此 `unbounded_buffer` 消息块。 此 `propagate` 方法由源块调用时由方法调用。

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

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

将放置 `message` `_PMessage` 在此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>备注

如果中的另一条消息已在中，则在 `unbounded_buffer` 接受或使用以前的消息之前，将不会发生传播到链接目标。 成功的第一个链接目标 `accept` 或 `consume` 消息取得所有权，而其他目标则无法获取该消息。

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

将放置 `message` `_PMessage` 在此 `unbounded_buffer` 消息块中，并尝试将其提供给所有链接目标。

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

## <a name="release_message"></a><a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 要释放的对象的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此消息块先前提供的消息 `unbounded_buffer` 。

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

## <a name="send_message"></a><a name="send_message"></a>send_message

将消息从块同步传递 `ISource` 到此 `unbounded_buffer` 消息块。 此 `send` 方法由源块调用时由方法调用。

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

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**`true`** 因为块不会推迟所提供的消息。

## <a name="unbounded_buffer"></a><a name="ctor"></a>unbounded_buffer

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

该类型 `filter_method` 是具有签名的函子， `bool (_Type const &)` 此消息块调用此方法 `unbounded_buffer` 来确定它是否应接受提供的消息。

## <a name="unbounded_buffer"></a><a name="dtor"></a>~ unbounded_buffer

销毁 `unbounded_buffer` 消息块。

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[single_assignment 类](single-assignment-class.md)
