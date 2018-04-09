---
title: C + + 中 Windows 编程概述 |Microsoft 文档
ms.custom: ''
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e00159c828a87eba58920f90b6cd73d1b216232
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2018
---
# <a name="overview-of-windows-programming-in-c"></a>C++ 中 Windows 编程概述

你可以使用 Visual c + + 编写在 (x 86、 x64 或 ARM），Windows PC 上运行的程序的许多类型在 Windows server，在云中，或在 Xbox 上。 编写良好的 c + + 程序具有这些特性：
- 高效的内存要求
- 节约功耗 
- 能够充分利用多核和众核设备
- 能够执行图形处理单元 (GPU) 上的常规计算   
- 能够利用硬件中的其他最新的技术进步。

Windows 应用有好几大类别可以使用 Visual C ++ 进行开发。 这些类别具有不同的编程模型或应用模型，这在年中引入了。 每个模型使用不同的库和 Api 提供对平台的访问和创建用户界面，例如窗口和对话框。 可在任何这些类别，有几个限制适用于 UWP 的 c + + 标准库以及第三方库。

- [Windows 通用应用](#BK_WindowsUniversal)。 Windows 8 引入了第三类 Windows 应用，并且该类别的应用在 Windows 10 中继续受支持。 这些应用通常被认为只是“Windows 应用”，并且它们包括面向各种设备的桌面和移动应用。 通过使用 Windows 运行时库 (WRL)，可以使用 C ++/CX 或标准的 C++ 和 COM 编写这些应用，C ++/CX 是 C++ 的一种方言，支持 Windows 运行时开发。 虽然在 Windows 10 中，用户可以选择在桌面窗口中运行这些应用，但其实它们的最初设计是用于运行全屏幕。 这些应用面向触摸设备，但如果用户爱好或触摸屏不可用，也可以使用鼠标进行操作。 从 Microsoft 应用商店中，因此，导致它们被称为"存储"应用分发这些应用。

UWP 应用将能够在所有 Windows 10 设备，例如平板电脑和移动手机，以及在桌面上运行。 在桌面上，它们能够作为桌面窗口运行而不始终运行全屏幕。 这些应用还可以在 Xbox 上以及在将来使用的设备上运行。  UWP 应用的运行 Windows 运行时，它提供用户界面元素、 服务和在 Windows 支持的各种硬件设备的接口。  

你可以编写 UWP 应用在 C + + /CX 中，c + +，方言可以使用[C + + /cli WinRT 库](https://moderncpp.com/)在某些情况下。 UWP 应用编译为本机代码和具有 XAML 用户界面，或使用 DirectX。 用本机代码可使用这些用其他语言编写的 UWP 应用程序编写的 Windows 运行时组件。 有关详细信息，请参阅[在 c + + 中创建通用 Windows 平台应用](http://go.microsoft.com/fwlink/?LinkID=534976)，[创建第一个 UWP 游戏使用 DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656)，和[c + + 创建 Windows 运行时组件](http://go.microsoft.com/fwlink/p/?LinkId=244658)。

   此类别还包括在服务器和云编程的上下文中使用 C++ 编写核心组件和计算代码。 有时，还会使用 C++ 编写核心服务器或云应用程序的性能强化代码以最大化性能。 可以将此类代码编译为 DLL，并通过 C# 或 Visual Basic 使用它。

- **.NET framework 应用程序**。 大多数 .NET Framework 应用程序都是使用 C# 或 Visual Basic 编写的，但也可以使用 C++/CLI（Visual C++ 中的/clr 编译器选项）编写。 我们建议在包含托管和本机代码的较大应用程序中使用 C++/CLI 编写最小互操作层。

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

使用 Windows 10，应用程序能够在所有 Windows 10 设备（如平板电脑和移动电话）上以及在桌面上运行。 在桌面上，它们能够作为桌面窗口运行而不始终运行全屏幕。 这些应用还可以在 Xbox 上以及在将来使用的设备上运行。  这两种类型的应用的编程模型不同于 Win32 桌面应用程序。 这些 Windows 应用可以在 Windows 运行时上运行，Windows 运行时可以为这些应用提供用户界面元素和重要服务以及为受支持的各种硬件设备提供接口。 这些应用编译为本机代码，具有 XAML 用户界面，或使用 DirectX。 你还可以在其他 Windows 应用可以使用的本机代码中编写 Windows 运行时组件，其中包括在 C#、 Visual Basic 或 JavaScript 编写的应用程序。 有关详细信息，请参阅[在 c + + 中创建的 UWP"Hello world"应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)，[使用 DirectX 创建简单的 UWP 游戏](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)，和[c + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

> [!TIP]
> 对于 Windows 10 中，你可以使用桌面应用转换器你现有桌面应用程序打包以部署通过 Microsoft 应用商店。 有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)（在 Centennial 项目中使用 Visual C++ 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。

有关通用 Windows 平台的示例，请参阅 [GitHub 上的 Windows 通用示例](https://github.com/Microsoft/Windows-universal-samples)

如果你有现有的 Windows 8.1 项目并想要将其移植到 Windows 10，请参阅[移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)。 如果将现有的经典 Win32 桌面库和代码，你想要将集成到 UWP 应用，请参阅[如何： 在通用 Windows 平台应用中使用现有 c + + 代码](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)。

有关详细信息 UWP 一般情况下，请参阅[什么是通用 Windows 平台 (UWP) 应用？](/windows/uwp/get-started/whats-a-uwp)。

所有这些概念的详细信息，请参阅[Windows 通用应用指南](http://go.microsoft.com/fwlink/p/?linkid=534605)。

##  <a name="BK_Native"></a> 桌面和服务器应用程序

若要了解桌面 Windows 客户端应用程序的基础知识，请参阅 [使用 C++ 开发 Windows 应用程序](http://msdn.microsoft.com/vstudio//hh304489) 和 [使用 C++ 的 Windows 编程介绍](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx)。

在 Windows 10 中，可以使用 Visual c + + 创建多种的桌面程序：

- 命令行应用和实用工具。 有关详细信息，请参阅[控制台应用程序](../windows/console-applications-in-visual-cpp.md)。

- 具有复杂图形用户界面的使用者应用程序。 有关详细信息，请参阅 [Hilo：开发适用于 Windows 的 C++ 应用程序](http://go.microsoft.com/fwlink/p/?LinkId=256417)

- 在.NET Framework 运行的企业和业务线应用。 大多数.NET Framework 应用程序的 C# 或 Visual Basic 中编写。 你可以使用 C + + /cli CLI 来创建启用.NET 代码，以使用本机 c + + 库的互操作层。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

- 在本机代码中运行的 SQL 数据库客户端。 有关详细信息，请参阅[SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

- Microsoft Office 应用程序的外接程序。 有关详细信息，请参阅 [为 Outlook 2010 构建 C++ 外接程序](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- 设备驱动程序。 有关详细信息，请参阅 [Windows 驱动程序工具包 (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Windows 服务。 有关详细信息，请参阅 [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications)。

你可以使用 Visual C++ 在 Win32 DLL 或 COM DLL 中打包绝大多数自定义高性能功能，这些功能可供 C++ 应用或使用其他语言（例如，C# 或 Visual Basic）编写的应用使用。 有关 Win32 DLL 的详细信息，请参阅 [DLLs in Visual C++](../build/dlls-in-visual-cpp.md)。 有关 COM 开发的详细信息，请参阅[组件对象模型 (COM)](https://msdn.microsoft.com/library/windows/desktop/ms680573)。

## <a name="games"></a>游戏

DirectX 游戏可以在 PC 或 Xbox 上运行。 有关详细信息，请参阅 [DirectX 开发人员中心](http://go.microsoft.com/fwlink/p/?LinkId=256418)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 库和标头文件

Visual c + + 包含 C 运行库 (CRT)、 c + + 标准库和其他 Microsoft 特定库。 包含这些库的标头文件的包含文件夹位于 \VC\ 文件夹下或在的 CRT，Windows SDK 安装文件夹中的情况下的 Visual Studio 安装目录中。   

你可以使用[Vcpkg 程序包管理器](../vcpkg.md)方便地为 Windows 安装数百个第三方的开源库。

Microsoft 库包括：

- Microsoft 基础类 (MFC)：一种面向对象的框架，用于创建传统的 Windows 程序（特别是企业级应用程序），这些应用程序具有诸如功能按钮、列表框、树视图和其他控件等丰富的用户界面。 有关详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- 活动模板库 (ATL)：一种功能强大的帮助程序库，用于创建 COM 组件。 有关详细信息，请参阅 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：一种可以在 GPU 上实现高性能泛型计算工作的库。 有关详细信息，请参阅 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 并发运行时：一种可以简化多核和众核设备编程的并行和异步编程工作的库。 有关详细信息，请参阅 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

许多 Windows 编程方案还需要 Windows SDK，Windows SDK 包括可以实现对 Windows 操作系统组件访问的标头文件。 默认情况下，Visual Studio 安装 Windows SDK 的 c + + 桌面工作负荷，这样的通用 Windows 应用开发的组件。 若要开发 UWP 应用，你需要 Windows 10 版本的 Windows sdk。 有关信息，请参阅[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (有关适用于 Windows 的早期版本的 Windows Sdk 的详细信息，请参阅[Windows SDK 存档](https://developer.microsoft.com/windows/downloads/sdk-archive))。 

**程序文件 (x86) \Windows 工具包**是适用于已安装的 Windows sdk 的所有版本的默认位置。

其他平台（例如，Xbox 和 Azure）有自己 SDK，你可能需要安装这些 SDK。 有关详细信息，请参阅 DirectX 开发人员中心和 Azure 开发人员中心。

## <a name="development-tools"></a>开发工具

Visual Studio 包含一个功能强大的本机代码调试器、静态分析工具、图形调试工具、一个功能齐全的代码编辑器、单元测试支持，以及许多其他工具和实用程序。 有关详细信息，请参阅[开始使用 Visual Studio 进行开发](/visualstudio/ide/get-started-developing-with-visual-studio)，和[IDE 和开发工具](../ide/ide-and-tools-for-visual-cpp-development.md)。

## <a name="related-articles"></a>相关文章

|标题|描述|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual c + + 开发人员内容的父主题。|
