---
title: IAnalyzer 类
description: C++生成见解 SDK IAnalyzer 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329177"
---
# <a name="ianalyzer-class"></a>IAnalyzer 类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`IAnalyzer`类提供了一个用于分析 Windows （ETW） 跟踪的事件跟踪的接口。 它与[制作动态分析器组](../functions/make-dynamic-analyzer-group.md)、[使动态重新记录组](../functions/make-dynamic-relogger-group.md)、[使静态分析器组](../functions/make-dynamic-analyzer-group.md)和[使静态重新记录组](../functions/make-static-analyzer-group.md)功能一起使用。 用作`IAnalyzer`基类，创建自己的分析器，该分析器可以是分析器或重新记录组的一部分。

## <a name="syntax"></a>语法

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>备注

派生自`IAnalyzer`的类可用作分析器和重新记录器。 当用作重新记录器时，重新记录特定的函数重定向到其分析器等效项。 相反，情况并非如此：派生自`IRelogger`的类不能用作分析器。 在重新记录组中使用分析器是一种常见的模式。 当放置在重新记录组的早期位置时，分析仪可以预先计算信息，并使其可用于以后位置的重新记录。

未重写的所有函数的默认返回值为`AnalysisControl::CONTINUE`。 有关详细信息，请参阅[分析控制](analysis-control-enum-class.md)。

## <a name="members"></a>成员

除了`IRelogger`接口中的`IAnalyzer` [OnTraceInfo](irelogger-class.md#on-trace-info)成员外，该类还包含以下成员：

### <a name="destructor"></a>析构函数

[*IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>函数

[上开始分析](#on-begin-analysis)\
[OnBegin分析通行证](#on-begin-analysis-pass)\
[在开始重新记录](#on-begin-relogging)\
[在"开始记录"Pass](#on-begin-relogging-pass)\
[结束分析](#on-end-analysis)\
[上端分析通](#on-end-analysis-pass)\
[结束重新记录](#on-end-relogging)\
[结束重新记录通道](#on-end-relogging-pass)\
[在Simple事件上](#on-simple-event)\
[启动活动](#on-start-activity)\
[停止活动](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>*IAnalyzer

销毁 IAnalyzer 类。

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>上开始分析

对于分析器组一部分的分析器，在第一次分析传递开始之前调用此函数。 对于重新记录组中的分析器部分，在重新记录传递开始之前调用此功能。 对于同一重新记录会话的分析器和重新记录组部分的分析器，在第一次分析传递开始之前，将调用此函数两次。

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBegin分析通行证

对于分析器组一部分的分析器，在每次分析传递开始时调用此函数。 对于重新记录组中的分析器，此函数在重新记录器传递的开头调用。 对于同一重新记录会话的分析器和重新记录组部分的分析器，在每次分析通过开始时和重新记录器传递开始时调用此功能。

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>在开始重新记录

```cpp
AnalysisControl OnBeginRelogging() final;
```

无法重写此功能。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 此函数将调用重定向到[OnBeginAnalysis](#on-begin-analysis)。

### <a name="return-value"></a>返回值

[OnBegin 分析](#on-begin-analysis)调用的结果。

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>在"开始记录"Pass

无法重写此功能。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 此函数将调用重定向到[OnBegin 分析Pass](#on-begin-analysis-pass)。

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>返回值

[OnBegin分析通](#on-begin-analysis-pass)电话的结果。

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>结束分析

对于分析器组一部分的分析器，在最后一次分析传递结束后调用此功能。 对于作为重新记录组一部分的分析仪，在重新记录传递结束后调用此功能。 对于属于同一重新日志记录会话的分析器和重新记录组一部分的分析器，此函数调用两次：

1. 所有分析通过结束后和重新记录通过开始之前，
1. 重新记录通过结束后。

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>上端分析通

对于分析器组一部分的分析器，每次分析传递结束时都会调用此函数。 对于重新记录组中的分析器，此函数在重新记录器通过结束时调用。 对于同一重新记录会话的分析器和重新记录组部分的分析器，在每次分析通过结束时和重新记录器通过结束时调用此功能。

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>结束重新记录

无法重写此功能。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 此函数将调用重定向到[OnEndAnalysis](#on-end-analysis)。

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>返回值

[OnEnd 分析](#on-end-analysis)调用的结果。

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>结束重新记录通道

无法重写此功能。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 此函数将调用重定向到[OnEndAnalysisPass](#on-end-analysis-pass)。

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>返回值

[OnendAnalysisPass](#on-end-analysis-pass)调用的结果。

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>在Simple事件上

正在处理简单事件时调用此函数。 无法重写此函数的第二个版本。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 对版本 2 的所有调用都重定向到版本 1。

### <a name="version-1"></a>版本 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>版本 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>参数

*事件堆栈*\
此简单事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*重新登录会话*\
未使用此参数。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onstartactivity"></a><a name="on-start-activity"></a>启动活动

正在处理活动启动事件时调用此函数。 无法重写此函数的第二个版本。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 对版本 2 的所有调用都重定向到版本 1。

### <a name="version-1"></a>版本 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>版本 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>参数

*事件堆栈*\
此活动启动事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*重新登录会话*\
未使用此参数。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>停止活动

正在处理活动停止事件时调用此函数。 无法重写此函数的第二个版本。 当分析器是重新记录组的一部分时，C++生成见解 SDK 调用它。 对版本 2 的所有调用都重定向到版本 1。

### <a name="version-1"></a>版本 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>版本 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>参数

*事件堆栈*\
此活动停止事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*重新登录会话*\
未使用此参数。

### <a name="return-value"></a>返回值

分析[控制](analysis-control-enum-class.md)代码，描述接下来会发生什么。

::: moniker-end
