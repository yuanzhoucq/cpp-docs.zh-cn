---
title: C++ 中 Windows 编程概述
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359948"
---
# <a name="overview-of-windows-programming-in-c"></a>C++ 中 Windows 编程概述

可以使用C++创建多个广泛的 Windows 应用程序类别。 每个库都有自己的编程模型和一组特定于 Windows 的库，但C++标准库和第三方C++库都可以在任何库中使用。

本节讨论如何使用 Visual Studio 和 MFC/ATL 包装库创建 Windows 程序。 有关 Windows 平台本身的文档，请参阅[Windows 文档](/windows/index)。

## <a name="command-line-console-applications"></a>命令行（控制台）应用程序

C++控制台应用程序从控制台窗口中的命令行运行，并且只能显示文本输出。 有关详细信息，请参阅[创建C++控制台应用项目](../get-started/tutorial-console-cpp.md)。

## <a name="native-desktop-client-applications"></a>本机桌面客户端应用程序

*本机桌面客户端应用程序*是使用原始本机[Windows C API 或组件对象模型 （COM） API](/windows/win32/apiindex/windows-api-list)访问操作系统的 C 或 C++窗口应用程序。 这些 API 本身主要用 C 编写。创建本机桌面应用的方法不止一种：您可以使用 Win32 API 直接编程，使用处理操作系统事件的 C 样式消息循环。 或者，您可以使用 Microsoft*基础类*（MFC） 进行编程，这是一个稍微面向对象的C++库，可以包装 Win32。 与通用 Windows 平台 （UWP） 相比，这两种方法都不被视为"现代"，但两者都完全支持，并且当今世界有数百万行代码运行。 在窗口中运行的 Win32 应用程序要求开发人员在 Windows 过程函数中显式处理 Windows 消息。 尽管名称，Win32 应用程序可以编译为 32 位 （x86） 或 64 位 （x64） 二进制文件。 在视觉工作室 IDE 中，术语 x86 和 Win32 是同义词。

