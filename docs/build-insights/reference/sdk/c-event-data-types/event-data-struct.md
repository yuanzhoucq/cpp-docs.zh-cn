---
title: EVENT_DATA 结构
description: C++生成见解 SDK EVENT_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422906"
---
# <a name="event_data-structure"></a>EVENT_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA` 结构描述从分析或 relogging 会话接收的事件。 这些会话通过调用分析、 [AnalyzeA](../functions/analyze-a.md)、 [AnalyzeW](../functions/analyze-w.md) [、重新](../functions/relog.md)[分析](../functions/analyze.md)、 [RelogA](../functions/relog-a.md)或[RelogW](../functions/relog-w.md)函数启动。

## <a name="syntax"></a>语法

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `EventId` | 标识事件的数字。 有关事件标识符的列表，请参阅[EVENT_ID](event-id-enum.md)。 |
| `EventInstanceId` | 一个数字，用于唯一标识跟踪内的当前事件。 多次分析或 relogging 同一跟踪时，此值不会发生更改。 使用此字段来标识多个分析或 relogging 中的同一事件通过同一跟踪。 |
| `TickFrequency` | 计算以计时周期度量的持续时间时，每秒要使用的计时周期数。 |
| `StartTimestamp` | 当事件为*活动*时，此字段设置为活动启动时捕获的滴答值。 如果此事件为*简单事件*，则此字段设置为事件发生时捕获的滴答值。 |
| `StopTimestamp` | 当事件为*活动*时，此字段设置为活动停止时捕获的滴答值。 如果尚未收到此活动的停止事件，则此字段设置为零。 如果此事件为*简单事件*，则此字段设置为零。 |
| `ExclusiveDurationTicks` | 如果此事件为*活动*，则此字段设置为在此活动中直接发生的计时周期数。 子活动中发生的计时周期数被排除。 对于*简单事件*，此字段设置为零。 |
| `CPUTicks` | 如果此事件为*活动*，则此字段设置为在此活动期间发生的 CPU 计时周期数。 CPU 滴答与常规计时周期不同。 仅当 CPU 执行活动中的代码时，才对 CPU 计时周期计数。 与活动关联的线程处于睡眠状态时，不会对 CPU 计时周期计数。 对于*简单事件*，此字段设置为零。 |
| `ExclusiveCPUTicks` | 此字段与 `CPUTicks`的含义相同，不同之处在于它不包括子活动中发生的 CPU 时间刻度。 对于*简单事件*，此字段设置为零。 |
| `WallClockTimeResponsibilityTicks` | 如果此事件为*活动*，则此字段设置为表示此活动对总时钟时间的贡献的滴答计数。 时钟周期时间责任周期不同于常规时钟周期。 时钟周期时间责任刻度考虑活动之间的并行度。 例如，两个并行活动的持续时间可能为50，并且具有相同的开始时间和停止时间。 在这种情况下，将为这两个时钟周期分配时钟周期的时间。 对于*简单事件*，此字段设置为零。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此字段与 `WallClockTimeResponsibilityTicks`的含义相同，不同之处在于它不包含子级活动的时钟时间责任刻度。 对于*简单事件*，此字段设置为零。 |
| `Data` | 指向存储在事件中的其他数据。 指向的数据类型不同，具体取决于 `EventId` 字段。 |
| `ProcessId` | 发生事件的进程的标识符。 |
| `ThreadId` | 发生事件的线程的标识符。 |
| `ProcessorIndex` | 事件发生时的零索引 CPU 号。 |
| `EventName` | 包含由 `EventId`标识的实体名称的 ANSI 字符串。 |
| `EventWideName` | 宽字符串，其中包含由 `EventId`标识的实体的名称。 |

## <a name="remarks"></a>备注

`EVENT_DATA` 中的许多字段都包含滴答计数。 C++Build Insights 使用窗口的性能计数器作为刻度的源。 滴答计数必须与 "`TickFrequency`" 字段一起使用，以将其转换为适当的时间单位，如秒。 请参阅下面的示例以执行此转换。 `EVENT_DATA` 不包含活动的常规滴答计数字段。 若要获取此值，请从 `StopTimestamp`中减去 `StartTimestamp`。 `EVENT_DATA` 是一种结构，由 C API 用户使用。 对于C++ API 用户，[事件](../cpp-event-data-types/event.md)等类将自动进行时间转换。

"`EVENT_DATA` `Data`" 字段的值取决于其 `EventId` 字段的值。 下表描述了 `Data` 的值。 下表中可能缺少某些实体标识符。 在这种情况下，"`Data`" 字段设置为 `nullptr` 或零。

| `EventId` 值 | 指向的类型 `Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>刻度转换示例

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
