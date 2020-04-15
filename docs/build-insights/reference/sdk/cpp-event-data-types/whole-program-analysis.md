---
title: 整个程序分析类
description: C++生成见解 SDK 整个程序分析类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c68441b7da09f9880bbb2f97544b1ad8da2f631f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324120"
---
# <a name="wholeprogramanalysis-class"></a>整个程序分析类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`WholeProgramAnalysis`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)事件。

## <a name="syntax"></a>语法

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`WholeProgramAnalysis`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[整个程序分析](#whole-program-analysis)

## <a name="wholeprogramanalysis"></a><a name="whole-program-analysis"></a>整个程序分析

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)事件。

::: moniker-end
