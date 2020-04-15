---
title: EVENT_DATA结构
description: C++生成见解 SDK EVENT_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325597"
---
# <a name="event_data-structure"></a>EVENT_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`EVENT_DATA`描述从分析或重新记录会话接收的事件。 这些会话通过调用[分析](../functions/analyze.md)、[分析A、](../functions/analyze-a.md)[分析W、](../functions/analyze-w.md)[重新日志](../functions/relog.md)、[重新登录](../functions/relog-a.md)或[RelogW](../functions/relog-w.md)函数开始。

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
| `EventInstanceId` | 唯一标识跟踪内当前事件的数字。 多次分析或重新记录同一跟踪时，此值不会更改。 使用此字段可识别多个分析或通过同一跟踪的重新记录传递中的同一事件。 |
| `TickFrequency` | 评估以刻度为单位测量的持续时间时每秒使用的刻度数。 |
| `StartTimestamp` | 当事件为*活动*时，此字段设置为活动启动时捕获的刻度值。 如果此事件是*简单事件*，则此字段设置为事件发生时捕获的刻度值。 |
| `StopTimestamp` | 当事件为*活动*时，此字段设置为活动停止时捕获的刻度值。 如果尚未收到此活动的停止事件，则此字段设置为零。 如果此事件是*简单事件*，则此字段设置为零。 |
| `ExclusiveDurationTicks` | 如果此事件是*活动*，则此字段设置为此活动中直接发生的刻度数。 不包括子活动中发生的刻度数。 此字段设置为 *"简单事件*"为零。 |
| `CPUTicks` | 如果此事件是*活动*，则此字段设置为在此活动期间发生的 CPU 刻度数。 CPU 刻度不同于常规刻度。 仅当 CPU 在活动中执行代码时，才会计算 CPU 刻度。 当与活动关联的线程处于睡眠状态时，不会计算 CPU 刻度。 此字段设置为 *"简单事件*"为零。 |
| `ExclusiveCPUTicks` | 此字段的含义与`CPUTicks`相同，只不过它不包括子活动中发生的 CPU 刻度。 此字段设置为 *"简单事件*"为零。 |
| `WallClockTimeResponsibilityTicks` | 如果此事件是*活动*，则此字段设置为表示此活动对总挂钟时间的贡献的刻度计数。 挂钟时间责任刻度不同于常规刻度。 钟点时间责任滴答声考虑了活动之间的并行性。 例如，两个并行活动的持续时间可能为 50 个刻度，并且相同的开始和停止时间相同。 在这种情况下，两者将被分配 25 个刻度的挂钟时间责任。 此字段设置为 *"简单事件*"为零。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此字段的含义与`WallClockTimeResponsibilityTicks`相同，只是不包括儿童活动的挂钟时间责任刻度。 此字段设置为 *"简单事件*"为零。 |
| `Data` | 指向事件中存储的其他数据。 指向的数据类型因字段而异`EventId`。 |
| `ProcessId` | 事件发生的进程的标识符。 |
| `ThreadId` | 发生事件的线程的标识符。 |
| `ProcessorIndex` | 事件发生的零索引 CPU 编号。 |
| `EventName` | 包含 标识`EventId`的实体名称的 ANSI 字符串。 |
| `EventWideName` | 包含 标识`EventId`的实体名称的宽字符串。 |

## <a name="remarks"></a>备注

中的`EVENT_DATA`许多字段包含刻度计数。 C++生成见解使用窗口的性能计数器作为报价源。 必须将刻度计数与`TickFrequency`字段一起使用，将其转换为适当的时间单位，如秒。 有关执行此转换，请参阅下面的示例。 `EVENT_DATA`不包含活动常规刻度计数的字段。 要获取此值，从`StartTimestamp``StopTimestamp`中减去 。 `EVENT_DATA`是一个结构，供 C API 用户使用。 对于C++ API 用户，像[事件](../cpp-event-data-types/event.md)这样的类会自动进行时间转换。

字段的值`EVENT_DATA`取决于其`EventId`字段的值。 `Data` 下表描述了`Data`的值。 下表中可能缺少某些实体标识符。 在这种情况下，字段`Data`设置为`nullptr`或 零。

| `EventId` 值 | 类型指向`Data` |
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
