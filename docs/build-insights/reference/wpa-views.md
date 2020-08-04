---
title: 参考：Windows Performance Analyzer 视图
description: Windows Performance Analyzer 中可用的 C++ Build Insights 视图的参考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8bbcc43ef19adfd85a3679a2136d471333a74a10
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224092"
---
# <a name="reference-windows-performance-analyzer-views"></a>参考：Windows Performance Analyzer 视图

::: moniker range="<=vs-2017"

Visual Studio 2019 中提供 C++ 生成见解工具。 若要查看此版本对应的文档，请将本文的 Visual Studio“版本”选择器控件设置为“Visual Studio 2019”。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range="vs-2019"

本文详细介绍了 Windows Performance Analyzer (WPA) 中可用的每个 C++ Build Insights 视图。 使用此页可查找：

- 数据列说明；以及
- 每个视图的可用预设，包括其预期用途和首选视图模式。

如果你是刚开始接触 WPA，建议先了解[适用于 C++ Build Insights 的 WPA 基础知识](/cpp/build-insights/tutorials/wpa-basics)。

## <a name="build-explorer"></a>生成资源管理器

“生成资源管理器”视图用于：

- 诊断并行度问题；
- 确定生成时间是否由解析、代码生成或链接所支配；以及
- 识别瓶颈和耗时异常长的生成活动。

### <a name="build-explorer-view-data-columns"></a>“生成资源管理器”视图数据列

| 列名 | 描述 |
|-|-|
| BuildTimelineDescription | 发生当前活动或属性的时间线的文本说明。 |
| BuildTimelineId          | 发生当前活动或属性的时间线的标识符（从零开始）。 |
| 组件                | 当前事件发出时正在编译或链接的组件。 如果没有组件与这一事件关联，此列的值为 \<Invocation X Info\>。 X 是在事件发出时执行的调用的唯一数值标识符。 此标识符与这一事件的 InvocationId 列中的标识符相同。 |
| 计数                    | 此数据行表示的活动或属性的数量。 此值始终为 1，只在对多行进行分组的聚合方案中有用。 |
| ExclusiveCPUTime         | 此活动使用的 CPU 时间量（以毫秒为单位）。 此时间量不包括子活动所用的时间。 |
| ExclusiveDuration        | 活动的持续时间（以毫秒为单位）。 此时间量不包括子活动的持续时间。 |
| InclusiveCPUTime         | 此活动和所有子活动使用的 CPU 时间量（以毫秒为单位）。 |
| InclusiveDuration        | 此活动的持续时间（以毫秒为单位），包括所有子活动的持续时间。 |
| InvocationDescription    | 发生此事件的调用的文本说明。 此说明包括它是 cl.exe 还是 link.exe，以及唯一数值调用标识符。 它还包括在调用期间编译或链接的组件的完整路径（若有）。 对于没有生成任何组件的调用或生成多个组件的调用，路径是空白的。 此调用标识符与 InvocationId 列中的标识符相同。 |
| InvocationId             | 发生此事件的调用的唯一数值标识符。 |
| “属性”                     | 此事件表示的活动或属性的名称。 |
| 时间                     | 标识事件发生时间的时间戳。 |
| 工具                     | 发生此事件时执行的工具。 此列的值为 CL 或 Link。 |
| 类型                     | 当前事件的类型。 此值为 Activity 或 Property。 |
| “值”                    | 如果当前事件是属性，则此列包含属性值。 如果当前事件是活动，则此列保留为空白。 |

### <a name="build-explorer-view-presets"></a>“生成资源管理器”视图预设

