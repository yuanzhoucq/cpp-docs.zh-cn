---
title: ANALYSIS_CALLBACKS 结构
description: C++生成见解 SDK ANALYSIS_CALLBACKS 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334144"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

当初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)对象时，将使用 `ANALYSIS_CALLBACKS` 结构。 它指定在分析或 relogging Windows 事件跟踪（ETW）跟踪期间要调用的函数。

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `OnStartActivity` | 调用以处理活动开始事件。 |
| `OnStopActivity` | 调用以处理活动停止事件。 |
| `OnSimpleEvent` | 调用以处理简单事件。 |
| `OnTraceInfo` | 对于分析会话，在每个分析过程开始时调用。 对于 relogging 会话，在每个分析过程开始时调用，并在 relogging pass 开始时再次调用。 仅在调用 OnBeginAnalysisPass 之后，才会调用此函数。 |
| `OnBeginAnalysis` | 对于分析会话，在任何分析传递开始之前调用。 对于 relogging 会话，在分析阶段开始之前称为两次：一次是宣布开始 relogging 会话，然后再宣布分析阶段开始。 |
| `OnEndAnalysis` | 对于分析会话，在所有分析通过结束后调用此函数。 对于 relogging 会话，在分析阶段的所有分析通过结束时，将调用此函数。 然后，在 relogging pass 结束后再次调用它。 |
| `OnBeginAnalysisPass` | 在处理任何事件之前开始分析 pass 或 relogging pass 时调用。 |
| `OnEndAnalysisPass` | 在处理完所有事件之后，在结束分析过程或 relogging 通过时调用。 |

## <a name="remarks"></a>备注

Relogging 会话的分析阶段被视为 relogging 会话的一部分，并且可能包含多个分析传递。 出于此原因，在 relogging 会话开始时，在行中调用了两次 `OnBeginAnalysis`。 `OnEndAnalysis` 在分析阶段结束时调用，在开始 relogging 阶段之前，在 relogging 阶段结束后再次调用。 Relogging 阶段始终包含单个 relogging pass。

分析器可以作为 relogging 会话的分析和 relogging 阶段的一部分。 这些分析器可以通过跟踪 OnBeginAnalysis 和 `OnEndAnalysis` 调用对，来确定当前正在进行的阶段。 没有任何 `OnEndAnalysis` 调用的两个 `OnBeginAnalysis` 调用意味着分析阶段正在进行。 两次 `OnBeginAnalysis` 调用和一个 `OnEndAnalysis` 调用表示 relogging 阶段正在进行。 两个 OnBeginAnalysis 和两个 `OnEndAnalysis` 调用都表示两个阶段都已结束。

`ANALYSIS_CALLBACKS` 结构的所有成员都必须指向有效的函数。 有关接受的函数签名的详细信息，请参阅[OnAnalysisEventFunc](on-analysis-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
