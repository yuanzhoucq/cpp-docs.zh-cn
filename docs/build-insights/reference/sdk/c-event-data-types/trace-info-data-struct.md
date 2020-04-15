---
title: TRACE_INFO_DATA结构
description: C++生成见解 SDK TRACE_INFO_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325282"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`TRACE_INFO_DATA`描述要分析或重新记录的跟踪。

## <a name="syntax"></a>语法

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `LogicalProcessorCount` | 收集跟踪的计算机上的逻辑处理器数。 |
| `TickFrequency` | 评估以刻度为单位测量的持续时间时每秒使用的刻度数。 |
| `StartTimestamp` | 此字段设置为在开始跟踪时捕获的刻度值。 |
| `StopTimestamp` | 此字段设置为停止跟踪时捕获的刻度值。 |

## <a name="remarks"></a>备注

从`StartTimestamp`中`StopTimestamp`减去以获取整个跟踪期间经过的刻度数。 用于`TickFrequency`将生成的值转换为时间单位。 有关将刻度转换为时间单位的示例，请参阅[EVENT_DATA](event-data-struct.md)。

::: moniker-end
