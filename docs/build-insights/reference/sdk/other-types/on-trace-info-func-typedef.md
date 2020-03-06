---
title: OnTraceInfoFunc typedef
description: C++生成见解 SDK OnTraceInfoFunc typedef 引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333988"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`OnTraceInfoFunc` typedef 是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)和[RELOG_CALLBACKS](relog-callbacks-struct.md)结构中使用的函数签名之一。

## <a name="syntax"></a>语法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>参数

*traceInfo*\
一个[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)对象，它包含有关当前正在分析或 relogged 的跟踪的信息。

*callbackContext*\
在[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中为此回调设置的上下文值。

### <a name="return-value"></a>返回值

一个[CALLBACK_CODE](callback-code-enum.md)值，该值控制接下来应执行的操作。

::: moniker-end
