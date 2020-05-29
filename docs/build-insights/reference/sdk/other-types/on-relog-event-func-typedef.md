---
title: OnRelogEventFunc 类型def
description: C++在 RelogEventFunc 类型定义引用上生成见解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329068"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc 类型def

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnRelogEventFunc`是[RELOG_CALLBACKS](relog-callbacks-struct.md)结构中使用的函数签名之一。

## <a name="syntax"></a>语法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>参数

*事件堆栈*\
当前事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*重新登录会话*\
调用[InjectEvent](../functions/inject-event.md)时使用的重新记录会话指针。

*回调上下文*\
为RELOG_DESCRIPTOR[中为此](analysis-descriptor-struct.md)回调设置的上下文值。

### <a name="return-value"></a>返回值

控制接下来会发生什么[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
