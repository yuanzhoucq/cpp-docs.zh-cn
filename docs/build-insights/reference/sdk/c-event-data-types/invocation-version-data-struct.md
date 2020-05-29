---
title: INVOCATION_VERSION_DATA结构
description: C++生成见解 SDK INVOCATION_VERSION_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325474"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`INVOCATION_VERSION_DATA`将版本号描述为一组积分值。

## <a name="syntax"></a>语法

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `VersionMajor` | 版本的主要编号。 |
| `VersionMinor` | 版本的次要编号。 |
| `BuildNumberMajor` | 生成的主要编号。 |
| `BuildNumberMinor` | 生成的小数。 |

::: moniker-end
