---
title: MSVC_TOOL_CODE枚举
description: C++生成见解 SDK MSVC_TOOL_CODE枚举引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MSVC_TOOL_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96b650b5bce304ad6e487cb100f2b8f85df34eb9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325454"
---
# <a name="msvc_tool_code-enum"></a>MSVC_TOOL_CODE枚举

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`MSVC_TOOL_CODE`举。

## <a name="members"></a>成员

| “属性” | “值” | 说明 |
|--|--|--|
| `MSVC_TOOL_CODE_CL` | 0 （0x000000） | 编译器（cl.exe）。 |
| `MSVC_TOOL_CODE_LINK` | 1 (0x00000001) | 链接器（链接.exe）。 |

## <a name="remarks"></a>备注

由 C SDK 函数使用。

::: moniker-end
