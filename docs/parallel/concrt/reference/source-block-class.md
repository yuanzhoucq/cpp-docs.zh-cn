---
title: source_block 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f5b84020d9428066bdadfff53500d671233f07d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386716"
---
# <a name="sourceblock-class"></a>source_block 类

`source_block` 是仅限于源的块的抽象基类。 该类提供基本链接管理功能和常见错误检查。

## <a name="syntax"></a>语法

```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

#### <a name="parameters"></a>参数

*_TargetLinkRegistry*<br/>
若要用来存放目标链接的链接注册表。

*_MessageProcessorType*<br/>
消息处理的处理器类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`target_iterator`|要向已连接的目标的迭代器。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[source_block](#ctor)|构造 `source_block` 对象。|
|[~ source_block 析构函数](#dtor)|销毁`source_block`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[accept](#accept)|接受提供的这一条消息`source_block`对象，将所有权传递给调用方。|
|[acquire_ref](#acquire_ref)|获取对此的引用计数`source_block`对象，以防止删除。|
|[consume](#consume)|使用以前由此消息`source_block`对象，并成功由目标，将所有权传递给调用方保留。|
|[link_target](#link_target)|目标块链接到此`source_block`对象。|
|[release](#release)|释放上一个成功的消息保留。|
|[release_ref](#release_ref)|释放对此的引用计数`source_block`对象。|
|[reserve](#reserve)|保留以前由此一条消息`source_block`对象。|
|[unlink_target](#unlink_target)|取消链接此目标块`source_block`对象。|
|[unlink_targets](#unlink_targets)|取消链接所有目标块与该`source_block`对象。 (重写[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[accept_message](#accept_message)|当在派生类中重写，接受由源提供的消息。 消息块应重写此方法可以验证`_MsgId`并返回一条消息。|
|[async_send](#async_send)|异步消息排队和启动传播任务，如果这不已完成|
|[consume_message](#consume_message)|当在派生类中重写，使用先前保留的消息。|
|[enable_batched_processing](#enable_batched_processing)|启用该块的批处理。|
|[initialize_source](#initialize_source)|初始化`message_propagator`在此`source_block`。|
|[link_target_notification](#link_target_notification)|通知新的目标已链接到此回调`source_block`对象。|
|[process_input_messages](#process_input_messages)|处理输入消息。 这只适用于从源块派生的传播器块。|
|[propagate_output_messages](#propagate_output_messages)|将消息传播到目标。|
|[propagate_to_any_targets](#propagate_to_any_targets)|当在派生类中重写，将传播到链接的目标的任意或全部给定的消息。 这是消息块的主要传播例程。|
|[release_message](#release_message)|当在派生类中重写时释放以前的消息保留。|
|[remove_targets](#remove_targets)|删除此源块的所有目标链接。 这应从析构函数调用。|
|[reserve_message](#reserve_message)|当在派生类中重写时保留消息以前由此`source_block`对象。|
|[resume_propagation](#resume_propagation)|当在派生类中重写时保留已释放之后继续传播。|
|[sync_send](#sync_send)|同步消息进行排队，并启动传播任务，如果这不已完成。|
|[unlink_target_notification](#unlink_target_notification)|通知已取消此目标的回调`source_block`对象。|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|等待所有异常传播完成。 此传播器特定于旋转等待消息块的析构函数中使用，以确保所有异步传播有时间完成，然后再销毁块。|

## <a name="remarks"></a>备注

消息块应派生自此块，以便充分利用链接管理和同步此类提供。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="accept"></a> 接受

接受提供的这一条消息`source_block`对象，将所有权传递给调用方。

```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`accept`方法。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

`accept`由此提供一条消息时，目标调用方法`ISource`块。 消息指针返回可能不同于传递到`propagate`方法的`ITarget`阻止，如果此源决定发出消息的副本。

##  <a name="accept_message"></a> accept_message

当在派生类中重写，接受由源提供的消息。 消息块应重写此方法可以验证`_MsgId`并返回一条消息。

```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
运行时对象标识的`message`对象。

### <a name="return-value"></a>返回值

指向调用方现在具有的所有权的消息的指针。

### <a name="remarks"></a>备注

若要转让所有权，应返回原始消息指针。 若要保留所有权，需要进行，并返回消息负载的副本。

##  <a name="acquire_ref"></a> acquire_ref

获取对此的引用计数`source_block`对象，以防止删除。

```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>备注

调用此方法`ITarget`对象，它被链接到此源期间`link_target`方法。

##  <a name="async_send"></a> async_send

异步消息排队和启动传播任务，如果这不已完成

