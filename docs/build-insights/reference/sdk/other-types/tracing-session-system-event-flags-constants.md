---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS 常量
description: C++生成见解 SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS 常数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333994"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS 常量

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_SYSTEM_EVENT_FLAGS` 常量用于描述在跟踪期间要收集的系统事件。 使用它们初始化[TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)结构的 `SystemEventFlags` 字段。

## <a name="syntax"></a>语法

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Members

| 名称 | 此标志打开的事件 |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | 即使未显式指定， C++生成见解 SDK 也会默认激活此标志。 它使C++生成见解所需的基本系统事件能够正常运行。 此标志启用的事件提供有关进程、线程和图像加载的信息。 不能禁用这些事件。 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 示例 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | 此标志会启用所有系统事件。 |

::: moniker-end
