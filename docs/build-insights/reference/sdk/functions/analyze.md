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
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324110"
---
# <a name="analyze"></a>分析

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Analyze`函数用于分析在跟踪C++生成时从 MSVC 获取的 Windows （ETW） 事件跟踪。 ETW 跟踪中的事件将按顺序转发到调用方提供的分析器组。 此功能支持多路分析，允许连续多次将事件流转发到分析器组。

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

*TAnalyzer组成员*\
始终推导此参数。

*输入日志文件*\
要从中读取事件的输入 ETW 跟踪。

*通道数*\
在输入跟踪上运行的分析数。 跟踪通过每个分析传递一次通过提供的分析器组。

*分析仪组*\
用于分析的分析器组。 调用[MakeStatic 分析器组](make-static-analyzer-group.md)以创建分析器组。 要使用从[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)获得的动态分析器组，首先通过将地址传递给`MakeStaticAnalyzerGroup`将其封装在静态分析器组中。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
