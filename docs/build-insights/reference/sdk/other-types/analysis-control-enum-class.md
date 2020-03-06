---
title: AnalysisControl 枚举类
description: C++生成见解 SDK AnalysisControl 枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334120"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl 枚举类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalysisControl` 枚举类用于控制分析或 relogging 会话的流动。 从[IAnalyzer](ianalyzer-class.md)或[IRelogger](irelogger-class.md)成员函数返回 `AnalysisControl` 代码，以控制接下来应执行的操作。

## <a name="members"></a>Members

|  |  |
|--|--|
| `BLOCK` | 防止当前事件在分析器或 relogger 组中进一步传播。 |
| `CANCEL` | 取消当前分析或 relogging 会话。 |
| `CONTINUE` | 正常继续当前分析或 relogging 会话。 将当前事件传播到下一个分析器或 relogger 组成员。 |
| `FAILURE` | 取消当前分析或 relogging 会话并发出错误消息。 |

::: moniker-end
