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
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139320"
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

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`source_type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[~ ISource 析构函数](#dtor)|销毁 `ISource` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[接受](#accept)|当在派生类中重写时，接受由此 `ISource` 块提供的消息，并将所有权转移到调用方。|
|[acquire_ref](#acquire_ref)|当在派生类中重写时，获取此 `ISource` 块上的引用计数，以防止删除。|
|[使用](#consume)|当在派生类中重写时，使用以前由此 `ISource` 块提供的消息，并通过目标成功保留该消息，并将所有权转移到调用方。|
|[link_target](#link_target)|当在派生类中重写时，将目标块链接到此 `ISource` 块。|
|[release](#release)|当在派生类中重写时，释放以前的成功消息保留。|
|[release_ref](#release_ref)|当在派生类中重写时，释放此 `ISource` 块上的引用计数。|
|[reserve](#reserve)|当在派生类中重写时，保留以前由此 `ISource` 块提供的消息。|
|[unlink_target](#unlink_target)|当在派生类中重写时，如果发现以前已链接，则取消链接此 `ISource` 块中的目标块。|
|[unlink_targets](#unlink_targets)|当在派生类中重写时，将所有目标块与此 `ISource` 块断开。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISource`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="accept"></a>接受

当在派生类中重写时，接受由此 `ISource` 块提供的消息，并将所有权转移到调用方。

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `accept` 方法的目标块的指针。

### <a name="return-value"></a>返回值

指向调用方现在具有所有权的消息的指针。

### <a name="remarks"></a>备注

在此 `ISource` 块提供消息时，目标调用 `accept` 方法。 如果此源决定创建消息的副本，则返回的消息指针可能与传入 `ITarget` 块 `propagate` 方法的消息指针不同。

## <a name="acquire_ref"></a>acquire_ref

当在派生类中重写时，获取此 `ISource` 块上的引用计数，以防止删除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由在 `link_target` 方法中链接到此源的 `ITarget` 对象调用。

## <a name="consume"></a>接受

当在派生类中重写时，使用以前由此 `ISource` 块提供的消息，并通过目标成功保留该消息，并将所有权转移到调用方。

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="dtor"></a>~ ISource

销毁 `ISource` 的对象。

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

当在派生类中重写时，将目标块链接到此 `ISource` 块。

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向链接到此 `ISource` 块的目标块的指针。

## <a name="release"></a>拆卸

当在派生类中重写时，释放以前的成功消息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
保留 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `release` 方法的目标块的指针。

## <a name="release_ref"></a>release_ref

当在派生类中重写时，释放此 `ISource` 块上的引用计数。

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向正在调用此方法的目标块的指针。

### <a name="remarks"></a>备注

此方法由正在从此源取消链接的 `ITarget` 对象调用。 允许源块释放为目标块保留的任何资源。

## <a name="reserve"></a>保留

当在派生类中重写时，保留以前由此 `ISource` 块提供的消息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_MsgId*<br/>
提供的 `message` 对象的 `runtime_object_identity`。

*_PTarget*<br/>
指向调用 `reserve` 方法的目标块的指针。

### <a name="return-value"></a>返回值

如果消息已成功保留，**则为 true** ; 否则为**false** 。 预留可能因为众多原因失败，包括：消息已预留或已由另一目标接受，源可能拒绝预留等。

### <a name="remarks"></a>备注

调用 `reserve`后，如果成功，则必须调用 `consume` 或 `release` 以便分别获取或放弃该消息。

## <a name="unlink_target"></a>unlink_target

当在派生类中重写时，如果发现以前已链接，则取消链接此 `ISource` 块中的目标块。

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
指向与此 `ISource` 块取消链接的目标块的指针。

## <a name="unlink_targets"></a>unlink_targets

当在派生类中重写时，将所有目标块与此 `ISource` 块断开。

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ITarget 类](itarget-class.md)
