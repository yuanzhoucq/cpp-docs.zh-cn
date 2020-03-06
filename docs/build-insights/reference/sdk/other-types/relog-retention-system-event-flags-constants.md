---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常量
description: C++生成见解 SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333964"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常量

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_RETENTION_SYSTEM_EVENT_FLAGS` 常量用于描述要保存在 relogged 跟踪中的系统事件。 使用它们初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)结构的 `SystemEventsRetentionFlags` 字段。

## <a name="syntax"></a>语法

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | 在 relogged 跟踪中保留 CPU 示例系统事件。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 将所有系统事件都保存在 relogged 跟踪中。 |

## <a name="remarks"></a>备注

::: moniker-end
