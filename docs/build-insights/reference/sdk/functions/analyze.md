---
title: 分析
description: C++生成见解 SDK 分析函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334432"
---
# <a name="analyze"></a>分析

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Analyze` 函数用于分析在跟踪C++生成时从 MSVC 获取的 Windows 事件跟踪（ETW）跟踪。 ETW 跟踪中的事件按顺序转发给调用方提供的分析器组。 此函数支持多通路分析，允许在一行中多次将事件流转发到分析器组。

## <a name="syntax"></a>语法

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>参数

*TAnalyzerGroupMembers*\
始终推导此参数。

*inputLogFile*\
要从中读取事件的输入 ETW 跟踪。

*numberOfPasses*\
要在输入跟踪上运行的分析传递的数量。 跟踪在每个分析传递后通过提供的分析器组传递。

*analyzerGroup*\
用于分析的分析器组。 调用[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)创建分析器组。 若要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获取的动态分析器组，请先将其地址传递到 `MakeStaticAnalyzerGroup`，然后将其封装在静态分析器组内。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
