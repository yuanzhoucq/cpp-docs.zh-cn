---
title: C++构建见解 SDK
description: 可视化工作室C++构建见解 SDK 的概述。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323263"
---
# <a name="c-build-insights-sdk"></a>C++构建见解 SDK

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

C++构建见解 SDK 是 API 的集合，允许您在C++构建见解平台的基础上创建个性化工具。 本页提供高级概述，以帮助您入门。

## <a name="obtaining-the-sdk"></a>获取 SDK

您可以按照以下步骤下载C++生成见解 SDK 作为 NuGet 包：

1. 从 Visual Studio 2017 及以上，创建新C++项目。
1. 在 **"解决方案资源管理器"** 窗格中，右键单击项目。
1. 从上下文菜单中选择 **"管理 NuGet 包**"。
1. 在右上角，选择**nuget.org**包源。
1. 搜索最新版本的 Microsoft.Cpp.BuildInsights 包。
1. 选择 **"安装**"。
1. 接受许可证。

请继续阅读，了解有关 SDK 周围的一般概念的信息。 您还可以访问正式[C++生成见解示例 GitHub 存储库](https://github.com/microsoft/cpp-build-insights-samples)，以查看使用 SDK 的实际C++应用程序的示例。

## <a name="collecting-a-trace"></a>收集跟踪

使用C++生成见解 SDK 分析来自 MSVC 工具链的事件需要您首先收集跟踪。 SDK 利用 Windows 事件跟踪 （ETW） 作为基础跟踪技术。 收集跟踪可通过两种方式完成：

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法 1：在 2019 年及以上视觉工作室中使用 vcperf

1. 打开 VS 2019 的提升 x64 本机工具命令提示。
1. 运行以下命令：`vcperf /start MySessionName`
1. 生成项目。
1. 运行以下命令：`vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > 使用`/stopnoanalyze`vcperf 停止跟踪时，请使用 该命令。 不能使用C++生成见解 SDK 来分析常规`/stop`命令停止的跟踪。

### <a name="method-2-programmatically"></a>方法 2：以编程方式

使用这些C++生成见解 SDK 跟踪收集函数中的任何一个以编程方式启动和停止跟踪。 **执行这些函数调用的程序必须具有管理权限。** 只有启动和停止跟踪函数需要管理权限。 C++生成见解 SDK 中的所有其他功能都可以在没有这些功能的情况下执行。

### <a name="sdk-functions-related-to-trace-collection"></a>与跟踪收集相关的 SDK 函数

| 功能 | C++ API | C API |
|--|--|--|
| 启动跟踪 | [开始跟踪会话](functions/start-tracing-session.md) | [开始跟踪会话A](functions/start-tracing-session-a.md)<br />[开始跟踪会话W](functions/start-tracing-session-w.md) |
| 停止跟踪 | [停止跟踪会话](functions/stop-tracing-session.md) | [停止跟踪会话A](functions/stop-tracing-session-a.md)<br />[停止跟踪会话W](functions/stop-tracing-session-w.md) |
| 停止跟踪和<br />立即分析结果 | [停止和分析跟踪会话](functions/stop-and-analyze-tracing-session.md) | [停止和分析跟踪会话A](functions/stop-and-analyze-tracing-session-a.md)<br />[停止和分析跟踪会话](functions/stop-and-analyze-tracing-session-w.md) |
| 停止跟踪和<br />立即重新记录结果 | [停止和重新记录跟踪会话](functions/stop-and-relog-tracing-session.md) | [停止和重新登录跟踪会话A](functions/stop-and-relog-tracing-session-a.md)<br />[停止和重新记录跟踪会话W](functions/stop-and-relog-tracing-session-w.md) |

以下各节将介绍如何配置分析或重新记录会话。 组合功能功能（如[StopAndAnalyze 跟踪会话](functions/stop-and-analyze-tracing-session.md)）是必需的。

## <a name="consuming-a-trace"></a>使用跟踪

获得 ETW 跟踪后，请使用C++生成见解 SDK 将其解压缩。 SDK 以允许您快速开发工具的格式为您提供事件。 我们不建议您不使用 SDK 使用原始 ETW 跟踪。 MSVC 使用的事件格式没有记录，经过优化以扩展到大型生成，而且很难理解。 此外，C++生成见解 SDK API 是稳定的，而原始 ETW 跟踪格式可能会更改，恕不另行通知。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>与跟踪消耗相关的 SDK 类型和函数

| 功能 | C++ API | C API | 说明 |
|--|--|--|--|
| 设置事件回调 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++生成见解 SDK 通过回调功能提供事件。 在C++，通过创建继承 IAnalyzer 或 IRelogger 接口的分析器或重新记录器类来实现回调函数。 在 C 中，在全局函数中实现回调，并在ANALYSIS_CALLBACKS或RELOG_CALLBACKS结构中提供指向它们的指针。 |
| 建筑组 | [使静态分析器组](functions/make-static-analyzer-group.md)<br />[使静态重新记录组](functions/make-static-relogger-group.md)<br />[制作动态分析器组](functions/make-dynamic-analyzer-group.md)<br />[使动态重新记录组](functions/make-dynamic-relogger-group.md) |  | C++ API 提供帮助器功能和类型，将多个分析器和重新记录对象组合在一起。 组是将复杂分析划分为更简单步骤的巧妙方法。 [vcperf](https://github.com/microsoft/vcperf)是以这种方式组织的。 |
| 分析或重新记录 | [分析](functions/analyze.md)<br />[重新登录](functions/relog.md) | [分析A](functions/analyze-a.md)<br />[分析W](functions/analyze-w.md)<br />[雷洛加](functions/relog-a.md)<br />[雷洛格瓦](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>分析和重新记录

使用跟踪是通过分析会话或重新记录会话完成的。

使用常规分析适用于大多数方案。 此方法使您能够灵活地选择输出格式：`printf`文本、xml、JSON、数据库、REST 调用等。

重新记录用于需要生成 ETW 输出文件的特殊用途分析。 使用重新登录，您可以将C++生成见解事件转换为您自己的 ETW 事件格式。 适当使用重新日志记录是C++构建见解数据与现有的 ETW 工具和基础结构挂钩。 例如[，vcperf](https://github.com/microsoft/vcperf)利用重新记录接口。 这是因为它必须生成 Windows 性能分析器（ETW 工具）可以理解的数据。 如果您计划使用重新记录接口，则需要事先了解 ETW 的工作原理。

### <a name="creating-analyzer-groups"></a>创建分析器组

了解如何创建组非常重要。 下面是一个示例，演示如何创建打印*Hello，世界的分析*器组！ 对于它接收的每个活动开始事件。

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>使用事件

### <a name="sdk-types-and-functions-related-to-events"></a>与事件相关的 SDK 类型和函数

| 功能 | C++ API | C API | 说明 |
|--|--|--|--|
| 匹配和筛选事件 | [匹配事件堆栈成员函数](functions/match-event-stack-in-member-function.md)<br />[匹配事件堆栈](functions/match-event-stack.md)<br />[匹配事件成员函数](functions/match-event-in-member-function.md)<br />[匹配事件](functions/match-event.md) |  | C++ API 提供了功能，便于从跟踪中提取您关心的事件。 使用 C API 时，必须手动完成此筛选。 |
| 事件数据类型 | [活动](cpp-event-data-types/activity.md)<br />[后端通行证](cpp-event-data-types/back-end-pass.md)<br />[自下而上](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[代码生成](cpp-event-data-types/code-generation.md)<br />[命令行](cpp-event-data-types/command-line.md)<br />[编译器](cpp-event-data-types/compiler.md)<br />[编译器通行证](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[事件](cpp-event-data-types/event.md)<br />[活动组](cpp-event-data-types/event-group.md)<br />[事件堆栈](cpp-event-data-types/event-stack.md)<br />[可执行图像输出](cpp-event-data-types/executable-image-output.md)<br />[Exp输出](cpp-event-data-types/exp-output.md)<br />[文件输入](cpp-event-data-types/file-input.md)<br />[文件输出](cpp-event-data-types/file-output.md)<br />[力因内](cpp-event-data-types/force-inlinee.md)<br />[前端文件](cpp-event-data-types/front-end-file.md)<br />[前端文件组](cpp-event-data-types/front-end-file-group.md)<br />[前端通票](cpp-event-data-types/front-end-pass.md)<br />[函数](cpp-event-data-types/function.md)<br />[ImpLib输出](cpp-event-data-types/imp-lib-output.md)<br />[调用](cpp-event-data-types/invocation.md)<br />[调用组](cpp-event-data-types/invocation-group.md)<br />[Lib输出](cpp-event-data-types/lib-output.md)<br />[链接器](cpp-event-data-types/linker.md)<br />[链接器组](cpp-event-data-types/linker-group.md)<br />[链接器Pass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[Obj输出](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[通行证1](cpp-event-data-types/pass1.md)<br />[通行证2](cpp-event-data-types/pass2.md)<br />[前LTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[简单事件](cpp-event-data-types/simple-event.md)<br />[符号名称](cpp-event-data-types/symbol-name.md)<br />[模板即时性](cpp-event-data-types/template-instantiation.md)<br />[模板即时组](cpp-event-data-types/template-instantiation-group.md)<br />[线程](cpp-event-data-types/thread.md)<br />[自上而下](cpp-event-data-types/top-down.md)<br />[跟踪信息](cpp-event-data-types/trace-info.md)<br />[整个程序分析](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>活动和简单活动

活动分为两类：*活动和**简单活动*。 活动是及时进行的过程，有开始和结束。 简单的事件是准时发生的事件，没有持续时间。 使用C++生成见解 SDK 分析 MSVC 跟踪时，当活动启动和停止时，您将收到单独的事件。 当发生简单事件时，您只能收到一个事件。

### <a name="parent-child-relationships"></a>父子关系

活动和简单事件通过父子关系彼此相关。 活动或简单事件的父级是发生活动时包含的活动。 例如，编译源文件时，编译器必须分析该文件，然后生成代码。 解析和代码生成活动都是编译器活动的子级。

简单的事件没有持续时间，所以里面没有其他事件。 因此，他们从来没有孩子。

[事件表中](event-table.md)指示每个活动和简单事件的父子关系。 在使用C++生成见解事件时，了解这些关系非常重要。 您通常必须依靠它们来了解事件的完整上下文。

### <a name="properties"></a>属性

所有事件都具有以下属性：

| Property | 说明 |
|--|--|
| 类型标识符 | 唯一标识事件类型的数字。 |
| 实例标识符 | 唯一标识跟踪中事件的数字。 如果跟踪中发生两个相同类型的事件，则两者都将获得唯一的实例标识符。 |
| 开始时间 | 活动开始的时间或发生简单事件的时间。 |
| 流程标识符 | 标识事件发生过程的数字。 |
| 线程标识符 | 标识事件发生的线程的数字。 |
| 处理器索引 | 一个从零开始索引，指示事件由哪个逻辑处理器发出。 |
| 事件名称 | 描述事件类型的字符串。 |

简单事件以外的所有活动也具有以下属性：

| Property | 说明 |
|--|--|
| 停止时间 | 活动停止的时间。 |
| 独家持续时间 | 在活动中花费的时间，不包括在其子活动中花费的时间。 |
| CPU 时间 | CPU 在附加到活动的线程中执行代码的时间。 它不包括附加到活动线程睡眠的时间。 |
| 专属 CPU 时间 | 与 CPU 时间相同，但不包括子活动花费的 CPU 时间。 |
| 钟点时间责任 | 活动对总挂钟时间的贡献。 钟点时间责任考虑到活动之间的并行性。 例如，假设两个不相关的活动并行运行。 两者都有 10 秒的持续时间，并且完全相同的开始和停止时间。 在这种情况下，Build Insights 会同时分配 5 秒的挂钟时间责任。 相反，如果这些活动一个接一个地运行，没有重叠，则它们都分配了 10 秒的挂钟时间责任。 |
| 独家挂钟时间责任 | 与挂钟时间责任相同，但不包括儿童活动的挂钟时间责任。 |

某些事件具有超出上述属性的属性。 在这种情况下，这些附加属性列在[事件表中](event-table.md)。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>使用C++生成见解 SDK 提供的事件

#### <a name="the-event-stack"></a>事件堆栈

每当C++生成见解 SDK 为您提供事件时，它都会以堆栈的形式出现。 堆栈中的最后一个条目是当前事件，其之前的条目是其父层次结构。 例如[，LTCG](event-table.md#ltcg)启动和停止事件发生在链接器的通过 1 期间。 在这种情况下，您收到的堆栈包含\[[：LINKER、PASS1](event-table.md#linker)、LTCG [PASS1](event-table.md#pass1)\]。 父层次结构很方便，因为您可以将事件追溯到其根。 如果上述 LTCG 活动速度较慢，您可以立即了解涉及哪个链接器调用。

#### <a name="matching-events-and-event-stacks"></a>匹配事件和事件堆栈

C++生成见解 SDK 为您提供跟踪中的每个事件，但大多数时候您只关心其中的子集。 在某些情况下，您可能只关心*事件堆栈的*子集。 SDK 提供了帮助您快速提取所需事件或事件堆栈以及拒绝不需要的事件或事件堆栈的设施。 它通过以下匹配功能完成：

|  |  |
|--|--|
| [匹配事件](functions/match-event.md) | 如果事件与指定类型之一匹配，请保留该事件。 将匹配的事件转发到 lambda 或其他可调用类型。 此函数不考虑事件的父层次结构。 |
| [匹配事件成员函数](functions/match-event-in-member-function.md) | 如果事件与成员函数参数中指定的类型匹配，请保留该事件。 将匹配的事件转发到成员函数。 此函数不考虑事件的父层次结构。 |
| [匹配事件堆栈](functions/match-event-stack.md) | 如果事件及其父层次结构都与指定的类型匹配，则保留事件。 将事件和匹配的父层次结构事件转发到 lambda 或其他可调用类型。 |
| [匹配事件堆栈成员函数](functions/match-event-stack-in-member-function.md) | 如果事件及其父层次结构与成员函数参数列表中指定的类型匹配，则保留事件。 将事件和匹配的父层次结构事件转发到成员函数。 |

事件堆栈匹配函数，`MatchEventStack`如在描述父层次结构时允许间隙匹配。 例如，你可以说你对\[[LINKER，LTCG](event-table.md#linker)[LTCG](event-table.md#ltcg)\]堆栈感兴趣。 它还匹配\[LINKER，PASS1，LTCG[PASS1](event-table.md#pass1)\]堆栈。 指定的最后一种类型必须是要匹配的事件类型，并且不是父层次结构的一部分。

#### <a name="capture-classes"></a>捕获类

使用`Match*`函数需要指定要匹配的类型。 这些类型是从*捕获类*列表中选择的。 捕获类分为几个类别，如下所述。

| 类别 | 说明 |
|--|--|
| Exact | 这些捕获类用于匹配特定事件类型，而没有其他类型。 例如[，编译器](cpp-event-data-types/compiler.md)类与[编译器](event-table.md#compiler)事件匹配。 |
| 通配符 | 这些捕获类可用于匹配其支持的事件列表中的任何事件。 例如，"[活动](cpp-event-data-types/activity.md)通配符"与任何活动事件匹配。 另一个示例是[编译器Pass](cpp-event-data-types/compiler-pass.md)通配符，它可以匹配[FRONT_END_PASS](event-table.md#front-end-pass)或[BACK_END_PASS](event-table.md#back-end-pass)事件。 |
| 组 | 组捕获类的名称以*组*结尾。 它们用于匹配一行中同一类型的多个事件，而忽略间隙。 它们仅在匹配递归事件时才有意义，因为您不知道事件堆栈中存在多少个。 例如，每次编译器分析文件时，都会发生[FRONT_END_FILE](event-table.md#front-end-file)活动。 此活动是递归的，因为编译器在分析文件时可能会找到包含指令。 [FrontEndFile](cpp-event-data-types/front-end-file.md)类仅匹配堆栈中一个FRONT_END_FILE事件。 使用[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)类匹配整个包含层次结构。 |
| 通配符组 | 通配符组合并通配符和组的属性。 此类别的唯一类是[调用组](cpp-event-data-types/invocation-group.md)，它匹配和捕获单个事件堆栈中的所有[LINKER](event-table.md#linker)和[编译器](event-table.md#compiler)事件。 |

请参阅[事件表](event-table.md)以了解可以使用哪些捕获类来匹配每个事件。

#### <a name="after-matching-using-captured-events"></a>匹配后：使用捕获的事件

匹配成功完成后，`Match*`函数将构造捕获类对象并将其转发到指定的函数。 使用这些捕获类对象访问事件的属性。

#### <a name="example"></a>示例

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
