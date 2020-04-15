---
title: 停止和重新登录跟踪会话A
description: C++生成见解 SDK 停止和重新log跟踪会话A函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa70d50ba79a7829adb985ab4d884b5773b5d40f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323672"
---
# <a name="stopandrelogtracingsessiona"></a>停止和重新登录跟踪会话A

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`StopAndRelogTracingSessionA`函数停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，使用临时文件作为输入立即启动重新日志记录会话。 重新日志记录会话生成的最终重新记录跟踪将保存在调用方指定的文件中。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>参数

*会话名称*\
要停止的跟踪会话的名称。 使用与传递给["开始跟踪会话](start-tracing-session.md)"、[开始跟踪会话A](start-tracing-session-a.md)或["开始跟踪会话W"](start-tracing-session-w.md)的会话名称相同的会话名称。

*输出日志文件*\
用于写入重新记录会话生成的重新记录跟踪的文件。

*统计*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 `StopAndRelogTracingSessionA`返回之前，在此对象中写入跟踪集合统计信息。

*分析描述符*\
指向[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)对象的指针。 使用此对象可以配置 由`StopAndRelogTracingSessionA`启动的重新日志记录会话。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
