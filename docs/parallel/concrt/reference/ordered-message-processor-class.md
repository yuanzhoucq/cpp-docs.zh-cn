---
title: ordered_message_processor 类
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138787"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor 类

`ordered_message_processor` 是允许消息块按接收顺序处理消息的 `message_processor`。

## <a name="syntax"></a>语法

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>参数

*T*<br/>
处理器处理的消息的负载类型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`type`|`T`的类型别名。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[ordered_message_processor](#ctor)|构造 `ordered_message_processor` 对象。|
|[~ ordered_message_processor 析构函数](#dtor)|销毁 `ordered_message_processor` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[async_send](#async_send)|异步对消息进行排队并启动处理任务（如果尚未这样做）。 （重写[message_processor：： async_send](message-processor-class.md#async_send)。）|
|[初始化](#initialize)|用适当的回调函数、计划程序和计划组初始化 `ordered_message_processor` 对象。|
|[initialize_batched_processing](#initialize_batched_processing)|初始化消息的批处理|
|[sync_send](#sync_send)|同步地对消息进行排队并启动处理任务（如果尚未这样做）。 （重写[message_processor：： sync_send](message-processor-class.md#sync_send)。）|
|[再](#wait)|在消息块的析构函数中使用的特定于处理器的自旋等待，以确保所有异步处理任务在销毁块之前都有时间完成。 （重写[message_processor：： wait](message-processor-class.md#wait)。）|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|异步调用的处理函数。 它取消排队消息并开始处理消息。 （重写[message_processor：:p rocess_incoming_message](message-processor-class.md#process_incoming_message)。）|

## <a name="inheritance-hierarchy"></a>继承层次结构

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="async_send"></a>async_send

异步对消息进行排队并启动处理任务（如果尚未这样做）。

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
指向消息的指针。

## <a name="initialize"></a>初始化

用适当的回调函数、计划程序和计划组初始化 `ordered_message_processor` 对象。

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>参数

*_PScheduler*<br/>
指向要用于计划轻量任务的计划程序的指针。

*_PScheduleGroup*<br/>
一个指针，指向要用于计划轻量任务的计划组。

*_Handler*<br/>
在回调过程中调用的处理程序函子。

## <a name="initialize_batched_processing"></a>initialize_batched_processing

初始化消息的批处理

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>参数

*_Processor*<br/>
在回调过程中调用的处理器函子。

*_Propagator*<br/>
在回调过程中调用的传播函子。

## <a name="ctor"></a>ordered_message_processor

构造 `ordered_message_processor` 对象。

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>备注

在调用 `initialize` 函数之前，此 `ordered_message_processor` 将不会计划异步或同步处理程序。

## <a name="dtor"></a>~ ordered_message_processor

销毁 `ordered_message_processor` 的对象。

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>备注

销毁处理器之前等待所有未完成的异步操作。

## <a name="process_incoming_message"></a>process_incoming_message

异步调用的处理函数。 它取消排队消息并开始处理消息。

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

同步地对消息进行排队并启动处理任务（如果尚未这样做）。

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>参数

*_Msg*<br/>
指向消息的指针。

## <a name="wait"></a>再

在消息块的析构函数中使用的特定于处理器的自旋等待，以确保所有异步处理任务在销毁块之前都有时间完成。

```cpp
virtual void wait();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
