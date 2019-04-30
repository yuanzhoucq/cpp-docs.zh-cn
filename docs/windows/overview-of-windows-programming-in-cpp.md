---
title: C++ 中 Windows 编程概述
ms.date: 03/28/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 48c7f419b6c69955ab25db528c8d3d86a7249391
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362343"
---
# <a name="overview-of-windows-programming-in-c"></a>C++ 中 Windows 编程概述

有几个大类别可以使用创建的 Windows 应用程序的C++。 每个都有其自己的编程模型和组特定于 Windows 的库，但C++标准库，以及第三方C++库可在其中任何一个。 

## <a name="command-line-console-applications"></a>命令行 （控制台） 应用程序

C++控制台应用程序从命令行控制台窗口中运行，并可以显示仅文本输出。 有关详细信息，请参阅[控制台应用程序](console-applications-in-visual-cpp.md)。
 
## <a name="native-desktop-client-applications"></a>本机桌面客户端应用程序

术语*本机桌面客户端应用程序*指的是 C 或C++窗口中应用程序使用的原始本机[Windows C Api 和/或 COM Api](/windows/desktop/apiindex/windows-api-list)访问操作系统。 这些 Api 是自行写入主要是用 c 语言在创建此类应用程序时，您可以选择直接针对 C 样式消息循环，用于处理操作系统事件进行编程或使用*Microsoft 基础类*(MFC)C++包装库Win32 是某种程度上是面向对象的方式。 两种方法被视为"现代"相比通用 Windows 平台 （见下文），但同时仍是完全受支持并且具有数百万行的当今世界中运行的代码。 在窗口中运行的 Win32 应用程序需要开发人员显式使用 Windows 过程函数中的 Windows 消息。 虽然名为 32 位，但 Win32 应用程序可以编译为 32 位 (x86) 或 64 位 (x64) 二进制程序。 在 Visual Studio IDE 中，x86 和 Win32 这两个术语是同义的。

