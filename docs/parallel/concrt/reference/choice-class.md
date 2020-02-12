---
title: choice 类
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142216"
---
# <a name="choice-class"></a>choice 类

`choice` 消息块是多源、单目标的块，表示与一组源进行的控制流交互。 choice 块将等待多个源中的任何一个源以生成消息，并将传播生成该消息的源的索引。

## <a name="syntax"></a>语法

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>参数

*T*<br/>
一个基于 `tuple`的类型，表示输入源的负载。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|`type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[choice](#ctor)|已重载。 构造 `choice` 消息块。|
|[~ choice 析构函数](#dtor)|销毁 `choice` 消息块。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[accept](#accept)|接受由此 `choice` 块提供的消息，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|获取此 `choice` 消息块上的引用计数，以防止删除。|
|[consume](#consume)|使用以前由此 `choice` 消息块提供的消息，并已成功保留该消息，并将所有权转移给调用方。|
|[has_value](#has_value)|检查是否已使用值对此 `choice` 消息块进行了初始化。|
|[index](#index)|返回 `tuple` 的索引，该索引表示由 `choice` 消息块选择的元素。|
|[link_target](#link_target)|将目标块链接到此 `choice` 消息块。|
|[release](#release)|释放以前成功的消息保留。|
|[release_ref](#release_ref)|释放此 `choice` 消息块上的引用计数。|
|[reserve](#reserve)|保留此 `choice` 消息块之前提供的消息。|
|[unlink_target](#unlink_target)|将目标块与此 `choice` 消息块断开。|
|[unlink_targets](#unlink_targets)|将此 `choice` 消息块中的所有目标断开。 （重写[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|
|[value](#value)|获取 `choice` 消息块已选择其索引的消息。|

## <a name="remarks"></a>备注

选择块可确保仅使用其中一个传入消息。

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a>接受

接受由此 `choice` 块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `accept` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

## <a name="acquire_ref"></a>acquire_ref

获取此 `choice` 消息块上的引用计数，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `link_target` 方法中链接到此源的 `ITarget` 对象调用。

## <a name="ctor"></a>选择

构造 `choice` 消息块。

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>参数

*_Tuple*<br/>
choice 的源的 `tuple` 。

*_PScheduler*<br/>
在其中计划了 `Scheduler` 消息块的传播任务的 `choice` 对象。

*_PScheduleGroup*<br/>
在其中计划了 `ScheduleGroup` 消息块的传播任务的 `choice` 对象。 所用 `Scheduler` 对象由该计划组提示。

*_Choice*<br/>
要从中进行复制的 `choice` 消息块。 请注意原始对象是孤立的，使之成为一个移动构造函数。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PScheduleGroup` 函数，运行时将使用默认的计划程序。

在锁定状态下不执行移动构造，这意味着应由用户确保在移动期间没有轻量任务处于飞行状态。 否则可能会发生大量争用，从而导致异常或不一致的状态。

## <a name="dtor"></a>~ choice

销毁 `choice` 消息块。

```cpp
~choice();
```

## <a name="consume"></a>接受

使用以前由此 `choice` 消息块提供的消息，并已成功保留该消息，并将所有权转移给调用方。

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

## <a name="has_value"></a>has_value

检查是否已使用值对此 `choice` 消息块进行了初始化。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>返回值

如果块接收到值，**则为 true** ; 否则为**false** 。

## <a name="index"></a>编入

返回 `tuple` 的索引，该索引表示由 `choice` 消息块选择的元素。

```cpp
size_t index();
```

### <a name="return-value"></a>返回值

消息索引。

### <a name="remarks"></a>备注

可以使用 `get` 方法提取消息有效负载。

## <a name="link_target"></a>link_target

将目标块链接到此 `choice` 消息块。

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向 `ITarget` 块的指针，该指针指向此 `choice` 消息块。

## <a name="release"></a>拆卸

释放以前成功的消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
正在释放的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `release` 方法的目标块的指针。

## <a name="release_ref"></a>release_ref

释放此 `choice` 消息块上的引用计数。

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由正在从此源取消链接的 `ITarget` 对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a>保留

保留此 `choice` 消息块之前提供的消息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `reserve` 方法的目标块的指针。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用 `reserve`后，如果成功，则必须调用 `consume` 或 `release` 以便分别获取或放弃该消息。

## <a name="unlink_target"></a>unlink_target

将目标块与此 `choice` 消息块断开。

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向要从此 `choice` 消息块断开链接的 `ITarget` 块的指针。

## <a name="unlink_targets"></a>unlink_targets

将此 `choice` 消息块中的所有目标断开。

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>备注

不需要从析构函数中调用此方法，因为内部 `single_assignment` 块的析构函数会正确取消链接。

## <a name="value"></a>负值

获取 `choice` 消息块已选择其索引的消息。

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>参数

*_Payload_type*<br/>
消息负载的类型。

### <a name="return-value"></a>返回值

消息的负载。

### <a name="remarks"></a>备注

因为 `choice` 消息块可以采用不同负载类型的输入，您必须指定检索时的负载类型。 您可以根据 `index` 方法的结果确定类型。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[join 类](join-class.md)<br/>
[single_assignment 类](single-assignment-class.md)
