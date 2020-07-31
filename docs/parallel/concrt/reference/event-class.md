---
title: event 类
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3f2ec71083f7a7905bad5cda014baba914e31e79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215798"
---
# <a name="event-class"></a>event 类

明确感知并发运行时的手动重置事件。

## <a name="syntax"></a>语法

```cpp
class event;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[~ 事件析构函数](#dtor)|销毁事件。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[reset](#reset)|将事件重置为非终止状态。|
|[set](#set)|发出事件信号。|
|[再](#wait)|等待事件进入终止状态。|
|[wait_for_multiple](#wait_for_multiple)|等待多个事件发出信号。|

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|指示等待永远不应超时的值。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`event`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="event"></a><a name="ctor"></a> 事件

构造一个新事件。

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>备注

## <a name="event"></a><a name="dtor"></a>~ 事件

销毁事件。

```cpp
~event();
```

### <a name="remarks"></a>备注

当析构函数运行时，预期不会有等待事件的线程。 在线程仍处于等待状态时允许析构事件会导致未定义的行为。

## <a name="reset"></a><a name="reset"></a>&

将事件重置为非终止状态。

```cpp
void reset();
```

## <a name="set"></a><a name="set"></a>字符集

发出事件信号。

```cpp
void set();
```

### <a name="remarks"></a>备注

发出事件信号会导致等待该事件的任意数量的上下文变为可运行。

## <a name="timeout_infinite"></a><a name="timeout_infinite"></a>timeout_infinite

指示等待永远不应超时的值。

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a><a name="wait"></a>再

等待事件进入终止状态。

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*_Timeout*<br/>
指示等待超时前等待的毫秒数。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示没有超时。

### <a name="return-value"></a>返回值

如果已满足等待，则返回值 `0` ; 否则返回值，该值 `COOPERATIVE_WAIT_TIMEOUT` 指示等待超时，而不会向事件发出信号。

> [!IMPORTANT]
> 在通用 Windows 平台（UWP）应用程序中，不要 `wait` 在 ASTA 线程上调用，因为此调用会阻止当前线程，并可能导致应用程序停止响应。

## <a name="wait_for_multiple"></a><a name="wait_for_multiple"></a>wait_for_multiple

等待多个事件发出信号。

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*_PPEvents*<br/>
要等待的事件的数组。 数组中的事件数由 `count` 参数表示。

*计数*<br/>
参数中提供的数组中的事件计数 `_PPEvents` 。

*_FWaitAll*<br/>
如果设置为值 **`true`** ，则参数指定在参数中提供的数组中的所有事件 `_PPEvents` 必须变为已发出信号，以便满足等待。 如果设置为值 **`false`** ，则它指定在参数中提供的数组中的任何事件 `_PPEvents` 都将满足等待。

*_Timeout*<br/>
指示等待超时前等待的毫秒数。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示没有超时。

### <a name="return-value"></a>返回值

如果已满足等待，则为满足等待条件的参数中提供的数组中的索引 `_PPEvents` ; 否则为 `COOPERATIVE_WAIT_TIMEOUT` 指示等待超时且未满足条件的值。

### <a name="remarks"></a>备注

如果将参数 `_FWaitAll` 设置为值， **`true`** 以指示所有事件都必须收到信号才能满足等待，则函数返回的索引不会对不是值这一事实产生任何特殊意义 `COOPERATIVE_WAIT_TIMEOUT` 。

> [!IMPORTANT]
> 在通用 Windows 平台（UWP）应用程序中，不要 `wait_for_multiple` 在 ASTA 线程上调用，因为此调用会阻止当前线程，并可能导致应用程序停止响应。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
