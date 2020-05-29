---
title: 教程：vcperf 和 Windows Performance Analyzer
description: 关于如何使用 vcperf 和 WPA 来分析 C++ 生成跟踪的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 724df913400abb6d33c333f0a16c20fb982769bc
ms.sourcegitcommit: 98139766b548c55181ff5ec5ad3bfd9db2bf5c89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83865047"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>教程：vcperf 和 Windows Performance Analyzer

::: moniker range="<=vs-2017"

Visual Studio 2019 中提供 C++ 生成见解工具。 若要查看此版本对应的文档，请将本文的 Visual Studio“版本”选择器控件设置为“Visual Studio 2019”。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range="vs-2019"

在本教程中，你将学习如何使用 vcperf.exe 来收集 C++ 生成跟踪。 此外，你还将学习如何在 Windows Performance Analyzer 中查看此跟踪。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>步骤 1：安装和配置 Windows Performance Analyzer

WPA 是 Windows 评估和部署工具包 (ADK) 中提供的跟踪查看器。 它是一个单独的实用工具，不属于可以用 Visual Studio 安装程序安装的组件。

目前，只有 Windows ADK Insider Preview 中提供支持 C ++ 生成见解的 WPA 版本。 若要访问此预览版，必须注册 [Windows 预览体验计划](https://insider.windows.com)。 不需要安装 Windows 10 Insider Preview 操作系统来获取 Windows ADK 预览版。 只需向 Windows 预览体验计划注册你的 Microsoft 帐户即可。

### <a name="to-download-and-install-wpa"></a>下载和安装 WPA 的具体步骤

注意：安装 Windows Performance Analyzer 需要 Windows 8 或更高版本的操作系统。

1. 转到 Windows ADK [下载页](https://docs.microsoft.com/windows-hardware/get-started/adk-install)。

1. 下载并安装最新版 Windows ADK。

1. 当提示选择要安装的功能时，请选中“Windows Performance Toolkit”。 可以根据需要选中其他功能，但这些功能并不是安装 WPA 所必需。

   ![Windows Performance Analyzer 安装程序的功能选择屏幕](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> 配置 WPA 的具体步骤

在 WPA 中查看 C++ 生成见解跟踪需要一个特殊的加载项。 若要安装此加载项，请按照以下步骤操作：

1. 通过下载下面的组件之一来获取此加载项。 不需要两个组件都下载。 请选择你认为最方便的。
    1. [Visual Studio 2019 版本 16.6 及更高版本](https://visualstudio.microsoft.com/downloads/)，或
    1. [C++ 生成见解 NuGet 包](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/)。

1. 将 `perf_msvcbuildinsights.dll` 文件复制到 WPA 安装目录中。
    1. 在 Visual Studio 2019 版本 16.6 及更高版本中，此文件位于以下位置：`C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}`。
    1. 在 C++ 生成见解 NuGet 包中，此文件位于以下位置：`wpa\{Architecture}`。
    1. 在上面的路径中，替换用大括号括起来的变量，如下所述：
        1. `{Edition}` 是 Visual Studio 2019 版本（如 Community、Professional 或 Enterprise）。
        1. `{Version}` 是 MSVC 版本。 请选择最高版本。
        1. `{Architecture}`：如果使用的是 64 位版 Windows，请选择“`x64`”。 否则，请选择“`x86`”。
    1. WPA 安装目录通常为 `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit`。

1. 在 WPA 安装目录中，打开 `perfcore.ini` 文件，并为 `perf_msvcbuildinsights.dll` 添加一个条目。

## <a name="step-2-trace-your-build-with-vcperfexe"></a>步骤 2：使用 vcperf.exe 跟踪生成

若要查看 C++ 生成见解数据，请先按照以下步骤操作，将数据收集到跟踪文件中：

1. 在管理员模式下，打开适用于 VS 2019 的 x64 或 x86 本机工具命令提示。 （右键单击“开始”菜单项，然后依次选择“更多” > “以管理员身份运行”。）
    1. 如果使用的是 64 位版 Windows，请选择“x64”。 否则，请选择“x86”。

1. 在命令提示符窗口中，输入以下命令：

   vcperf.exe /start SessionName

   为 SessionName 选择易记的会话名称。

1. 照常生成项目。 不需要使用相同的命令提示符窗口来生成项目。

1. 在命令提示符窗口中，输入以下命令：

   vcperf.exe /stop SessionName traceFile.etl 

   使用之前为 SessionName 选择的相同会话名称。 为 traceFile.etl 跟踪文件选择适当的名称。

下面展示了开发人员命令提示符窗口中的典型 vcperf.exe 命令序列：

![简单的 vcperf.exe 使用方案](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>关于 vcperf.exe 的重要说明

- 必须有管理员权限，才能启动或停止 vcperf 跟踪。 请使用通过“以管理员身份运行”打开的开发人员命令提示符窗口。

- 一次只能在一台计算机上运行一个跟踪会话。

- 请务必记住用于启动跟踪的会话名称。 在不知道会话名称的情况下停止正在运行的会话可能会很麻烦。

- 与 cl.exe 和 link.exe 一样，命令行实用工具 vcperf.exe 也包含在 MSVC 安装中。 获取此组件不需要执行任何额外步骤。

- vcperf.exe 收集关于在系统上运行的所有 MSVC 工具的信息。 因此，不必在用于收集跟踪的同一命令提示符中启动生成。 可以在不同的命令提示符中生成项目，甚至在 Visual Studio 中也可以。

### <a name="vcperfexe-is-open-source"></a>vcperf.exe 是开放源代码的

若要生成和运行你自己版本的 vcperf.exe，随时都可以从 [vcperf GitHub 存储库](https://github.com/microsoft/vcperf)中克隆它。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>步骤 3：在 Windows Performance Analyzer 中查看跟踪

启动 WPA，并打开刚刚收集的跟踪。 WPA 应该会将它识别为 C++ 生成见解跟踪，并且 Graph 浏览器面板左侧应该会显示以下视图：

- 生成资源管理器
- 文件
- 函数
- 模板实例化

如果看不到这些视图，请再次检查 WPA 是否按[第 1 步](#configuration-steps)中所述进行了正确配置。 可以通过将视图拖到右侧的空“分析”窗口来查看生成数据，如下所示：

![在 Windows Performance Analyzer 中查看 C++ 生成见解跟踪](media/wpa-viewing-trace.gif)

Graph 浏览器面板中还有其他视图。 如果对它们包含的信息感兴趣，请将它们拖到“分析”窗口中。 其中一个很有用的视图是“CPU (采样)”，它显示了整个生成过程中的 CPU 使用率。

## <a name="more-information"></a>详细信息

[教程：Windows Performance Analyzer 基础知识](wpa-basics.md)\
了解有助于分析生成跟踪的常见 WPA 操作。

[参考：vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
vcperf 命令参考列出了所有可用的命令选项。

[参考：Windows Performance Analyzer 视图](/cpp/build-insights/reference/wpa-views)\
若要详细了解 WPA 中的 C++ 生成见解视图，请参阅这篇文章。

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
WPA 官方文档网站。

::: moniker-end
