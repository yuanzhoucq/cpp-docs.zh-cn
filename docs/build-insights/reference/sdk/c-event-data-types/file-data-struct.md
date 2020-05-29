---
title: FILE_DATA结构
description: C++生成见解 SDK FILE_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b7b0129c54fa4b1d5285bafb38761da45bab4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325589"
---
# <a name="file_data-structure"></a>FILE_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`FILE_DATA`描述文件输入或输出。

## <a name="syntax"></a>语法

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `Path` | 文件的绝对路径 |
| `TypeCode` | 描述文件类型的代码。 有关详细信息，请参阅[FILE_TYPE_CODE](file-type-code-enum.md)。 |

::: moniker-end
