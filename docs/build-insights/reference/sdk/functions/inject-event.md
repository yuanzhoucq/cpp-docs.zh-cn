---
title: InjectEvent
description: C++ BUILD Insights SDK InjectEvent 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334414"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`InjectEvent` 函数在实现[IRelogger](../other-types/irelogger-class.md)接口的 relogger 中调用。 它用于在 relogging 会话的输出跟踪文件中写入 Windows 事件跟踪（ETW）事件。

## <a name="syntax"></a>语法

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>参数

*relogSession*\
指向 relogging 会话的指针。 为实现 `IRelogger` 接口的 reloggers 提供了 relogging 会话。 有关详细信息，请参阅[IRelogger](../other-types/irelogger-class.md)。

*providerId*\
用于获取 ETW 事件 relogged 的 Windows 事件跟踪（ETW）提供程序 GUID。

*eventDescriptor*\
Relogged 的 ETW 事件的 ETW 事件说明符。

*processId*\
Relogged 的 ETW 事件的进程标识符（PID）。

*threadId*\
Relogged 的 ETW 事件的线程标识符（TID）。

*processorIndex*\
Relogged 的 ETW 事件的处理器索引。

*timestamp*\
Relogged 的 ETW 事件的时间戳。

*数据*\
指向应包含在 relogged ETW 事件中的数据的指针。

*byteCount*\
数据所指向的数据的大小（以字节为单位 *）。*

## <a name="remarks"></a>备注

有关 ETW 概念（如*提供程序 GUID*和*事件描述符*）的详细信息，请参阅[etw 文档](/windows/win32/etw/about-event-tracing)。 有关如何使用C++生成见解 SDK 启动 relogging 会话的详细信息，[请参阅重新](relog.md)生成。

::: moniker-end
