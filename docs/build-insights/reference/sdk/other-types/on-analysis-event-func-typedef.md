---
title: 上分析事件丰型
description: C++在分析事件丰体引用上构建见解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eacd174279caff0db22586d5e40d3a866afc4459
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329125"
---
# <a name="onanalysiseventfunc-typedef"></a>上分析事件丰型

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnAnalysisEventFunc`是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)结构中使用的函数签名之一。

## <a name="syntax"></a>语法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>参数

*事件堆栈*\
当前事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*回调上下文*\
ANALYSIS_DESCRIPTOR[或](analysis-descriptor-struct.md)[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中为此回调设置的上下文值。

### <a name="return-value"></a>返回值

控制接下来会发生什么[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
