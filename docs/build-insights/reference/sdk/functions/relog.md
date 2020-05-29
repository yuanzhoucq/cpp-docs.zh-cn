---
title: Relog
description: C++生成见解 SDK 重新日志函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323782"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Relog`函数用于从 Windows （ETW） 跟踪的事件跟踪读取 MSVC 事件，并将它们写入新的修改后的 ETW 跟踪中。

## <a name="syntax"></a>语法

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>参数

*TAnalyzer组成员*\
始终推导此参数。

*TReloggerGroup成员*\
始终推导此参数。

*输入日志文件*\
要从中读取事件的输入 ETW 跟踪。

*输出日志文件*\
写入新事件的文件。

*分析通道数*\
在输入跟踪上运行的分析数。 跟踪通过每个分析传递一次通过提供的分析器组。

*系统事件保留标志*\
指定要在重新记录的跟踪中保留哪些系统 ETW 事件的位掩码。 有关详细信息，请参阅[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)。

*分析仪组*\
用于重新记录会话分析阶段的分析器组。 调用[MakeStatic 分析器组](make-static-analyzer-group.md)以创建分析器组。 要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获得的动态分析器组，首先通过将地址传递给`MakeStaticAnalyzerGroup`将其封装在静态分析器组中。

*重新记录组*\
重新记录组，将事件重新记录到*输出日志文件中*指定的跟踪文件中。 调用[使静态重新记录组](make-static-relogger-group.md)创建重新记录组。 要使用从[MakeDynamic ReloggerGroup](make-dynamic-relogger-group.md)获得的动态重新记录组，首先通过将其地址传递给`MakeStaticReloggerGroup`将其封装在静态重新记录组中。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

### <a name="remark"></a>备注

输入跟踪通过分析器组*编号分析传递次数分析。* 没有类似的重新记录通行证选项。 跟踪在完成所有分析过程后，仅通过一次重新记录组槽。

不支持重新记录类中的系统事件（如 CPU 样本）的重新记录。 使用*系统事件保留标志*参数决定要在输出跟踪中保留哪些系统事件。

::: moniker-end
