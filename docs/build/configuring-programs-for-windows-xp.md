---
title: 配置适用于 Windows XP 的程序
ms.date: 05/16/2019
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 55753737b4868f33487ed980eaf37a8801f59638
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450700"
---
# <a name="configuring-programs-for-windows-xp"></a>配置适用于 Windows XP 的程序

因为 Visual Studio 支持多个平台工具集，所以可以面向不受默认工具集支持的操作系统和运行时库。 例如，通过切换平台工具集，可以在 Visual Studio 中使用受 MSVC 编译器支持的 C++11、C++14 和 C++17 语言增强来创建面向 Windows XP 和 Windows Server 2003 的应用。 还可以使用较旧的平台工具集来维护二进制兼容旧代码，同时仍然可以利用 Visual Studio IDE 的最新功能。

Visual Studio 2019 及更高版本不支持使用 v142 工具集为 Windows XP 创建代码。 支持使用 Visual Studio 2017 中附带的 v141 工具集进行 Windows XP 开发，该支持作为 Visual Studio 安装程序中的可选组件提供。

## <a name="install-the-windows-xp-platform-toolset"></a>安装 Windows XP 平台工具集

要获取平台工具集和组件以在 Visual Studio 2017 中针对 Windows XP 和 Windows Server 2003 进行开发，请运行 Visual Studio 安装程序。 在最初安装 Visual Studio 时或选择“修改”以修改现有安装时，请确保选择“使用 C++ 的桌面开发”工作负载   。 在此工作负载的可选组件列表中，选择“针对 C++ 的 Windows XP 支持”，然后选择“安装”或“修改”    。

## <a name="windows-xp-targeting-experience"></a>Windows XP 定向体验

Visual Studio 中内含的 Windows XP 平台工具集是 Windows 7 SDK 的一个版本，但它使用当前的 C++ 编译器。 它还将项目属性配置为适当的默认值，例如，为低级别的定向规范兼容的链接器。 只有通过使用 Windows XP 平台工具集创建的 Windows 桌面应用才能在 Windows XP 和 Windows Server 2003 上运行，不过这些应用也可以在更新的 Windows 操作系统上运行。

#### <a name="to-target-windows-xp"></a>若要针对 Windows XP

1. 在“解决方案资源管理器”  中，打开项目的快捷菜单，然后选择“属性”  。

1. 在项目的“属性页”对话框中，在“配置属性” > “常规”下，将“平台工具集”属性设置为所需的 Windows XP 工具集     。 例如，选择“Visual Studio 2017 - Windows XP (v141_xp)”，通过使用 Visual Studio 2017 中的 Microsoft C++ 编译器为 Windows XP 和 Windows Server 2003 创建代码  。

### <a name="c-runtime-support"></a>C++ 运行时支持

Windows XP 平台工具集、C 运行库 (CRT)、C++ 标准库、活动模板库 (ATL)、并发运行时库 (ConCRT)、并行模式库 (PPL)、Microsoft 基础类库 (MFC) 和 C++ AMP（C++ 加速大规模编程）库均包括对 Windows XP 和 Windows Server 2003 的运行时支持。 对于这些操作系统，支持的最低版本是适用于 x86 的 Windows XP Service Pack 3 (SP3)、适用于 x64 的 Windows XP Service Pack 2 (SP2) 以及适用于 x86 和 x64 的 Windows Server 2003 Service Pack 2 (SP2)。

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

由于平台和库支持的不同，使用 Windows XP 平台工具集的应用的开发体验不及使用默认的 Visual Studio 平台工具集的应用完整。

- **C++ 语言功能**

   在使用 v110\_xp 平台工具集的应用中仅支持在 Visual Studio 2012 中实现的 C++ 语言功能。 在使用 v120\_xp 平台工具集的应用中仅支持在 Visual Studio 2013 中实现的 C++ 语言功能。 在使用 v140\_xp 平台工具集的应用中仅支持在 Visual Studio 2015 中实现的 C++ 语言功能。 Visual Studio 在使用较旧的平台工具集进行生成时会使用相应的编译器。 请使用最新的 Windows XP 平台工具集以利用在该版本的编译器中实现的其他 C++ 语言功能。

- **远程调试**

   Visual Studio 远程工具不支持在 Windows XP 或 Windows Server 2003 上进行远程调试。 对于在 Windows XP 或 Windows Server 2003 上运行的应用，若要对其进行调试，可使用来自 Visual Studio 较早版本的调试器，以本地或远程方式对其进行调试。 这类似于调试 Windows Vista 上的应用程序的体验，因为它是平台工具集的运行时目标，而不是远程调试的目标。

- **静态分析**

   Windows XP 平台工具集不支持静态分析，因为 Windows 7 SDK 的 SAL 批注和运行时库不兼容。 如果想对支持 Windows XP 或 Windows Server 2003 的应用执行静态分析，可以临时将解决方案切换为针对目标默认平台工具集，从而进行分析，然后再切换回 Windows XP 平台工具集来构建应用。

- **调试 DirectX 图形**

   因为图形调试器不支持 Direct3D 9 API，所以它不能用于调试在 Windows XP 或 Windows Server 2003 上使用 Direct3D 的应用。 但是，如果应用程序可实现使用 Direct3D 10 或 Direct3D 11 API 的备用呈现器，则可以使用图形调试器来诊断有关这些 API 的使用情况的问题。

- **生成 HLSL**

   默认情况下，Windows XP 工具集不编译 HLSL 源代码文件。 若要编译 HLSL 文件，请下载并安装 2010 年 6 月发行的 DirectX SDK，然后设置项目的 VC 目录以将其包含在内。 有关详细信息，请参阅 [2010 年 6 月 DirectX SDK 下载页](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)的“DirectX SDK 不会使用 Visual Studio 2010 注册 Include/Library 路径”部分。
