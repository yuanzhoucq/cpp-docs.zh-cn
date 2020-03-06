---
title: MakeDynamicAnalyzerGroup
description: C++ BUILD Insights SDK MakeDynamicAnalyzerGroup 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334402"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicAnalyzerGroup` 函数用于创建动态分析器组。 分析器组的成员从左到右逐个接收事件，直到跟踪分析中的所有事件为止。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>参数

*分析器*\
动态分析器组中包含的[IAnalyzer](../other-types/ianalyzer-class.md)指针的矢量。 这些指针可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。

### <a name="return-value"></a>返回值

动态分析器组。 使用**auto**关键字来捕获返回值。

## <a name="remarks"></a>备注

与静态分析器组不同，动态分析器组的成员不需要在编译时已知。 可以在运行时基于程序输入或在编译时未知的其他值选择分析器组成员。 与静态分析器组不同，动态分析器组中的[IAnalyzer](../other-types/ianalyzer-class.md)指针具有多态行为，并正确调度虚拟函数调用。 这种灵活性会降低事件处理时间。 在编译时已知所有分析器组成员时，如果不需要多态行为，请考虑使用静态分析器组。 若要使用静态分析器组，请改为调用[MakeStaticAnalyzerGroup](make-static-analyzer-group.md) 。

动态分析器组可以在静态分析器组中进行封装。 这是通过将其地址传递给[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)来完成的。 使用此方法将动态分析器组传递到[分析](analyze.md)等功能，这些功能仅接受静态分析器组。

::: moniker-end
