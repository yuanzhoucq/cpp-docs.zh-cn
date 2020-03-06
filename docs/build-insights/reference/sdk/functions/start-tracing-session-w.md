---
title: StartTracingSessionW
description: C++ BUILD Insights SDK StartTracingSessionW 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 072b02166f2841e6d210306ef75c9fc64fea9778
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334246"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`StartTracingSessionW` 函数启动跟踪会话。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>参数

*sessionName*\
要启动的跟踪会话的名称。 在调用[StopTracingSessionW](stop-tracing-session-w.md)时使用相同的名称，或使用任何其他停止跟踪函数。

*选项*\
指向[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)对象的指针。 使用此对象可选择跟踪会话应收集的事件。

### <a name="return-value"></a>返回值

[RESULT_CODE](../other-types/result-code-enum.md)枚举中的结果代码。

::: moniker-end
