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
ms.openlocfilehash: c648e77e404cf39eab281a93e03d8b427da375f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205855"
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
`tuple`块加入和传播的消息的负载类型。

*_Jtype*<br/>
`join`此块的类型为， `greedy` 或`non_greedy`

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|的类型别名 `T` 。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[multitype_join](#ctor)|已重载。 构造 `multitype_join` 消息块。|
|[~ multitype_join 析构函数](#dtor)|销毁 `multitype_join` 消息块。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[接受](#accept)|接受此块提供的消息 `multitype_join` ，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|获取此消息块上的引用计数 `multitype_join` ，以防止删除。|
|[接受](#consume)|使用消息块先前提供的消息 `multitype_join` ，并由目标成功保留该消息，并将所有权转移到调用方。|
|[link_target](#link_target)|将目标块链接到此 `multitype_join` 消息块。|
|[拆卸](#release)|释放以前成功的消息保留。|
|[release_ref](#release_ref)|释放此消息块上的引用计数 `multiple_join` 。|
|[保留](#reserve)|保留此消息块先前提供的消息 `multitype_join` 。|
|[unlink_target](#unlink_target)|将目标块与此 `multitype_join` 消息块断开。|
|[unlink_targets](#unlink_targets)|从此消息块取消所有目标的 `multitype_join` 锁定。 （重写[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a><a name="accept"></a>接受

接受此块提供的消息 `multitype_join` ，并将所有权转移到调用方。

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `accept` 。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

获取此消息块上的引用计数 `multitype_join` ，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `ITarget` 方法中链接到此源的对象调用 `link_target` 。

## <a name="consume"></a><a name="consume"></a>接受

使用消息块先前提供的消息 `multitype_join` ，并由目标成功保留该消息，并将所有权转移到调用方。

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `consume` 。

### <a name="return-value"></a>返回值

指向 `message` 调用方现在具有所有权的对象的指针。

### <a name="remarks"></a>备注

此 `consume` 方法类似于 `accept` ，但必须始终在之前调用 `reserve` 返回的 **`true`** 。

## <a name="link_target"></a><a name="link_target"></a>link_target

将目标块链接到此 `multitype_join` 消息块。

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向 `ITarget` 链接到此消息块的块的指针 `multitype_join` 。

## <a name="multitype_join"></a><a name="ctor"></a>multitype_join

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

## <a name="multitype_join"></a><a name="dtor"></a>~ multitype_join

销毁 `multitype_join` 消息块。

```cpp
~multitype_join();
```

## <a name="release"></a><a name="release"></a>拆卸

释放以前成功的消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 要释放的对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `release` 。

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

释放此消息块上的引用计数 `multiple_join` 。

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由 `ITarget` 正在从此源取消链接的对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a><a name="reserve"></a>保留

保留此消息块先前提供的消息 `multitype_join` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity` `message` 保留的对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `reserve` 。

### <a name="return-value"></a>返回值

**`true`** 如果消息已成功保留，则 **`false`** 为; 否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用后 `reserve` ，如果成功，则必须调用或，才能 `consume` `release` 分别获取或放弃消息的所有权。

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

将目标块与此 `multitype_join` 消息块断开。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向 `ITarget` 要从此消息块断开链接的块的指针 `multitype_join` 。

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

从此消息块取消所有目标的 `multitype_join` 锁定。

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[choice 类](choice-class.md)<br/>
[联接类](join-class.md)
