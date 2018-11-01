---
title: 配置 Windows XP 的程序
ms.date: 02/02/2018
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 73fc66c358f2bfa390177557da2f114f225cec1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582736"
---
# <a name="configuring-programs-for-windows-xp"></a>配置 Windows XP 的程序

由于 Visual Studio 支持多个平台工具集，可面向的操作系统和不受默认工具集的运行时库。 例如，通过切换平台工具集，您可以使用 C + + 11、 C + + 14 和支持的 Visual Studio 中的 Visual c + + 编译器的 C + + 17 语言增强功能来创建面向 Windows XP 和 Windows Server 2003 的应用。 可以还使用较旧的平台工具集来维护二进制兼容旧代码，并仍充分利用 Visual Studio IDE 的最新功能。

## <a name="install-the-windows-xp-platform-toolset"></a>安装 Windows XP 平台工具集

若要在 Visual Studio 2017 中获取的平台工具集和目标 Windows XP 和 Windows Server 2003 的组件，请运行 Visual Studio 安装程序。 在最初安装 Visual Studio 时或在选择**修改**若要修改现有安装，请确保**使用 c + + 的桌面开发**选择工作负荷。 在为此工作负荷的可选组件列表中，选择**针对 c + + 的 Windows XP 支持**，然后选择**安装**或**修改**。

## <a name="windows-xp-targeting-experience"></a>Windows XP 定向体验

包含在 Visual Studio 中的 Windows XP 平台工具集版本的 Windows 7 SDK，但它使用当前的 c + + 编译器。 它还将配置项目属性设置为适当的默认值，例如，兼容的链接器的低级别的定向规范。 仅 Windows 桌面应用程序使用 Windows XP 和 Windows Server 2003 上运行的 Windows XP 平台工具集创建的但这些应用还可以在较新的 Windows 操作系统上运行。

#### <a name="to-target-windows-xp"></a>若要针对 Windows XP

1. 在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“属性”。

1. 在中**属性页**对话框中的项目，在**配置属性** > **常规**，将**平台工具集**属性设置为所需的 Windows XP 工具集。 例如，选择**Visual Studio 2017 的 Windows XP (v141_xp)** 若要使用 Microsoft Visual c + + 2017年编译器适用于 Windows XP 和 Windows Server 2003 中创建的代码。

### <a name="c-runtime-support"></a>C++ 运行时支持

与 Windows XP 平台工具集、 C 运行时库 (CRT)、 c + + 标准库、 活动模板库 (ATL)、 并发运行时库 (ConCRT)、 并行模式库 (PPL)、 Microsoft 基础类库 (MFC) 和 c + + AMP （c + +加速大规模编程） 库包含适用于 Windows XP 和 Windows Server 2003 的运行时支持。 对于这些操作系统，最小支持的版本为 Windows XP Service Pack 3 (SP3) 的 x86 Windows XP Service Pack 2 (SP2) 对于 x64 和 Windows Server 2003 Service Pack 2 (SP2) 的 x86 和 x64。

这些库支持安装的 Visual Studio 中，具体取决于目标平台工具集：

|库|面向 Windows 桌面应用程序的默认平台工具集|默认平台工具集目标应用商店应用程序|面向 Windows XP、 Windows Server 2003 的 Windows XP 平台工具集|
|---|---|---|---|
|CRT|X|X|X|
|C++ 标准库|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> 应用程序用 C + + /cli CLI 和面向.NET Framework 4 运行 Windows XP 和 Windows Server 2003 上。

### <a name="differences-between-the-toolsets"></a>工具集之间的差异

由于平台和库支持的不同，使用 Windows XP 平台工具集的应用程序的开发体验不是为使用默认 Visual Studio 平台工具集的应用与已完成的。

- **C + + 语言功能**

   在 Visual Studio 2012 中实现的仅 c + + 语言功能支持的应用中的使用 v110\_xp 平台工具集。 在 Visual Studio 2013 中实现的仅 c + + 语言功能支持的应用中的使用 v120\_xp 平台工具集。 在 Visual Studio 2015 中实现的仅 c + + 语言功能支持的应用中的使用 v140\_xp 平台工具集。 生成使用较旧的平台工具集时，visual Studio 将使用相应的编译器。 要利用在该版本的编译器中实现的其他 c + + 语言功能，请使用最新的 Windows XP 平台工具集。

- **远程调试**

   Visual Studio 远程工具不支持在 Windows XP 或 Windows Server 2003 上的远程调试。 若要在 Windows XP 或 Windows Server 2003 上运行时调试应用程序，可以使用从较旧版本的 Visual Studio 调试器以本地或远程调试。 这类似于调试 Windows Vista 上的应用程序的体验，因为它是平台工具集的运行时目标，而不是远程调试的目标。

- **静态分析**

   Windows XP 平台工具集不支持静态分析，因为 Windows 7 SDK 和运行时库的 SAL 批注不兼容。 当你想要支持 Windows XP 或 Windows Server 2003 的应用程序执行静态分析时，可以暂时将解决方案切换为目标默认平台工具集来执行分析，并再切换回 Windows XP 平台工具集来生成应用程序。

- **调试 DirectX 图形**

   因为图形调试器不支持 Direct3D 9 API，它不能用于调试在 Windows XP 或 Windows Server 2003 上使用 Direct3D 的应用。 但是，如果应用程序可实现使用 Direct3D 10 或 Direct3D 11 API 的备用呈现器，则可以使用图形调试器来诊断有关这些 API 的使用情况的问题。

- **正在生成 HLSL**

   默认情况下，Windows XP 工具集不编译 HLSL 源代码文件。 若要编译 HLSL 文件，请下载并安装 2010 年 6 月发行的 DirectX SDK，然后设置项目的 VC 目录以将其包含在内。 有关详细信息，请参阅"DirectX SDK 不会注册 Include/Library 路径使用 Visual Studio 2010"部分[2010 年 6 月 DirectX SDK 下载页](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)。
