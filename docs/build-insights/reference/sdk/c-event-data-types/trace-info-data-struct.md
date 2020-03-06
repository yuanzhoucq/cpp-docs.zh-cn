---
title: TRACE_INFO_DATA 结构
description: C++生成见解 SDK TRACE_INFO_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335050"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA` 结构描述正在分析或 relogged 的跟踪。

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `LogicalProcessorCount` | 收集跟踪的计算机上的逻辑处理器的数目。 |
| `TickFrequency` | 计算以计时周期度量的持续时间时，每秒要使用的计时周期数。 |
| `StartTimestamp` | 此字段设置为启动跟踪时捕获的滴答值。 |
| `StopTimestamp` | 此字段设置为在跟踪停止时捕获的滴答值。 |

## <a name="remarks"></a>备注

从 `StopTimestamp` 中减去 `StartTimestamp` 以获取整个跟踪期间所用的计时周期数。 使用 `TickFrequency` 将生成的值转换为时间单位。 有关将计时周期转换为时间单位的示例，请参阅[EVENT_DATA](event-data-struct.md)。

::: moniker-end