若要开始使用传统的 WindowsC++编程，请参见[开始使用 Win32 和C++ ](/windows/desktop/LearnWin32/learn-to-program-for-windows)。 获取 Win32 一定了解后，可以将其更轻松地了解[MFC 桌面应用程序](/mfc/mfc-desktop-applications)。 有关的传统示例C++桌面应用程序使用复杂的图形，请参阅[Hilo:开发C++适用于 Windows 应用程序](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C++或.NET？ 

对于大多数桌面应用程序方案 (即，不面向 UWP)，请考虑使用C#若要创建的用户界面。 这是因为.NET 编程是通常不太复杂、 更不易于出错，并且具有比 Win32 或 MFC 一个更现代的面向对象的 API。 在大多数情况下，其性能就足够了。 可以使用 Win32，以及 （请参阅下面的 UWP） 的新式 Windows 运行时 API 和.NET 功能的丰富图形，Windows Presentation Foundation (WPF)。 作为一般规则，我们建议使用C++时所需的桌面应用程序：

- 对内存使用情况精确的控制
- 中电源消耗最经济
- gpu 的常规计算的使用情况
- directx 访问
- 标准的高使用率C++库

可以创建中的用户界面C#，并使用C++/CLI 若要启用应用程序来使用本机C++库。 有关详细信息，请参阅[.NET 编程与C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="com-components"></a>COM 组件

[组件对象模型 (COM)](/windows/desktop/com/the-component-object-model)是一种规范，用来相互通信的不同语言编写的程序。 许多 Windows 组件作为 COM 对象实现，并且遵循标准 COM 规则对象的创建过程的接口发现和对象的析构。  使用 COM 对象从C++桌面应用程序是相对简单，但更高级编写你自己的 COM 对象。 [活动模板库 (ATL)](../atl/atl-com-desktop-components.md)提供宏和 helper 函数，简化了 COM 开发。 有关详细信息，请参阅[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)。

## <a name="windows-universal-apps"></a>Windows 通用应用

通用 Windows 平台 (UWP) 是现代 Windows API。 UWP 应用任何 Windows 10 设备上运行，XAML 用于用户界面和完全启用触控的。 有关 UWP 的详细信息，请参阅[通用 Windows 平台 (UWP) 应用是什么？](/windows/uwp/get-started/whats-a-uwp)并[Windows 通用应用指南](/windows/uwp/get-started/universal-application-platform-guide)。

原始C++对 UWP 包含 (1) 的支持C++/CX，一种方言C++语法扩展插件，或 （2） 将 Windows 运行时库 (WRL) 基于标准C++和 com。 同时C++/CX 和 WRL 仍受支持。 我们建议为新项目[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)完全基于标准C++，并提供更快的性能。 

## <a name="desktop-bridge"></a>桌面桥

在 Windows 10 中，可以将现有的桌面应用程序或者 COM 对象打包为 UWP 应用并添加 UWP 功能，如触摸屏输入，或从现代 Windows API 集调用 API。 还可以向 Visual Studio 的桌面解决方案中添加 UWP 应用，然后将其封装在单个包中，使用 Windows API 在其间通信。

在 Visual Studio 2017 版本 15.4 及更高版本中，可以创建一个 Windows 应用程序包项目，大大简化打包现有桌面应用程序的工作。 桌面应用程序使用的注册表调用或 API 存在一些限制，但多数情况下，在应用包中运行时，可以创建替代代码路径来实现类似功能。 有关详细信息，请参阅[桌面桥](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>游戏

DirectX 游戏可以在电脑或 Xbox 上运行。 有关详细信息，请参阅[DirectX 图形和游戏](/windows/desktop/directx)。

## <a name="sql-server-database-clients"></a>SQL Server 数据库客户端

若要从本机代码访问 SQL Server 数据库，请使用 ODBC 或 OLE DB。 有关详细信息，请参阅 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 设备驱动程序

驱动程序是低级别组件，可以从硬件设备的数据应用程序可以访问和其他操作系统组件。 有关详细信息，请参阅[Windows Driver Kit (WDK)](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服务

Windows*服务*是可以在使用很少或没有用户交互在后台中运行的程序。 在 UNIX 这些被称为*守护程序*。 有关详细信息，请参阅[Services](/windows/desktop/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 库和标头文件

Visual Studio 包含 C 运行时库 (CRT)C++标准库，以及其他特定于 Microsoft 的库。 包含这些库的标头文件的包含文件夹位于 \VC\ 文件夹下或在 CRT 中的 Windows SDK 安装文件夹的情况下的 Visual Studio 安装目录中。

可以使用[Vcpkg 程序包管理器](../build/vcpkg.md)方便地安装用于 Windows 的数百个第三方开放源代码库。

Microsoft 库包括：

- Microsoft 基础类 (MFC):面向对象的框架，用于创建传统 Windows 程序 — 特别是企业应用程序 — 功能按钮、 列表框、 树视图和其他控件具有丰富的用户界面。 有关详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- 活动模板库 (ATL):用于创建 COM 组件的功能强大的帮助程序库。 有关详细信息，请参阅 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++A m P (C++ Accelerated Massive Parallelism):一种库，允许在 GPU 上的高性能泛型计算工作。 有关详细信息，请参阅 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 并发运行时：一个库，简化了并行和异步编程的多核和众核设备工作。 有关详细信息，请参阅 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

许多 Windows 编程方案还需要 Windows SDK，Windows SDK 包括可以实现对 Windows 操作系统组件访问的标头文件。 默认情况下，Visual Studio 安装 Windows SDK 为的一个组件C++桌面工作负载，从而使通用 Windows 应用的开发。 若要开发 UWP 应用，需要 Windows SDK 的 Windows 10 版本。 有关信息，请参阅[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (适用于 Windows 的早期版本的 Windows sdk 的详细信息，请参阅[Windows SDK 存档](https://developer.microsoft.com/windows/downloads/sdk-archive))。

**程序文件 (x86) \Windows 工具包**是已安装的 Windows sdk 的所有版本的默认位置。

其他平台（例如，Xbox 和 Azure）有自己 SDK，你可能需要安装这些 SDK。 有关详细信息，请参阅 DirectX 开发人员中心和 Azure 开发人员中心。

## <a name="development-tools"></a>开发工具

Visual Studio 包含一个功能强大的本机代码调试器、静态分析工具、图形调试工具、一个功能齐全的代码编辑器、单元测试支持，以及许多其他工具和实用程序。 有关详细信息，请参阅[开始使用 Visual Studio 进行开发](/visualstudio/ide/get-started-developing-with-visual-studio)，并[概述C++Visual Studio 中的开发](../overview/overview-of-cpp-development.md)。

## <a name="in-this-section"></a>本节内容
|标题|描述|
|-----------|-----------------|
|[演练：创建标准 C++ 程序](walkthrough-creating-a-standard-cpp-program-cpp.md)| 创建一个 Windows 控制台应用程序。|
|[演练：创建 Windows 桌面应用程序 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|创建一个简单的 Windows 桌面应用程序。|
|[Windows 桌面向导](windows-desktop-wizard.md)|使用向导来创建新的 Windows 项目。|
|[活动模板库 (ATL)](../atl/TOC.md)|使用 ATL 库创建的 COM 组件C++。|
|[Microsoft 基础类 (MFC)](../mfc/TOC.md)|使用 MFC 创建大或小 Windows 应用程序使用对话框和控件|
|[ATL 和 MFC 共享类](../atl-mfc-shared/TOC.md)|使用 ATL 和 MFC 中的共享如 CString 类。|
|[数据访问](../data/data-access-in-cpp.md)| OLE DB 和 ODBC|
|[文本和字符串](../text/text-and-strings-in-visual-cpp.md)|在 Windows 上的各种字符串类型。|
|[有关使用 DirectX 创建游戏的资源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用资源文件](working-with-resource-files.md)|如何将图像、 图标、 字符串表和其他资源添加到桌面应用程序。|
|[使用 DirectX 创建游戏的资源 (C++)](resources-for-creating-a-game-using-directx.md)|用于创建游戏中的内容的链接C++。|
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|
|[部署本机桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)|部署在 Windows 上的本机应用程序。|


## <a name="related-articles"></a>相关文章

|标题|描述|
|-----------|-----------------|
|[Visual C++](../overview/visual-cpp-in-visual-studio.md)|视觉对象的父主题C++开发人员内容。|
[使用 C++/CLI 的 .NET开发](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|创建包装的本机C++库，使其能够使用.NET 应用程序和组件进行通信。|
|[ .NET 和 UWP 的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)|共享的语法元素的引用C++/CX 和C++/CLI。|
|[通用 Windows 应用 (C++)](universal-windows-apps-cpp.md)|编写 UWP 应用程序使用C++/CX 或 Windows 运行时模板库 (WRL)。|
|[COM 和 .NET 的 C++ 属性](attributes/cpp-attributes-com-net.md)|使用.NET 或 com。 仅限 Windows 的编程的非标准属性|

