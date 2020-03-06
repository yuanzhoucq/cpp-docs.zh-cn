---
title: AnalyzeW
description: C++ BUILD Insights SDK AnalyzeW 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bd9b401f08941134d3c267df5c23c5d9e981cb86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334486"
---
# <a name="analyzew"></a>AnalyzeW

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalyzeW` 函数用于分析从 Windows 输入事件跟踪（ETW）跟踪读取的 MSVC 事件。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE AnalyzeW(
    const wchar_t*             inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>参数

*inputLogFile*\
要从中读取事件的输入 ETW 跟踪。

*analysisDescriptor*\
指向[ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)对象的指针。 使用此对象配置分析。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
