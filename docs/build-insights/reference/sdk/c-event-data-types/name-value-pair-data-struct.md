---
title: NAME_VALUE_PAIR_DATA 结构
description: C++生成见解 SDK NAME_VALUE_PAIR_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6c4f6fef11e6365bdc930d5df1f48f72186ebdb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335098"
---
# <a name="name_value_pair_data-structure"></a>NAME_VALUE_PAIR_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`NAME_VALUE_PAIR_DATA` 结构描述了名称和值对。

## <a name="syntax"></a>语法

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Name` | 名称。 |
| `Value` | 值。 |

::: moniker-end
