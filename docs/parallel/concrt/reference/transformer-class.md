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
ms.openlocfilehash: adc83ab2d8268460b3a35be44f5733c8b6fa1c43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217891"
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

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[转换器](#ctor)|已重载。 构造 `transformer` 消息块。|
|[~ 转换器析构函数](#dtor)|销毁 `transformer` 消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受此消息块提供的消息 `transformer` ，并将所有权转移到调用方。|
|[consume_message](#consume_message)|使用之前由提供 `transformer` 并由目标保留的消息，将所有权转移到调用方。|
|[link_target_notification](#link_target_notification)|通知新目标已链接到此 `transformer` 消息块的回调。|
|[propagate_message](#propagate_message)|将消息从块异步传递 `ISource` 到此 `transformer` 消息块。 此 `propagate` 方法由源块调用时由方法调用。|
|[propagate_to_any_targets](#propagate_to_any_targets)|执行输入消息中的转换器函数。|
|[release_message](#release_message)|释放以前的消息保留。 （重写[source_block：： release_message](source-block-class.md#release_message)。）|
|[reserve_message](#reserve_message)|保留此消息块先前提供的消息 `transformer` 。 （重写[source_block：： reserve_message](source-block-class.md#reserve_message)。）|
|[resume_propagation](#resume_propagation)|释放保留后恢复传播。 （重写[source_block：： resume_propagation](source-block-class.md#resume_propagation)。）|
|[send_message](#send_message)|将消息从块同步传递 `ISource` 到此 `transformer` 消息块。 此 `send` 方法由源块调用时由方法调用。|
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

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

接受此消息块提供的消息 `transformer` ，并将所有权转移到调用方。

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

使用之前由提供 `transformer` 并由目标保留的消息，将所有权转移到调用方。

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 所使用的对象的。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

类似于 `accept` ，但后面始终是对的调用 `reserve` 。

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

通知新目标已链接到此 `transformer` 消息块的回调。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

将消息从块异步传递 `ISource` 到此 `transformer` 消息块。 此 `propagate` 方法由源块调用时由方法调用。

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

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

执行输入消息中的转换器函数。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

保留此消息块先前提供的消息 `transformer` 。

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

将消息从块同步传递 `ISource` 到此 `transformer` 消息块。 此 `send` 方法由源块调用时由方法调用。

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

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**`true`** 因为块不会推迟所提供的消息。

## <a name="transformer"></a><a name="ctor"></a>转换器

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

该类型 `_Transform_method` 是具有签名的函子， `_Output (_Input const &)` 此 `transformer` 消息块调用此消息块来处理消息。

该类型 `filter_method` 是具有签名的函子， `bool (_Input const &)` 此消息块调用此方法 `transformer` 来确定它是否应接受提供的消息。

## <a name="transformer"></a><a name="dtor"></a>~ 转换器

销毁 `transformer` 消息块。

```cpp
~transformer();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[call 类](call-class.md)
