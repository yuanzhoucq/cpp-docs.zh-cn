---
title: StopTracingSessionA
description: C++ BUILD Insights SDK StopTracingSessionA 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 12f0c7a9665c47f36fb5e88d799673918017bb98
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334192"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StopTracingSessionA` 函数将停止正在进行的跟踪会话并生成原始跟踪文件。 可以将原始跟踪文件传递到 "[分析](analyze.md)"、" [AnalzeA](analyze-a.md)" 和 " [AnalyzeW](analyze-w.md) " 函数以启动分析会话。 还可以将原始跟踪文件传递给重新运行、 [RelogA](relog-a.md)和[RelogW](relog-w.md) [函数，以](relog.md)启动 relogging 会话。 调用 `StopTracingSessionA` 的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>参数

*sessionName*\
要停止的跟踪会话的名称。 使用与传递到[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)的会话相同的会话名称。

*outputLogFile*\
应在其中保存原始跟踪的最终输出日志文件的路径。

*统计信息*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 在返回之前，`StopTracingSessionA` 将跟踪集合统计信息写入此对象中。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
