---
title: EVENT_DATA 结构
description: C++ Build Insights SDK EVENT_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ccba320a8bb9279b874fae2484c71af913253148
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229917"
---
# <a name="event_data-structure"></a>EVENT_DATA 结构

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA` 结构描述了从分析或重新记录会话收到的事件。 这些会话是通过调用 [Analyze](../functions/analyze.md)、[AnalyzeA](../functions/analyze-a.md)、[AnalyzeW](../functions/analyze-w.md)、[Relog](../functions/relog.md)、[RelogA](../functions/relog-a.md) 或 [RelogW](../functions/relog-w.md) 函数启动的。

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
| `EventId` | 标识事件的数字。 有关事件标识符的列表，请参阅 [EVENT_ID](event-id-enum.md)。 |
| `EventInstanceId` | 在跟踪中唯一标识当前事件的数字。 当多次分析或重新记录相同的跟踪时，此值不会改变。 使用此字段来在多个通过同一跟踪的分析或重新记录过程中标识同一个事件。 |
| `TickFrequency` | 在计算持续时间（以“滴答”为计量单位）时使用的每秒滴答数。 |
| `StartTimestamp` | 如果这一事件是“活动”，则此字段设置为在活动启动时捕获的滴答值。 如果这一事件是“简单事件”，则此字段设置为在事件发生时捕获的滴答值。 |
| `StopTimestamp` | 如果这一事件是“活动”，则此字段设置为在活动停止时捕获的滴答值。 如果还没有收到这一活动的停止事件，则此字段设置为 0。 如果这一事件是“简单事件”，则此字段设置为 0。 |
| `ExclusiveDurationTicks` | 如果这一事件是“活动”，则此字段设置为这一活动中直接发生的滴答数。 子活动中发生的滴答数被排除在外。 对于“简单事件”，此字段设置为 0。 |
| `CPUTicks` | 如果这一事件是“活动”，则此字段设置为在这一活动期间发生的 CPU 滴答数。 CPU 滴答不同于常规滴答。 只有当 CPU 在活动中执行代码时，才对 CPU 滴答进行计数。 当与活动关联的线程处于睡眠状态时，不会对 CPU 滴答进行计数。 对于“简单事件”，此字段设置为 0。 |
| `ExclusiveCPUTicks` | 此字段与 `CPUTicks` 的含义相同，不同之处在于此字段不包括子活动中发生的 CPU 滴答数。 对于“简单事件”，此字段设置为 0。 |
| `WallClockTimeResponsibilityTicks` | 如果这一事件是“活动”，则此字段设置为表示这一活动对总时钟时间的贡献的滴答计数。 时钟时间责任滴答不同于常规滴答。 时钟时间责任滴答考虑了活动之间的并行度。 例如，两个并行活动的持续时间可能为 50 个滴答，并且开始时间和停止时间相同。 在此示例中，两个活动都会分配有 25 个时钟时间责任滴答。 对于“简单事件”，此字段设置为 0。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此字段与 `WallClockTimeResponsibilityTicks` 的含义相同，不同之处在于此字段不包括子活动中发生的时钟时间责任滴答数。 对于“简单事件”，此字段设置为 0。 |
| `Data` | 指向存储在事件中的其他数据。 所指向的数据的类型因 `EventId` 字段而异。 |
| `ProcessId` | 发生了事件的进程的标识符。 |
| `ThreadId` | 发生了事件的线程的标识符。 |
| `ProcessorIndex` | 发生了事件的 CPU 编号（从零开始编制索引）。 |
| `EventName` | 包含由 `EventId` 标识的实体的名称的 ANSI 字符串。 |
| `EventWideName` | 包含由 `EventId` 标识的实体的名称的宽字符串。 |

## <a name="remarks"></a>备注

`EVENT_DATA` 中的许多字段都包含滴答计数。 C++ Build Insights 使用 Windows 的性能计数器作为滴答源。 滴答计数必须与 `TickFrequency` 字段一起使用，以将其转换为适当的时间单位（如秒）。 若要了解如何执行此转换，请参阅下面的示例。 `EVENT_DATA` 不包含用于活动的常规滴答计数的字段。 若要获取此值，请用 `StopTimestamp` 减去 `StartTimestamp`。 `EVENT_DATA` 是供 C API 用户使用的结构。 对于 C++ API 用户，像 [Event](../cpp-event-data-types/event.md) 这样的类会自动进行时间转换。

`EVENT_DATA` `Data` 字段的值取决于其 `EventId` 字段的值。 下表描述了 `Data` 的值。 下表中可能缺少一些实体标识符。 在此示例中，`Data` 字段设置为 `nullptr` 或 0。

| `EventId` 值 | `Data` 所指向的类型 |
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

## <a name="tick-conversion-example"></a>滴答转换示例

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
