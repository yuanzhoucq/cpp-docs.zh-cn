---
title: IRelogger 类
description: C++ BUILD Insights SDK IRelogger 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857046"
---
# <a name="irelogger-class"></a>IRelogger 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`IRelogger` 类提供一个接口，用于 relogging Windows 事件跟踪（ETW）跟踪。 它与[MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)和[MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)函数结合使用。 使用 `IRelogger` 作为基类来创建自己的 relogger，可以是 relogger 组的一部分。

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

所有未重写的函数的默认返回值都是 `AnalysisControl::CONTINUE`。 有关详细信息，请参阅[AnalysisControl](analysis-control-enum-class.md)。

## <a name="members"></a>成员

### <a name="destructor"></a>析构函数

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>函数

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

销毁 IRelogger 类。

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

在 relogging 传递开始之前调用此函数。

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

此函数在 relogging pass 开始时调用。

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-end-relogging"></a>OnEndRelogging

Relogging pass 结束后，调用此函数。

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

此函数在 relogging pass 结束时调用。

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

处理简单事件时将调用此函数。

### <a name="parameters"></a>parameters

*eventStack*\
此简单事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

处理活动开始事件时将调用此函数。

### <a name="parameters"></a>parameters

*eventStack*\
此活动开始事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-stop-activity"></a>OnStopActivity

处理活动停止事件时将调用此函数。

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>parameters

*eventStack*\
此活动停止事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

每次分析或 relogging 通过时调用此函数一次。

### <a name="parameters"></a>parameters

*traceInfo*\
一个[TraceInfo](../cpp-event-data-types/trace-info.md)对象，它包含有关所使用的跟踪的有用属性。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

::: moniker-end
