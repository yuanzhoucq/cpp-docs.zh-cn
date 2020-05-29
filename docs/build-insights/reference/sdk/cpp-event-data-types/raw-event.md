---
title: RawEvent 类
description: C++生成见解 SDK RawEvent 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324374"
---
# <a name="rawevent-class"></a>RawEvent 类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`RawEvent`类用于表示[事件堆栈](event-stack.md)中的常规事件。

## <a name="syntax"></a>语法

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>备注

`RawEvent`类中的多个成员函数返回刻度计数。 C++生成见解使用 Windows 的性能计数器作为报价源。 刻度计数必须与刻度频率一起使用，才能将其转换为时间单位（如秒）。 可以`TickFrequency`调用成员函数以获取滴答频率。 有关如何将刻度转换为时间单位的示例，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)页。

如果不想自己转换刻度，`RawEvent`类提供以纳秒为单位返回时间值的成员函数。 使用标准C++`chrono`库将纳秒转换为其他时间单位。

## <a name="members"></a>成员

### <a name="constructor"></a>构造函数

[原始事件](#raw-event)

### <a name="functions"></a>函数

[CPUTicks](#cpu-ticks)\
[CPU时间](#cpu-time)\
[数据](#data)\
[时间](#duration)\
[事件 Id](#event-id)
[事件实例 Id](#event-instance-id)
[事件名称](#event-name)\
[事件宽名称](#event-wide-name)\
[独家CPUTicks](#exclusive-cpu-ticks)\
[独家CPU时间](#exclusive-cpu-time)\
[独家持续时间](#exclusive-duration)\
[独家持续时间提示](#exclusive-duration-ticks)\
[独家华尔街时间责任](#exclusive-wall-clock-time-responsibility)\
[独家华尔街时间责任提示](#exclusive-wall-clock-time-responsibility-ticks)\
[进程 Id](#process-id)\
[处理器索引](#processor-index)\
[开始时间戳](#start-timestamp)\
[停止时间戳](#stop-timestamp)\
[线程 Id](#thread-id)\
[滴答频率](#tick-frequency)\
[墙钟时间责任](#wall-clock-time-responsibility)\
[墙钟时间责任提示](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>原始事件

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>参数

*事件*\
事件数据。

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>返回值

在此活动期间发生的 CPU 刻度数。 CPU 刻度不同于常规刻度。 仅当 CPU 在活动中执行代码时，才会计算 CPU 刻度。 当与活动关联的线程处于睡眠状态时，不会计算 CPU 刻度。

## <a name="cputime"></a><a name="cpu-time"></a>CPU时间

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>返回值

CPU 在此活动中执行代码的时间量。 如果在单独的线程上执行子活动，则此值可能高于活动的持续时间。 该值以纳秒为单位返回。

## <a name="data"></a><a name="data"></a>数据

```cpp
const void* Data() const;
```

### <a name="return-value"></a>返回值

指向此事件中包含的额外数据的指针。 有关如何解释此字段的详细信息，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="duration"></a><a name="duration"></a>时间

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>返回值

活动持续时间（以纳秒为单位）。

## <a name="eventid"></a><a name="event-id"></a>事件 Id

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>返回值

标识事件类型的数字。 有关事件标识符的列表，请参阅[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>事件实例 Id

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>返回值

唯一标识跟踪内事件的数字。 多次分析或重新记录同一跟踪时，此值不会更改。 使用此值可识别多个分析或重新记录通过同一跟踪中的同一事件。

## <a name="eventname"></a><a name="event-name"></a>事件名称

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>返回值

包含[事件 Id](#event-id)标识的事件类型名称的 ANSI 字符串。

## <a name="eventwidename"></a><a name="event-wide-name"></a>事件宽名称

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>返回值

包含[事件 Id](#event-id)标识的事件类型名称的宽字符串。

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>独家CPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>返回值

与[CPUTick 相同](#cpu-ticks)，但不包括子活动中发生的 CPU 刻度。

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>独家CPU时间

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>返回值

与[CPUTime](#cpu-time)相同，但不包括子活动的 CPU 时间。

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>独家持续时间

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>返回值

活动持续时间（以纳秒为单位），不包括在子活动中花费的时间量。

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>独家持续时间提示

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>返回值

在此活动中发生的刻度数，不包括子活动中发生的刻度数。

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>独家华尔街时间责任

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>返回值

与["墙钟时间责任"](#wall-clock-time-responsibility)相同，但不包括儿童活动的挂钟时间责任。

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>独家华尔街时间责任提示

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>返回值

与["墙钟时间责任"相同](#wall-clock-time-responsibility-ticks)，但不包括儿童活动的挂钟时间责任。

## <a name="processid"></a><a name="process-id"></a>进程 Id

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>返回值

事件发生的进程的标识符。

## <a name="processorindex"></a><a name="processor-index"></a>处理器索引

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>返回值

事件发生的逻辑处理器的零基索引。

## <a name="starttimestamp"></a><a name="start-timestamp"></a>开始时间戳

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>返回值

活动开始时捕获的刻度值。

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>停止时间戳

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>返回值

活动停止时捕获的刻度值。

## <a name="threadid"></a><a name="thread-id"></a>线程 Id

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>返回值

发生事件的线程的标识符。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答频率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

评估以此事件的刻度为单位的持续时间时，每秒使用的刻度数。

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>墙钟时间责任

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>返回值

此活动的挂钟时间责任，以纳秒为单位。 有关挂钟时间责任的含义的详细信息，请参阅["挂时钟时间责任提示](#wall-clock-time-responsibility-ticks)"。

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>墙钟时间责任提示

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>返回值

表示此活动对总挂钟时间的贡献的刻度计数。 挂钟时间责任刻度不同于常规刻度。 钟点时间责任滴答声考虑了活动之间的并行性。 两个并行活动的持续时间可能为 50 个刻度，并且相同的开始和停止时间相同。 在这种情况下，两者都被分配了 25 个刻度的挂钟时间责任。

::: moniker-end
