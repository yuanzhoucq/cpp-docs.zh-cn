---
title: 开始跟踪会话W
description: C++生成见解 SDK 开始跟踪会话W 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: af67c3be50cb19ccbfb7fe286e5d61cd1d241bf8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323799"
---
# <a name="starttracingsessionw"></a>开始跟踪会话W

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

函数`StartTracingSessionW`启动跟踪会话。 调用此函数的可执行文件必须具有管理员权限。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>参数

*会话名称*\
要启动的跟踪会话的名称。 调用[停止跟踪会话W](stop-tracing-session-w.md)或任何其他停止跟踪函数时使用相同的名称。

*选项*\
指向[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)对象的指针。 使用此对象可选择要由跟踪会话收集的事件。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
