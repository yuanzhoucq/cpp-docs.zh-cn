---
title: CL_PASS_DATA结构
description: C++生成见解 SDK CL_PASS_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0a41e59068ade285f1ffa1a9ce13734ef5f1f32
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325699"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`CL_PASS_DATA`描述编译传递。

## <a name="syntax"></a>语法

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `TranslationUnitPassCode` | 标识正在执行的编译传递的代码。 有关详细信息，请参阅[TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md)。 |
| `InputSourcePath` | 正在执行此编译传递的 C 或 C++源文件。 |
| `OutputObjectPath` | 编译器正在生成的对象文件。 |

::: moniker-end
