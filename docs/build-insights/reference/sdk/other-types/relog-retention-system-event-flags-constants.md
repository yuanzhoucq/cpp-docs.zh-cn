---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量
description: C++生成见解 SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323473"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

常`RELOG_RETENTION_SYSTEM_EVENT_FLAGS`量用于描述要在重新记录的跟踪中保留哪些系统事件。 使用它们初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)结构的`SystemEventsRetentionFlags`字段。

## <a name="syntax"></a>语法

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | 将 CPU 示例系统事件保持在已记录的跟踪中。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 将所有系统事件保留在已记录的跟踪中。 |

## <a name="remarks"></a>备注

::: moniker-end
