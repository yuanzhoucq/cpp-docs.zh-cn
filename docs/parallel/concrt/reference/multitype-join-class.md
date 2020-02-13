---
title: multitype_join 类
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138956"
---
# <a name="multitype_join-class"></a>multitype_join 类

`multitype_join` 消息块是多源、单目标的消息块，可以合并来自其每个源的不同类型的消息并向其目标提供合并的消息的元组。

## <a name="syntax"></a>语法

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>参数

*T*<br/>
块所联接和传播的消息 `tuple` 负载类型。

*_Jtype*<br/>
`join` 块的类型为，`greedy` 或 `non_greedy`

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[multitype_join](#ctor)|已重载。 构造 `multitype_join` 消息块。|
|[~ multitype_join 析构函数](#dtor)|销毁 `multitype_join` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[接受](#accept)|接受由此 `multitype_join` 块提供的消息，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|获取此 `multitype_join` 消息块上的引用计数，以防止删除。|
|[使用](#consume)|使用以前由 `multitype_join` 消息块提供的消息，并通过目标成功保留该消息，从而将所有权转移给调用方。|
|[link_target](#link_target)|将目标块链接到此 `multitype_join` 消息块。|
|[release](#release)|释放以前成功的消息保留。|
|[release_ref](#release_ref)|释放此 `multiple_join` 消息块上的引用计数。|
|[reserve](#reserve)|保留此 `multitype_join` 消息块之前提供的消息。|
|[unlink_target](#unlink_target)|将目标块与此 `multitype_join` 消息块断开。|
|[unlink_targets](#unlink_targets)|将此 `multitype_join` 消息块中的所有目标断开。 （重写[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a>接受

接受由此 `multitype_join` 块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `accept` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

## <a name="acquire_ref"></a>acquire_ref

获取此 `multitype_join` 消息块上的引用计数，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `link_target` 方法中链接到此源的 `ITarget` 对象调用。

## <a name="consume"></a>接受

使用以前由 `multitype_join` 消息块提供的消息，并通过目标成功保留该消息，从而将所有权转移给调用方。

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `consume` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的 `message` 对象的指针。

### <a name="remarks"></a>备注

`consume` 方法类似于 `accept`，但必须始终调用返回**true**的 `reserve`。

## <a name="link_target"></a>link_target

将目标块链接到此 `multitype_join` 消息块。

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向 `ITarget` 块的指针，该指针指向此 `multitype_join` 消息块。

## <a name="ctor"></a>multitype_join

构造 `multitype_join` 消息块。

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>参数

*_Tuple*<br/>
此 `tuple` 消息块的源的 `multitype_join` 。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。

*_Join*<br/>
要从中进行复制的 `multitype_join` 消息块。 请注意原始对象是孤立的，使之成为一个移动构造函数。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

在锁定状态下不执行移动构造，这意味着应由用户确保在移动期间没有轻量任务处于飞行状态。 否则可能会发生大量争用，从而导致异常或不一致的状态。

## <a name="dtor"></a>~ multitype_join

销毁 `multitype_join` 消息块。

```cpp
~multitype_join();
```

## <a name="release"></a>拆卸

释放以前成功的消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `release` 方法的目标块的指针。

## <a name="release_ref"></a>release_ref

释放此 `multiple_join` 消息块上的引用计数。

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由正在从此源取消链接的 `ITarget` 对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a>保留

保留此 `multitype_join` 消息块之前提供的消息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `reserve` 方法的目标块的指针。

### <a name="return-value"></a>返回值

`true` 如果消息已成功保留，则为 `false` 否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用 `reserve`后，如果成功，则必须调用 `consume` 或 `release` 以便分别获取或放弃该消息。

## <a name="unlink_target"></a>unlink_target

将目标块与此 `multitype_join` 消息块断开。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向要从此 `multitype_join` 消息块断开链接的 `ITarget` 块的指针。

## <a name="unlink_targets"></a>unlink_targets

将此 `multitype_join` 消息块中的所有目标断开。

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[choice 类](choice-class.md)<br/>
[join 类](join-class.md)
