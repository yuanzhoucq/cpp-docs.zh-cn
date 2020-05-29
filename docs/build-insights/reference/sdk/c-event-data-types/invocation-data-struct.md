---
title: INVOCATION_DATA结构
description: C++生成见解 SDK INVOCATION_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325490"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`INVOCATION_DATA`描述编译器或链接器调用。

## <a name="syntax"></a>语法

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `MSVCToolCode` | 标识调用类型的代码。 有关详细信息，请参阅[MSVC_TOOL_CODE](msvc-tool-code-enum.md)。 |
| `ToolVersion` | 将被调用的工具版本存储为一组积分值的对象。 |
| `ToolVersionString` | 以文本形式描述被调用的工具版本。 |
| `WorkingDirectory` | 调用的目录。 |
| `ToolPath` | 被调用的工具的绝对路径。 |

::: moniker-end
