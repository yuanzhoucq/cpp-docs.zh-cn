---
title: 使静态分析器组
description: C++生成见解 SDK 使静态分析器组函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323931"
---
# <a name="makestaticanalyzergroup"></a>使静态分析器组

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MakeStaticAnalyzerGroup`函数用于创建一个静态分析器组，该组可以传递给[分析或](analyze.md)[重新记录](relog.md)等函数。 分析器组的成员从左到右逐个接收事件，直到分析跟踪中的所有事件。

## <a name="syntax"></a>语法

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>参数

*TAnalyzerPtrs*\
始终推导此参数。

*分析仪*\
静态[分析器组中包含的 IAnalyzer](../other-types/ianalyzer-class.md)指针的参数包。 这些指针可以是生的，`std::unique_ptr`也可以`std::shared_ptr`是 。

### <a name="return-value"></a>返回值

静态分析器组。 使用**自动**关键字捕获返回值。

## <a name="remarks"></a>备注

与动态分析器组不同，静态分析器组的成员必须在编译时知道。 此外，静态分析器组包含没有多态行为的[IAnalyzer](../other-types/ianalyzer-class.md)指针。 当使用静态分析器组分析 Windows （ETW） 跟踪的事件跟踪时，对接口`IAnalyzer`的调用始终解析为分析器组成员直接指向的对象。 这种灵活性的丧失具有更快的事件处理时间的可能性。 如果在编译时无法知道分析器组的成员，或者在`IAnalyzer`指针上需要多态行为，请考虑使用动态分析器组。 要使用动态分析器组，请改为调用["动态分析器组](make-static-analyzer-group.md)"。

::: moniker-end
