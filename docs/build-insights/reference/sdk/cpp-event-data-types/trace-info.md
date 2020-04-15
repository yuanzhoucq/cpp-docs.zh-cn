---
title: 跟踪信息类
description: C++生成见解 SDK 跟踪信息类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324176"
---
# <a name="traceinfo-class"></a>跟踪信息类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

类`TraceInfo`用于访问有关要分析或重新记录的跟踪的有用属性。

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

`StartTimestamp`从中`StopTimestamp`减去 以获取整个跟踪期间经过的刻度数。 用于`TickFrequency`将生成的值转换为时间单位。 有关将刻度转换为时间的示例，请参阅[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

如果不想自己转换刻度，`TraceInfo`类提供一个成员函数，以纳秒为单位返回跟踪持续时间。 使用标准C++`chrono`库将此值转换为其他时间单位。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

[跟踪信息](#trace-info)

### <a name="functions"></a>函数

[持续时间](#duration)
[逻辑处理器计数](#logical-processor-count)
[开始时间戳](#start-timestamp)
[停止时间戳](#stop-timestamp)
[刻度频率](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>时间

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>返回值

活动持续时间（以纳秒为单位）。

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>逻辑处理器计数

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>返回值

收集跟踪的计算机上的逻辑处理器数。

## <a name="starttimestamp"></a><a name="start-timestamp"></a>开始时间戳

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>返回值

在开始跟踪时捕获的刻度值。

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>停止时间戳

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>返回值

在停止跟踪时捕获的刻度值。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答频率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>返回值

评估以刻度为单位测量的持续时间时每秒使用的刻度数。

## <a name="traceinfo"></a><a name="trace-info"></a>跟踪信息

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>参数

*数据*\
包含有关跟踪的信息的数据。

::: moniker-end
