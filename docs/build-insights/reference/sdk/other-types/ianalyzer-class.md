---
title: IAnalyzer 类
description: C++ BUILD Insights SDK IAnalyzer 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334078"
---
# <a name="ianalyzer-class"></a>IAnalyzer 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`IAnalyzer` 类提供了一个接口，用于分析 Windows 事件跟踪（ETW）跟踪。 它用于[MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)、 [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)、 [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)和[MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)函数。 使用 `IAnalyzer` 作为基类来创建自己的分析器，该分析器可以是 analyzer 或 relogger 组的一部分。

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

派生自 `IAnalyzer` 的类可用作分析器和 reloggers。 当使用 reloggers 时，relogger 特定函数会重定向到其分析器等效项。 反之亦然：派生自 `IRelogger` 的类不能用作分析器。 在 relogger 组中使用分析器是一种常见模式。 当放置在 relogger 组的早期位置时，分析器可以预计算信息并使其在以后的位置可用于 reloggers。

所有未重写的函数的默认返回值都是 `AnalysisControl::CONTINUE`。 有关详细信息，请参阅[AnalysisControl](analysis-control-enum-class.md)。

## <a name="members"></a>Members

除了 `IRelogger` 接口中的[OnTraceInfo](irelogger-class.md#on-trace-info)成员以外，`IAnalyzer` 类包含以下成员：

### <a name="destructor"></a>析构函数

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>函数

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

销毁 IAnalyzer 类。

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

对于分析器组的分析器部分，将在第一个分析传递开始之前调用此函数。 对于 relogger 组的分析器部分，将在 relogging 传递开始之前调用此函数。 对于同一 relogging 会话的分析器和 relogger 组的分析器部分，在第一个分析传递开始之前调用此函数两次。

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

对于分析器组的分析器部分，将在每个分析过程开始时调用此函数。 对于 relogger 组的分析器部分，将在 relogger 传递的开头调用此函数。 对于同一 relogging 会话的分析器和 relogger 组的分析器部分，将在每个分析过程开始时调用此函数，并在 relogger pass 开始时调用此函数。

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

此函数不能重写。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 此函数将调用重定向到[OnBeginAnalysis](#on-begin-analysis)。

### <a name="return-value"></a>返回值

[OnBeginAnalysis](#on-begin-analysis)调用的结果。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

此函数不能重写。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 此函数将调用重定向到[OnBeginAnalysisPass](#on-begin-analysis-pass)。

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>返回值

[OnBeginAnalysisPass](#on-begin-analysis-pass)调用的结果。

## <a name="on-end-analysis"></a>OnEndAnalysis

对于作为分析器组的一部分的分析器，在最后的分析结束后调用此函数。 对于作为 relogger 组一部分的分析器，在 relogging pass 结束后调用此函数。 对于同一 relogging 会话的分析器和 relogger 组的一部分的分析器，此函数称为两次：

1. 所有分析传递结束后，在 relogging 传递开始之前，
1. relogging pass 结束后。

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

对于分析器组的分析器部分，将在每个分析通过结束时调用此函数。 对于 relogger 组的分析器部分，将在 relogger pass 结束时调用此函数。 对于同一 relogging 会话的分析器和 relogger 组的分析器部分，将在每个分析过程结束时调用此函数，并在 relogger pass 结束时调用此函数。

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-end-relogging"></a>OnEndRelogging

此函数不能重写。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 此函数将调用重定向到[OnEndAnalysis](#on-end-analysis)。

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>返回值

[OnEndAnalysis](#on-end-analysis)调用的结果。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

此函数不能重写。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 此函数将调用重定向到[OnEndAnalysisPass](#on-end-analysis-pass)。

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>返回值

[OnEndAnalysisPass](#on-end-analysis-pass)调用的结果。

## <a name="on-simple-event"></a>OnSimpleEvent

处理简单事件时将调用此函数。 不能重写此函数的第二个版本。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 对版本2的所有调用都将重定向到版本1。

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

*eventStack*\
此简单事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*relogSession*\
未使用此参数。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-start-activity"></a>OnStartActivity

处理活动开始事件时将调用此函数。 不能重写此函数的第二个版本。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 对版本2的所有调用都将重定向到版本1。

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

*eventStack*\
此活动开始事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*relogSession*\
未使用此参数。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

## <a name="on-stop-activity"></a>OnStopActivity

处理活动停止事件时将调用此函数。 不能重写此函数的第二个版本。 当分析器是 relogger 组C++的一部分时，生成见解 SDK 会调用它。 对版本2的所有调用都将重定向到版本1。

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

*eventStack*\
此活动停止事件的事件堆栈。 有关事件堆栈的详细信息，请参阅[事件](../event-table.md)。

*relogSession*\
未使用此参数。

### <a name="return-value"></a>返回值

描述接下来应执行的操作的[AnalysisControl](analysis-control-enum-class.md)代码。

::: moniker-end
