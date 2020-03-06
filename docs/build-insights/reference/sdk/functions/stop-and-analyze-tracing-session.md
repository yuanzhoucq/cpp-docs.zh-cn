---
title: StopAndAnalyzeTracingSession
description: C++ BUILD Insights SDK StopAndAnalyzeTracingSession 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b1c605bb63ac093f90128a03c37b186226130912
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334216"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndAnalyzeTracingSession` 函数将停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，将使用临时文件作为输入立即开始分析会话。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>参数

*sessionName*\
要停止的跟踪会话的名称。 使用与传递到[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)的会话相同的会话名称。

*numberOfAnalysisPasses*\
要在跟踪上运行的分析传递的数目。 跟踪在每个分析传递后通过提供的分析器组传递。

*统计信息*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 在返回之前，`StopAndAnalyzeTracingSession` 将跟踪集合统计信息写入此对象中。

*analyzerGroup*\
用于分析的分析器组。 调用[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)创建分析器组。 如果要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获取的动态分析器组，请先将其地址传递到 `MakeStaticAnalyzerGroup`，然后将其封装在静态分析器组内。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
