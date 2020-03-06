---
title: 教程： Windows 性能分析器基础知识
description: 有关如何在 Windows 性能分析器中完成基本操作的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f197e7dfd852cd66039f7279f90e42b0cf75fd86
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333886"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>教程： Windows 性能分析器基础知识

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 中提供了生成见解工具。 若要查看该版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

有效C++使用生成见解需要了解 Windows 性能分析器（WPA）。 本文可帮助你熟悉常见的 WPA 操作。 有关如何使用 WPA 的详细信息，请参阅[Windows 性能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)文档。

## <a name="change-the-view-mode"></a>更改视图模式

WPA 提供两种基本的视图模式供您浏览跟踪：

- graph 模式和
- 表模式。

您可以使用 "视图" 窗格顶部的 "视图模式" 图标在它们之间进行切换：

![在关系图模式和表模式间切换。](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>选择预设

大多数C++生成见解 WPA 视图都有多个预设供你选择。 您可以使用 "视图" 窗格顶部的下拉菜单来选择所需预设：

![选择预设。](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>放大和缩小

某些生成跟踪很大，因此很难提供详细信息。 若要放大感兴趣的区域，请右键单击关系图，然后选择 "**缩放**"。 您始终可以通过选择 "**撤消缩放**" 返回到以前的设置。 此图显示了使用选择和**缩放**命令放大关系图的某个部分的示例：

![放大关系图。](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>按不同列分组

您可以自定义跟踪的显示方式。 单击视图窗格顶部的齿轮图标，然后在 "生成资源管理器视图编辑器" 中重新排列这些列。 此对话框中的黄色行上方的列是对数据行进行分组所依据的列。 黄色线条上方的列是特殊的：在图形视图中，它显示在彩色条上。

此图显示了链接调用的示例条形图。 我们使用齿轮图标打开 "生成资源管理器视图编辑器" 对话框。 然后，将 "组件" 和 "名称" 列项拖至黄色行的上方。 更改配置以提高详细程度，并查看链接器中实际发生的情况。

![放大关系图。](media/wpa-grouping.gif)

## <a name="see-also"></a>另请参阅

[教程： vcperf 和 Windows 性能分析器](vcperf-and-wpa.md)\
[参考： vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
[参考： Windows 性能分析器视图](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
