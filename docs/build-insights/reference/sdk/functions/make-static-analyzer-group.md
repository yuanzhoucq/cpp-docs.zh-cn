---
title: MakeStaticAnalyzerGroup
description: C++ Build Insights SDK MakeStaticAnalyzerGroup 函数参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81c5654c78e086af1c33d0791768ceea52575c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224170"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticAnalyzerGroup` 函数用于创建可以传递到 [`Analyze`](analyze.md) 或 [`Relog`](relog.md) 等函数的静态分析器组。 分析器组的成员从左到右逐个接收事件，直到分析完跟踪中的所有事件为止。

## <a name="syntax"></a>语法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>参数

TAnalyzerPtrs\
此参数始终是推导出来的。

analyzers\
静态分析器组中包含的 [`IAnalyzer`](../other-types/ianalyzer-class.md) 指针的参数包。 这些指针可以是 raw、`std::unique_ptr` 或 `std::shared_ptr`。

### <a name="return-value"></a>返回值

静态分析器组。 使用 `auto` 关键字来捕获返回值。

## <a name="remarks"></a>备注

与动态分析器组不同，静态分析器组的成员在编译时必须是已知的。 此外，静态分析器组包含没有多变行为的 [`IAnalyzer`](../other-types/ianalyzer-class.md) 指针。 当使用静态分析器组分析 Windows 事件跟踪 (ETW) 跟踪时，对 `IAnalyzer` 接口的调用始终解析为分析器组成员直接指向的对象。 这种灵活性损失带来了事件处理速度更快的可能性。 如果在编译时无法知道分析器组的成员，或者在 `IAnalyzer` 指针上需要多变行为，请考虑使用动态分析器组。 若要使用动态分析器组，请改为调用 [`MakeDynamicAnalyzerGroup`](make-static-analyzer-group.md)。

::: moniker-end
