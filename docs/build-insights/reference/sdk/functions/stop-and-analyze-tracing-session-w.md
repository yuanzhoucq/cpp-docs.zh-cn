---
title: StopAndAnalyzeTracingSessionW
description: C++ BUILD Insights SDK StopAndAnalyzeTracingSessionW 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec36162efcd2bfcf17cb07a997a7ff170338d3d2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334264"
---
# <a name="stopandanalyzetracingsessionw"></a>StopAndAnalyzeTracingSessionW

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndAnalyzeTracingSessionW` 函数将停止正在进行的跟踪会话，并将生成的跟踪保存在临时文件中。 然后，将使用临时文件作为输入立即开始分析会话。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionW(
    const wchar_t*              sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>参数

*sessionName*\
要停止的跟踪会话的名称。 使用与传递到[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)的会话相同的会话名称。

*统计信息*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)对象的指针。 在返回之前，`StopAndAnalyzeTracingSessionW` 将跟踪集合统计信息写入此对象中。

*analysisDescriptor*\
指向[ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)对象的指针。 使用此对象配置 `StopAndAnalyzeTracingSessionW`启动的分析会话。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
