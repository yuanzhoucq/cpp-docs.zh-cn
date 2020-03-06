---
title: TraceInfo 类
description: C++ BUILD Insights SDK TraceInfo 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334498"
---
# <a name="traceinfo-class"></a>TraceInfo 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TraceInfo` 类用于访问有关正在分析或 relogged 的跟踪的有用属性。

## <a name="syntax"></a>语法

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>备注

从 `StopTimestamp` 中减去 `StartTimestamp` 以获取整个跟踪期间所用的计时周期数。 使用 `TickFrequency` 将生成的值转换为时间单位。 有关将计时周期转换为 time 的示例，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

如果不想自行转换刻度，则 `TraceInfo` 类将提供一个成员函数，该函数返回以毫微秒为单位的跟踪持续时间。 使用标准C++ `chrono` 库将此值转换为其他时间单位。

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

[TraceInfo](#trace-info)

### <a name="functions"></a>函数

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>持续时间

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>返回值

活动的持续时间，以纳秒为单位。

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>返回值

收集跟踪的计算机上的逻辑处理器的数目。

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>返回值

开始跟踪时捕获的滴答值。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>返回值

跟踪停止时捕获的滴答值。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

计算以计时周期度量的持续时间时，每秒要使用的计时周期数。

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>参数

*数据*\
包含有关跟踪的信息的数据。

::: moniker-end
