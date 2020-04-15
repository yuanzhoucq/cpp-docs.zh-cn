---
title: 停止和重新记录跟踪会话
description: C++生成见解 SDK 停止和重新记录跟踪会话函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323666"
---
# <a name="stopandrelogtracingsession"></a>停止和重新记录跟踪会话

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`StopAndRelogTracingSession`函数停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，使用临时文件作为输入立即启动重新日志记录会话。 重新日志记录会话生成的最终重新记录跟踪将保存在调用方指定的文件中。 调用此函数的可执行文件必须具有管理员权限。

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

*会话名称*\
要停止的跟踪会话的名称。 使用与传递给["开始跟踪会话](start-tracing-session.md)"、[开始跟踪会话A](start-tracing-session-a.md)或["开始跟踪会话W"](start-tracing-session-w.md)的会话名称相同的会话名称。

*输出日志文件*\
用于写入重新记录会话生成的重新记录跟踪的文件。

*统计*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 `StopAndRelogTracingSession`返回之前，在此对象中写入跟踪集合统计信息。

*分析通道数*\
要在跟踪上运行的分析数。 跟踪通过每个分析传递一次通过提供的分析器组。

*系统事件保留标志*\
指定要在重新记录的跟踪中保留哪些系统 ETW 事件的[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)位掩码。

*分析仪组*\
用于重新记录会话分析阶段的分析器组。 调用[MakeStatic 分析器组](make-static-analyzer-group.md)以创建分析器组。 如果要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获得的动态分析器组，首先通过将地址传递给`MakeStaticAnalyzerGroup`将其封装在静态分析器组中。

*重新记录组*\
重新记录组，将事件重新记录到*输出日志文件中*指定的跟踪文件中。 调用[使静态重新记录组](make-static-relogger-group.md)创建重新记录组。 如果你想使用从[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)获得的动态重新记录器组，首先通过将其地址传递给`MakeStaticReloggerGroup`将其封装在静态重新记录器组中。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

### <a name="remarks"></a>备注

输入跟踪通过分析器组*编号分析传递次数分析。* 没有类似的重新记录通行证选项。 跟踪在完成所有分析过程后，仅通过一次重新记录组槽。

不支持重新记录类中的系统事件（如 CPU 样本）的重新记录。 使用*系统事件保留标志*参数决定要在输出跟踪中保留哪些系统事件。

::: moniker-end
