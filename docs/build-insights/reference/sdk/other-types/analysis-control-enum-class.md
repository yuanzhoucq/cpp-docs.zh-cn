---
title: 分析控制枚举类
description: C++生成见解 SDK 分析控制枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323632"
---
# <a name="analysiscontrol-enum-class"></a>分析控制枚举类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`AnalysisControl`举类用于控制分析或重新记录会话的流。 从`AnalysisControl`[IAnalyzer](ianalyzer-class.md)或[IRelogger](irelogger-class.md)成员函数返回代码，以控制接下来会发生什么。

## <a name="members"></a>成员

|  |  |
|--|--|
| `BLOCK` | 防止当前事件在分析器或重新记录组中进一步传播。 |
| `CANCEL` | 取消当前分析或重新记录会话。 |
| `CONTINUE` | 正常继续当前分析或重新记录会话。 将当前事件传播到下一个分析器或重新记录组成员。 |
| `FAILURE` | 取消当前分析或重新记录会话并发出错误信号。 |

::: moniker-end
