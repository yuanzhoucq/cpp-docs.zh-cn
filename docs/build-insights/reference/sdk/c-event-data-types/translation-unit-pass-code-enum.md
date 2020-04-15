---
title: TRANSLATION_UNIT_PASS_CODE枚举
description: C++生成见解 SDK TRANSLATION_UNIT_PASS_CODE枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0162d7e53bb7ee7035b94a6b640f6db87cd8b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325290"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE枚举

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`TRANSLATION_UNIT_PASS_CODE`举。

## <a name="members"></a>成员

| “属性” | “值” | 说明 |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 （0x000000） | 前端传递，负责分析源代码并将其转换为中间语言。 |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | 后端通，负责优化中间语言并将其转换为机器代码。 |

## <a name="remarks"></a>备注

由 C SDK 函数使用。

::: moniker-end
