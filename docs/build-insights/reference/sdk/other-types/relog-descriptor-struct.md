---
title: RELOG_DESCRIPTOR 结构
description: C++生成见解 SDK RELOG_DESCRIPTOR 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333970"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_DESCRIPTOR` 结构与[RelogA](../functions/relog-a.md)和[RelogW](../functions/relog-w.md)函数结合使用。 它介绍了 Windows 事件跟踪（ETW）跟踪的 relogged。

## <a name="syntax"></a>语法

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | 在 relogging 会话的分析阶段，应在 ETW 跟踪上完成的分析传递的数量。 |
| `AnalysisCallbacks` | 一个[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)对象，该对象指定在 relogging 会话分析阶段要调用的函数。 |
| `RelogCallbacks` | 一个[RELOG_CALLBACKS](relog-callbacks-struct.md)对象，该对象指定在 relogging 会话的 relogging 阶段要调用的函数。 |
| `SystemEventsRetentionFlags` | 一个[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)位掩码，它指定要在 relogged 跟踪中保留的系统 ETW 事件。 |
| `AnalysisContext` | 用户提供的上下文，作为参数传递给在 `AnalysisCallbacks` 中指定的所有回调函数 |
| `RelogContext` | 用户提供的上下文，作为参数传递给在 `RelogCallbacks` 中指定的所有回调函数 |

## <a name="remarks"></a>备注

Relogging 会话期间 ETW 事件的 relogging 由用户通过 `RelogCallbacks`中指定的回调函数控制。 但是，系统 ETW 事件（例如 CPU 示例）不会转发到这些回调函数。 使用 "`SystemEventsRetentionFlags`" 字段可以控制系统 ETW 事件的 relogging。

`AnalysisCallbacks` 和 `RelogCallbacks` 结构仅接受指向非成员函数的指针。 可以通过将其设置为对象指针来绕过此限制。 此对象指针将作为参数传递给所有非成员回调函数。 使用此指针从非成员回调函数内调用成员函数。

Relogging 会话的分析阶段始终在 relogging 阶段之前执行。

::: moniker-end
