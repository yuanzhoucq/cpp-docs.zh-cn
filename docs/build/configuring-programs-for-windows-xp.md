---
title: 配置适用于 Windows XP 的程序
description: 如何在 Visual Studio 中安装C++和使用 Windows XP 工具集。
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440476"
---
# <a name="configuring-programs-for-windows-xp"></a>配置适用于 Windows XP 的程序

Visual Studio 支持多个平台工具集。 这意味着，可以将默认工具集不支持的操作系统和运行库作为目标。 例如，通过切换平台工具集，可以使用 Visual Studio 2017 C++编译器来创建面向 Windows XP 和 windows Server 2003 的应用。 还可以使用较旧的平台工具集来维护二进制兼容旧代码，同时仍然可以利用 Visual Studio IDE 的最新功能。

::: moniker range="vs-2019"

Visual Studio 2019 中提供的 v142 工具集不支持为 Windows XP 创建代码。 使用 Visual Studio 2017 v141_xp 工具集对 Windows XP 开发的支持作为 Visual Studio 安装程序中的单个组件选项提供。

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>安装 Windows XP 平台工具集

::: moniker range="<=vs-2017"

若要获取 Visual Studio 2017 平台工具集和组件以面向 Windows XP 和 Windows Server 2003，请运行 Visual Studio 安装程序。 首次安装 Visual Studio 或修改现有安装时，请确保选中 "**使用C++** 工作负荷进行桌面开发"。 在此工作负载的可选组件列表中，选择“针对 C++ 的 Windows XP 支持”，然后选择“安装”或“修改”。

::: moniker-end

::: moniker range="vs-2019"

若要获取 v141_xp 平台工具集和组件以面向 Windows XP 和 Windows Server 2003，请运行 Visual Studio 安装程序。 首次安装 Visual Studio 时，或修改现有安装时，请确保选中 "**使用C++** 工作负荷进行桌面开发"。 在 "**单个组件**" 选项卡中，在 "**编译器"、"生成工具" 和 "运行时**" 下，选择**Modify**  **C++ "Windows XP 对 VS 2017 （v141）工具的支持 \[不推荐使用）** "，然后选择 "**安装**"

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Windows XP 定向体验

Visual Studio 中包含的 Windows XP 平台工具集是 Windows 7 SDK 的一个版本，但它使用 Visual Studio 2017 C++编译器。 它还将项目属性配置为适当的默认值，例如，为低级别的定向规范兼容的链接器。 只有使用 Windows XP 平台工具集创建的 Windows 桌面应用程序可以在 Windows XP 和 Windows Server 2003 上运行。 这些应用还可以在最新的 Windows 操作系统上运行。

### <a name="to-target-windows-xp"></a>若要针对 Windows XP

1. 在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“属性”。

1. 在项目的 "**属性页**" 对话框中，选择 "**配置属性**" > **常规**"。 将 "**平台工具集**" 属性设置为首选的 Windows XP 工具集。 例如，选择“Visual Studio 2017 - Windows XP (v141_xp)”，通过使用 Visual Studio 2017 中的 Microsoft C++ 编译器为 Windows XP 和 Windows Server 2003 创建代码。

### <a name="c-runtime-support"></a>C++ 运行时支持

除了 Windows XP 平台工具集，多个库还包含对 Windows XP 和 Windows Server 2003 的运行时支持。 这些库包括： C 运行时库（CRT）、 C++标准库、活动模板库（ATL）、并发运行时库（ConCRT）、并行模式库（PPL）、MICROSOFT 基础类库（MFC）和C++ AMP （C++加速大规模编程）库。 对于这些操作系统，支持的最低版本为：适用于 x86 的 Windows XP Service Pack 3 （SP3）、适用于 x64 的 windows XP service pack 2 （SP2）以及适用于 x86 和 x64 的 Windows Server 2003 Service Pack 2 （SP2）。

这些库受通过 Visual Studio 安装的平台工具集的支持，具体取决于目标：

|库|面向 Windows 桌面应用程序的默认平台工具集|面向 Store 应用的默认平台工具集|面向 Windows XP 和 Windows Server 2003 的 Windows XP 平台工具集|
|---|---|---|---|
|CRT|X|X|X|
|C++ 标准库|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 用 C++/CLI 编写且面向 .NET Framework 4 的应用在 Windows XP 和 Windows Server 2003 上运行。

### <a name="differences-between-the-toolsets"></a>工具集之间的差异

由于平台和库支持之间的差异，使用 Windows XP 平台工具集的应用程序的开发体验与使用默认 Visual Studio 平台工具集的应用程序的开发体验并不完全相同。

- **C++ 语言功能**

   在使用 v110\_xp 平台工具集的应用中仅支持在 Visual Studio 2012 中实现的 C++ 语言功能。 在使用 v120\_xp 平台工具集的应用中仅支持在 Visual Studio 2013 中实现的 C++ 语言功能。 在使用 v140\_xp 平台工具集的应用中仅支持在 Visual Studio 2015 中实现的 C++ 语言功能。 使用C++ v141\_xp 平台工具集的应用程序仅支持在 Visual Studio 2017 中实现的语言功能。 Visual Studio 在使用较旧的平台工具集进行生成时会使用相应的编译器。 请使用最新的 Windows XP 平台工具集以利用在该版本的编译器中实现的其他 C++ 语言功能。

- **远程调试**

   Visual Studio 远程工具不支持在 Windows XP 或 Windows Server 2003 上进行远程调试。 若要在 Windows XP 或 Windows Server 2003 上本地或远程调试应用程序，请使用早期版本的 Visual Studio 中的调试器。 它类似于在 Windows Vista 上调试应用程序，该应用程序是平台工具集的运行时目标，而不是远程调试目标。

- **静态分析**

   Windows XP 平台工具集不支持静态分析，因为 Windows 7 SDK 的 SAL 批注和运行时库不兼容。 你仍可以在支持 Windows XP 或 Windows Server 2003 的应用上执行静态分析。 暂时切换解决方案以面向分析的默认平台工具集，然后切换回 Windows XP 平台工具集以生成应用程序。

- **调试 DirectX 图形**

   因为图形调试器不支持 Direct3D 9 API，所以它不能用于调试使用 Windows XP 或 Windows Server 2003 上的 Direct3D 的应用程序。 但是，如果应用基于 Direct3D 10 或 Direct3D 11 Api 实现了替代呈现器，则可以使用图形调试器诊断问题。

- **生成 HLSL**

   默认情况下，Windows XP 工具集不会编译 HLSL 源代码文件。 若要编译 HLSL 文件，请下载并安装 2010 年 6 月发行的 DirectX SDK，然后设置项目的 VC 目录以将其包含在内。 有关详细信息，请参阅 [2010 年 6 月 DirectX SDK 下载页](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)的“DirectX SDK 不会使用 Visual Studio 2010 注册 Include/Library 路径”部分。
