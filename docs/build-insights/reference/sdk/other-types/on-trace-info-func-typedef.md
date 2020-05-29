---
title: 在TraceInfoFunc类型定义
description: C++在TraceinfoFunc类型定义引用上构建见解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329024"
---
# <a name="ontraceinfofunc-typedef"></a>在TraceInfoFunc类型定义

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnTraceInfoFunc`是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)和[RELOG_CALLBACKS](relog-callbacks-struct.md)结构中使用的函数签名之一。

## <a name="syntax"></a>语法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>参数

*跟踪信息*\
包含有关当前正在分析或重新记录的跟踪的信息[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)对象。

*回调上下文*\
ANALYSIS_DESCRIPTOR[或](analysis-descriptor-struct.md)[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中为此回调设置的上下文值。

### <a name="return-value"></a>返回值

控制接下来会发生什么[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
