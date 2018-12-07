---
title: C++ 中 Windows 编程概述
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: b33236df6e4c7f679ff1dd9f9f8bc409c86e011a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693851"
---
# <a name="overview-of-windows-programming-in-c"></a>C++ 中 Windows 编程概述

有好几大类别可以使用 c + + 创建的 Windows 应用程序。 每个有其自己的编程模型和组的特定于 Windows 的库，但可以在其中任何一个使用 c + + 标准库以及第三方 c + + 库。 

## <a name="command-line-console-applications"></a>命令行 （控制台） 应用程序

C + + 控制台应用程序从命令行控制台窗口中运行，并可以显示仅文本输出。 有关详细信息，请参阅[控制台应用程序](console-applications-in-visual-cpp.md)。
 
## <a name="native-desktop-client-applications"></a>本机桌面客户端应用程序

术语*本机桌面客户端应用程序*引用 C 或 c + + 窗口使用的应用程序原始 Windows Win32 Api 以访问操作系统。 这些 Api 是自行写入主要是用 c 语言在创建此类应用程序时，您可以选择直接针对 C 样式消息循环，用于处理操作系统事件进行编程或使用*Microsoft 基础类*(MFC) 包装 Win32 c + + 库中是某种程度上面向对象的一种方法。 两种方法被视为"现代"相比通用 Windows 平台 （见下文），但同时仍是完全受支持并且具有数百万行的当今世界中运行的代码。

