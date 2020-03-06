---
title: FILE_DATA 结构
description: C++生成见解 SDK FILE_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335194"
---
# <a name="file_data-structure"></a>FILE_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_DATA` 结构描述文件输入或输出。

## <a name="syntax"></a>语法

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `Path` | 文件的绝对路径 |
| `TypeCode` | 描述文件的类型的代码。 有关详细信息，请参阅[FILE_TYPE_CODE](file-type-code-enum.md)。 |

::: moniker-end
