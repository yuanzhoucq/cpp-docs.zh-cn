---
title: source_block 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866129"
---
# <a name="source_block-class"></a>source_block 类

`source_block` 是仅限于源的块的抽象基类。 该类提供基本链接管理功能和常见错误检查。

## <a name="syntax"></a>语法

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>参数

*_TargetLinkRegistry*<br/>
将用于保存目标链接的注册表链接到。

*_MessageProcessorType*<br/>
用于消息处理的处理器类型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`target_iterator`|用于遍历连接的目标的迭代器。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[source_block](#ctor)|构造 `source_block` 对象。|
|[~ source_block 析构函数](#dtor)|销毁 `source_block` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[接受](#accept)|接受此 `source_block` 对象提供的消息，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|获取此 `source_block` 对象上的引用计数，以防止删除。|
|[使用](#consume)|使用以前由此 `source_block` 对象提供的消息，并通过目标成功保留该消息，并将所有权转移到调用方。|
|[link_target](#link_target)|将目标块链接到此 `source_block` 对象。|
|[release](#release)|释放以前成功的消息保留。|
|[release_ref](#release_ref)|释放此 `source_block` 对象上的引用计数。|
|[reserve](#reserve)|保留此 `source_block` 对象先前提供的消息。|
|[unlink_target](#unlink_target)|将目标块与此 `source_block` 对象断开。|
|[unlink_targets](#unlink_targets)|将所有目标块与此 `source_block` 对象断开。 （重写[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[accept_message](#accept_message)|当在派生类中重写时，根据源接受提供的消息。 消息块应重写此方法以验证 `_MsgId` 并返回一条消息。|
|[async_send](#async_send)|异步对消息进行排队并启动传播任务（如果尚未执行此操作）|
|[consume_message](#consume_message)|当在派生类中重写时，将使用之前保留的消息。|
|[enable_batched_processing](#enable_batched_processing)|启用该块的批处理。|
|[initialize_source](#initialize_source)|初始化此 `source_block`中的 `message_propagator`。|
|[link_target_notification](#link_target_notification)|通知新目标已链接到此 `source_block` 对象的回调。|
|[process_input_messages](#process_input_messages)|处理输入消息。 这只适用于从源块派生的传播器块。|
|[propagate_output_messages](#propagate_output_messages)|将消息传播到目标。|
|[propagate_to_any_targets](#propagate_to_any_targets)|当在派生类中重写时，将给定的消息传播到任何或所有链接目标。 这是消息块的主要传播例程。|
|[release_message](#release_message)|当在派生类中重写时，释放以前的消息保留。|
|[remove_targets](#remove_targets)|删除此源块的所有目标链接。 这应从析构函数调用。|
|[reserve_message](#reserve_message)|当在派生类中重写时，保留此 `source_block` 对象先前提供的消息。|
|[resume_propagation](#resume_propagation)|当在派生类中重写时，在释放保留后恢复传播。|
|[sync_send](#sync_send)|如果尚未执行此操作，请以同步方式对消息进行排队并启动传播任务。|
|[unlink_target_notification](#unlink_target_notification)|一个回调，通知目标已从此 `source_block` 对象取消链接。|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|等待所有异步传播完成。 此特定于传播程序的自旋 wait 用于消息块的析构函数中，以确保所有异步传播在销毁块之前都有时间完成。|

## <a name="remarks"></a>备注

消息块应从此块派生，以利用此类提供的链接管理和同步。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a>接受

接受此 `source_block` 对象提供的消息，并将所有权转移到调用方。

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `accept` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

在此 `ISource` 块提供消息时，目标调用 `accept` 方法。 如果此源决定创建消息的副本，则返回的消息指针可能与传入 `ITarget` 块 `propagate` 方法的消息指针不同。

## <a name="accept_message"></a>accept_message

当在派生类中重写时，根据源接受提供的消息。 消息块应重写此方法以验证 `_MsgId` 并返回一条消息。

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`message` 对象的运行时对象标识。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

### <a name="remarks"></a>备注

若要转移所有权，应返回原始消息指针。 若要保持所有权，需要发出并返回消息负载的副本。

## <a name="acquire_ref"></a>acquire_ref

获取此 `source_block` 对象上的引用计数，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>备注

此方法由在 `link_target` 方法中链接到此源的 `ITarget` 对象调用。

## <a name="async_send"></a>async_send

异步对消息进行排队并启动传播任务（如果尚未执行此操作）

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
指向要异步发送的 `message` 对象的指针。

## <a name="consume"></a>接受

使用以前由此 `source_block` 对象提供的消息，并通过目标成功保留该消息，并将所有权转移到调用方。

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `consume` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

如果参数 `_PTarget` 不表示调用 `reserve`的目标，则该方法引发[bad_target](bad-target-class.md)异常。

`consume` 方法类似于 `accept`，但必须始终调用返回**true**的 `reserve`。

## <a name="consume_message"></a>consume_message

当在派生类中重写时，将使用之前保留的消息。

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
所使用的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

### <a name="remarks"></a>备注

与 `accept`类似，但前面总是调用 `reserve`。

## <a name="enable_batched_processing"></a>enable_batched_processing

启用该块的批处理。

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

初始化此 `source_block`中的 `message_propagator`。

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>参数

*_PScheduler*<br/>
用于计划任务的计划程序。

*_PScheduleGroup*<br/>
用于计划任务的计划组。

## <a name="link_target"></a>link_target

将目标块链接到此 `source_block` 对象。

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向链接到此 `source_block` 对象的 `ITarget` 块的指针。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

## <a name="link_target_notification"></a>link_target_notification

通知新目标已链接到此 `source_block` 对象的回调。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

处理输入消息。 这只适用于从源块派生的传播器块。

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

## <a name="propagate_output_messages"></a>propagate_output_messages

将消息传播到目标。

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

当在派生类中重写时，将给定的消息传播到任何或所有链接目标。 这是消息块的主要传播例程。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要传播的消息的指针。

## <a name="release"></a>拆卸

释放以前成功的消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `release` 方法的目标块的指针。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

如果参数 `_PTarget` 不表示调用 `reserve`的目标，则该方法引发[bad_target](bad-target-class.md)异常。

## <a name="release_message"></a>release_message

当在派生类中重写时，释放以前的消息保留。

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

## <a name="release_ref"></a>release_ref

释放此 `source_block` 对象上的引用计数。

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由正在从此源取消链接的 `ITarget` 对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="remove_targets"></a>remove_targets

删除此源块的所有目标链接。 这应从析构函数调用。

```cpp
void remove_targets();
```

## <a name="reserve"></a>保留

保留此 `source_block` 对象先前提供的消息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `reserve` 方法的目标块的指针。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

调用 `reserve`后，如果成功，则必须调用 `consume` 或 `release` 以便分别获取或放弃该消息。

## <a name="reserve_message"></a>reserve_message

当在派生类中重写时，保留此 `source_block` 对象先前提供的消息。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留的 `message` 对象的 `runtime_object_identity`。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。

### <a name="remarks"></a>备注

调用 `reserve` 后，如果返回**true**，则必须调用 `consume` 或 `release`，才能获取或释放消息的所有权。

## <a name="resume_propagation"></a>resume_propagation

当在派生类中重写时，在释放保留后恢复传播。

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

构造 `source_block` 对象。

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

销毁 `source_block` 的对象。

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

如果尚未执行此操作，请以同步方式对消息进行排队并启动传播任务。

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
指向要同步发送的 `message` 对象的指针。

## <a name="unlink_target"></a>unlink_target

将目标块与此 `source_block` 对象断开。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向要从此 `source_block` 对象断开链接的 `ITarget` 块的指针。

### <a name="remarks"></a>备注

如果参数 `_PTarget` `NULL`，则该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

## <a name="unlink_target_notification"></a>unlink_target_notification

一个回调，通知目标已从此 `source_block` 对象取消链接。

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
已取消链接的 `ITarget` 块。

## <a name="unlink_targets"></a>unlink_targets

将所有目标块与此 `source_block` 对象断开。

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

等待所有异步传播完成。 此特定于传播程序的自旋 wait 用于消息块的析构函数中，以确保所有异步传播在销毁块之前都有时间完成。

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISource 类](isource-class.md)
