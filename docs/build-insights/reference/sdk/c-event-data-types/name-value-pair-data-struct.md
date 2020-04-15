---
title: NAME_VALUE_PAIR_DATA结构
description: C++生成见解 SDK NAME_VALUE_PAIR_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4a0bf8e8ba32d94d30a56d0ef26ca4ed0c9b0711
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325359"
---
# <a name="name_value_pair_data-structure"></a>NAME_VALUE_PAIR_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`NAME_VALUE_PAIR_DATA`描述名称和值对。

## <a name="syntax"></a>语法

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `Name` | 名称。 |
| `Value` | 值。 |

::: moniker-end
