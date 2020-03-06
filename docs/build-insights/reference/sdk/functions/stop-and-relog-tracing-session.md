---
title: StopAndRelogTracingSession
description: C++ BUILD Insights SDK StopAndRelogTracingSession 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334198"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSession` 函数将停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，relogging 会话立即开始使用临时文件作为输入。 Relogging 会话生成的最终 relogged 跟踪保存在由调用方指定的文件中。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>参数

*sessionName*\
要停止的跟踪会话的名称。 使用与传递到[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)的会话相同的会话名称。

*outputLogFile*\
要在其中写入 relogging 会话生成的 relogged 跟踪的文件。

*统计信息*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 在返回之前，`StopAndRelogTracingSession` 将跟踪集合统计信息写入此对象中。

*numberOfAnalysisPasses*\
要在跟踪上运行的分析传递的数目。 跟踪在每个分析传递后通过提供的分析器组传递。

*systemEventsRetentionFlags*\
一个[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)位掩码，它指定要在 relogged 跟踪中保留的系统 ETW 事件。

*analyzerGroup*\
用于 relogging 会话分析阶段的分析器组。 调用[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)创建分析器组。 如果要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获取的动态分析器组，请先将其地址传递到 `MakeStaticAnalyzerGroup`，然后将其封装在静态分析器组内。

*reloggerGroup*\
Relogger 组将事件 relogs 到*outputLogFile*中指定的跟踪文件中。 调用[MakeStaticReloggerGroup](make-static-relogger-group.md)创建 relogger 组。 如果要使用从[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)获取的动态 relogger 组，请先将其地址传递到 `MakeStaticReloggerGroup`，并将其封装在静态 relogger 组内。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

### <a name="remarks"></a>备注

输入跟踪通过分析器组*numberOfAnalysisPasses*时间传递。 Relogging pass 没有类似的选项。 所有分析传递完成后，只会在 relogger 组通过传递一次跟踪。

系统事件的 relogging （如 relogger 类中的 CPU 示例）不受支持。 使用*systemEventsRetentionFlags*参数来决定要在输出跟踪中保留的系统事件。

::: moniker-end
