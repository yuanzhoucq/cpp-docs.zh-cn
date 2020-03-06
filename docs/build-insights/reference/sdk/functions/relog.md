---
title: Relog
description: C++生成见解 SDK 重新生成函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334282"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Relog` 函数用于从 Windows 事件跟踪（ETW）跟踪读取 MSVC 事件，并将这些事件写入新的已修改 ETW 跟踪。

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

*TAnalyzerGroupMembers*\
始终推导此参数。

*TReloggerGroupMembers*\
始终推导此参数。

*inputLogFile*\
要从中读取事件的输入 ETW 跟踪。

*outputLogFile*\
要在其中写入新事件的文件。

*numberOfAnalysisPasses*\
要在输入跟踪上运行的分析传递的数量。 跟踪在每个分析传递后通过提供的分析器组传递。

*systemEventsRetentionFlags*\
一个位掩码，它指定要在 relogged 跟踪中保留的系统 ETW 事件。 有关详细信息，请参阅[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)。

*analyzerGroup*\
用于 relogging 会话分析阶段的分析器组。 调用[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)创建分析器组。 若要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获取的动态分析器组，请先将其地址传递到 `MakeStaticAnalyzerGroup`，然后将其封装在静态分析器组内。

*reloggerGroup*\
Relogger 组将事件 relogs 到*outputLogFile*中指定的跟踪文件中。 调用[MakeStaticReloggerGroup](make-static-relogger-group.md)创建 relogger 组。 若要使用从[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)获取的动态 relogger 组，请先将其地址传递到 `MakeStaticReloggerGroup`，并将其封装在静态 relogger 组内。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

### <a name="remark"></a>备注

输入跟踪通过分析器组*numberOfAnalysisPasses*时间传递。 Relogging pass 没有类似的选项。 所有分析传递完成后，只会在 relogger 组通过传递一次跟踪。

系统事件的 relogging （如 relogger 类中的 CPU 示例）不受支持。 使用*systemEventsRetentionFlags*参数来决定要在输出跟踪中保留的系统事件。

::: moniker-end
