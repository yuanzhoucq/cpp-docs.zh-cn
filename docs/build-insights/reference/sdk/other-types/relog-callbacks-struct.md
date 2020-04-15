---
title: RELOG_CALLBACKS结构
description: C++构建见解 SDK RELOG_CALLBACKS结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328963"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

在`RELOG_CALLBACKS`初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)对象时，将使用该结构。 它指定在重新记录 Windows （ETW） 跟踪的事件跟踪期间调用哪些函数。

## <a name="syntax"></a>语法

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `OnStartActivity` | 调用以处理活动开始事件。 |
| `OnStopActivity` | 调用以处理活动停止事件。 |
| `OnSimpleEvent` | 调用 以处理简单事件。 |
| `OnTraceInfo` | 调用一次在重新记录通过开始，之后`OnBeginReloggingPass`已被调用。 |
| `OnBeginRelogging` | 在开始重新记录会话时调用，在重新记录通道开始之前。 |
| `OnEndRelogging` | 在结束重新记录会话时调用，重新记录通过结束后。 |
| `OnBeginReloggingPass` | 在处理任何事件之前，在开始重新记录传递时调用。 |
| `OnEndReloggingPass` | 在处理所有事件后结束重新记录传递时调用。 |

## <a name="remarks"></a>备注

`RELOG_CALLBACKS`结构的所有成员必须指向有效的函数。 有关接受的函数签名的详细信息，请参阅[OnRelogEventFunc、OnTraceInfoFunc](on-relog-event-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。 [OnTraceInfoFunc](on-trace-info-func-typedef.md)

::: moniker-end
