---
title: single_assignment 类
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 6b92508c81311774816e804eb36ac8fbfb2aa82b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219555"
---
# <a name="single_assignment-class"></a>single_assignment 类

`single_assignment` 消息块是多目标、多源、有序的 `propagator_block`，能够存储单个一次写入的 `message`。

## <a name="syntax"></a>语法

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>参数

*T*<br/>
缓冲区存储和传播的消息的负载类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[single_assignment](#ctor)|已重载。 构造 `single_assignment` 消息块。|
|[~ single_assignment 析构函数](#dtor)|销毁 `single_assignment` 消息块。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[has_value](#has_value)|检查是否已 `single_assignment` 使用值初始化此消息块。|
|[value](#value)|获取对消息块中所存储消息的当前有效负载的引用 `single_assignment` 。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此消息块提供的消息 `single_assignment` ，并将该消息的副本返回给调用方。|
|[consume_message](#consume_message)|使用之前由提供的消息 `single_assignment` ，并由目标保留，将消息的副本返回给调用方。|
|[link_target_notification](#link_target_notification)|通知新目标已链接到此 `single_assignment` 消息块的回调。|
|[propagate_message](#propagate_message)|将消息从块异步传递 `ISource` 到此 `single_assignment` 消息块。 此 `propagate` 方法由源块调用时由方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|将放置 `message _PMessage` 在此 `single_assignment` 消息块中，并将其提供给所有链接目标。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此消息块先前提供的消息 `single_assignment` 。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从块同步传递 `ISource` 到此 `single_assignment` 消息块。 此 `send` 方法由源块调用时由方法调用。|

## <a name="remarks"></a>备注

`single_assignment`消息块将其消息的副本传播到每个目标。

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此消息块提供的消息 `single_assignment` ，并将该消息的副本返回给调用方。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

`single_assignment`消息块将消息的副本返回到其目标，而不是转移当前保存的消息的所有权。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

使用之前由提供的消息 `single_assignment` ，并由目标保留，将消息的副本返回给调用方。

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

## <a name="has_value"></a><a name="has_value"></a>has_value

检查是否已 `single_assignment` 使用值初始化此消息块。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果块接收了值，则 **`false`** 为; 否则为。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

通知新目标已链接到此 `single_assignment` 消息块的回调。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

将消息从块异步传递 `ISource` 到此 `single_assignment` 消息块。 此 `propagate` 方法由源块调用时由方法调用。

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

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

将放置 `message` `_PMessage` 在此 `single_assignment` 消息块中，并将其提供给所有链接目标。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
一个指向的指针 `message` ，该 `single_assignment` 消息块已获取的所有权。

## <a name="release_message"></a><a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 要释放的对象的。

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

保留此消息块先前提供的消息 `single_assignment` 。

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

## <a name="send_message"></a><a name="send_message"></a>send_message

将消息从块同步传递 `ISource` 到此 `single_assignment` 消息块。 此 `send` 方法由源块调用时由方法调用。

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

## <a name="single_assignment"></a><a name="ctor"></a>single_assignment

构造 `single_assignment` 消息块。

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>参数

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `single_assignment` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `single_assignment` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

该类型 `filter_method` 是具有签名的函子， `bool (T const &)` 此消息块调用此方法 `single_assignment` 来确定它是否应接受提供的消息。

## <a name="single_assignment"></a><a name="dtor"></a>~ single_assignment

销毁 `single_assignment` 消息块。

```cpp
~single_assignment();
```

## <a name="value"></a><a name="value"></a> 值

获取对消息块中所存储消息的当前有效负载的引用 `single_assignment` 。

```cpp
T const& value();
```

### <a name="return-value"></a>返回值

存储消息的负载。

### <a name="remarks"></a>备注

如果消息块中当前未存储消息，此方法将等待消息到达 `single_assignment` 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[unbounded_buffer 类](unbounded-buffer-class.md)
