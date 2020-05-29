---
title: ANALYSIS_CALLBACKS结构
description: C++生成见解 SDK ANALYSIS_CALLBACKS结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323512"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

在`ANALYSIS_CALLBACKS`初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)对象时，将使用该结构。 它指定在分析或重新记录 Windows （ETW） 跟踪的事件跟踪期间调用哪些函数。

## <a name="syntax"></a>语法

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `OnStartActivity` | 调用以处理活动开始事件。 |
| `OnStopActivity` | 调用以处理活动停止事件。 |
| `OnSimpleEvent` | 调用 以处理简单事件。 |
| `OnTraceInfo` | 对于分析会话，在每个分析传递开始时调用。 对于重新记录会话，在每次分析传递开始时调用，在重新记录传递开始时再次调用。 仅当调用 OnBegin 分析通点后，才调用此功能。 |
| `OnBeginAnalysis` | 对于分析会话，在开始任何分析传递之前调用。 对于重新记录会话，在分析阶段开始之前调用两次：一次宣布重新记录会话的开始，再一次宣布分析阶段的开始。 |
| `OnEndAnalysis` | 对于分析会话，在结束所有分析过程后调用此函数。 对于重新记录会话，当分析阶段的所有分析通过都结束时，将调用此函数。 然后，在重新日志记录通过结束后再次调用它。 |
| `OnBeginAnalysisPass` | 在处理任何事件之前，在开始分析传递或重新日志记录传递时调用。 |
| `OnEndAnalysisPass` | 在处理所有事件后结束分析传递或重新日志记录传递时调用。 |

## <a name="remarks"></a>备注

重新记录会话的分析阶段被视为重新记录会话的一部分，可能包含多个分析过程。 因此，`OnBeginAnalysis`在重新记录会话开始时连续调用两次。 `OnEndAnalysis`在分析阶段结束时调用，在开始重新记录阶段之前，在重新记录阶段结束时再次调用。 重新日志记录阶段始终包含单个重新日志记录通道。

分析器有可能成为重新记录会话分析和重新记录阶段的一部分。 这些分析器可以通过跟踪 OnBegin 分析和`OnEndAnalysis`呼叫对来确定当前正在进行的阶段。 两`OnBeginAnalysis`次没有`OnEndAnalysis`调用的呼叫意味着分析阶段正在进行。 两`OnBeginAnalysis`个呼叫和`OnEndAnalysis`一个呼叫意味着重新记录阶段正在进行中。 两个 OnBegin`OnEndAnalysis`分析和两个呼叫意味着两个阶段都结束了。

`ANALYSIS_CALLBACKS`结构的所有成员必须指向有效的函数。 有关接受的功能签名的详细信息，请参阅[OnAnalysisEventFunc、OnTraceInfoFunc](on-analysis-event-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。 [OnTraceInfoFunc](on-trace-info-func-typedef.md)

::: moniker-end
