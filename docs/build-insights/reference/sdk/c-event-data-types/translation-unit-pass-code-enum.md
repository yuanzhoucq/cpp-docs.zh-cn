---
title: TRANSLATION_UNIT_PASS_CODE 枚举
description: C++生成见解 SDK TRANSLATION_UNIT_PASS_CODE 枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335044"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE 枚举

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TRANSLATION_UNIT_PASS_CODE` 枚举。

## <a name="members"></a>Members

| 名称 | 值 | 说明 |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0（0x00000000） | 前端通过，负责分析源代码并将其转换为中间语言。 |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | 后端通过，负责优化中间语言，并将其转换为机器代码。 |

## <a name="remarks"></a>备注

由 C SDK 函数使用。

::: moniker-end
