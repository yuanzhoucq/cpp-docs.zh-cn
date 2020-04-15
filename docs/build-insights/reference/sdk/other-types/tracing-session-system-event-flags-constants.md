---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS常量
description: C++生成见解 SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS常量引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323274"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS常量

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

常`TRACING_SESSION_SYSTEM_EVENT_FLAGS`量用于描述在跟踪期间要收集的系统事件。 使用它们初始化[TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)结构的`SystemEventFlags`字段。

## <a name="syntax"></a>语法

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成员

| 名称 | 此标志打开的事件 |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | 默认情况下，C++生成见解 SDK 会激活此标志，即使未显式指定也是如此。 它使C++生成见解所需的基本系统事件能够正常运行。 此标志启用的事件提供有关进程、线程和图像加载的信息。 无法禁用这些事件。 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 样本 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | 此标志将打开所有系统事件。 |

::: moniker-end
