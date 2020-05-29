---
title: ANALYSIS_DESCRIPTOR结构
description: C++生成见解 SDK ANALYSIS_DESCRIPTOR结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323610"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`ANALYSIS_DESCRIPTOR`结构与[分析A](../functions/analyze-a.md)[和分析W](../functions/analyze-w.md)函数一起使用。 它描述了如何分析 Windows （ETW） 跟踪的事件跟踪。

## <a name="syntax"></a>语法

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `NumberOfPasses` | 应通过 ETW 跟踪执行的分析次数。 |
| `Callbacks` | 指定[在](analysis-callbacks-struct.md)分析会话期间调用哪些函数ANALYSIS_CALLBACKS对象。 |
| `Context` | 以参数传递给在`Callbacks` |

## <a name="remarks"></a>备注

结构`Callbacks`仅接受指向非成员函数的指针。 您可以通过设置`Context`到对象指针来绕过此限制。 此对象指针将作为参数传递给所有非成员回调函数。 使用此指针可以从非成员回调函数中调用成员函数。

::: moniker-end
