---
title: MakeDynamicAnalyzerGroup
description: C++ Build Insights SDK MakeDynamicAnalyzerGroup 函数参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4c244066b41837a8dd95b44bab2b096134ed5d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224196"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicAnalyzerGroup` 函数用于创建动态分析器组。 分析器组的成员从左到右逐个接收事件，直到分析完跟踪中的所有事件为止。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>参数

analyzers\
动态分析器组中包含的 [IAnalyzer](../other-types/ianalyzer-class.md) 指针的矢量。 这些指针可以是 raw、`std::unique_ptr` 或 `std::shared_ptr`。

### <a name="return-value"></a>返回值

动态分析器组。 使用 `auto` 关键字来捕获返回值。

## <a name="remarks"></a>备注

与静态分析器组不同，动态分析器组的成员在编译时不必是已知的。 可以在运行时根据程序输入或在编译时未知的其他值选择分析器组成员。 与静态分析器组不同，动态分析器组中的 [`IAnalyzer`](../other-types/ianalyzer-class.md) 指针有多变行为，并虚拟函数调用被正确地分派。 这种灵活性的代价可能是事件处理速度减慢。 如果所有分析器组成员在编译时都是已知的，并且你不需要多变行为，请考虑使用静态分析器组。 若要使用静态分析器组，请改为调用 [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md)。

动态分析器组可以封装在静态分析器组中。 可通过将它的地址传递给 [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md) 来完成。 使用这种技术将动态分析器组传递到 [`Analyze`](analyze.md) 等函数，这些函数只接受静态分析器组。

::: moniker-end
