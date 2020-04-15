---
title: 停止跟踪会话A
description: C++生成见解 SDK 停止跟踪会话A 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15560ecf4959ccda0d617c09d3645750210f331a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323492"
---
# <a name="stoptracingsessiona"></a>停止跟踪会话A

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`StopTracingSessionA`函数停止正在进行的跟踪会话并生成原始跟踪文件。 原始跟踪文件可以传递到[分析](analyze.md)、[分析](analyze-a.md)A和[分析W](analyze-w.md)函数以启动分析会话。 原始跟踪文件也可以传递到[Relog、RelogA](relog-a.md)和[RelogW](relog-w.md)函数以开始重新记录会话。 [Relog](relog.md) 调用的可执行`StopTracingSessionA`文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>参数

*会话名称*\
要停止的跟踪会话的名称。 使用与传递给["开始跟踪会话](start-tracing-session.md)"、[开始跟踪会话A](start-tracing-session-a.md)或["开始跟踪会话W"](start-tracing-session-w.md)的会话名称相同的会话名称。

*输出日志文件*\
应保存原始跟踪的最终输出日志文件的路径。

*统计*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 `StopTracingSessionA`返回之前，在此对象中写入跟踪集合统计信息。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
