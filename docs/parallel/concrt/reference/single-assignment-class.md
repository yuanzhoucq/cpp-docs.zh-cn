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
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142736"
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

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[single_assignment](#ctor)|已重载。 构造 `single_assignment` 消息块。|
|[~ single_assignment 析构函数](#dtor)|销毁 `single_assignment` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[has_value](#has_value)|检查是否已使用值对此 `single_assignment` 消息块进行了初始化。|
|[value](#value)|获取对 `single_assignment` 消息块中所存储消息的当前有效负载的引用。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `single_assignment` 消息块提供的消息，并将消息的副本返回到调用方。|
|[consume_message](#consume_message)|使用之前由 `single_assignment` 提供的消息，并由目标保留，将消息的副本返回给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `single_assignment` 消息块。|
|[propagate_message](#propagate_message)|将消息从 `ISource` 块异步传递到此 `single_assignment` 消息块。 它由源块调用时由 `propagate` 方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|将 `message _PMessage` 放置在此 `single_assignment` 消息块中，并将其提供给所有链接目标。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `single_assignment` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从 `ISource` 块同步传递到此 `single_assignment` 消息块。 它由源块调用时由 `send` 方法调用。|

## <a name="remarks"></a>备注

`single_assignment` 消息块会将其消息的副本传播到每个目标。

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

## <a name="accept_message"></a>accept_message

接受此 `single_assignment` 消息块提供的消息，并将消息的副本返回到调用方。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

`single_assignment` 消息块将消息的副本返回到其目标，而不是转让当前保存的消息的所有权。

## <a name="consume_message"></a>consume_message

使用之前由 `single_assignment` 提供的消息，并由目标保留，将消息的副本返回给调用方。

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

检查是否已使用值对此 `single_assignment` 消息块进行了初始化。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>返回值

如果块接收到值，**则为 true** ; 否则为**false** 。

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `single_assignment` 消息块。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

## <a name="propagate_message"></a>propagate_message

将消息从 `ISource` 块异步传递到此 `single_assignment` 消息块。 它由源块调用时由 `propagate` 方法调用。

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

将 `message` `_PMessage` 置于此 `single_assignment` 消息块中，并将其提供给所有链接目标。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向此 `single_assignment` 消息块已取得所有权的 `message` 的指针。

## <a name="release_message"></a>release_message

释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

保留此 `single_assignment` 消息块之前提供的消息。

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

## <a name="send_message"></a>send_message

将消息从 `ISource` 块同步传递到此 `single_assignment` 消息块。 它由源块调用时由 `send` 方法调用。

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

## <a name="ctor"></a>single_assignment

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

类型 `filter_method` 是具有签名 `bool (T const &)` 的函子，此 `single_assignment` 消息块调用此方法来确定它是否应接受提供的消息。

## <a name="dtor"></a>~ single_assignment

销毁 `single_assignment` 消息块。

```cpp
~single_assignment();
```

## <a name="value"></a>负值

获取对 `single_assignment` 消息块中所存储消息的当前有效负载的引用。

```cpp
T const& value();
```

### <a name="return-value"></a>返回值

存储消息的负载。

### <a name="remarks"></a>备注

如果 `single_assignment` 消息块中当前没有消息存储，则此方法将等待消息到达。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[unbounded_buffer 类](unbounded-buffer-class.md)
