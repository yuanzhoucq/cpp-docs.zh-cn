---
title: unbounded_buffer 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46789b74d0b7b8d882a1e2ea90103c4c2f1e934b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396338"
---
`unbounded_buffer` 消息块是多目标、多源、有序的 `propagator_block`，能够存储不限数量的消息。

## <a name="syntax"></a>语法

```
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

#### <a name="parameters"></a>参数

*类型 （_t)*<br/>
存储和传播被缓冲区的消息的负载类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unbounded_buffer](#ctor)|已重载。 构造`unbounded_buffer`消息块。|
|[~ unbounded_buffer 析构函数](#dtor)|销毁`unbounded_buffer`消息块。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[dequeue](#dequeue)|移除的项从`unbounded_buffer`消息块。|
|[enqueue](#enqueue)|将项添加到`unbounded_buffer`消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受提供的这一条消息`unbounded_buffer`消息块，将所有权传递给调用方。|
|[consume_message](#consume_message)|使用以前提供的一条消息`unbounded_buffer`消息块和目标，将所有权传递给调用方保留。|
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`unbounded_buffer`消息块。|
|[process_input_messages](#process_input_messages)|位数`message``_PMessage`在此`unbounded_buffer`消息块，尝试它提供给所有链接的目标。|
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`到此块`unbounded_buffer`消息块。 由调用`propagate`方法，调用由源块时。|
|[propagate_output_messages](#propagate_output_messages)|位数`message``_PMessage`在此`unbounded_buffer`消息块，尝试它提供给所有链接的目标。 (重写[source_block:: propagate_output_messages](source-block-class.md#propagate_output_messages)。)|
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留以前由此一条消息`unbounded_buffer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|将在保留已发布后继续传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|
|[send_message](#send_message)|以同步方式从将消息传递`ISource`到此块`unbounded_buffer`消息块。 由调用`send`方法，调用由源块时。|
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 (重写[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|

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

##  <a name="accept_message"></a> accept_message

接受提供的这一条消息`unbounded_buffer`消息块，将所有权传递给调用方。

```
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

##  <a name="consume_message"></a> consume_message

使用以前提供的一条消息`unbounded_buffer`消息块和目标，将所有权传递给调用方保留。

```
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象已使用。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

类似于`accept`，但通过调用前面始终有`reserve`。

##  <a name="dequeue"></a> 取消排队

移除的项从`unbounded_buffer`消息块。

```
_Type dequeue();
```

### <a name="return-value"></a>返回值

从删除消息的负载`unbounded_buffer`。

##  <a name="enqueue"></a> 排入队列

将项添加到`unbounded_buffer`消息块。

```
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>参数

*项目 （_i)*<br/>
要添加的项。

### <a name="return-value"></a>返回值

`true` 如果该项已被接受，`false`否则为。

##  <a name="link_target_notification"></a> link_target_notification

通知新的目标已链接到此回调`unbounded_buffer`消息块。

```
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

##  <a name="propagate_message"></a> propagate_message

以异步方式从将消息传递`ISource`到此块`unbounded_buffer`消息块。 由调用`propagate`方法，调用由源块时。

```
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md#message_status)的目标决定如何处理该消息指示。

##  <a name="propagate_output_messages"></a> propagate_output_messages

位数`message``_PMessage`在此`unbounded_buffer`消息块，尝试它提供给所有链接的目标。

```
virtual void propagate_output_messages();
```

### <a name="remarks"></a>备注

如果另一条消息已提前在这个`unbounded_buffer`，接受或使用了任何更早的消息之前，不会发生传播到链接的目标。 第一个已成功链接到目标`accept`或`consume`消息取得所有权，和任何其他目标，可以获取该消息。

##  <a name="process_input_messages"></a> process_input_messages

位数`message``_PMessage`在此`unbounded_buffer`消息块，尝试它提供给所有链接的目标。

```
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

##  <a name="release_message"></a> release_message

释放以前的消息保留。

```
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

##  <a name="reserve_message"></a> reserve_message

保留以前由此一条消息`unbounded_buffer`消息块。

```
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象所保留。

### <a name="return-value"></a>返回值

`true` 如果消息已成功保留，`false`否则为。

### <a name="remarks"></a>备注

之后`reserve`调用时，如果它将返回`true`、 任一`consume`或`release`必须调用以获取或释放消息的所有权。

##  <a name="resume_propagation"></a> resume_propagation

将在保留已发布后继续传播。

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

以同步方式从将消息传递`ISource`到此块`unbounded_buffer`消息块。 由调用`send`方法，调用由源块时。

```
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md#message_status)的目标决定如何处理该消息指示。

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

`true` 因为该块没有推迟所提供的消息。

##  <a name="ctor"></a> unbounded_buffer

构造`unbounded_buffer`消息块。

```
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

*筛选 （_f)*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
`Scheduler`对象在其中的传播任务的`unbounded_buffer`计划消息块。

*_PScheduleGroup*<br/>
`ScheduleGroup`对象在其中的传播任务的`unbounded_buffer`计划消息块。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型`filter_method`是具有签名的伪函数`bool (_Type const &)`调用此`unbounded_buffer`消息块，以确定它是否应接受提供的消息。

##  <a name="dtor"></a> ~ unbounded_buffer

销毁`unbounded_buffer`消息块。

```
~unbounded_buffer();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[single_assignment 类](single-assignment-class.md)

