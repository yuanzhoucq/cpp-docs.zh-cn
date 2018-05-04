---
title: 适用于 Windows XP 配置程序 |Microsoft 文档
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a846ea5508173ce0e383b1c4b8798b896ae5be0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-programs-for-windows-xp"></a>适用于 Windows XP 配置程序

由于 Visual Studio 支持多个平台工具集，则可以面向操作系统和不受默认工具集的运行时库。 例如，通过切换平台工具集，你可以使用 C + + 11、 C + + 14 中和 Visual Studio 中的 Visual c + + 编译器支持的 C + + 17 语言增强功能以便创建面向的应用[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 你可以还使用较旧的平台工具集来维护二进制兼容旧代码，同时仍然可以利用 Visual Studio IDE 的最新功能。

## <a name="install-the-windows-xp-platform-toolset"></a>安装 Windows XP 平台工具集
若要获取的平台工具集和目标组件[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]在 Visual Studio 2017，运行 Visual Studio 安装程序。 在最初安装 Visual Studio 时或当你选择**修改**若要修改现有安装，请确保**使用 c + + 桌面开发**选择工作负荷。 在此工作负荷的可选组件的列表中，选择**c + + 的 Windows XP 支持**，然后选择**安装**或**修改**。

## <a name="windows-xp-targeting-experience"></a>Windows XP 定向体验

Visual Studio 中包含 Windows XP 平台工具集，则的版本[!INCLUDE[win7](../build/includes/win7_md.md)]SDK，但它使用当前的 c + + 编译器。 它还将配置为适当的默认值，例如，兼容的链接器为低级别的定向规范的项目属性。 只有通过使用 Windows XP 平台工具集创建的桌面应用程序运行的 Windows[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]，但是这些应用程序也可以在较新的 Windows 操作系统上运行。

#### <a name="to-target-windows-xp"></a>若要针对 Windows XP

1. 在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“属性”。

1. 在**属性页**对话框中的项目中，在**配置属性** > **常规**，将其设置**平台工具集**到所需的 Windows XP 工具集的属性。 例如，选择**Visual Studio 2017-Windows XP (v141_xp)** 创建代码[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]通过使用 Microsoft Visual c + + 2017年编译器。

### <a name="c-runtime-support"></a>C++ 运行时支持

以及 Windows XP 平台工具集、 C 运行库 (CRT)、 c + + 标准库、 活动模板库 (ATL)、 并发运行时库 (ConCRT)、 并行模式库 (PPL)、 Microsoft 基础类库 (MFC) 和 c + + AMP （c + +加速大规模编程） 库包括对运行时支持[!INCLUDE[winxp](../build/includes/winxp_md.md)]和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 对于这些操作系统，最小支持的版本为[!INCLUDE[winxp](../build/includes/winxp_md.md)]适用于 x86、 Service Pack 3 (SP3)[!INCLUDE[winxp](../build/includes/winxp_md.md)]对于 x64，Service Pack 2 (SP2) 和[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]适用于 x86 和 x64 的 Service Pack 2 (SP2)。

安装 Visual Studio 中，具体取决于目标平台工具集支持这些库：

|库|面向 Windows 桌面应用程序的默认平台工具集|默认平台工具集目标应用商店应用程序|面向 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的 Windows XP 平台工具集|
|---|---|---|---|
|CRT|X|X|X|
|C++ 标准库|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 用 C++/CLI 编写且面向 .NET Framework 4 的应用程序在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上运行。

### <a name="differences-between-the-toolsets"></a>工具集之间的差异

由于平台和库支持不同，使用 Windows XP 平台工具集的应用程序的开发体验不为使用默认 Visual Studio 平台工具集的应用与已完成。

- **C + + 语言功能**

   在 Visual Studio 2012 中实现的仅 c + + 语言功能支持的应用程序使用 v110\_xp 平台工具集。 在 Visual Studio 2013 中实现的仅 c + + 语言功能支持的应用程序使用 v120\_xp 平台工具集。 在 Visual Studio 2015 中实现的仅 c + + 语言功能支持的应用程序使用 v140\_xp 平台工具集。 在构建使用较旧的平台工具集时，visual Studio 将使用相应的编译器。 使用最新的 Windows XP 平台工具集以利用在该版本的编译器中实现的其他 c + + 语言功能。

- **远程调试**

   Visual Studio 远程工具不支持上的远程调试[!INCLUDE[winxp](../build/includes/winxp_md.md)]或[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]。 若要调试的应用程序运行时[!INCLUDE[winxp](../build/includes/winxp_md.md)]或[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]，你可以使用从较旧版本的 Visual Studio 调试器调试本地或远程调试它。 这类似于调试 Windows Vista 上的应用程序的体验，因为它是平台工具集的运行时目标，而不是远程调试的目标。

- **静态分析**

   Windows XP 平台工具集不支持静态分析，因为 [!INCLUDE[win7](../build/includes/win7_md.md)] SDK 的 SAL 批注和运行时库不兼容。 如果想对支持 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的应用程序执行静态分析，可以临时将解决方案切换为针对目标默认平台工具集来进行分析，然后再切换回 Windows XP 平台工具集来构建应用程序。

- **调试 DirectX 图形**

     因为图形调试器不支持 Direct3D 9 API，所以它不能用于调试在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上使用 Direct3D 的应用程序。 但是，如果应用程序可实现使用 Direct3D 10 或 Direct3D 11 API 的备用呈现器，则可以使用图形调试器来诊断有关这些 API 的使用情况的问题。

- **正在生成 HLSL**

   默认情况下，Windows XP 工具集不编译 HLSL 源代码文件。 若要编译 HLSL 文件，请下载并安装 2010 年 6 月发行的 DirectX SDK，然后设置项目的 VC 目录以将其包含在内。 有关详细信息，请参阅"DirectX SDK 未注册使用 Visual Studio 2010 的 Include/Library 路径"部分[2010 年 6 月 DirectX SDK 下载页](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)。
