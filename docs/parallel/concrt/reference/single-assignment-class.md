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
ms.openlocfilehash: 5a27fb6cdc13fbbd3ceb8a85adacf5491ddc3ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593471"
---
# <a name="singleassignment-class"></a>single_assignment 类

`single_assignment` 消息块是多目标、多源、有序的 `propagator_block`，能够存储单个一次写入的 `message`。

## <a name="syntax"></a>语法

```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>参数

*T*<br/>
消息的负载类型存储和传播缓冲区。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[single_assignment](#ctor)|已重载。 构造 `single_assignment` 消息块。|
|[~ single_assignment 析构函数](#dtor)|销毁`single_assignment`消息块。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[has_value](#has_value)|检查是否这`single_assignment`消息块具有尚未初始化的值。|
|[value](#value)|获取对存储在消息的当前负载`single_assignment`消息块。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|接受提供的这一条消息`single_assignment`消息块，返回到调用方的消息的副本。|
|[consume_message](#consume_message)|使用以前提供的一条消息`single_assignment`和目标，该消息的副本返回给调用方保留。|
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`single_assignment`消息块。|
|[propagate_message](#propagate_message)|以异步方式从将消息传递`ISource`到此块`single_assignment`消息块。 由调用`propagate`方法，调用由源块时。|
|[propagate_to_any_targets](#propagate_to_any_targets)|位数`message _PMessage`在此`single_assignment`消息块和它提供给所有链接的目标。|
|[release_message](#release_message)|释放以前的消息保留。 (重写[source_block:: release_message](source-block-class.md#release_message)。)|
|[reserve_message](#reserve_message)|保留以前由此一条消息`single_assignment`消息块。 (重写[source_block:: reserve_message](source-block-class.md#reserve_message)。)|
|[resume_propagation](#resume_propagation)|将在保留已发布后继续传播。 (重写[source_block:: resume_propagation](source-block-class.md#resume_propagation)。)|
|[send_message](#send_message)|以同步方式从将消息传递`ISource`到此块`single_assignment`消息块。 由调用`send`方法，调用由源块时。|

## <a name="remarks"></a>备注

一个`single_assignment`消息块传播到每个目标其消息的副本。

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

##  <a name="accept_message"></a> accept_message

接受提供的这一条消息`single_assignment`消息块，返回到调用方的消息的副本。

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

`single_assignment`消息传送到其目标消息块返回副本，而不是将当前持有的消息的所有权。

##  <a name="consume_message"></a> consume_message

使用以前提供的一条消息`single_assignment`和目标，该消息的副本返回给调用方保留。

```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象已使用。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

类似于`accept`，但通过调用前面始终有`reserve`。

##  <a name="has_value"></a> has_value

检查是否这`single_assignment`消息块具有尚未初始化的值。

```
bool has_value() const;
```

### <a name="return-value"></a>返回值

**true**块已接收一个值，如果**false**否则为。

##  <a name="link_target_notification"></a> link_target_notification

通知新的目标已链接到此回调`single_assignment`消息块。

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向新链接的目标的指针。

##  <a name="propagate_message"></a> propagate_message

以异步方式从将消息传递`ISource`到此块`single_assignment`消息块。 由调用`propagate`方法，调用由源块时。

```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

位数`message``_PMessage`在此`single_assignment`消息块和它提供给所有链接的目标。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
一个指向`message`此`single_assignment`消息块已取得的所有权。

##  <a name="release_message"></a> release_message

释放以前的消息保留。

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

##  <a name="reserve_message"></a> reserve_message

保留以前由此一条消息`single_assignment`消息块。

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

以同步方式从将消息传递`ISource`到此块`single_assignment`消息块。 由调用`send`方法，调用由源块时。

```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向源块提供消息的指针。

### <a name="return-value"></a>返回值

一个[message_status](concurrency-namespace-enums.md)的目标决定如何处理该消息指示。

##  <a name="ctor"></a> single_assignment

构造 `single_assignment` 消息块。

```
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

*筛选 （_f)*<br/>
确定是否应接受提供的消息的筛选器函数。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `single_assignment` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `single_assignment` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

类型`filter_method`是具有签名的伪函数`bool (T const &)`调用此`single_assignment`消息块，以确定它是否应接受提供的消息。

##  <a name="dtor"></a> ~ single_assignment

销毁`single_assignment`消息块。

```
~single_assignment();
```

##  <a name="value"></a> 值

获取对存储在消息的当前负载`single_assignment`消息块。

```
T const& value();
```

### <a name="return-value"></a>返回值

存储消息的负载。

### <a name="remarks"></a>备注

此方法将等待消息到达时，如果没有消息当前存储在`single_assignment`消息块。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[overwrite_buffer 类](overwrite-buffer-class.md)<br/>
[unbounded_buffer 类](unbounded-buffer-class.md)

