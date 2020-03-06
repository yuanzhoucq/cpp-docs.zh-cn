---
title: 参考： Windows 性能分析器视图
description: 适用于C++ Windows 性能分析器中的生成见解视图的参考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eb3e20ed3ca4231b10efaf36310f6fbc0f5980bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333892"
---
# <a name="reference-windows-performance-analyzer-views"></a>参考： Windows 性能分析器视图

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 中提供了生成见解工具。 若要查看该版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

本文提供了有关 Windows 性能分析器（ C++ WPA）中提供的每个生成见解视图的详细信息。 使用此页可以查找：

- 数据列说明;与
- 每个视图的可用预设，包括其预期用途和首选的查看模式。

如果你不熟悉 WPA，我们建议首先熟悉[适用于C++ BUILD Insights 的 WPA 基础知识](/cpp/build-insights/tutorials/wpa-basics)。

## <a name="build-explorer"></a>生成资源管理器

"生成资源管理器" 视图用于：

- 诊断并行问题，
- 确定您的生成时间是否是通过分析、代码生成或链接进行的。
- 确定瓶颈和特别长的生成活动。

### <a name="build-explorer-view-data-columns"></a>生成资源管理器视图数据列

| 列名 | 说明 |
|-|-|
| BuildTimelineDescription | 文本说明当前活动或属性发生的时间线。 |
| BuildTimelineId          | 当前活动或属性发生于时间线的从零开始的标识符。 |
| 组件                | 发出当前事件时正在编译或链接的组件。 如果没有与此事件关联的组件，此列的值将 *\<调用 X Info\>* 。 X 是发出事件时执行的调用的唯一数值标识符。 此标识符与此事件的 InvocationId 列中的相同。 |
| Count                    | 此数据行表示的活动或属性的数目。 此值始终为1，并且仅在分组多行时才适用于聚合方案。 |
| ExclusiveCPUTime         | 此活动使用的 CPU 时间量（以毫秒为单位）。 此量中不包括子活动所用的时间。 |
| ExclusiveDuration        | 活动的毫秒持续时间。 子活动的持续时间不包括在此数量中。 |
| InclusiveCPUTime         | 此活动和所有子活动使用的 CPU 时间量（以毫秒为单位）。 |
| InclusiveDuration        | 此活动的毫秒持续时间，包括所有子活动。 |
| InvocationDescription    | 发生此事件的调用的文本说明。 说明包括是*cl .exe*还是*share.exe*，以及唯一的数字调用标识符。 如果适用，它包括在调用过程中编译或链接的组件的完整路径。 对于没有生成任何组件的调用或生成多个组件的调用，路径为空。 调用标识符与 InvocationId 列中的标识符相同。 |
| InvocationId             | 发生此事件的调用的唯一数值标识符。 |
| 名称                     | 此事件表示的活动或属性的名称。 |
| 时间                     | 标识事件发生时间的时间戳。 |
| 工具                     | 此事件发生时执行的工具。 此列的值为 CL 或 Link。 |
| 类型                     | 当前事件的类型。 此值为活动或属性。 |
| 值                    | 如果当前事件为属性，则此列将包含其值。 当当前事件为活动时，此列为空。 |

### <a name="build-explorer-view-presets"></a>生成资源管理器视图预设

| 预设名称           | 首选视图模式 | 使用方法 |
|-----------------------|---------------------|------------|
| 活动统计信息   | 图形/表       | 使用此预设可查看所有生成资源管理器活动的聚合统计信息。 在表模式下，如果您的生成是通过分析、代码生成或链接器来确定的，请一目了然。 每个活动的聚合持续时间按降序排序。 展开顶级节点可轻松找到这些顶级活动最多花费时间的调用，以进行深化。 如果需要，可以调整 WPA 设置以显示平均值或其他类型的聚合。 在图形模式下，查看在生成过程中每个活动何时处于活动状态。 |
| 发出           | 图形               | 在图形视图中向下滚动查看按开始时间排序的一系列调用。 可以将其与 "CPU" （采样）视图一起使用，以查找与 "低 CPU 使用率" 区域对齐的调用。 检测并行性问题。 |
| 调用属性 | 表               | 快速查找有关给定编译器或链接器调用的关键信息。 确定用于调用它的版本、工作目录或完整命令行。 |
| 时间线             | 图形               | 请参阅如何并行化生成的条形图。 一目了然地确定并行性问题和瓶颈。 配置 WPA，根据需要为条形分配不同的含义。 选择 "调用说明" 作为最后一组列，查看所有调用的颜色编码条形图。 它可帮助你快速识别使用原因的时间。 然后，放大并选择活动名称作为最后一组列，查看最长的部分。 |

## <a name="files"></a>Files

"文件" 视图用于：

- 确定最常包含的标头，并
- 帮助您决定要包含在预编译标头（PCH）中的内容。

### <a name="files-view-data-columns"></a>文件查看数据列

| 列名              | 说明 |
|--------------------------|-------------|
| ActivityName             | 发出此文件事件时正在进行的活动。 目前，此值始终为 "*分析*"。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 组件                | * |
| Count                    | * |
| 深度                    | 包含此文件的包含树中的从零开始的位置。 计数从包含树的根开始。 值0通常对应于 .c/.cpp 文件。 |
| ExclusiveDuration        | * |
| IncludedBy               | 包含当前文件的文件的完整路径。 |
| IncludedPath             | 当前文件的完整路径。 |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | 表示当前文件事件发出时间的时间戳。 |
| 工具                     | * |

\* 此列的值与 "[生成资源管理器](#build-explorer-view-data-columns)" 视图中的值相同。

### <a name="files-view-presets"></a>文件视图预设

| 预设名称 | 首选视图模式 | 使用方法 |
|-------------|---------------------|------------|
| 统计信息  | 表               | 通过以降序查看列表，查看哪些文件的聚合分析时间最高。 使用此信息可帮助您重建标头或确定要在 PCH 中包含的内容。 |

## <a name="functions"></a>函数

"函数" 视图用于标识代码生成时间过长的函数。

### <a name="functions-view-data-columns"></a>函数查看数据列

| 列名              | 说明 |
|--------------------------|-------------|
| ActivityName             | 发出此函数事件时正在进行的活动。 目前，此值始终为*microsoft.extensions.codegeneration*。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 组件                | * |
| Count                    | * |
| 持续时间                 | 此函数的代码生成活动的持续时间。 |
| FunctionName             | 正在生成代码的函数的名称。 |
| InvocationId             | * |
| StartTime                | 表示何时发出当前函数事件的时间戳。 |
| 工具                     | * |

\* 此列的值与 "[生成资源管理器](#build-explorer-view-data-columns)" 视图中的值相同。

### <a name="functions-view-presets"></a>函数视图预设

| 预设名称 | 首选视图模式 | 使用方法 |
|-------------|---------------------|------------|
| 统计信息  | 表               | 通过以降序查看列表，查看哪些函数的聚合代码生成时间最高。 它们可能提示你的代码 overuses 关键字 **__forceinline**的位置，或者某些函数可能太大。 |
| 时间线   | 图形               | 查看此条形图，了解生成时间最长的函数的位置和持续时间。 查看 "生成资源管理器" 视图中是否与瓶颈保持一致。 如果是这样，请采取适当的措施来减少代码生成时间，并使您的生成时间受益。 |

## <a name="see-also"></a>另请参阅

Build Insights\ 入门[ C++ ](/cpp/build-insights/get-started-with-cpp-build-insights)
[参考： vcperf 命令](vcperf-commands.md)\
[教程： Windows 性能分析器基础](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