| 预设名称           | 首选视图模式 | 使用方法 |
|-----------------------|---------------------|------------|
| 活动统计信息   | 图形/表       | 使用此预设来查看所有“生成资源管理器”活动的聚合统计信息。 在表模式下，可以一目了然地判断生成是否由解析、代码生成或链接器所支配。 每个活动的聚合持续时间按降序排序。 通过展开顶部节点进行钻取，可以轻松地找到哪些调用在这些排名靠前的活动中花费的时间最多。 如果愿意，可以调整 WPA 设置，以显示平均值或其他类型的聚合。 在图形模式下，可以查看在生成过程中每个活动何时处于活动状态。 |
| 调用           | Graph               | 在图形视图中向下滚动查看按开始时间排序的调用列表。 可以将它与“CPU (采样)”视图一起使用，以查找与低 CPU 使用率区域匹配的调用。 检测并行度问题。 |
| 调用属性 | 表               | 快速查找有关给定编译器或链接器调用的关键信息。 确定它的版本、工作目录或用于调用它的完整命令行。 |
| 时间线             | Graph               | 查看关于生成如何并行化的条形图。 一眼就能识别并行度问题和瓶颈。 将 WPA 配置为根据你的需要为条形分配不同的含义。 选择“调用说明”作为最后一个分组列，以查看所有调用的彩色编码条形图。 它可以帮助你快速识别耗费时间的主要原因。 然后，放大并选择活动名称作为最后一个分组列，以查看最长的部分。 |

## <a name="files"></a>文件

“文件”视图用于：

- 确定最常包含的头；以及
- 帮助你决定要在预编译头 (PCH) 中包含什么。

### <a name="files-view-data-columns"></a>“文件”视图数据列

| 列名              | 描述 |
|--------------------------|-------------|
| ActivityName             | 发出此文件事件时正在进行的活动。 目前，此值始终为 Parsing。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 组件                | * |
| 计数                    | * |
| 深度                    | 在包含树中找到此文件的位置（从零开始）。 计数从包含树的根开始。 值 0 通常对应于 .c/.cpp 文件。 |
| ExclusiveDuration        | * |
| IncludedBy               | 包含当前文件的文件的完整路径。 |
| IncludedPath             | 当前文件的完整路径。 |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | 表示当前文件事件发出时间的时间戳。 |
| 工具                     | * |

\* 此列的值与[“生成资源管理器”](#build-explorer-view-data-columns)视图中的值相同。

### <a name="files-view-presets"></a>“文件”视图预设

| 预设名称 | 首选视图模式 | 使用方法 |
|-------------|---------------------|------------|
| 统计信息  | 表               | 查看按降序排序的列表，了解哪些文件的聚合分析时间最长。 使用此信息来帮助你重新构建头或决定要在 PCH 中包含什么。 |

## <a name="functions"></a>函数

“函数”视图用于标识代码生成时间过长的函数。

### <a name="functions-view-data-columns"></a>“函数”视图数据列

| 列名              | 描述 |
|--------------------------|-------------|
| ActivityName             | 发出此函数事件时正在进行的活动。 目前，此值始终为 CodeGeneration。 |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| 组件                | * |
| 计数                    | * |
| 持续时间                 | 此函数的代码生成活动的持续时间。 |
| FunctionName             | 正在生成代码的函数的名称。 |
| InvocationId             | * |
| StartTime                | 表示当前函数事件发出时间的时间戳。 |
| 工具                     | * |

\* 此列的值与[“生成资源管理器”](#build-explorer-view-data-columns)视图中的值相同。

### <a name="functions-view-presets"></a>“函数”视图预设

| 预设名称 | 首选视图模式 | 使用方法 |
|-------------|---------------------|------------|
| 统计信息  | 表               | 查看按降序排序的列表，了解哪些函数的聚合代码生成时间最长。 它们可能暗示代码在哪些地方过度使用了 `__forceinline` 关键字，或者某些函数可能太大了。 |
| 时间线   | Graph               | 查看此条形图，了解生成时间最长的函数的位置和持续时间。 确定它们是否与“生成资源管理器”视图中的瓶颈匹配。 如果匹配，则采取适当的措施来缩短代码生成时间，并有利于生成时间。 |

## <a name="see-also"></a>请参阅

[C++ Build Insights 入门](/cpp/build-insights/get-started-with-cpp-build-insights)\
[参考：vcperf 命令](vcperf-commands.md)\
[教程：Windows Performance Analyzer 基础知识](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
