---
title: OnAnalysisEventFunc typedef
description: C++生成见解 SDK OnAnalysisEventFunc typedef 引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d260f6060e759f315589abda82e31c2c2b95a65e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334060"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc typedef

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`OnAnalysisEventFunc` typedef 是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)结构中使用的函数签名之一。

## <a name="syntax"></a>语法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>参数

*eventStack*\
当前事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*callbackContext*\
在[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中为此回调设置的上下文值。

### <a name="return-value"></a>返回值

一个[CALLBACK_CODE](callback-code-enum.md)值，该值控制接下来应执行的操作。

::: moniker-end
