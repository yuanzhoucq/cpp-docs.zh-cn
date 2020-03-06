---
title: CALLBACK_CODE 枚举
description: C++生成见解 SDK CALLBACK_CODE 枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334090"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE 枚举

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`CALLBACK_CODE` 枚举用于控制分析或 relogging 会话的流动。 从[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)或[RELOG_CALLBACKS](relog-callbacks-struct.md)中的函数返回 CALLBACK_CODE 值，以控制接下来应执行的操作。

## <a name="members"></a>Members

| 名称 | 值 | 说明 |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 正常继续当前分析或 relogging 会话。 |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2（0x00000002） | 取消当前分析或 relogging 会话并发出错误消息。 |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4（0x00000004） | 取消当前分析或 relogging 会话。 |

::: moniker-end
