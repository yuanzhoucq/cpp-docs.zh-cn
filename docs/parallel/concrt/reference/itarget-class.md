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
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142036"
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

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`filter_method`|块所使用的任何方法的签名，该方法返回 `bool` 值以确定是否应接受所提供的消息。|
|`type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[~ ITarget 析构函数](#dtor)|销毁 `ITarget` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[传](#propagate)|当在派生类中重写时，以异步方式将消息从源块传递到此目标块。|
|[发送](#send)|当在派生类中重写时，将消息同步传递到目标块。|
|[supports_anonymous_source](#supports_anonymous_source)|在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回**true**，则目标无法推迟所提供的消息，因为稍后延迟的消息的消耗需要在其源链接注册表中标识源。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
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

## <a name="dtor"></a>~ ITarget

销毁 `ITarget` 的对象。

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

当在派生类中重写时，将指定的源块链接到此 `ITarget` 块。

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PSource*<br/>
正在链接到此 `ITarget` 块的 `ISource` 块。

### <a name="remarks"></a>备注

不应直接在 `ITarget` 块上调用此函数。 应使用 `ISource` 块上的 `link_target` 方法将块连接在一起，这将调用相应目标上的 `link_source` 方法。

## <a name="propagate"></a>传

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

如果 `NULL``_PMessage` 或 `_PSource` 参数，该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

## <a name="send"></a>发送

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

如果 `NULL``_PMessage` 或 `_PSource` 参数，该方法将引发[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

使用消息启动之外的 `send` 方法，在网络内传播消息是危险的，可能会导致死锁。

当 `send` 返回时，消息已被接受，并传输到目标块中，或者被目标拒绝。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

在派生类中重写时，根据消息块是否接受未链接到它的源提供的消息返回 true 或 false。 如果重写的方法返回**true**，则目标无法推迟所提供的消息，因为稍后延迟的消息的消耗需要在其源链接注册表中标识源。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>返回值

如果块可以接受来自未链接到它的源的消息，**则为 true** ; 否则为**false** 。

## <a name="unlink_source"></a>unlink_source

当在派生类中重写时，将指定的源块与此 `ITarget` 块断开。

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>参数

*_PSource*<br/>
正与此 `ITarget` 块取消链接 `ISource` 块。

### <a name="remarks"></a>备注

不应直接在 `ITarget` 块上调用此函数。 应使用 `unlink_target` 或 `unlink_targets` 方法将块与 `ISource` 块断开连接，这将调用相应目标上的 `unlink_source` 方法。

## <a name="unlink_sources"></a>unlink_sources

当在派生类中重写时，将所有源块与此 `ITarget` 块断开。

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISource 类](isource-class.md)
