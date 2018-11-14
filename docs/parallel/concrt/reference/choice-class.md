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
ms.openlocfilehash: 60b09b674bec58a7d35a9a37d9a8f4c40d8cd522
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522722"
---
# <a name="choice-class"></a>choice 类

`choice` 消息块是多源、单目标的块，表示与一组源进行的控制流交互。 choice 块将等待多个源中的任何一个源以生成消息，并将传播生成该消息的源的索引。

## <a name="syntax"></a>语法

```
template<
    class T
>
class choice: public ISource<size_t>;
```

#### <a name="parameters"></a>参数

*T*<br/>
一个`tuple`-基于类型，表示输入源的有效负载。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|类型别名`T`。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[choice](#ctor)|已重载。 构造 `choice` 消息块。|
|[~ choice 析构函数](#dtor)|销毁`choice`消息块。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[accept](#accept)|接受提供的这一条消息`choice`块中，将所有权传递给调用方。|
|[acquire_ref](#acquire_ref)|获取对此的引用计数`choice`消息传递块中，若要防止删除。|
|[consume](#consume)|使用以前由此消息`choice`消息块并成功由目标，将所有权传递给调用方保留。|
|[has_value](#has_value)|检查是否这`choice`消息块具有尚未初始化的值。|
|[index](#index)|返回到一个索引`tuple`表示所选的元素`choice`消息块。|
|[link_target](#link_target)|目标块链接到此`choice`消息块。|
|[release](#release)|释放上一个成功的消息保留。|
|[release_ref](#release_ref)|释放对此的引用计数`choice`消息块。|
|[reserve](#reserve)|保留以前由此一条消息`choice`消息块。|
|[unlink_target](#unlink_target)|取消链接此目标块`choice`消息块。|
|[unlink_targets](#unlink_targets)|取消链接所有目标从此`choice`消息块。 (重写[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|
|[value](#value)|获取选定的索引的消息`choice`消息块。|

## <a name="remarks"></a>备注

Choice 块可确保只有一个传入消息的使用。

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="accept"></a> 接受

接受提供的这一条消息`choice`块中，将所有权传递给调用方。

```
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`提供的`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`accept`方法。

### <a name="return-value"></a>返回值

指向调用方现在具有的所有权的消息的指针。

##  <a name="acquire_ref"></a> acquire_ref

获取对此的引用计数`choice`消息传递块中，若要防止删除。

```
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向调用此方法的目标块的指针。

### <a name="remarks"></a>备注

调用此方法`ITarget`对象，它被链接到此源期间`link_target`方法。

##  <a name="ctor"></a> 选择

构造 `choice` 消息块。

```
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

##  <a name="dtor"></a> ~ 的选择

销毁`choice`消息块。

```
~choice();
```

##  <a name="consume"></a> 使用

使用以前由此消息`choice`消息块并成功由目标，将所有权传递给调用方保留。

```
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的保留`message`对象。

*_PTarget*<br/>
正在调用的目标块的指针`consume`方法。

### <a name="return-value"></a>返回值

一个指向`message`对象调用方现在具有的所有权。

### <a name="remarks"></a>备注

`consume`方法是类似于`accept`，但始终必须通过调用带`reserve`返回**true**。

##  <a name="has_value"></a> has_value

检查是否这`choice`消息块具有尚未初始化的值。

```
bool has_value() const;
```

### <a name="return-value"></a>返回值

**true**块已接收一个值，如果**false**否则为。

##  <a name="index"></a> 索引

返回到一个索引`tuple`表示所选的元素`choice`消息块。

```
size_t index();
```

### <a name="return-value"></a>返回值

消息的索引。

### <a name="remarks"></a>备注

可以使用提取的消息有效负载`get`方法。

##  <a name="link_target"></a> link_target

目标块链接到此`choice`消息块。

```
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
一个指向`ITarget`块要链接到此`choice`消息块。

##  <a name="release"></a> 版本

释放上一个成功的消息保留。

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象被释放。

*_PTarget*<br/>
正在调用的目标块的指针`release`方法。

##  <a name="release_ref"></a> release_ref

释放对此的引用计数`choice`消息块。

```
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向调用此方法的目标块的指针。

### <a name="remarks"></a>备注

调用此方法`ITarget`从此源取消链接的对象。 源块允许释放任何资源保留目标块的。

##  <a name="reserve"></a> 保留

保留以前由此一条消息`choice`消息块。

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`的`message`对象所保留。

*_PTarget*<br/>
正在调用的目标块的指针`reserve`方法。

### <a name="return-value"></a>返回值

**true**成功保留该消息，如果**false**否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用后`reserve`，如果成功，必须调用`consume`或`release`为了采用或分别放弃的消息的所有权。

##  <a name="unlink_target"></a> unlink_target

取消链接此目标块`choice`消息块。

```
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
一个指向`ITarget`块来取消链接此`choice`消息块。

##  <a name="unlink_targets"></a> unlink_targets

取消链接所有目标从此`choice`消息块。

```
virtual void unlink_targets();
```

### <a name="remarks"></a>备注

此方法不需要从析构函数调用，因为析构函数内部`single_assignment`块将正确地取消链接。

##  <a name="value"></a> 值

获取选定的索引的消息`choice`消息块。

```
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

因为 `choice` 消息块可以采用不同负载类型的输入，您必须指定检索时的负载类型。 您可以确定基于的结果类型`index`方法。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[join 类](join-class.md)<br/>
[single_assignment 类](single-assignment-class.md)
