---
title: MakeStaticAnalyzerGroup
description: C++ BUILD Insights SDK MakeStaticAnalyzerGroup 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334390"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticAnalyzerGroup` 函数用于创建可传递给函数（如分析[或重新](relog.md)[分析](analyze.md)）的静态分析器组。 分析器组的成员从左到右逐个接收事件，直到跟踪分析中的所有事件为止。

## <a name="syntax"></a>语法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>参数

*TAnalyzerPtrs*\
始终推导此参数。

*分析器*\
静态分析器组中包含的[IAnalyzer](../other-types/ianalyzer-class.md)指针的参数包。 这些指针可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。

### <a name="return-value"></a>返回值

静态分析器组。 使用**auto**关键字来捕获返回值。

## <a name="remarks"></a>备注

与动态分析器组不同，静态分析器组的成员在编译时必须是已知的。 此外，静态分析器组包含不具有多态行为的[IAnalyzer](../other-types/ianalyzer-class.md)指针。 当使用静态分析器组分析 Windows 事件跟踪（ETW）跟踪时，对 `IAnalyzer` 接口的调用将始终解析为分析器组成员直接指向的对象。 这种灵活性损失会导致事件处理速度更快。 如果在编译时无法知道分析器组的成员，或者在 `IAnalyzer` 指针上需要多态行为，请考虑使用动态分析器组。 若要使用动态分析器组，请改为调用[MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) 。

::: moniker-end
