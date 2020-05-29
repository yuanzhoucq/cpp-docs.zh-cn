---
title: RELOG_DESCRIPTOR结构
description: C++生成见解 SDK RELOG_DESCRIPTOR结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328942"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`RELOG_DESCRIPTOR`结构与[RelogA](../functions/relog-a.md)和[RelogW](../functions/relog-w.md)函数一起使用。 它描述了如何重新记录 Windows （ETW） 跟踪的事件跟踪。

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

## <a name="members"></a>成员

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | 在重新记录会话的分析阶段，应在 ETW 跟踪上执行的分析通过数。 |
| `AnalysisCallbacks` | [指定](analysis-callbacks-struct.md)在重新记录会话分析阶段调用哪些函数ANALYSIS_CALLBACKS对象。 |
| `RelogCallbacks` | 指定[在](relog-callbacks-struct.md)重新记录会话的重新记录阶段调用哪些函数RELOG_CALLBACKS对象。 |
| `SystemEventsRetentionFlags` | 指定要在重新记录的跟踪中保留哪些系统 ETW 事件的[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)位掩码。 |
| `AnalysisContext` | 以参数传递给在 中指定的所有回调函数的用户提供的上下文`AnalysisCallbacks` |
| `RelogContext` | 以参数传递给在 中指定的所有回调函数的用户提供的上下文`RelogCallbacks` |

## <a name="remarks"></a>备注

在重新日志记录会话期间重新记录 ETW 事件由用户通过 中`RelogCallbacks`指定的回调功能进行控制。 但是，系统 ETW 事件（如 CPU 样本）不会转发到这些回调函数。 使用该`SystemEventsRetentionFlags`字段控制系统 ETW 事件的重新日志记录。

`AnalysisCallbacks`和`RelogCallbacks`结构仅接受指向非成员函数的指针。 通过将此限制设置为对象指针，可以绕过此限制。 此对象指针将作为参数传递给所有非成员回调函数。 使用此指针可以从非成员回调函数中调用成员函数。

重新记录会话的分析阶段始终在重新记录阶段之前执行。

::: moniker-end
