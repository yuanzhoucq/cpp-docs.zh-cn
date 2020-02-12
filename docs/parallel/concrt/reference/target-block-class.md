---
title: target_block 类
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: 4009133161133a99aeb0ee040f0c82fdbabecaa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142642"
---
# <a name="target_block-class"></a>target_block 类

`target_block` 类是抽象基类，它提供基本链接管理功能和针对仅限于目标的块的错误检查。

## <a name="syntax"></a>语法

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>参数

*_SourceLinkRegistry*<br/>
用于保存源链接的链接注册表。

*_MessageProcessorType*<br/>
用于消息处理的处理器类型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`source_iterator`|此 `target_block` 对象的 `source_link_manager` 的迭代器的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[target_block](#ctor)|构造 `target_block` 对象。|
|[~ target_block 析构函数](#dtor)|销毁 `target_block` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[传](#propagate)|将消息从源块异步传递到此目标块。|
|[发送](#send)|将消息从源块同步传递到此目标块。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[async_send](#async_send)|异步发送消息以进行处理。|
|[decline_incoming_messages](#decline_incoming_messages)|向块指示应拒绝新消息。|
|[enable_batched_processing](#enable_batched_processing)|启用该块的批处理。|
|[initialize_target](#initialize_target)|初始化基对象。 具体来说，需要对 `message_processor` 对象进行初始化。|
|[link_source](#link_source)|将指定的源块链接到此 `target_block` 对象。|
|[process_input_messages](#process_input_messages)|处理作为输入接收的消息。|
|[process_message](#process_message)|在派生类中重写时，处理由该 `target_block` 对象接受的消息。|
|[propagate_message](#propagate_message)|当在派生类中重写时，此方法将消息从 `ISource` 块异步传递到此 `target_block` 对象。 它由源块调用时由 `propagate` 方法调用。|
|[register_filter](#register_filter)|注册将对收到的每条消息调用的筛选器方法。|
|[remove_sources](#remove_sources)|等待未完成的异步发送操作完成后，断开所有源。|
|[send_message](#send_message)|当在派生类中重写时，此方法将消息从 `ISource` 块同步传递到此 `target_block` 对象。 它由源块调用时由 `send` 方法调用。|
|[sync_send](#sync_send)|同步发送消息以进行处理。|
|[unlink_source](#unlink_source)|从此 `target_block` 对象取消指定的源块。|
|[unlink_sources](#unlink_sources)|将所有源块与此 `target_block` 对象断开。 （重写[ITarget：： unlink_sources](itarget-class.md#unlink_sources)。）|
|[wait_for_async_sends](#wait_for_async_sends)|等待所有异步传播完成。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="async_send"></a>async_send

异步发送消息以进行处理。

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向正在发送的消息的指针。

## <a name="decline_incoming_messages"></a>decline_incoming_messages

向块指示应拒绝新消息。

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>备注

此方法由析构函数调用，以确保在析构正在进行时，新消息被拒绝。

## <a name="enable_batched_processing"></a>enable_batched_processing

启用该块的批处理。

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a>initialize_target

初始化基对象。 具体来说，需要对 `message_processor` 对象进行初始化。

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>参数

*_PScheduler*<br/>
用于计划任务的计划程序。

*_PScheduleGroup*<br/>
用于计划任务的计划组。

## <a name="link_source"></a>link_source

将指定的源块链接到此 `target_block` 对象。

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>参数

*_PSource*<br/>
指向要链接的 `ISource` 块的指针。

### <a name="remarks"></a>备注

不应直接对 `target_block` 对象调用此函数。 应使用 `ISource` 块上的 `link_target` 方法将块连接在一起，这将调用相应目标上的 `link_source` 方法。

## <a name="process_input_messages"></a>process_input_messages

处理作为输入接收的消息。

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向要处理的消息的指针。

## <a name="process_message"></a>process_message

在派生类中重写时，处理由该 `target_block` 对象接受的消息。

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a>传

将消息从源块异步传递到此目标块。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

### <a name="remarks"></a>备注

如果 `NULL``_PMessage` 或 `_PSource` 参数，该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

## <a name="propagate_message"></a>propagate_message

当在派生类中重写时，此方法将消息从 `ISource` 块异步传递到此 `target_block` 对象。 它由源块调用时由 `propagate` 方法调用。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

## <a name="register_filter"></a>register_filter

注册将对收到的每条消息调用的筛选器方法。

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>参数

*_Filter*<br/>
筛选器方法。

## <a name="remove_sources"></a>remove_sources

等待未完成的异步发送操作完成后，断开所有源。

```cpp
void remove_sources();
```

### <a name="remarks"></a>备注

所有目标块都应调用此例程，以删除其析构函数中的源。

## <a name="send"></a>发送

将消息从源块同步传递到此目标块。

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

### <a name="remarks"></a>备注

如果 `NULL``_PMessage` 或 `_PSource` 参数，该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

使用消息启动之外的 `send` 方法，在网络内传播消息是危险的，可能会导致死锁。

当 `send` 返回时，消息已被接受，并传输到目标块中，或者被目标拒绝。

## <a name="send_message"></a>send_message

当在派生类中重写时，此方法将消息从 `ISource` 块同步传递到此 `target_block` 对象。 它由源块调用时由 `send` 方法调用。

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

### <a name="remarks"></a>备注

默认情况下，除非由派生类重写，否则此块将返回 `declined`。

## <a name="sync_send"></a>sync_send

同步发送消息以进行处理。

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向正在发送的消息的指针。

## <a name="ctor"></a>target_block

构造 `target_block` 对象。

```cpp
target_block();
```

## <a name="dtor"></a>~ target_block

销毁 `target_block` 的对象。

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a>unlink_source

从此 `target_block` 对象取消指定的源块。

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>参数

*_PSource*<br/>
指向要取消链接的 `ISource` 块的指针。

## <a name="unlink_sources"></a>unlink_sources

将所有源块与此 `target_block` 对象断开。

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a>wait_for_async_sends

等待所有异步传播完成。

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>备注

消息块析构函数使用此方法，以确保所有异步操作在销毁块之前都有时间完成。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ITarget 类](itarget-class.md)
