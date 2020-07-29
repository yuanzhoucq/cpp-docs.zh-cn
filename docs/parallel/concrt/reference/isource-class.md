---
title: ISource 类
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: df592e965b436ed5a1d60702f9e57088887d5a94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222701"
---
# <a name="isource-class"></a>ISource 类

`ISource` 类是所有源块的接口。 源块将消息传播到 `ITarget` 块。

## <a name="syntax"></a>语法

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>参数

*T*<br/>
源块生成的消息内有效负载的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`source_type`|的类型别名 `T` 。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[~ ISource 析构函数](#dtor)|销毁 `ISource` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[接受](#accept)|当在派生类中重写时，接受此块提供的消息 `ISource` ，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|当在派生类中重写时，获取此块上的引用计数 `ISource` ，以防止删除。|
|[接受](#consume)|当在派生类中重写时，使用以前由此块提供的消息， `ISource` 并已成功保留目标，将所有权转移给调用方。|
|[link_target](#link_target)|当在派生类中重写时，将目标块链接到此 `ISource` 块。|
|[拆卸](#release)|当在派生类中重写时，释放以前的成功消息保留。|
|[release_ref](#release_ref)|当在派生类中重写时，释放此块上的引用计数 `ISource` 。|
|[保留](#reserve)|当在派生类中重写时，保留此块先前提供的消息 `ISource` 。|
|[unlink_target](#unlink_target)|当在派生类中重写时， `ISource` 如果发现以前已链接，则取消链接此块中的目标块。|
|[unlink_targets](#unlink_targets)|当在派生类中重写时，将此块中的所有目标块断开 `ISource` 。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISource`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a><a name="accept"></a>接受

当在派生类中重写时，接受此块提供的消息 `ISource` ，并将所有权转移到调用方。

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `accept` 。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

### <a name="remarks"></a>备注

`accept`此方法由目标在此块提供消息时调用 `ISource` 。 `propagate` `ITarget` 如果此源决定创建消息的副本，则返回的消息指针可能不同于传递到块的方法中的消息指针。

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

当在派生类中重写时，获取此块上的引用计数 `ISource` ，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `ITarget` 方法中链接到此源的对象调用 `link_target` 。

## <a name="consume"></a><a name="consume"></a>接受

当在派生类中重写时，使用以前由此块提供的消息， `ISource` 并已成功保留目标，将所有权转移给调用方。

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="isource"></a><a name="dtor"></a>~ ISource

销毁 `ISource` 对象。

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a>link_target

当在派生类中重写时，将目标块链接到此 `ISource` 块。

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向链接到此块的目标块的指针 `ISource` 。

## <a name="release"></a><a name="release"></a>拆卸

当在派生类中重写时，释放以前的成功消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `release` 。

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

当在派生类中重写时，释放此块上的引用计数 `ISource` 。

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由 `ITarget` 正在从此源取消链接的对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a><a name="reserve"></a>保留

当在派生类中重写时，保留此块先前提供的消息 `ISource` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
`runtime_object_identity`所提供的 `message` 对象的。

*_PTarget*<br/>
指向调用方法的目标块的指针 `reserve` 。

### <a name="return-value"></a>返回值

**`true`** 如果消息已成功保留，则 **`false`** 为; 否则为。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用后 `reserve` ，如果成功，则必须调用或，才能 `consume` `release` 分别获取或放弃消息的所有权。

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

当在派生类中重写时， `ISource` 如果发现以前已链接，则取消链接此块中的目标块。

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在从此块取消链接的目标块的指针 `ISource` 。

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

当在派生类中重写时，将此块中的所有目标块断开 `ISource` 。

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ITarget 类](itarget-class.md)
