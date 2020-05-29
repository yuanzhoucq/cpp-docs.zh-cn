---
title: IRelogger 类
description: C++生成见解 SDK IRelogger 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329146"
---
# <a name="irelogger-class"></a>IRelogger 类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`IRelogger`类提供了一个接口，用于重新记录 Windows （ETW） 跟踪的事件跟踪。 它与[MakeDynamic ReloggerGroup](../functions/make-dynamic-relogger-group.md)和[使静态重新记录组](../functions/make-static-analyzer-group.md)功能一起使用。 用作`IRelogger`基类，创建自己的重新记录器，该重新记录器可以是重新记录组的一部分。

## <a name="syntax"></a>语法

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>备注

未重写的所有函数的默认返回值为`AnalysisControl::CONTINUE`。 有关详细信息，请参阅[分析控制](analysis-control-enum-class.md)。

## <a name="members"></a>成员

### <a name="destructor"></a>析构函数

[*IRelogger](#irelogger-destructor)

### <a name="functions"></a>函数

[在开始重新记录](#on-begin-relogging)\
[在"开始记录"Pass](#on-begin-relogging-pass)\
[结束重新记录](#on-end-relogging)\
[结束重新记录通道](#on-end-relogging-pass)\
[在Simple事件上](#on-simple-event)\
[启动活动](#on-start-activity)\
[停止活动](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>*IRelogger

销毁 IRelogger 类。

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>在开始重新记录

在重新日志记录传递开始之前调用此功能。

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>在"开始记录"Pass

此函数在重新记录通道的开头调用。

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>结束重新记录

重新记录传递结束后调用此功能。

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>结束重新记录通道

此函数在重新记录通道结束时调用。

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>在Simple事件上

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

正在处理简单事件时调用此函数。

### <a name="parameters"></a>参数

*事件堆栈*\
此简单事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onstartactivity"></a><a name="on-start-activity"></a>启动活动

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

正在处理活动启动事件时调用此函数。

### <a name="parameters"></a>参数

*事件堆栈*\
此活动启动事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>停止活动

正在处理活动停止事件时调用此函数。

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>参数

*事件堆栈*\
此活动停止事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

此函数在每个分析或重新记录传递开始时调用一次。

### <a name="parameters"></a>参数

*跟踪信息*\
包含有关要消耗的跟踪的有用属性的[TraceInfo](../cpp-event-data-types/trace-info.md)对象。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

::: moniker-end
