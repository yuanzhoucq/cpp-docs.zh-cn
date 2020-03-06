---
title: FRONT_END_FILE_DATA 结构
description: C++生成见解 SDK FRONT_END_FILE_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 33232a0f83566e58e64964e84961a7ade2de7b7c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335182"
---
# <a name="front_end_file_data-structure"></a>FRONT_END_FILE_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FRONT_END_FILE_DATA` 结构描述了编译器前端对文件的处理。

## <a name="syntax"></a>语法

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Path` | 文件的绝对路径，以 UTF-8 编码。 |

::: moniker-end
