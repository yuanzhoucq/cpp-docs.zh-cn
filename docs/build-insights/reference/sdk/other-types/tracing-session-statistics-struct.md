---
title: TRACING_SESSION_STATISTICS 结构
description: C++生成见解 SDK TRACING_SESSION_OPTIONS 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333862"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS` 结构描述了所收集的跟踪的统计信息。 在停止跟踪会话时设置其字段。

## <a name="syntax"></a>语法

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `MSVCEventsLost` | 已删除的 MSVC 事件的数目。 |
| `MSVCBuffersLost` | 已丢弃的 MSVC 事件缓冲区数。 |
| `SystemEventsLost` | 已删除的系统事件数。 |
| `SystemBuffersLost` | 已删除的系统事件缓冲区数。 |

## <a name="remarks"></a>备注

在调用以下函数时，将填充此结构：

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
