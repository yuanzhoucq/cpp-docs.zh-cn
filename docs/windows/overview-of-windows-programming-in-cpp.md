---
title: C++ 中 Windows 编程概述
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 0aa667168f88f48458ae3a9b3541d4944f7530cc
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404982"
---
# <a name="overview-of-windows-programming-in-c"></a>C++ 中 Windows 编程概述

可以通过 c + + 创建几种种类广泛的 Windows 应用程序。 每个都有其自己的编程模型和一组特定于 Windows 的库，但可以在任何这些库中使用 c + + 标准库和第三方 c + + 库。

本部分讨论如何使用 Visual Studio 和 MFC/ATL 包装库来创建 Windows 程序。 有关 Windows 平台本身的文档，请参阅[windows 文档](/windows/index)。

## <a name="command-line-console-applications"></a>命令行（控制台）应用程序

C + + 控制台应用程序从控制台窗口中的命令行运行，并且只能显示文本输出。 有关详细信息，请参阅[使用 c + + 创建控制台计算器](../get-started/tutorial-console-cpp.md)。

## <a name="native-desktop-client-applications"></a>本机桌面客户端应用程序

*本机桌面客户端应用程序*是一个 c 或 c + + 窗口应用程序，它使用原始本机[Windows C Api 或组件对象模型（COM） api](/windows/win32/apiindex/windows-api-list)来访问操作系统。 这些 Api 在大多数情况下都是以 C 编写的。有多种方法可以创建本机桌面应用程序：可以使用处理操作系统事件的 C 样式消息循环直接使用 Win32 Api 进行编程。 或者，你可以使用*Microsoft 基础类*（MFC）来编程，这是一个非常轻的面向对象的 c + + 库，用于包装 Win32。 与通用 Windows 平台（UWP）相比，这两种方法都不会被视为 "新式"，但这两种方法仍完全受支持，并在世界各地运行了数百万行代码。 在窗口中运行的 Win32 应用程序要求开发人员在 Windows 过程函数内显式处理 Windows 消息。 不管名称如何，Win32 应用程序都可以编译为32位（x86）或64位（x64）二进制。 在 Visual Studio IDE 中，x86 和 Win32 术语是同义词。

若要开始实现传统的 Windows c + + 编程，请参阅[Win32 和 c + + 入门](/windows/win32/LearnWin32/learn-to-program-for-windows)。 了解 Win32 后，就可以更轻松地了解[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)。 有关使用复杂图形的传统 c + + 桌面应用程序的示例，请参阅[Hilo：开发适用于 Windows 的 c + + 应用](/previous-versions/msdn10/ff708696(v=msdn.10))程序。

### <a name="c-or-net"></a>C + + 或 .NET？

通常，c # 中的 .NET 编程不太复杂，不易出错，并且具有比 Win32 或 MFC 更现代的面向对象的 API。 在大多数情况下，其性能会更好。 .NET 功能适用于丰富图形的 Windows Presentation Foundation （WPF），你可以同时使用 Win32 和新式 Windows 运行时 API。 作为一般规则，我们建议在需要时使用适用于桌面应用程序的 c + +：

- 精确控制内存使用情况
- 能源消耗的经济动力
- 使用 GPU 进行常规计算
- 访问 DirectX
- 标准 c + + 库的高使用量

还可以将 c + + 的强大功能和效率与 .NET 编程结合起来。 您可以使用 c # 创建一个用户界面，并使用 c + +/CLI 使该应用程序能够使用本机 c + + 库。 有关详细信息，请参阅[用 c + +/cli 进行 .Net 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="com-components"></a>COM 组件

[组件对象模型（COM）](/windows/win32/com/the-component-object-model)是一种规范，用不同语言编写的程序可以相互通信。 许多 Windows 组件是作为 COM 对象实现的，并遵循用于对象创建、接口发现和对象析构的标准 COM 规则。  使用 c + + 桌面应用程序中的 COM 对象相对简单，但编写自己的 COM 对象更高级。 [活动模板库（ATL）](../atl/atl-com-desktop-components.md)提供了可简化 COM 开发的宏和帮助程序函数。 有关详细信息，请参阅[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)。

## <a name="universal-windows-platform-apps"></a>通用 Windows 平台应用

通用 Windows 平台（UWP）是新式 Windows API。 UWP 应用在任何 Windows 10 设备上运行，将 XAML 用于用户界面，并完全支持触摸。 有关 UWP 的详细信息，请参阅[什么是通用 Windows 平台（UWP）应用](/windows/uwp/get-started/whats-a-uwp)和[Windows 通用应用指南](/windows/uwp/get-started/universal-application-platform-guide)。

适用于 UWP 的原始 c + + 支持包括（1） c + +/CX、带有语法扩展的 c + + 方言，或（2） Windows 运行时库（WRL），它基于标准 c + + 和 COM。 C + +/CX 和 WRL 仍受支持。 对于新项目，我们建议[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)，它完全基于标准 c + + 并提供更快的性能。

## <a name="desktop-bridge"></a>桌面桥

在 Windows 10 中，你可以将现有的桌面应用程序或 COM 对象打包为 UWP 应用，并添加 UWP 功能（如触控）或从新式 Windows API 集中调用 Api。 你还可以在 Visual Studio 中向桌面解决方案添加 UWP 应用，并将其打包在单个包中，并使用 Windows Api 在它们之间进行通信。