要开始使用传统的 Windows C++编程，请参阅[使用 Win32 入门和C++](/windows/win32/LearnWin32/learn-to-program-for-windows)。 了解 Win32 后，将更容易了解[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)。 有关使用复杂图形的传统C++桌面应用程序的示例，请参阅[Hilo：为 Windows 开发C++应用程序](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C++还是 .NET？

通常，C# 中的 .NET 编程不太复杂，不易出错，并且具有比 Win32 或 MFC 更现代的面向对象的 API。 在大多数情况下，其性能远远不够。 .NET 具有用于丰富图形的 Windows 演示基础 （WPF），您可以使用 Win32 和现代 Windows 运行时 API。 通常，我们建议您在需要时对桌面应用程序使用C++：

- 精确控制内存使用情况
- 最大的经济消耗
- GPU 用于一般计算
- 访问 DirectX
- 大量使用标准C++库

还可以将C++的功率和效率与 .NET 编程相结合。 您可以在 C# 中创建用户界面，并使用C++/CLI使应用程序能够使用本机C++库。 有关详细信息，请参阅[.NET 编程与C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="com-components"></a>COM 组件

[组件对象模型 （COM）](/windows/win32/com/the-component-object-model)是一种规范，它允许用不同语言编写的程序相互通信。 许多 Windows 组件作为 COM 对象实现，并遵循对象创建、接口发现和对象破坏的标准 COM 规则。  使用来自C++桌面应用程序中的 COM 对象相对简单，但编写自己的 COM 对象更高级。 [活动模板库 （ATL）](../atl/atl-com-desktop-components.md)提供宏和帮助器功能，可简化 COM 开发。 有关详细信息，请参阅[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)。

## <a name="universal-windows-platform-apps"></a>通用 Windows 平台应用

通用 Windows 平台 （UWP） 是现代 Windows API。 UWP 应用在任何 Windows 10 设备上运行，使用 XAML 进行用户界面，并且完全启用触摸。 有关 UWP 的详细信息，[Guide to Windows Universal Apps](/windows/uwp/get-started/universal-application-platform-guide)请参阅[什么是通用 Windows 平台 （UWP） 应用？](/windows/uwp/get-started/whats-a-uwp)

对 UWP 的原始C++支持包括 （1） C++/CX，一种带有语法扩展的C++方言，或 （2） 基于标准C++和 COM 的 Windows 运行时库 （WRL）。 仍然支持C++/CX 和 WRL。 对于新项目，我们建议[C++/WinRT，](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)它完全基于标准C++并提供更快的性能。

## <a name="desktop-bridge"></a>桌面桥

在 Windows 10 中，您可以将现有桌面应用程序或 COM 对象打包为 UWP 应用，并添加 UWP 功能（如触摸）或从现代 Windows API 集中调用 API。 您还可以将 UWP 应用添加到 Visual Studio 中的桌面解决方案，并将它们打包在单个包中，并使用 Windows API 在它们之间进行通信。

Visual Studio 2017 版本 15.4 及更高版本允许您创建 Windows 应用程序包项目，以大大简化打包现有桌面应用程序的工作。 一些限制适用于桌面应用程序可以使用的注册表调用或 API。 但是，在许多情况下，您可以创建备用代码路径，以便在应用包中运行时实现类似的功能。 有关详细信息，请参阅[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>游戏

DirectX 游戏可以在 PC 或 Xbox 上运行。 有关详细信息，请参阅[DirectX 图形和游戏](/windows/win32/directx)。

## <a name="sql-server-database-clients"></a>SQL 服务器数据库客户端

要从本机代码访问 SQL Server 数据库，请使用 ODBC 或 OLE DB。 有关详细信息，请参阅 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 设备驱动程序

驱动程序是低级组件，使应用程序和其他操作系统组件可以访问来自硬件设备的数据。 有关详细信息，请参阅[Windows 驱动程序工具包 （WDK）。](/windows-hardware/drivers/index)

## <a name="windows-services"></a>Windows 服务

Windows*服务*是在后台运行的程序，很少或根本没有用户交互。 这些程序在 UNIX 系统上称为*守护进程*。 有关详细信息，请参阅 [服务](/windows/win32/services/services)。

## <a name="sdks-libraries-and-header-files"></a>SDK、库和标头文件

可视化工作室包括 C 运行时库 （CRT）、C++标准库和其他特定于 Microsoft 的库。 包含这些库的标头文件的大多数包含文件夹位于 [VC] 文件夹下的 Visual Studio 安装目录中。 Windows 和 CRT 标头文件位于 Windows SDK 安装文件夹中。

[Vcpkg 包管理器](../build/vcpkg.md)允许您方便地安装数百个适用于 Windows 的第三方开源库。

微软库包括：

- Microsoft 基础类 (MFC)：一种面向对象的框架，用于创建传统的 Windows 程序（特别是企业级应用程序），这些应用程序具有诸如功能按钮、列表框、树视图和其他控件等丰富的用户界面。 有关详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- 活动模板库 (ATL)：一种功能强大的帮助程序库，用于创建 COM 组件。 有关详细信息，请参阅 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：一种可以在 GPU 上实现高性能泛型计算工作的库。 有关详细信息，请参阅 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 并发运行时：一种可以简化多核和众核设备编程的并行和异步编程工作的库。 有关详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。

许多 Windows 编程方案还需要 Windows SDK，Windows SDK 包括可以实现对 Windows 操作系统组件访问的标头文件。 默认情况下，Visual Studio 将 Windows SDK 安装为 C++桌面工作负载的组件，从而支持通用 Windows 应用的开发。 要开发 UWP 应用，您需要 Windows 10 版本的 Windows SDK。 有关详细信息，请参阅[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 （有关早期版本的 Windows 的 Windows SDK 的详细信息，请参阅[Windows SDK 存档](https://developer.microsoft.com/windows/downloads/sdk-archive)。

**程序文件 （x86）\Windows 工具包**是已安装的所有版本的 Windows SDK 的默认位置。

其他平台（例如，Xbox 和 Azure）有自己 SDK，你可能需要安装这些 SDK。 有关详细信息，请参阅 DirectX 开发人员中心和 Azure 开发人员中心。

## <a name="development-tools"></a>开发工具

Visual Studio 包含一个功能强大的本机代码调试器、静态分析工具、图形调试工具、一个功能齐全的代码编辑器、单元测试支持，以及许多其他工具和实用程序。 有关详细信息，请参阅使用[Visual Studio 开始开发](/visualstudio/ide/get-started-developing-with-visual-studio)，以及[可视化工作室中C++开发概述](../overview/overview-of-cpp-development.md)。

## <a name="in-this-section"></a>在本节中

|Title|描述|
|-----------|-----------------|
|[演练：创建标准C++计划](walkthrough-creating-a-standard-cpp-program-cpp.md)| 创建 Windows 控制台应用程序。|
|[演练：创建 Windows 桌面应用程序 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|创建本机 Windows 桌面应用程序。|
|[Windows 桌面向导](windows-desktop-wizard.md)|使用向导创建新的 Windows 项目。|
|[活动模板库 (ATL)](../atl/atl-com-desktop-components.md)|使用 ATL 库在C++中创建 COM 组件。|
|[Microsoft 基础类 (MFC)](../mfc/mfc-desktop-applications.md)|使用 MFC 创建具有对话框和控件的大型或小型 Windows 应用程序|
|[ATL 和 MFC 共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)|使用在 ATL 和 MFC 中共享的 CString 等类。|
|[数据访问](../data/data-access-in-cpp.md)| OLE DB 和 ODBC|
|[文本和字符串](../text/text-and-strings-in-visual-cpp.md)|Windows 上的各种字符串类型。|
|[使用 DirectX 创建游戏的资源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用资源文件](working-with-resource-files.md)|如何向桌面应用程序添加图像、图标、字符串表和其他资源。|
|[有关使用 DirectX 创建游戏的资源 (C++)](resources-for-creating-a-game-using-directx.md)|指向C++中创建游戏的内容的链接。|
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|
|[部署本机桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)|在 Windows 上部署本机应用程序。|

## <a name="related-articles"></a>相关文章

|Title|描述|
|-----------|-----------------|
|[视觉工作室中的C++](../overview/visual-cpp-in-visual-studio.md)|VisualC++开发人员内容的父主题。|
[.NET 开发，带C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|为本机C++库创建包装器，使其能够与 .NET 应用程序和组件通信。|
|[.NET 和 UWP 的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)|C++/CX 和 C++/CLI 共享的语法元素的引用。|
|[通用 Windows 应用 (C++)](../cppcx/universal-windows-apps-cpp.md)|使用C++/CX 或 Windows 运行时模板库 （WRL） 写入 UWP 应用程序。|
|[C++ COM 和 .NET 的属性](attributes/cpp-attributes-com-net.md)|使用 .NET 或 COM 的仅 Windows 编程的非标准属性。|
