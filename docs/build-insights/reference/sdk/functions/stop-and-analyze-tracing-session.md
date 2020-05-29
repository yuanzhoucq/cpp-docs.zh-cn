---
title: 停止和分析跟踪会话
description: C++生成见解 SDK 停止和分析跟踪会话函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c9bd4a092c22dfcdfb6d463b74207ec11ee6d64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323704"
---
# <a name="stopandanalyzetracingsession"></a>停止和分析跟踪会话

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`StopAndAnalyzeTracingSession`函数停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，使用临时文件作为输入立即启动分析会话。 调用此函数的可执行文件必须具有管理员权限。

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

*会话名称*\
要停止的跟踪会话的名称。 使用与传递给["开始跟踪会话](start-tracing-session.md)"、[开始跟踪会话A](start-tracing-session-a.md)或["开始跟踪会话W"](start-tracing-session-w.md)的会话名称相同的会话名称。

*分析通道数*\
要在跟踪上运行的分析数。 跟踪通过每个分析传递一次通过提供的分析器组。

*统计*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 `StopAndAnalyzeTracingSession`返回之前，在此对象中写入跟踪集合统计信息。

*分析仪组*\
用于分析的分析器组。 调用[MakeStatic 分析器组](make-static-analyzer-group.md)以创建分析器组。 如果要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获得的动态分析器组，首先通过将地址传递给`MakeStaticAnalyzerGroup`将其封装在静态分析器组中。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
