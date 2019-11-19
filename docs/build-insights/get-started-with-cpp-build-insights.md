---
title: C++生成见解入门
description: 概述如何使用C++生成时性能分析工具，这些工具是生成见解的一部分。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c31d317cd7b9c6465362e3e532db2128303f602
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633224"
---
# <a name="get-started-with-c-build-insights"></a>C++生成见解入门

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 中提供了生成见解工具。 若要查看该版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights 是一系列工具，提供对 Microsoft Visual C++ （MSVC）工具链的更多可见性。 这些工具收集有关您C++的生成的数据，并以可以帮助您回答常见问题的格式提供这些信息，如：

- 我的生成是否足以并行化？
- 我应将预编译标头（PCH）包含哪些内容？
- 我是否应重点关注特定瓶颈以提高生成速度？

这项技术的两个主要组件是用于 Windows 性能分析器（WPA）跟踪查看器的命令行实用程序*vcperf*和外接程序。 实用工具用于收集生成的跟踪，而外接程序允许您在 WPA 中查看它们。 按照以下步骤开始使用这两个工具。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>步骤1：安装和配置 Windows 性能分析器

WPA 是 Windows 评估和部署工具包（ADK）中提供的跟踪查看器。 它是一个独立的实用工具，不是可以使用 Visual Studio 安装程序安装的组件的一部分。

支持C++生成见解的 WPA 版本目前仅在 Windows ADK 有问必答预览版中提供。 若要访问此预览版，你必须注册[Windows 预览体验计划](https://insider.windows.com)。 不需要安装 Windows 10 预览体验版预览版操作系统即可获取 Windows ADK 预览版。 只需向 Windows 预览体验计划注册 Microsoft 帐户。

### <a name="to-download-and-install-wpa"></a>下载并安装 WPA

1. 浏览到 Windows ADK 有问必答 Preview[下载页](https://www.microsoft.com/software-download/windowsinsiderpreviewADK)。

1. 下载 Windows ADK 有问必答 Preview。 它是磁盘映像。

1. 打开磁盘映像并运行*adksetup*安装程序。

1. 当系统提示你输入要安装的功能时，请选择 " **Windows 性能工具包**"。 你可以选择其他功能（如果需要），但不需要安装 WPA。

   ![Windows 性能分析器安装程序的 "功能选择" 屏幕](media/wpa-installation.png)

### <a name="configuration-steps"></a>配置 Build Insights

1. 启动 WPA。

1. 选择 "**窗口**" >**选择表（实验性）** 。

1. 向下滚动到 "**诊断**" 部分。

1. 选择所有 MSVC Build Insights 视图。

   ![Windows 性能分析器的表选择面板](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>步骤2：通过 vcperf 跟踪生成

若要C++查看 Build Insights 数据，请先按照以下步骤将其收集到跟踪文件中：

1. 在管理员模式下打开本机工具或跨工具开发人员命令2019提示。 （右键单击 "开始" 菜单项并选择 "**更多** > "**以管理员身份运行**"。）

1. 在命令提示符窗口中，输入以下命令：

   **vcperf/start _SessionName_**

   选择*要记住的会话*名称。

1. 按常规方式生成项目。 您无需使用同一个命令提示符窗口来生成。

1. 在命令提示符窗口中，输入以下命令：

   **vcperf/stop _SessionName_ _traceFile_**

   使用之前为*SessionName*选择的会话名称。 为*traceFile*跟踪文件选择适当的名称。

下面是典型的*vcperf*命令序列在 "开发人员命令提示" 窗口中的外观：

![简单的 vcperf 使用方案](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>有关 vcperf 的重要说明

- 需要管理员权限才能启动或停止*vcperf*跟踪。 使用通过 "以**管理员身份运行**" 打开的 "开发人员命令提示" 窗口。

- 一次只能有一个跟踪会话在计算机上运行。

- 请确保记住用于启动跟踪的会话名称。 停止正在运行的会话时，无需知道其名称，这可能会很麻烦。

- 与*cl* *和 node.js*一样，命令行实用程序*vcperf*包含在 MSVC 安装中。 获取此组件不需要执行其他步骤。

- *vcperf*收集有关你的系统上运行的所有 MSVC 工具的信息。 因此，你无需从用于收集跟踪的相同命令提示符中启动生成。 你可以从不同的命令提示符，甚至在 Visual Studio 中生成项目。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>步骤3：在 Windows 性能分析器中查看跟踪

启动 WPA 并打开刚刚收集的跟踪。 WPA 应将C++其识别为 Build Insights 跟踪，并且以下视图应显示在左侧的图形资源管理器面板中：

- 生成资源管理器
- 文件
- 函数

如果看不到这些视图，请仔细检查是否已正确配置 WPA，如[步骤 1](#configuration-steps)中所述。 可以通过将视图拖动到右侧的空 "分析" 窗口来查看生成数据，如下所示：

![在 Windows C++性能分析器中查看 Build Insights 跟踪](media/wpa-viewing-trace.gif)

图形资源管理器面板中提供了其他视图。 如果对所包含的信息感兴趣，请将其拖动到 "分析" 窗口。 这是一种很有用的视图，它是 CPU （采样）视图，在整个生成过程中显示 CPU 使用率。

## <a name="more-information"></a>更多信息

[Windows 性能分析器基础知识](wpa-basics.md)\
了解可帮助您分析生成跟踪的常见 WPA 操作。

[vcperf 引用](vcperf-reference.md)\
*Vcperf*命令引用列出了所有可用的命令选项。

[Windows 性能分析器视图参考](wpa-views-reference.md)\
请参阅此文，了解有关 WPA C++中的生成见解视图的详细信息。

[Windows 性能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)\
官方 WPA 文档网站。

::: moniker-end
