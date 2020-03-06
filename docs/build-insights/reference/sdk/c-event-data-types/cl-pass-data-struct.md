---
title: CL_PASS_DATA 结构
description: C++生成见解 SDK CL_PASS_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335254"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`CL_PASS_DATA` 结构描述了编译过程。

## <a name="syntax"></a>语法

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `TranslationUnitPassCode` | 标识要执行的编译传递的代码。 有关详细信息，请参阅[TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md)。 |
| `InputSourcePath` | 正在执行此C++编译传递的 C 或源文件。 |
| `OutputObjectPath` | 编译器生成的对象文件。 |

::: moniker-end