```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
一个指向`message`以异步方式发送的对象。

##  <a name="consume"></a> 使用

使用以前由此消息`source_block`对象，并成功由目标，将所有权传递给调用方保留。

```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的保留`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`consume`方法。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

该方法将引发[bad_target](bad-target-class.md)异常如果参数`_PTarget`不表示调用目标`reserve`。

`consume`方法是类似于`accept`，但始终必须通过调用带`reserve`返回`true`。

##  <a name="consume_message"></a> consume_message

当在派生类中重写，使用先前保留的消息。

```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象已使用。

### <a name="return-value"></a>返回值

指向调用方现在具有的所有权的消息的指针。

### <a name="remarks"></a>备注

类似于`accept`，但通过调用前面始终有`reserve`。

##  <a name="enable_batched_processing"></a> enable_batched_processing

启用该块的批处理。

```
void enable_batched_processing();
```

##  <a name="initialize_source"></a> initialize_source

初始化`message_propagator`在此`source_block`。

```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>参数

*_PScheduler*<br/>
要用于计划任务计划程序。

*_PScheduleGroup*<br/>
要用于计划任务的计划组。

##  <a name="link_target"></a> link_target

目标块链接到此`source_block`对象。

```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
一个指向`ITarget`块要链接到此`source_block`对象。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

##  <a name="link_target_notification"></a> link_target_notification

通知新的目标已链接到此回调`source_block`对象。

```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

##  <a name="process_input_messages"></a> process_input_messages

处理输入消息。 这只适用于从源块派生的传播器块。

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

##  <a name="propagate_output_messages"></a> propagate_output_messages

将消息传播到目标。

```
virtual void propagate_output_messages();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

当在派生类中重写，将传播到链接的目标的任意或全部给定的消息。 这是消息块的主要传播例程。

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要传播消息的指针。

##  <a name="release"></a> 版本

释放上一个成功的消息保留。

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的保留`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`release`方法。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

该方法将引发[bad_target](bad-target-class.md)异常如果参数`_PTarget`不表示调用目标`reserve`。

##  <a name="release_message"></a> release_message

当在派生类中重写时释放以前的消息保留。

```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

##  <a name="release_ref"></a> release_ref

释放对此的引用计数`source_block`对象。

```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向调用此方法的目标块的指针。

### <a name="remarks"></a>备注

调用此方法`ITarget`从此源取消链接的对象。 源块允许释放任何资源保留目标块的。

##  <a name="remove_targets"></a> remove_targets

删除此源块的所有目标链接。 这应从析构函数调用。

```
void remove_targets();
```

##  <a name="reserve"></a> 保留

保留以前由此一条消息`source_block`对象。

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`reserve`方法。

### <a name="return-value"></a>返回值

`true` 如果消息已成功保留，`false`否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

调用后`reserve`，如果成功，必须调用`consume`或`release`为了采用或分别放弃的消息的所有权。

##  <a name="reserve_message"></a> reserve_message

当在派生类中重写时保留消息以前由此`source_block`对象。

```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象所保留。

### <a name="return-value"></a>返回值

`true` 如果消息已成功保留，`false`否则为。

### <a name="remarks"></a>备注

之后`reserve`调用时，如果它将返回`true`、 任一`consume`或`release`必须调用以获取或释放消息的所有权。

##  <a name="resume_propagation"></a> resume_propagation

当在派生类中重写时保留已释放之后继续传播。

```
virtual void resume_propagation() = 0;
```

##  <a name="ctor"></a> source_block

构造 `source_block` 对象。

```
source_block();
```

##  <a name="dtor"></a> ~ source_block

销毁`source_block`对象。

```
virtual ~source_block();
```

##  <a name="sync_send"></a> sync_send

同步消息进行排队，并启动传播任务，如果这不已完成。

```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
一个指向`message`以同步方式发送的对象。

##  <a name="unlink_target"></a> unlink_target

取消链接此目标块`source_block`对象。

```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
一个指向`ITarget`块来取消链接此`source_block`对象。

### <a name="remarks"></a>备注

该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果参数`_PTarget`是`NULL`。

##  <a name="unlink_target_notification"></a> unlink_target_notification

通知已取消此目标的回调`source_block`对象。

```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
`ITarget`已取消链接的块。

##  <a name="unlink_targets"></a> unlink_targets

取消链接所有目标块与该`source_block`对象。

```
virtual void unlink_targets();
```

##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends

等待所有异常传播完成。 此传播器特定于旋转等待消息块的析构函数中使用，以确保所有异步传播有时间完成，然后再销毁块。

```
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISource 类](isource-class.md)
