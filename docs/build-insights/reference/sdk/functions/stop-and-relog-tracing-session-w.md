---
title: StopAndRelogTracingSessionW
description: C++ BUILD Insights SDK StopAndRelogTracingSessionW 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 021ea5986714fa3432ab6e2831c6069356f380d5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334204"
---
# <a name="stopandrelogtracingsessionw"></a>StopAndRelogTracingSessionW

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSessionW` 函数将停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，relogging 会话立即开始使用临时文件作为输入。 Relogging 会话生成的最终 relogged 跟踪保存在由调用方指定的文件中。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StopAndRelogTracingSessionW(
    const wchar_t*              sessionName,
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>参数

*sessionName*\
要停止的跟踪会话的名称。 使用与传递到[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)的会话相同的会话名称。

*outputLogFile*\
要在其中写入 relogging 会话生成的 relogged 跟踪的文件。

*统计信息*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 在返回之前，`StopAndRelogTracingSessionW` 将跟踪集合统计信息写入此对象中。

*analysisDescriptor*\
指向[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)对象的指针。 使用此对象配置 `StopAndRelogTracingSessionW`启动的 relogging 会话。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
