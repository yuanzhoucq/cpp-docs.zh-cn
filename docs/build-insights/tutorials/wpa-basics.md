---
title: 教程：Windows 性能分析器基础知识
description: 有关如何在 Windows 性能分析器中完成基本操作的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323407"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>教程：Windows 性能分析器基础知识

::: moniker range="<=vs-2017"

C++构建见解工具可在 Visual Studio 2019 中使用。 要查看此版本的文档，请将本文的可视化工作室**版本**选择器控件设置为 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range="vs-2019"

有效地使用C++生成见解需要了解 Windows 性能分析器 （WPA）。 本文可帮助您熟悉常见的 WPA 操作。 有关如何使用 WPA 的详细信息，请参阅 Windows[性能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)文档。

## <a name="change-the-view-mode"></a>更改视图模式

WPA 提供两种基本视图模式，可供您探索您的跟踪：

- 图形模式，和
- 表模式。

您可以使用视图窗格顶部的视图模式图标在它们之间切换：

![在图形模式和表模式之间切换。](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>选择预设

大多数C++生成见解 WPA 视图有多个预设供您选择。 您可以使用视图窗格顶部的下拉菜单选择所需的预设：

![选择预设。](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>放大或缩小

有些生成痕迹太大，很难找出细节。 要放大您感兴趣的区域，请右键单击图形并选择 **"缩放**"。 通过选择 **"撤消缩放"，** 您始终可以返回以前的设置。 此图像显示了使用所选内容和**缩放**命令放大图形部分的示例：

![放大图形。](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>按不同列分组

您可以自定义跟踪的显示方式。 单击视图窗格顶部的齿轮图标，然后重新排列生成资源管理器视图编辑器中的列。 在此对话框中黄线上方找到的列是数据行分组的列。 黄线上方的列是特殊的：在图形视图中，它显示在彩色条上。

此图像显示链接调用的示例条形图。 我们使用齿轮图标打开"生成资源管理器视图编辑器"对话框。 然后，我们将"组件"和"名称"列条目拖动到黄线上方。 更改配置以提高详细级别，并查看链接器内实际发生的情况：

![放大图形。](media/wpa-grouping.gif)

## <a name="see-also"></a>另请参阅

[教程：vcperf 和 Windows 性能分析器](vcperf-and-wpa.md)\
[参考： vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
[参考：Windows 性能分析器视图](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
