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
ms.openlocfilehash: c07017539bc0125e9e8c27e208480a50ccc7a719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408058"
---
# <a name="transformer-class"></a>transformer 类

`transformer` 消息块是单目标、多源、有序的 `propagator_block`，它可以接受一个类型的消息，并能够存储不限数量的另一个类型的消息。

## <a name="syntax"></a>语法

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>参数

*_Input*<br/>
接受的缓冲区的消息的负载类型。

*_Output*<br/>
存储和传播缓冲区的消息的负载类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[transformer](#ctor)|已重载。 构造 `transformer` 消息块。|
|[~ transformer 析构函数](#dtor)|销毁`transformer`消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受提供的这一条消息`transformer`消息块，将所有权传递给调用方。|
|[consume_message](#consume_message)|使用以前提供的一条消息`transformer`和目标，将所有权传递给调用方保留。|
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`transformer`消息块。|
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`到此块`transformer`消息块。 由调用`propagate`方法，调用由源块时。|
|[propagate_to_any_targets](#propagate_to_any_targets)|执行输入消息中的转换器函数。|
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留以前由此一条消息`transformer`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|将在保留已发布后继续传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|
|[send_message](#send_message)|以同步方式从将消息传递`ISource`到此块`transformer`消息块。 由调用`send`方法，调用由源块时。|
|[supports_anonymous_source](#supports_anonymous_source)|重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。 (重写[itarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source)。)|

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

##  <a name="accept_message"></a> accept_message

接受提供的这一条消息`transformer`消息块，将所有权传递给调用方。

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

##  <a name="consume_message"></a> consume_message

使用以前提供的一条消息`transformer`和目标，将所有权传递给调用方保留。

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象已使用。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

类似于`accept`，但通过调用前面始终有`reserve`。

##  <a name="link_target_notification"></a> link_target_notification

通知新的目标已链接到此回调`transformer`消息块。

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

以异步方式从将消息传递`ISource`到此块`transformer`消息块。 由调用`propagate`方法，调用由源块时。

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

执行输入消息中的转换器函数。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

##  <a name="release_message"></a> release_message

释放以前的消息保留。

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

##  <a name="reserve_message"></a> reserve_message

保留以前由此一条消息`transformer`消息块。

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象所保留。

### <a name="return-value"></a>返回值

**true**成功保留该消息，如果**false**否则为。

### <a name="remarks"></a>备注

之后`reserve`调用时，如果它将返回**true**，而是`consume`或`release`必须调用以获取或释放消息的所有权。

##  <a name="resume_propagation"></a> resume_propagation

将在保留已发布后继续传播。

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

以同步方式从将消息传递`ISource`到此块`transformer`消息块。 由调用`send`方法，调用由源块时。

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

重写 `supports_anonymous_source` 方法，以指示该块可以接受由未链接的源为其提供的消息。

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**true**因为该块没有推迟提供的消息。

##  <a name="ctor"></a> 转换器

构造 `transformer` 消息块。

```
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
将为每个接受的消息调用一个函数。

*_PTarget*<br/>
指向要与转换器链接的目标块的指针。

*_Filter*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `transformer` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `transformer` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型`_Transform_method`是具有签名的伪函数`_Output (_Input const &)`调用此`transformer`消息块来处理消息。

类型`filter_method`是具有签名的伪函数`bool (_Input const &)`调用此`transformer`消息块，以确定它是否应接受提供的消息。

##  <a name="dtor"></a> ~transformer

销毁`transformer`消息块。

```
~transformer();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[call 类](call-class.md)
