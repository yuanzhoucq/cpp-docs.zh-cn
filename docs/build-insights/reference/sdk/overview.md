---
title: C++生成见解 SDK
description: Visual Studio C++ BUILD Insights SDK 的概述。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334030"
---
# <a name="c-build-insights-sdk"></a>C++生成见解 SDK

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

C++ BUILD insights SDK 是一组 api，可用于在C++ Build Insights 平台之上创建个性化工具。 本页提供了一个高级概述，帮助你入门。

## <a name="obtaining-the-sdk"></a>获取 SDK

可以通过执行以下C++步骤，将生成见解 SDK 下载为 NuGet 包：

1. 在 Visual Studio 2017 及更高版本中， C++创建一个新项目。
1. 在**解决方案资源管理器**窗格中，右键单击项目。
1. 从上下文菜单中选择 "**管理 NuGet 包**"。
1. 在右上角，选择 " **nuget.org** " 包源。
1. 搜索最新版本的 BuildInsights 包。
1. 选择 "**安装**"。
1. 接受许可证。

请继续阅读以获取有关 SDK 的一般概念的信息。 还可以访问官方[ C++ Build Insights 示例 GitHub 存储库](https://github.com/microsoft/cpp-build-insights-samples)，查看使用 SDK 的实际C++应用程序的示例。

## <a name="collecting-a-trace"></a>收集跟踪

使用C++ BUILD Insights SDK 分析来自 MSVC 工具链的事件要求您首先收集跟踪。 SDK 使用 Windows 事件跟踪（ETW）作为基础跟踪技术。 可以通过两种方式来收集跟踪：

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法1：在 Visual Studio 2019 及更高版本中使用 vcperf

1. 为 VS 2019 打开提升的 x64 本机工具命令提示。
1. 运行以下命令： `vcperf /start MySessionName`
1. 生成你的项目。
1. 运行以下命令： `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > 使用 vcperf 停止跟踪时，请使用 `/stopnoanalyze` 命令。 不能使用C++生成见解 SDK 分析常规 `/stop` 命令停止的跟踪。

### <a name="method-2-programmatically"></a>方法2：以编程方式

使用任何这些C++生成见解 SDK 跟踪集合函数以编程方式启动和停止跟踪。 **执行这些函数调用的程序必须具有管理特权。** 只有 start 和 stop 跟踪功能需要管理权限。 生成见解 SDK 中的C++所有其他函数均可在没有这些功能的情况下执行。

### <a name="sdk-functions-related-to-trace-collection"></a>与跟踪集合相关的 SDK 函数

| 功能 | C++ API | C API |
|--|--|--|
| 启动跟踪 | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| 停止跟踪 | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| 停止跟踪并<br />立即分析结果 | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| 停止跟踪并<br />立即 relogging 结果 | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

以下各节说明了如何配置分析或 relogging 会话。 组合功能函数（如[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md)）需要它。

## <a name="consuming-a-trace"></a>使用跟踪

使用 ETW 跟踪后，请使用C++生成见解 SDK 将其解包。 SDK 为你提供了一种格式的事件，可让你快速开发工具。 不建议在不使用 SDK 的情况下使用原始 ETW 跟踪。 MSVC 使用的事件格式未记录，经过优化，可以扩展到巨大的生成，并且难以理解。 此外， C++生成见解 SDK API 是稳定的，而原始 ETW 跟踪格式可能会更改，恕不另行通知。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>与跟踪消耗相关的 SDK 类型和函数

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 设置事件回调 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++ BUILD Insights SDK 通过回调函数提供事件。 在C++中，通过创建继承 IAnalyzer 或 IRelogger 接口的分析器或 relogger 类来实现回调函数。 在 C 中，在全局函数中实现回调，并在 ANALYSIS_CALLBACKS 或 RELOG_CALLBACKS 结构中提供指向它们的指针。 |
| 构建组 | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | C++ API 提供 helper 函数和类型，以便将多个分析器和 relogger 对象组合在一起。 组是将复杂分析分为更简单步骤的一种巧妙方法。 [vcperf](https://github.com/microsoft/vcperf)是以这种方式组织的。 |
| 分析或 relogging | [分析](functions/analyze.md)<br />[重新](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>分析和 relogging

使用跟踪是通过分析会话或 relogging 会话来完成的。

使用常规分析适用于大多数情况。 此方法使你可以灵活选择输出格式： `printf` 文本、xml、JSON、数据库、REST 调用等。

Relogging 用于需要生成 ETW 输出文件的特殊用途的分析。 使用 relogging，可以将C++ Build Insights 事件转换为自己的 ETW 事件格式。 Relogging 的适当用途是将构建见解数据C++挂钩到现有的 ETW 工具和基础结构。 例如， [vcperf](https://github.com/microsoft/vcperf)利用了 relogging 接口。 这是因为它必须生成可理解的 Windows 性能分析器（ETW 工具）的数据。 如果你计划使用 relogging 接口，一些事先了解 ETW 的工作方式是必需的。

### <a name="creating-analyzer-groups"></a>创建分析器组

必须知道如何创建组。 下面的示例演示如何创建一个可打印*Hello，world！* 它接收的每个活动启动事件。

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

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 匹配和筛选事件 | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | 该C++ API 提供了一些函数，使你可以轻松地从跟踪中提取你关注的事件。 使用 C API，必须手动完成此筛选。 |
| 事件数据类型 | [活动](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[Microsoft.extensions.codegeneration](cpp-event-data-types/code-generation.md)<br />[行为](cpp-event-data-types/command-line.md)<br />[编译程序](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[Value](cpp-event-data-types/environment-variable.md)<br />[Event](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[调用](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[链接器](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1.log](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[线程](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>活动和简单事件

事件分为两类：*活动*和*简单事件*。 活动是指在开始和结束时的正在进行的进程。 简单事件是 punctual 的，没有持续时间。 使用C++生成见解 SDK 分析 MSVC 跟踪时，当活动开始和停止时，你将收到单独的事件。 当发生简单事件时，你将只收到一个事件。

### <a name="parent-child-relationships"></a>父子关系

活动和简单事件通过父子关系相互关联。 活动或简单事件的父项是发生的活动。 例如，在编译源文件时，编译器必须分析文件，然后生成代码。 分析和代码生成活动都是编译器活动的子项。

简单事件不会有持续时间，因此不会发生任何其他事件。 因此，它们永远不会有任何子级。

[事件表](event-table.md)中指示了每个活动和简单事件的父子关系。 使用C++生成见解事件时，了解这些关系非常重要。 你经常需要依赖它们来了解事件的完整上下文。

### <a name="properties"></a>属性

所有事件都具有以下属性：

| 属性 | 说明 |
|--|--|
| 类型标识符 | 唯一标识事件类型的数字。 |
| 实例标识符 | 一个数字，用于唯一标识跟踪内的事件。 如果跟踪中出现两个相同类型的事件，都将获取唯一的实例标识符。 |
| 开始时间 | 活动启动的时间或简单事件发生的时间。 |
| 进程标识符 | 标识发生事件的进程的数字。 |
| 线程标识符 | 一个数字，用于标识发生事件的线程。 |
| 处理器索引 | 一个从零开始的索引，指示事件的发出逻辑处理器。 |
| 事件名称 | 描述事件类型的字符串。 |

除简单事件外的所有活动还具有以下属性：

| 属性 | 说明 |
|--|--|
| 停止时间 | 活动停止的时间。 |
| 独占持续时间 | 在活动中花费的时间，不包括其子活动所用的时间。 |
| CPU 时间 | CPU 在附加到活动的线程中执行代码所用的时间。 它不包括附加到活动的线程休眠的时间。 |
| 独占 CPU 时间 | 与 CPU 时间相同，但不包括子活动占用的 CPU 时间。 |
| 时钟时间责任 | 活动对总时钟时间的贡献。 时钟时间责任考虑到活动之间的并行度。 例如，假设并行运行两个不相关的活动。 两者的持续时间为10秒，且开始和停止时间完全相同。 在这种情况下，Build Insights 会将时钟时间的时间责任指定为5秒。 与此相反，如果这些活动逐个运行，而另一个不重叠，则会为其分配一个时间为10秒的时钟时间。 |
| 独占墙壁-时钟时间责任 | 与时钟时间责任相同，但不包括子活动的时钟时间责任。 |

有些事件的属性超出了所述的属性。 在这种情况下，这些附加属性在[事件表](event-table.md)中列出。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>使用C++生成见解 SDK 提供的事件

#### <a name="the-event-stack"></a>事件堆栈

每当C++生成见解 SDK 提供事件时，它都是堆栈的形式。 堆栈中的最后一项是当前事件，项在其父层次结构之前。 例如， [LTCG](event-table.md#ltcg)启动和停止事件发生在链接器的第1步中。 在这种情况下，你接收的堆栈包含： \[[链接器](event-table.md#linker)、 [pass1.log](event-table.md#pass1)、LTCG\]。 父层次结构很方便，因为可以将事件追溯到根层次结构。 如果上面提到的 LTCG 活动速度较慢，则可以立即了解涉及到的链接器调用。

#### <a name="matching-events-and-event-stacks"></a>匹配事件和事件堆栈

C++ BUILD Insights SDK 为你提供跟踪中的每个事件，但在大多数情况下，你只关心其中的一个子集。 在某些情况下，您可能只关心*事件堆栈*的一个子集。 SDK 提供的工具可帮助您快速提取所需的事件或事件堆栈，并拒绝不需要的事件或事件堆栈。 这是通过以下匹配函数完成的：

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | 如果事件与指定的类型之一匹配，则保留该事件。 将匹配的事件转发到 lambda 或其他可调用类型。 此函数不考虑事件的父层次结构。 |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | 如果事件与成员函数的参数中指定的类型相匹配，则保留该事件。 将匹配的事件转发到成员函数。 此函数不考虑事件的父层次结构。 |
| [MatchEventStack](functions/match-event-stack.md) | 如果事件及其父层次结构都与指定的类型相匹配，则保留事件。 将事件和匹配的父层次结构事件转发到 lambda 或其他可调用类型。 |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | 如果事件及其父层次结构都与成员函数的参数列表中指定的类型相匹配，则保留事件。 将事件和匹配的父层次结构事件转发到成员函数。 |

事件堆栈匹配函数（如 `MatchEventStack`）在描述要匹配的父层次结构时允许间隙。 例如，你可能会说你对 \[[链接器](event-table.md#linker) [LTCG](event-table.md#ltcg)\] 堆栈感兴趣。 它还会与 \[链接器、 [pass1.log](event-table.md#pass1)、LTCG\] 堆栈匹配。 指定的最后一个类型必须是要匹配的事件类型，而不是父层次结构的一部分。

#### <a name="capture-classes"></a>捕获类

使用 `Match*` 函数要求指定要匹配的类型。 这些类型是从*捕获类*的列表中选择的。 捕获类分为几个类别，如下所述。

| 类别 | 说明 |
|--|--|
| 完全 | 这些捕获类用于匹配特定事件类型，而不匹配任何其他事件类型。 例如，[编译器](cpp-event-data-types/compiler.md)类与[编译器](event-table.md#compiler)事件匹配。 |
| 通配符 | 这些捕获类可用于匹配其支持的事件列表中的任何事件。 例如，[活动](cpp-event-data-types/activity.md)通配符与任何活动事件匹配。 另一个示例是[CompilerPass](cpp-event-data-types/compiler-pass.md)通配符，它可匹配[FRONT_END_PASS](event-table.md#front-end-pass)或[BACK_END_PASS](event-table.md#back-end-pass)事件。 |
| 组 | 组捕获类的名称以*组*结尾。 它们用于匹配一行中同一类型的多个事件，同时忽略间隙。 它们仅在匹配递归事件时才有意义，因为您不知道事件堆栈中存在多少。 例如，每次编译器分析文件时，都将发生[FRONT_END_FILE](event-table.md#front-end-file)活动。 此活动是递归的，因为编译器在分析文件时可能会找到 include 指令。 [FrontEndFile](cpp-event-data-types/front-end-file.md)类仅与堆栈中的一个 FRONT_END_FILE 事件匹配。 使用[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)类来匹配整个 include 层次结构。 |
| 通配符组 | 通配符组将通配符和组的属性组合在一起。 此类别的唯一类为[InvocationGroup](cpp-event-data-types/invocation-group.md)，它匹配并捕获单个事件堆栈中的所有[链接器](event-table.md#linker)和[编译器](event-table.md#compiler)事件。 |

请参阅[事件表](event-table.md)，了解可使用哪些捕获类来匹配每个事件。

#### <a name="after-matching-using-captured-events"></a>匹配后：使用捕获的事件

匹配成功完成后，`Match*` 函数将构造捕获类对象并将其转发到指定的函数。 使用这些捕获类对象可访问事件的属性。

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