若要开始使用传统 Windows c + + 编程，请参阅[Win32 和 c + + 入门](/windows/desktop/LearnWin32/learn-to-program-for-windows)。 获取 Win32 一定了解后，可以将其更轻松地了解[MFC 桌面应用程序](/mfc/mfc-desktop-applications)。 传统的 c + + 桌面应用程序使用复杂的图形的示例，请参阅[Hilo： 开发 c + + 应用程序转换为 Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C + + 或.NET？ 

对于大多数桌面应用程序方案 (即，不面向 UWP)，请考虑使用C#和.NET。 这是因为.NET 编程是通常不太复杂、 更不易于出错，并且具有比 Win32 或 MFC 一个更现代的面向对象的 API。 在大多数情况下，其性能就足够了。 可以使用 Win32，以及 （请参阅下面的 UWP） 的新式 Windows 运行时 API 和.NET 功能的丰富图形，Windows Presentation Foundation (WPF)。 作为一般规则，我们建议使用 c + + 桌面应用程序，当你需要时：

- 对内存使用情况精确的控制
- 中电源消耗最经济
- gpu 的常规计算的使用情况
- directx 访问
- 标准 c + + 库的使用率很高

## <a name="com-components"></a>COM 组件

Windows 操作系统的许多部分都基于上组件对象模型 (COM) 的定义使组件可以从任何计算机语言编写的客户端应用程序使用一个二进制标准。 在 c + + 中可以使用活动模板库 (ATL) 来简化创建您自己的 COM 组件的工作。 有关详细信息，请参阅[组件对象模型 (COM)](/windows/desktop/com/component-object-model--com--portal)并[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)。

## <a name="windows-universal-apps"></a>Windows 通用应用

通用 Windows 平台 (UWP) 是现代 Windows API。 UWP 应用任何 Windows 10 设备上运行，XAML 用于用户界面和完全启用触控的。 有关 UWP 的详细信息，请参阅[通用 Windows 平台 (UWP) 应用是什么？](/windows/uwp/get-started/whats-a-uwp)并[Windows 通用应用指南](/windows/uwp/get-started/universal-application-platform-guide)。

包括适用于 UWP 的原始 c + + 支持的 （1） C + + /CX 中，一种方言语法扩展插件使用 c + + 或 （2） 将 Windows 运行时库 (WRL) 基于标准 c + + 和 com。 这两个 C + + /cli CX 和 WRL 仍受支持。 我们建议为新项目[C + + WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)这完全取决于标准 c + + 并提供更快的性能。 

适用于 Windows 10 可以打包现有 c + + 桌面应用程序作为-用于通过 Microsoft Store 的部署。 有关详细信息，请参阅[打包桌面应用程序 （桌面桥）](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>游戏

DirectX 游戏可以在电脑或 Xbox 上运行。 有关详细信息，请参阅[DirectX 图形和游戏](/windows/desktop/directx)。

## <a name="net-wrappers-for-c-libraries"></a>C + + 库的.NET 包装

您可以使用 C + + /cli CLI 来创建互操作层，使.NET 代码，以使用本机 c + + 库。 有关详细信息，请参阅[.NET 编程使用 C + + /cli CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="sql-server-database-clients"></a>SQL Server 数据库客户端

若要从本机代码访问 SQL Server 数据库，请使用 ODBC 或 OLE DB。 有关详细信息，请参阅 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 设备驱动程序

驱动程序是低级别组件，可以从硬件设备的数据应用程序可以访问和其他操作系统组件。 有关详细信息，请参阅[Windows Driver Kit (WDK)](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服务

Windows*服务*是可以在使用很少或没有用户交互在后台中运行的程序。 在 UNIX 这些被称为*守护程序*。 有关详细信息，请参阅[Services](/windows/desktop/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 库和标头文件

Visual Studio 包含 C 运行时库 (CRT)、 c + + 标准库和其他特定于 Microsoft 的库。 包含这些库的标头文件的包含文件夹位于 \VC\ 文件夹下或在 CRT 中的 Windows SDK 安装文件夹的情况下的 Visual Studio 安装目录中。

可以使用[Vcpkg 程序包管理器](../vcpkg.md)方便地安装用于 Windows 的数百个第三方开放源代码库。

Microsoft 库包括：

- Microsoft 基础类 (MFC)：一种面向对象的框架，用于创建传统的 Windows 程序（特别是企业级应用程序），这些应用程序具有诸如功能按钮、列表框、树视图和其他控件等丰富的用户界面。 有关详细信息，请参阅 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- 活动模板库 (ATL)：一种功能强大的帮助程序库，用于创建 COM 组件。 有关详细信息，请参阅 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：一种可以在 GPU 上实现高性能泛型计算工作的库。 有关详细信息，请参阅 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 并发运行时：一种可以简化多核和众核设备编程的并行和异步编程工作的库。 有关详细信息，请参阅 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

许多 Windows 编程方案还需要 Windows SDK，Windows SDK 包括可以实现对 Windows 操作系统组件访问的标头文件。 默认情况下，Visual Studio 安装 Windows SDK 的 c + + 桌面工作负载，从而使开发通用 Windows 应用的组件。 若要开发 UWP 应用，需要 Windows SDK 的 Windows 10 版本。 有关信息，请参阅[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (适用于 Windows 的早期版本的 Windows sdk 的详细信息，请参阅[Windows SDK 存档](https://developer.microsoft.com/windows/downloads/sdk-archive))。

**程序文件 (x86) \Windows 工具包**是已安装的 Windows sdk 的所有版本的默认位置。

其他平台（例如，Xbox 和 Azure）有自己 SDK，你可能需要安装这些 SDK。 有关详细信息，请参阅 DirectX 开发人员中心和 Azure 开发人员中心。

## <a name="development-tools"></a>开发工具

Visual Studio 包含一个功能强大的本机代码调试器、静态分析工具、图形调试工具、一个功能齐全的代码编辑器、单元测试支持，以及许多其他工具和实用程序。 有关详细信息，请参阅[开始使用 Visual Studio 进行开发](/visualstudio/ide/get-started-developing-with-visual-studio)，并[IDE 和开发工具](../ide/ide-and-tools-for-visual-cpp-development.md)。

## <a name="in-this-section"></a>本节内容
|标题|描述|
|-----------|-----------------|
|[C++ 中的 Windows 桌面应用程序](desktop-applications-visual-cpp.md)| 如何创建传统桌面应用程序。|
|[活动模板库 (ATL)](../atl/TOC.md)|使用 ATL 库在 c + + 中创建 COM 组件。|
|[Microsoft 基础类 (MFC)](../mfc/TOC.md)|使用 MFC 创建大或小 Windows 应用程序使用对话框和控件|
|[ATL 和 MFC 共享类](../atl-mfc-shared/TOC.md)|使用 ATL 和 MFC 中的共享如 CString 类。|
|[使用 C++/CLI 的 .NET开发](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|创建包装的本机 c + + 库，使其能够与.NET 应用程序和组件之间的通信。|
|[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)|引用的语法元素共享的 C + + /CX 和 C + + /cli CLI。|
|[通用 Windows 应用 (C++)](universal-windows-apps-cpp.md)|编写 UWP 应用程序使用 C + + /CX 或 Windows 运行时模板库 (WRL)。|
|[COM 和 .NET 的 C++ 属性](attributes/cpp-attributes-com-net.md)|使用.NET 或 com。 仅限 Windows 的编程的非标准属性|

## <a name="related-articles"></a>相关文章

|标题|描述|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual c + + 开发人员内容的父主题。|
