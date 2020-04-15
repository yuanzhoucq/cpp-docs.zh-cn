---
title: 制作动态分析器组
description: C++生成见解 SDK 使动态分析器组函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323962"
---
# <a name="makedynamicanalyzergroup"></a>制作动态分析器组

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MakeDynamicAnalyzerGroup`函数用于创建动态分析器组。 分析器组的成员从左到右逐个接收事件，直到分析跟踪中的所有事件。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>参数

*分析仪*\
动态[分析器组中包含的 IAnalyzer](../other-types/ianalyzer-class.md)指针的矢量。 这些指针可以是生的，`std::unique_ptr`也可以`std::shared_ptr`是 。

### <a name="return-value"></a>返回值

动态分析器组。 使用**自动**关键字捕获返回值。

## <a name="remarks"></a>备注

与静态分析器组不同，动态分析器组的成员不需要在编译时已知。 您可以根据程序输入或在运行时根据编译时未知的其他值选择分析器组成员。 与静态分析器组不同，动态分析器组中的[IAnalyzer](../other-types/ianalyzer-class.md)指针具有多态行为，并且虚拟函数调用正确调度。 这种灵活性的代价可能是较慢的事件处理时间。 当所有分析器组成员在编译时都已知，并且不需要多态行为时，请考虑使用静态分析器组。 要使用静态分析器组，请改为调用[MakeStaticAnalyzer 组](make-static-analyzer-group.md)。

动态分析器组可以封装在静态分析器组中。 这是通过传递其地址[到使静态分析器组](make-static-analyzer-group.md)。 使用此技术将动态分析器组传递给仅接受静态分析器[组等函数](analyze.md)。

::: moniker-end
