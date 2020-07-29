---
title: ITarget 类
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: 39aebd9d82f098225c1275ac6f43d64fc1ce3ba8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231710"
---
# <a name="itarget-class"></a>ITarget 类

`ITarget` 类是所有目标块的接口。 目标块使用 `ISource` 块提供给它们的消息。

## <a name="syntax"></a>语法

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>参数

*T*<br/>
目标块接受的消息内的负载的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`filter_method`|块所使用的任何方法的签名，该方法返回一个 **`bool`** 值以确定是否应接受所提供的消息。|
|`type`|的类型别名 `T` 。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[~ ITarget 析构函数](#dtor)|销毁 `ITarget` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[传](#propagate)|当在派生类中重写时，以异步方式将消息从源块传递到此目标块。|
|[send](#send)|当在派生类中重写时，将消息同步传递到目标块。|
|[supports_anonymous_source](#supports_anonymous_source)|在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 **`true`** ，则目标不能推迟所提供的消息，因为稍后延迟的消息的消耗需要在其源链接注册表中标识源。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[link_source](#link_source)|当在派生类中重写时，将指定的源块链接到此 `ITarget` 块。|
|[unlink_source](#unlink_source)|当在派生类中重写时，将指定的源块与此 `ITarget` 块断开。|
|[unlink_sources](#unlink_sources)|当在派生类中重写时，将所有源块与此 `ITarget` 块断开。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ITarget`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="itarget"></a><a name="dtor"></a>~ ITarget

销毁 `ITarget` 对象。

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a><a name="link_source"></a>link_source

当在派生类中重写时，将指定的源块链接到此 `ITarget` 块。

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PSource*<br/>
`ISource`正在链接到此块的块 `ITarget` 。

### <a name="remarks"></a>备注

不应直接在块上调用此函数 `ITarget` 。 块应使用方法连接在一起 `link_target` `ISource` ，这将对 `link_source` 相应目标调用方法。

## <a name="propagate"></a><a name="propagate"></a>传

当在派生类中重写时，以异步方式将消息从源块传递到此目标块。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

### <a name="remarks"></a>备注

如果[invalid_argument](../../../standard-library/invalid-argument-class.md) `_PMessage` 或参数为，方法将引发 invalid_argument 异常 `_PSource` `NULL` 。

## <a name="send"></a><a name="send"></a>发送

当在派生类中重写时，将消息同步传递到目标块。

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PMessage*<br/>
指向 `message` 对象的指针。

*_PSource*<br/>
指向提供消息的源块的指针。

### <a name="return-value"></a>返回值

[Message_status](concurrency-namespace-enums.md)指示目标决定对消息执行的操作。

### <a name="remarks"></a>备注

如果[invalid_argument](../../../standard-library/invalid-argument-class.md) `_PMessage` 或参数为，方法将引发 invalid_argument 异常 `_PSource` `NULL` 。

使用 `send` 消息启动外的方法和在网络内传播消息是危险的，可能会导致死锁。

当 `send` 返回时，消息已被接受，并传输到目标块中，或者被目标拒绝。

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回 **`true`** ，则目标无法推迟所提供的消息，因为稍后延迟的消息的使用需要在其源链接注册表中标识源。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

**`true`** 如果块可以接受来自未链接到它的源的消息，则为 **`false`** 。

## <a name="unlink_source"></a><a name="unlink_source"></a>unlink_source

当在派生类中重写时，将指定的源块与此 `ITarget` 块断开。

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PSource*<br/>
`ISource`正在从该块取消链接的块 `ITarget` 。

### <a name="remarks"></a>备注

不应直接在块上调用此函数 `ITarget` 。 应使用 `unlink_target` 或方法对块断开连接 `unlink_targets` `ISource` ，这将在 `unlink_source` 相应的目标上调用方法。

## <a name="unlink_sources"></a><a name="unlink_sources"></a>unlink_sources

当在派生类中重写时，将所有源块与此 `ITarget` 块断开。

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISource 类](isource-class.md)
