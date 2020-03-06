---
title: RELOG_CALLBACKS 结构
description: C++生成见解 SDK RELOG_CALLBACKS 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333982"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)对象时，将使用 `RELOG_CALLBACKS` 结构。 它指定在 relogging Windows 事件跟踪（ETW）跟踪时要调用的函数。

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `OnStartActivity` | 调用以处理活动开始事件。 |
| `OnStopActivity` | 调用以处理活动停止事件。 |
| `OnSimpleEvent` | 调用以处理简单事件。 |
| `OnTraceInfo` | 在调用 `OnBeginReloggingPass` 之后，在 relogging pass 开始时调用一次。 |
| `OnBeginRelogging` | 在开始 relogging 会话时调用，在 relogging pass 开始之前调用。 |
| `OnEndRelogging` | 在终止 relogging 会话时，在 relogging pass 结束后调用。 |
| `OnBeginReloggingPass` | 在处理任何事件之前，在开始 relogging 传递时调用。 |
| `OnEndReloggingPass` | 在处理完所有事件之后，在结束 relogging 传递时调用。 |

## <a name="remarks"></a>备注

`RELOG_CALLBACKS` 结构的所有成员都必须指向有效的函数。 有关接受的函数签名的详细信息，请参阅[OnRelogEventFunc](on-relog-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
