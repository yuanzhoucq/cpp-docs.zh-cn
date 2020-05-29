---
title: TRACING_SESSION_STATISTICS结构
description: C++构建见解 SDK TRACING_SESSION_OPTIONS结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323381"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`TRACING_SESSION_STATISTICS`结构描述收集的跟踪的统计信息。 停止跟踪会话时设置其字段。

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

## <a name="members"></a>成员

|  |  |
|--|--|
| `MSVCEventsLost` | 丢弃的 MSVC 事件数。 |
| `MSVCBuffersLost` | 丢弃的 MSVC 事件缓冲区数。 |
| `SystemEventsLost` | 丢弃的系统事件数。 |
| `SystemBuffersLost` | 丢弃的系统事件缓冲区数。 |

## <a name="remarks"></a>备注

调用以下函数时，将填充此结构：

- [停止跟踪会话](../functions/stop-tracing-session.md)
- [停止跟踪会话A](../functions/stop-tracing-session-a.md)
- [停止跟踪会话W](../functions/stop-tracing-session-w.md)
- [停止和分析跟踪会话](../functions/stop-and-analyze-tracing-session.md)
- [停止和分析跟踪会话A](../functions/stop-and-analyze-tracing-session-a.md)
- [停止和分析跟踪会话W](../functions/stop-and-analyze-tracing-session-w.md)
- [停止和重新记录跟踪会话](../functions/stop-and-relog-tracing-session.md)
- [停止和重新登录跟踪会话A](../functions/stop-and-relog-tracing-session-a.md)
- [停止和重新记录跟踪会话W](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
