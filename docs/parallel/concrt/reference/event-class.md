---
title: event 类
ms.date: 11/04/2016
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: aa9d46b868c1a31729a9590db3b3f67179903881
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264659"
---
# <a name="event-class"></a>event 类

明确感知并发运行时的手动重置事件。

## <a name="syntax"></a>语法

```
class event;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[~ event 析构函数](#dtor)|销毁一个事件。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[reset](#reset)|将事件重置为非终止状态。|
|[set](#set)|向事件发出信号。|
|[wait](#wait)|等待事件收到信号。|
|[wait_for_multiple](#wait_for_multiple)|等待多个事件收到信号。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|指示等待永远不应超时的值。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`event`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> 事件

构造一个新事件。

```
_CRTIMP event();
```

### <a name="remarks"></a>备注

##  <a name="dtor"></a> ~ 事件

销毁一个事件。

```
~event();
```

### <a name="remarks"></a>备注

应没有线程等待事件析构函数运行时。 在线程仍处于等待状态时允许析构事件会导致未定义的行为。

##  <a name="reset"></a> 重置

将事件重置为非终止状态。

```
void reset();
```

##  <a name="set"></a> 设置

向事件发出信号。

```
void set();
```

### <a name="remarks"></a>备注

发出事件信号会导致等待该事件的任意数量的上下文变为可运行。

##  <a name="timeout_infinite"></a> timeout_infinite

指示等待永远不应超时的值。

```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

##  <a name="wait"></a> 等待

等待事件收到信号。

```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*_Timeout*<br/>
表示毫秒的数之前等待超时。值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。

### <a name="return-value"></a>返回值

如果满足该等待，则这`0`返回; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示在等待而无需成为发出信号的事件已超时。

> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 应用中，不要调用`wait`对 ASTA 线程因为此调用可能会阻止当前线程，并可能导致应用停止响应。

##  <a name="wait_for_multiple"></a> wait_for_multiple

等待多个事件收到信号。

```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*_PPEvents*<br/>
要等待的事件的数组。 所指示的数组中的事件数`count`参数。

*count*<br/>
中提供的数组中的事件计数`_PPEvents`参数。

*_FWaitAll*<br/>
如果设置为值 **，则返回 true**，该数组内的所有事件中都提供的参数指定`_PPEvents`参数必须为满足在等待收到信号。 如果设置为值**false**，它指定数组中的任何事件中提供`_PPEvents`参数成为发出信号将满足等待。

*_Timeout*<br/>
表示毫秒的数之前等待超时。值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。

### <a name="return-value"></a>返回值

如果满足该等待，该数组内的索引中提供`_PPEvents`参数它满足等待的条件; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示在等待不满足该条件时已超时。

### <a name="remarks"></a>备注

如果将参数`_FWaitAll`设置为值`true`若要指示所有事件必须发出都信号以满足等待，该函数返回的索引没有任何特殊意义，它不是值的事实之外`COOPERATIVE_WAIT_TIMEOUT`。

> [!IMPORTANT]
> 在通用 Windows 平台 (UWP) 应用中，不要调用`wait_for_multiple`对 ASTA 线程因为此调用可能会阻止当前线程，并可能导致应用停止响应。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
