---
title: agent 类
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882933"
---
# <a name="agent-class"></a>agent 类

旨在用作所有独立代理的基类的类。 用于对其他代理隐藏状态并通过消息传递进行交互。

## <a name="syntax"></a>语法

```cpp
class agent;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[代理商](#ctor)|已重载。 构造代理。|
|[~ 代理析构函数](#dtor)|销毁代理。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[cancel](#cancel)|将代理从 `agent_created` 或 `agent_runnable` 状态移动到 `agent_canceled` 状态。|
|[start](#start)|将代理从 `agent_created` 状态移动到 `agent_runnable` 状态，并将其计划为执行。|
|[status](#status)|代理中状态信息的同步源。|
|[status_port](#status_port)|代理中状态信息的异步源。|
|[再](#wait)|等待代理完成其任务。|
|[wait_for_all](#wait_for_all)|等待所有指定的代理完成其任务。|
|[wait_for_one](#wait_for_one)|等待任一指定的代理完成其任务。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[效率](#done)|将代理移到 `agent_done` 状态，指示代理已完成。|
|[run](#run)|表示代理的主要任务。 应在派生类中重写 `run`，并指定代理在启动后应执行的操作。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`agent`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="ctor"></a>代理商

构造代理。

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>参数

*_PScheduler*<br/>
在其中计划代理的执行任务的 `Scheduler` 对象。

*_PGroup*<br/>
在其中计划代理的执行任务的 `ScheduleGroup` 对象。 所用 `Scheduler` 对象由该计划组提示。

### <a name="remarks"></a>备注

如果未指定 `_PScheduler` 或 `_PGroup` 函数，运行时将使用默认的计划程序。

## <a name="dtor"></a>~ 代理

销毁代理。

```cpp
virtual ~agent();
```

### <a name="remarks"></a>备注

销毁不处于终端状态的代理是错误的（`agent_done` 或 `agent_canceled`）。 在从 `agent` 类继承的类的析构函数中等待代理到达终端状态，这样可以避免这种情况。

## <a name="cancel"></a>取消

将代理从 `agent_created` 或 `agent_runnable` 状态移动到 `agent_canceled` 状态。

```cpp
bool cancel();
```

### <a name="return-value"></a>返回值

如果代理已取消，**则为 true** ; 否则为**false** 。 如果代理已经开始运行或已完成，则无法取消它。

## <a name="done"></a>效率

将代理移到 `agent_done` 状态，指示代理已完成。

```cpp
bool done();
```

### <a name="return-value"></a>返回值

如果代理移到 `agent_done` 状态，**则为 true** ; 否则为**false** 。 无法将已取消的代理移到 `agent_done` 状态。

### <a name="remarks"></a>备注

如果知道代理的执行已完成，则应在 `run` 方法的末尾调用此方法。

## <a name="run"></a>用

表示代理的主要任务。 应在派生类中重写 `run`，并指定代理在启动后应执行的操作。

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>备注

在调用此方法之前，代理状态将更改为 "`agent_started`"。 在返回之前，方法应在代理上调用 `done`，并可能不会引发任何异常。

## <a name="start"></a>start

将代理从 `agent_created` 状态移动到 `agent_runnable` 状态，并将其计划为执行。

```cpp
bool start();
```

### <a name="return-value"></a>返回值

如果代理正确启动，**则为 true** ; 否则为**false** 。 无法启动已取消的代理。

## <a name="status"></a>状态值

代理中状态信息的同步源。

```cpp
agent_status status();
```

### <a name="return-value"></a>返回值

返回代理的当前状态。 请注意，返回状态在返回后会立即更改。

## <a name="status_port"></a>status_port

代理中状态信息的异步源。

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>返回值

返回一个消息源，该消息源可以发送有关代理的当前状态的消息。

## <a name="wait"></a>再

等待代理完成其任务。

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*_PAgent*<br/>
一个指针，指向要等待的代理。

*_Timeout*<br/>
要等待的最大时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

等待完成时代理的 `agent_status`。 这可以是 `agent_canceled` 或 `agent_done`。

### <a name="remarks"></a>备注

代理任务在代理进入 `agent_canceled` 或 `agent_done` 状态时完成。

如果参数 `_Timeout` 的值不是常量 `COOPERATIVE_TIMEOUT_INFINITE`，则在代理完成其任务之前指定的时间量到期时，将引发异常[operation_timed_out](operation-timed-out-class.md) 。

## <a name="wait_for_all"></a>wait_for_all

等待所有指定的代理完成其任务。

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*count*<br/>
数组 `_PAgents`中存在的代理指针数。

*_PAgents*<br/>
指向要等待的代理的指针的数组。

*_PStatus*<br/>
指向代理状态的数组的指针。 当该方法返回时，每个状态值都将表示相应代理的状态。

*_Timeout*<br/>
要等待的最大时间（以毫秒为单位）。

### <a name="remarks"></a>备注

代理任务在代理进入 `agent_canceled` 或 `agent_done` 状态时完成。

如果参数 `_Timeout` 的值不是常量 `COOPERATIVE_TIMEOUT_INFINITE`，则在代理完成其任务之前指定的时间量到期时，将引发异常[operation_timed_out](operation-timed-out-class.md) 。

## <a name="wait_for_one"></a>wait_for_one

等待任一指定的代理完成其任务。

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>参数

*count*<br/>
数组 `_PAgents`中存在的代理指针数。

*_PAgents*<br/>
指向要等待的代理的指针的数组。

*_Status*<br/>
对将在其中放置代理状态的变量的引用。

*_Index*<br/>
对将在其中放置代理索引的变量的引用。

*_Timeout*<br/>
要等待的最大时间（以毫秒为单位）。

### <a name="remarks"></a>备注

代理任务在代理进入 `agent_canceled` 或 `agent_done` 状态时完成。

如果参数 `_Timeout` 的值不是常量 `COOPERATIVE_TIMEOUT_INFINITE`，则在代理完成其任务之前指定的时间量到期时，将引发异常[operation_timed_out](operation-timed-out-class.md) 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
