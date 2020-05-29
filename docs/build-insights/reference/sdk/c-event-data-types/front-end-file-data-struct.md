---
title: FRONT_END_FILE_DATA结构
description: C++生成见解 SDK FRONT_END_FILE_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7fb6b6fff4f309a3539a290f279d1e31cb1ed76b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325553"
---
# <a name="front_end_file_data-structure"></a>FRONT_END_FILE_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`FRONT_END_FILE_DATA`描述编译器前端对文件的处理。

## <a name="syntax"></a>语法

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `Path` | 文件的绝对路径，以 UTF-8 编码。 |

::: moniker-end
