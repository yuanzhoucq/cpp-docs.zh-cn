---
title: join 类
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139853"
---
# <a name="join-class"></a>join 类

`join` 消息块是单目标、多源、有序的 `propagator_block`，它可以合并来自其每个源的 `T` 类型消息。

## <a name="syntax"></a>语法

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>参数

*T*<br/>
块加入和传播的消息的负载类型。

*_Jtype*<br/>
`join` 块的类型为，`greedy` 或 `non_greedy`

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[join](#ctor)|已重载。 构造 `join` 消息块。|
|[~ join 析构函数](#dtor)|销毁 `join` 块。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `join` 消息块提供的消息，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由 `join` 消息块提供并由目标保留的消息，将所有权转移给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `join` 消息块。|
|[propagate_message](#propagate_message)|将消息从 `ISource` 块异步传递到此 `join` 消息块。 它由源块调用时由 `propagate` 方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|构造一个输出消息，其中包含来自每个源的输入消息。 向其每个目标发送输出消息。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `join` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept_message"></a>accept_message

接受此 `join` 消息块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

## <a name="consume_message"></a>consume_message

使用之前由 `join` 消息块提供并由目标保留的消息，将所有权转移给调用方。

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
所使用的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

与 `accept`类似，但前面总是调用 `reserve`。

## <a name="ctor"></a>收听

构造 `join` 消息块。

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>参数

*_NumInputs*<br/>
将允许此 `join` 块的输入数。

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `join` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `join` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型 `filter_method` 是具有签名 `bool (T const &)` 的函子，此 `join` 消息块调用此方法来确定它是否应接受提供的消息。

## <a name="dtor"></a>~ join

销毁 `join` 块。

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `join` 消息块。

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

将消息从 `ISource` 块异步传递到此 `join` 消息块。 它由源块调用时由 `propagate` 方法调用。

```cpp
message_status propagate_message(
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

构造一个输出消息，其中包含来自每个源的输入消息。 向其每个目标发送输出消息。

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

保留此 `join` 消息块之前提供的消息。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。

### <a name="remarks"></a>备注

调用 `reserve` 后，如果返回**true**，则必须调用 `consume` 或 `release`，才能获取或释放消息的所有权。

## <a name="resume_propagation"></a>resume_propagation

释放保留后恢复传播。

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[choice 类](choice-class.md)<br/>
[multitype_join 类](multitype-join-class.md)