使用 Visual Studio 2017 版本15.4 和更高版本，你可以创建一个 Windows 应用程序包项目，以大幅简化现有桌面应用程序的打包工作。 一些限制适用于你的桌面应用程序可以使用的注册表调用或 Api。 但是，在许多情况下，你可以创建备用代码路径，以便在应用包中运行时实现类似的功能。 有关详细信息，请参阅[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>游戏

DirectX 游戏可以在电脑或 Xbox 上运行。 有关详细信息，请参阅[DirectX 图形和游戏](/windows/win32/directx)。

## <a name="sql-server-database-clients"></a>SQL Server 数据库客户端

若要从本机代码访问 SQL Server 数据库，请使用 ODBC 或 OLE DB。 有关详细信息，请参阅 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 设备驱动程序

驱动程序是低级别的组件，可让应用程序和其他操作系统组件访问硬件设备中的数据。 有关详细信息，请参阅[Windows 驱动程序工具包（WDK）](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服务

Windows*服务*是一种可在后台运行，几乎无需用户交互的程序。 在 UNIX 系统上，这些程序称为*守护*程序。 有关详细信息，请参阅 [服务](/windows/win32/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、库和头文件

Visual Studio 包括 C 运行时库（CRT）、c + + 标准库和其他 Microsoft 特定库。 大多数包含这些库的标头文件的包含文件夹位于 \VC\ 文件夹下的 Visual Studio 安装目录中。 Windows 和 CRT 标头文件位于 Windows SDK 安装文件夹中。

[Vcpkg 包管理器](../build/vcpkg.md)可让你方便地安装数百个适用于 Windows 的第三方开源库。

Microsoft 库包括：

- Microsoft 基础类 (MFC)：一种面向对象的框架，用于创建传统的 Windows 程序（特别是企业级应用程序），这些应用程序具有诸如功能按钮、列表框、树视图和其他控件等丰富的用户界面。 有关详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- 活动模板库 (ATL)：一种功能强大的帮助程序库，用于创建 COM 组件。 有关详细信息，请参阅 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：一种可以在 GPU 上实现高性能泛型计算工作的库。 有关详细信息，请参阅 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 并发运行时：一种可以简化多核和众核设备编程的并行和异步编程工作的库。 有关详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。

许多 Windows 编程方案还需要 Windows SDK，Windows SDK 包括可以实现对 Windows 操作系统组件访问的标头文件。 默认情况下，Visual Studio 会将 Windows SDK 安装为 c + + 桌面工作负载的组件，这可以实现通用 Windows 应用的开发。 若要开发 UWP 应用，需要 Windows 10 版本的 Windows SDK。 有关信息，请参阅[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 （有关适用于 Windows 早期版本的 Windows Sdk 的详细信息，请参阅[Windows SDK 存档](https://developer.microsoft.com/windows/downloads/sdk-archive)）。

**Program Files （x86） \Windows 包**是所安装 Windows SDK 的所有版本的默认位置。

其他平台（例如，Xbox 和 Azure）有自己 SDK，你可能需要安装这些 SDK。 有关详细信息，请参阅 DirectX 开发人员中心和 Azure 开发人员中心。

## <a name="development-tools"></a>开发工具

Visual Studio 包含一个功能强大的本机代码调试器、静态分析工具、图形调试工具、一个功能齐全的代码编辑器、单元测试支持，以及许多其他工具和实用程序。 有关详细信息，请参阅 visual [studio 开发入门](/visualstudio/ide/get-started-developing-with-visual-studio)和[visual Studio 中的 c + + 开发概述](../overview/overview-of-cpp-development.md)。

## <a name="in-this-section"></a>本节内容

|Title|说明|
|-----------|-----------------|
|[演练：创建标准 c + + 程序](walkthrough-creating-a-standard-cpp-program-cpp.md)| 创建 Windows 控制台应用程序。|
|[演练：创建 Windows 桌面应用程序 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|创建本机 Windows 桌面应用程序。|
|[Windows 桌面向导](windows-desktop-wizard.md)|使用向导创建新的 Windows 项目。|
|[活动模板库 (ATL)](../atl/atl-com-desktop-components.md)|使用 ATL 库在 c + + 中创建 COM 组件。|
|[Microsoft 基础类 (MFC)](../mfc/mfc-desktop-applications.md)|使用 MFC 创建具有对话框和控件的大型或小型 Windows 应用程序|
|[ATL 和 MFC 共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)|使用在 ATL 和 MFC 中共享的类，如 CString。|
|[数据访问](../data/data-access-in-cpp.md)| OLE DB 和 ODBC|
|[文本和字符串](../text/text-and-strings-in-visual-cpp.md)|Windows 上的各种字符串类型。|
|[使用 DirectX 创建游戏的资源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用资源文件](working-with-resource-files.md)|如何向桌面应用程序添加图像、图标、字符串表以及其他资源。|
|[有关使用 DirectX 创建游戏的资源 (C++)](resources-for-creating-a-game-using-directx.md)|用 c + + 创建游戏的内容链接。|
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|
|[部署本机桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)|在 Windows 上部署本机应用程序。|

## <a name="related-articles"></a>相关文章

|Title|说明|
|-----------|-----------------|
|[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)|Visual C++ 开发人员内容的父主题。|
[用 c + +/CLI 进行 .NET 开发](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|为本机 c + + 库创建包装，使其能够与 .NET 应用程序和组件通信。|
|[适用于 .NET 和 UWP 的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)|C + +/CX 和 c + +/CLI 共享语法元素的参考|
|[通用 Windows 应用 (C++)](../cppcx/universal-windows-apps-cpp.md)|使用 c + +/CX 或 Windows 运行时模板库（WRL）编写 UWP 应用程序。|
|[适用于 COM 和 .NET 的 C++ 属性](attributes/cpp-attributes-com-net.md)|仅限 Windows 的非标准属性使用 .NET 或 COM 编程。|
