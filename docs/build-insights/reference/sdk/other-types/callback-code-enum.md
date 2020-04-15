---
title: CALLBACK_CODE枚举
description: C++生成见解 SDK CALLBACK_CODE枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329190"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE枚举

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`CALLBACK_CODE`举用于控制分析或重新记录会话的流。 从[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)或[RELOG_CALLBACKS](relog-callbacks-struct.md)中的函数返回CALLBACK_CODE值，以控制接下来会发生什么。

## <a name="members"></a>成员

| “属性” | “值” | 说明 |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 正常继续当前分析或重新记录会话。 |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 （0x0000002） | 取消当前分析或重新记录会话并发出错误信号。 |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 （0x0000004） | 取消当前分析或重新记录会话。 |

::: moniker-end
