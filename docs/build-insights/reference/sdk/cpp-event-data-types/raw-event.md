---
title: RawEvent 类
description: C++ BUILD Insights SDK RawEvent 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334600"
---
# <a name="rawevent-class"></a>RawEvent 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`RawEvent` 类用于表示[EventStack](event-stack.md)中的常规事件。

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

`RawEvent` 类中的几个成员函数返回一个滴答计数。 C++Build Insights 使用 Windows 性能计数器作为刻度的源。 滴答计数必须与计时周期一起使用，以将其转换为时间单位（如秒）。 可以调用 `TickFrequency` 成员函数以获取滴答频率。 请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)页面，以获取有关如何将刻度转换为时间单位的示例。

如果不想自行转换刻度，则 `RawEvent` 类将提供按毫微秒返回时间值的成员函数。 使用标准C++ `chrono` 库将毫微秒转换为其他时间单位。

## <a name="members"></a>Members

### <a name="constructor"></a>构造函数

[RawEvent](#raw-event)

### <a name="functions"></a>函数

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[数据](#data)\
[持续时间](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[事件名称](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>参数

*event*\
事件数据。

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>返回值

此活动期间发生的 CPU 计时周期数。 CPU 滴答与常规计时周期不同。 仅当 CPU 执行活动中的代码时，才对 CPU 计时周期计数。 与活动关联的线程处于睡眠状态时，不会对 CPU 计时周期计数。

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>返回值

CPU 在此活动内执行代码的时间长度。 如果子活动在单独的线程上执行，则此值可能高于活动的持续时间。 该值以毫微秒为单位返回。

## <a name="data"></a>数据

```cpp
const void* Data() const;
```

### <a name="return-value"></a>返回值

指向此事件中包含的额外数据的指针。 有关如何解释此字段的详细信息，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="duration"></a>持续时间

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>返回值

活动的持续时间，以纳秒为单位。

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>返回值

标识事件类型的数字。 有关事件标识符的列表，请参阅[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>返回值

一个数字，用于唯一标识跟踪内的事件。 多次分析或 relogging 同一跟踪时，此值不会发生更改。 此值用于标识多个分析中的同一事件，或 relogging 在同一跟踪上传递的事件。

## <a name="event-name"></a>名

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>返回值

包含[EventId](#event-id)标识的事件类型名称的 ANSI 字符串。

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>返回值

宽字符串，其中包含[EventId](#event-id)标识的事件类型的名称。

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>返回值

与[CPUTicks](#cpu-ticks)相同，但不包括子活动中发生的 CPU 时间刻度。

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>返回值

与[CPUTime](#cpu-time)相同，不同之处在于子活动的 CPU 时间不包括在内。

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>返回值

活动的持续时间，以纳秒为单位，不包括子活动中所用的时间量。

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>返回值

此活动中发生的计时周期数，不包括子活动中发生的计时周期数。

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>返回值

与[WallClockTimeResponsibility](#wall-clock-time-responsibility)相同，但不包括子活动的时钟时间责任。

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>返回值

与[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)相同，但不包括子活动的时钟时间责任时间刻度。

## <a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>返回值

发生事件的进程的标识符。

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>返回值

发生事件的逻辑处理器的从零开始的索引。

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>返回值

活动开始时捕获的滴答值。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>返回值

活动停止时捕获的滴答值。

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>返回值

发生事件的线程的标识符。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

计算此事件的持续时间时，每秒要使用的计时周期数。

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>返回值

此活动的时钟时间责任（以纳秒为单位）。 有关时钟时间责任的具体工作方式的详细信息，请参阅[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)。

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>返回值

表示此活动对总时钟时间的贡献的滴答计数。 时钟周期时间责任周期不同于常规时钟周期。 时钟周期时间责任刻度考虑活动之间的并行度。 两个并行活动的持续时间可能为50，并且具有相同的开始时间和停止时间。 在这种情况下，这两种情况均分配有25个时钟周期的时钟时间。

::: moniker-end
