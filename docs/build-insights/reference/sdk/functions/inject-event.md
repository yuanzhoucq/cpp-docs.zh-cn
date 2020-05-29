---
title: 注入事件
description: C++生成见解 SDK 注入事件函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324041"
---
# <a name="injectevent"></a>注入事件

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

函数`InjectEvent`在实现[IRelogger](../other-types/irelogger-class.md)接口的重新记录器中调用。 它用于在重新记录会话的输出跟踪文件中为 Windows （ETW） 事件编写事件跟踪。

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

*重新登录会话*\
指向重新记录会话的指针。 为实现`IRelogger`接口的重新记录提供重新记录会话。 有关详细信息，请参阅[IRelogger](../other-types/irelogger-class.md)。

*提供程序 Id*\
Windows （ETW） 提供程序 GUID 的事件跟踪，根据该跟踪，ETW 事件将重新记录。

*事件描述符*\
已重新记录的 ETW 事件的 ETW 事件描述符。

*进程 Id*\
重新记录的 ETW 事件的进程标识符 （PID）。

*线程 Id*\
已重新记录的 ETW 事件的线程标识符 （TID）。

*处理器索引*\
重新记录的 ETW 事件的处理器索引。

*时间 戳*\
已重新记录的 ETW 事件的时间戳。

*数据*\
指向应包含在重新记录的 ETW 事件中的数据的指针。

*字节计数*\
数据的大小（以字节为单位）由*数据*指向。

## <a name="remarks"></a>备注

有关 ETW 概念的详细信息（如*提供程序 GUID*和*事件描述符*），请参阅[ETW 文档](/windows/win32/etw/about-event-tracing)。 有关如何使用C++生成见解 SDK 启动重新日志记录会话的详细信息，请参阅[Relog](relog.md)。

::: moniker-end
