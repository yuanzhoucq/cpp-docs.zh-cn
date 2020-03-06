---
title: INVOCATION_DATA 结构
description: C++生成见解 SDK INVOCATION_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335140"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA` 结构描述了编译器或链接器调用。

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `MSVCToolCode` | 标识调用的类型的代码。 有关详细信息，请参阅[MSVC_TOOL_CODE](msvc-tool-code-enum.md)。 |
| `ToolVersion` | 一个对象，它将调用的工具的版本存储为一组整数值。 |
| `ToolVersionString` | 描述在文本窗体中调用的工具的版本。 |
| `WorkingDirectory` | 从中进行调用的目录。 |
| `ToolPath` | 调用的工具的绝对路径。 |

::: moniker-end
