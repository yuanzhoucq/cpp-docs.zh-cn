---
title: INVOCATION_VERSION_DATA 结构
description: C++生成见解 SDK INVOCATION_VERSION_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335128"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_VERSION_DATA` 结构将版本号描述为一组整数值。

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `VersionMajor` | 版本的主版本号。 |
| `VersionMinor` | 版本的次要版本号。 |
| `BuildNumberMajor` | 生成的主编号。 |
| `BuildNumberMinor` | 内部版本号。 |

::: moniker-end
