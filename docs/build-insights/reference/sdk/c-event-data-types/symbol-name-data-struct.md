---
title: SYMBOL_NAME_DATA结构
description: C++生成见解 SDK SYMBOL_NAME_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325340"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`SYMBOL_NAME_DATA`描述编译器前端符号。

## <a name="syntax"></a>语法

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `Key` | 符号的键。 此值在要分析的跟踪中是唯一的。 |
| `Name` | 符号的名称。 |

## <a name="remarks"></a>备注

来自两个不同的编译器前端传递的符号可能具有相同的名称，但密钥不同。 在这种情况下，使用符号名称确定两种类型是否相同。

::: moniker-end
