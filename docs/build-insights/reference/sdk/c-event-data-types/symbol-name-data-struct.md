---
title: SYMBOL_NAME_DATA 结构
description: C++生成见解 SDK SYMBOL_NAME_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335092"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`SYMBOL_NAME_DATA` 结构描述编译器前端符号。

## <a name="syntax"></a>语法

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Key` | 符号的键。 此值在要分析的跟踪中是唯一的。 |
| `Name` | 符号的名称。 |

## <a name="remarks"></a>备注

来自两个不同编译器前端传递的符号可能具有相同的名称，但具有不同的键。 在这种情况下，请使用符号名称确定两个类型是否相同。

::: moniker-end
