---
title: TRACING_SESSION_OPTIONS 结构
description: C++生成见解 SDK TRACING_SESSION_OPTIONS 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333868"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

当初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)结构时，将使用 `TRACING_SESSION_OPTIONS` 结构。 它描述在跟踪的收集过程中要捕获的事件。

## <a name="syntax"></a>语法

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `SystemEventFlags` | 一个位掩码，描述要捕获的系统事件。 有关详细信息，请参阅[TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md)。 |
| `MsvcEventFlags` | 一个位掩码，用于描述要捕获的 MSVC 事件。 有关详细信息，请参阅[TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md)。 |

::: moniker-end
