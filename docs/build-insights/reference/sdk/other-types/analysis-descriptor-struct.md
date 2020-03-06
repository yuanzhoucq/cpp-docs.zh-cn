---
title: ANALYSIS_DESCRIPTOR 结构
description: C++生成见解 SDK ANALYSIS_DESCRIPTOR 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334102"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_DESCRIPTOR` 结构与[AnalyzeA](../functions/analyze-a.md)和[AnalyzeW](../functions/analyze-w.md)函数结合使用。 本文介绍如何分析 Windows 事件跟踪（ETW）跟踪。

## <a name="syntax"></a>语法

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `NumberOfPasses` | 应通过 ETW 跟踪完成的分析传递的数量。 |
| `Callbacks` | 一个[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)对象，该对象指定分析会话期间要调用的函数。 |
| `Context` | 用户提供的上下文，作为参数传递给在中指定的所有回调函数 `Callbacks` |

## <a name="remarks"></a>备注

`Callbacks` 结构仅接受指向非成员函数的指针。 可以通过将 `Context` 设置为对象指针来绕过此限制。 此对象指针将作为参数传递给所有非成员回调函数。 使用此指针从非成员回调函数内调用成员函数。

::: moniker-end
