---
title: transformer 类
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: 75c7697087b8b3ad8ff15ae4d08f2b4701aaa36a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142356"
---
# <a name="transformer-class"></a>transformer 类

`transformer` 消息块是单目标、多源、有序的 `propagator_block`，它可以接受一个类型的消息，并能够存储不限数量的另一个类型的消息。

## <a name="syntax"></a>语法

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>参数

*_Input*<br/>
缓冲区接受的消息的负载类型。

*_Output*<br/>
缓冲区存储和传播的消息的负载类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[转换器](#ctor)|已重载。 构造 `transformer` 消息块。|
|[~ 转换器析构函数](#dtor)|销毁 `transformer` 消息块。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|接受此 `transformer` 消息块提供的消息，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由 `transformer` 提供的消息，并由目标保留，将所有权转移给调用方。|
|[link_target_notification](#link_target_notification)|一个回调，通知新目标已链接到此 `transformer` 消息块。|
|[propagate_message](#propagate_message)|将消息从 `ISource` 块异步传递到此 `transformer` 消息块。 它由源块调用时由 `propagate` 方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|执行输入消息中的转换器函数。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此 `transformer` 消息块之前提供的消息。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从 `ISource` 块同步传递到此 `transformer` 消息块。 它由源块调用时由 `send` 方法调用。|
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 （重写[ITarget：： supports_anonymous_source](itarget-class.md#supports_anonymous_source)。）|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept_message"></a>accept_message

接受此 `transformer` 消息块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

## <a name="consume_message"></a>consume_message

使用之前由 `transformer` 提供的消息，并由目标保留，将所有权转移给调用方。

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
所使用的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

与 `accept`类似，但前面总是调用 `reserve`。

## <a name="link_target_notification"></a>link_target_notification

一个回调，通知新目标已链接到此 `transformer` 消息块。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a>propagate_message

将消息从 `ISource` 块异步传递到此 `transformer` 消息块。 它由源块调用时由 `propagate` 方法调用。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

执行输入消息中的转换器函数。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

保留此 `transformer` 消息块之前提供的消息。

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

将消息从 `ISource` 块同步传递到此 `transformer` 消息块。 它由源块调用时由 `send` 方法调用。

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
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

## <a name="ctor"></a>转换器

构造 `transformer` 消息块。

```cpp
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>参数

*_Func*<br/>
将为每个已接受的消息调用的函数。

*_PTarget*<br/>
指向链接的目标块的指针。

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `transformer` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `transformer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型 `_Transform_method` 是具有签名 `_Output (_Input const &)` 的函子，此 `transformer` 消息块调用此方法来处理消息。

类型 `filter_method` 是具有签名 `bool (_Input const &)` 的函子，此 `transformer` 消息块调用此方法来确定它是否应接受提供的消息。

## <a name="dtor"></a>~ 转换器

销毁 `transformer` 消息块。

```cpp
~transformer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[call 类](call-class.md)
