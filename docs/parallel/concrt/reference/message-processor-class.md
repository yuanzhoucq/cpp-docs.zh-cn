---
title: message_processor 类
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: d6e45613e0b412b6b94dba3c4a435115e32c7d6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438215"
---
# <a name="messageprocessor-class"></a>message_processor 类

`message_processor` 类是用于处理 `message` 对象的抽象基类。 不能保证消息的排序。

## <a name="syntax"></a>语法

```
template<class T>
class message_processor;
```

#### <a name="parameters"></a>参数

*T*<br/>
在消息中的有效负载的数据类型由`message_processor`对象。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|类型别名`T`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[async_send](#async_send)|当在派生类中重写，以异步方式将消息放入块中。|
|[sync_send](#sync_send)|当在派生类中重写，以同步方式将消息放入块中。|
|[等待](#wait)|当在派生类中重写，等待所有异步操作完成。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|当在派生类中重写执行取块转发消息的处理。 每次添加一个新消息并找到队列为空，则调用一次。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`message_processor`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="async_send"></a> async_send

当在派生类中重写，以异步方式将消息放入块中。

```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>参数

*_Msg*<br/>
一个`message`以异步方式发送的对象。

### <a name="remarks"></a>备注

处理器实现应重写此方法。

##  <a name="process_incoming_message"></a> process_incoming_message

当在派生类中重写执行取块转发消息的处理。 每次添加一个新消息并找到队列为空，则调用一次。

```
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>备注

消息块实现应重写此方法。

##  <a name="sync_send"></a> sync_send

当在派生类中重写，以同步方式将消息放入块中。

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>参数

*_Msg*<br/>
一个`message`要发送的同步对象。

### <a name="remarks"></a>备注

处理器实现应重写此方法。

##  <a name="wait"></a> 等待

当在派生类中重写，等待所有异步操作完成。

```
virtual void wait() = 0;
```

### <a name="remarks"></a>备注

处理器实现应重写此方法。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ordered_message_processor 类](ordered-message-processor-class.md)
