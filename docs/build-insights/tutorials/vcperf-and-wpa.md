---
title: 教程：vcperf 和 Windows 性能分析器
description: 关于如何使用 vcperf 和 WPA 分析C++生成跟踪的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323415"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>教程：vcperf 和 Windows 性能分析器

::: moniker range="<=vs-2017"

C++构建见解工具可在 Visual Studio 2019 中使用。 要查看此版本的文档，请将本文的可视化工作室**版本**选择器控件设置为 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range="vs-2019"

在本教程中，您将学习如何使用*vcperf.exe*收集C++生成的痕迹。 您还将了解如何在 Windows 性能分析器中查看此跟踪。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>第 1 步：安装和配置 Windows 性能分析器

WPA 是 Windows 评估和部署工具包 （ADK） 中可用的跟踪查看器。 它是一个单独的实用程序，不属于您可以使用 Visual Studio 安装程序安装的组件。

支持C++生成见解的 WPA 版本目前仅在 Windows ADK 预览版中提供。 要访问此预览版，您必须注册 Windows[预览版程序](https://insider.windows.com)。 您无需安装 Windows 10 预览版操作系统来获取 Windows ADK 预览。 您只需向 Windows 预览版计划注册您的 Microsoft 帐户。

### <a name="to-download-and-install-wpa"></a>下载并安装 WPA

注意：安装 Windows 性能分析器需要 Windows 8 或以上。

1. 浏览到 Windows ADK 预览预览[下载页面](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)。

1. 下载 Windows ADK 预览版。 它是磁盘映像。

1. 打开磁盘映像并运行*adksetup.exe*安装程序。

1. 当提示要安装的功能时，请选择**Windows 性能工具包**。 如果需要，您可以选择其他功能，但它们不需要安装 WPA。

   ![Windows 性能分析器安装程序的功能选择屏幕](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>配置生成见解

1. 启动 WPA。

1. 选择**窗口**>**选择表（实验）。**

1. 向下滚动到**诊断**部分。

1. 选择所有 MSVC 生成见解视图。

   ![Windows 性能分析器的表选择面板](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>第 2 步：使用 vcperf.exe 跟踪您的生成

要查看C++生成见解数据，首先通过以下步骤将其收集到跟踪文件中：

1. 在管理员模式下打开 Visual Studio 2019 的本机工具或交叉工具开发人员命令提示。 （右键单击"开始"菜单项，然后选择 **"以管理员** > **身份运行**更多"。

1. 在命令提示窗口中，输入以下命令：

   **vcperf.exe /启动_会话名称_**

   选择会话*名称的会话名称*。

1. 像您通常一样构建项目。 不需要使用相同的命令提示窗口来生成。

1. 在命令提示窗口中，输入以下命令：

   **vcperf.exe /停止_会话名称名称__跟踪文件.etl_**

   使用之前为*会话名称*选择的相同会话名称。 为*跟踪文件.etl*跟踪文件选择适当的名称。

以下是典型的*vcperf.exe*命令序列在开发人员命令提示窗口中的外观：

![一个简单的 vcperf.exe 使用方案](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>关于vcperf.exe的重要说明

- 启动或停止*vcperf.exe*跟踪需要管理员权限。 使用使用 **"作为管理员运行"** 打开的开发人员命令提示窗口。

- 一次只能运行一个跟踪会话。

- 请确保记住用于启动跟踪的会话名称。 在不知道正在运行的会话名称的情况下停止正在运行的会话可能很麻烦。

- 就像*cl.exe*和*link.exe*一样，命令行实用程序*vcperf.exe*包含在MSVC安装中。 不需要执行其他步骤即可获取此组件。

- *vcperf.exe*收集有关系统上运行的所有 MSVC 工具的信息。 因此，您不必从用于收集跟踪的同一命令提示启动生成。 可以从不同的命令提示符，甚至 Visual Studio 中生成项目。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>第 3 步：在 Windows 性能分析器中查看跟踪

启动 WPA 并打开您刚刚收集的跟踪。 WPA 应将其识别为C++生成见解跟踪，并且以下视图应出现在左侧的图形资源管理器面板中：

- 生成资源管理器
- 文件
- 函数

如果看不到这些视图，请仔细检查 WPA 配置是否正确，如[步骤 1](#configuration-steps)中所述。 通过将视图拖动到右侧的空分析窗口中，可以查看生成数据，如下所示：

![在 Windows 性能分析器中查看C++生成见解跟踪](media/wpa-viewing-trace.gif)

其他视图在"图形资源管理器"面板中可用。 当您对它们包含的信息感兴趣时，将它们拖到"分析"窗口中。 有用的视图是 CPU（采样）视图，它显示了整个生成中的 CPU 利用率。

## <a name="more-information"></a>详细信息

[教程：Windows 性能分析器基础知识](wpa-basics.md)\
了解可帮助您分析生成跟踪的常见 WPA 操作。

[参考： vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
*vcperf.exe*命令引用列出了所有可用的命令选项。

[参考：Windows 性能分析器视图](/cpp/build-insights/reference/wpa-views)\
有关 WPA 中C++生成见解视图的详细信息，请参阅本文。

[Windows 性能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)\
正式 WPA 文档网站。

::: moniker-end
