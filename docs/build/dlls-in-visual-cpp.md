---
title: 在 Visual Studio 中创建 C/C++ DLL
description: 概述在 Visual Studio 中使用 C++ 创建和使用 DLL 的原因和方法。
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422828"
---
# <a name="create-cc-dlls-in-visual-studio"></a>在 Visual Studio 中创建 C/C++ DLL

在 Windows 中，动态链接库 (DLL) 是作为函数和资源的共享库的一种可执行文件。 动态链接是操作系统功能。 它可使执行文件调用函数或使用存储在单独文件中的资源。 可从使用这些函数和资源的可执行文件中对其分别进行编译和部署。

DLL 不是独立的可执行文件。 DLL 在调用它们的应用程序的上下文中运行。 操作系统将 DLL 加载到应用程序的内存空间中。 此操作要么在加载应用程序时（隐式链接）完成，要么在运行时按需（显式链接）完成   。 DLL 还可以在可执行文件之间轻松共享函数和资源。 多个应用程序可同时访问内存中单个 DLL 副本的内容。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>动态链接和静态链接之间的差异

静态链接将静态库中的所有对象代码复制到生成时使用它的可执行文件中。 动态链接仅包括 Windows 在运行时用于查找和加载含有数据项或函数的 DLL 所需的信息。 创建 DLL 时，还将创建包含此信息的导入库。 生成调用 DLL 的可执行文件时，链接器会使用导入库中的导出符号来为 Windows 加载程序存储此信息。 当加载程序加载 DLL 时，该 DLL 会映射到你的应用程序的内存空间中。 如果存在，则调用 DLL 中的特殊函数 `DllMain`，以执行 DLL 所需的任何初始化。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>应用程序和 DLL 之间的区别

尽管 DLL 和应用程序都是可执行文件模块，但它们之间也存在很多不同之处。 对用户来说，最明显的区别在于不能直接运行 DLL。 从系统的角度来看，应用程序和 Dll 之间有两个基本差异：

- 一是应用程序可以在系统中同时运行其自身的多个实例。 而 DLL 只能有一个实例。

- 二是应用程序可以作为进程进行加载。 它可以管理诸如堆栈、执行线程、全局内存、文件句柄和消息队列之类的资源。 而 DLL 不能管理这些资源。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>使用 DLL 的优点

与静态链接相比，动态链接到代码和资源有几个优点：

- 动态链接可节省内存，减少交换。 许多进程可以同时使用 DLL，并在内存中共享 DLL 只读部分的单个副本。 相反，使用静态链接库构建的每个应用程序都有一个完整的库代码副本，Windows 必须将其加载到内存中。

- 动态链接节省了磁盘空间和带宽。 许多应用程序可以在磁盘上共享 DLL 的单个副本。 相反，使用静态链接库构建的每个应用程序都是将库代码链接到其可执行映像中。 这会占用更多磁盘空间，并需要更多带宽来传输。

- 维护、安全修复和升级会更容易。 当应用程序在 DLL 中使用公共函数时，你可以实现 bug 修复并将更新部署到 DLL。 更新 DLL 时，不需要重新编译或重新链接使用它们的应用程序。 一旦部署了新的 DLL，应用程序就可以使用这些新的 DLL。 相反，当你在静态链接的对象代码中进行修复时，必须重新链接并重新部署使用 DLL 的每个应用程序。

- 可以使用 DLL 提供售后支持。 例如，可以修改显示驱动程序 DLL 以支持应用程序发布时不可用的显示。

- 可以使用显式链接在运行时发现和加载 DLL。 例如，无需重新生成或重新部署就可将新功能添加到你的应用的应用程序扩展。

- 对于用不同编程语言编写的应用程序，使用动态链接可以更轻松地对其提供支持。 用不同编程语言编写的程序只要遵循函数调用约定，就可以调用相同的 DLL 函数。 程序和 DLL 函数必须在以下方面兼容：函数期望将其参数推送到堆栈上的顺序。 函数或应用程序是否负责清理堆栈。 以及，是否有参数在寄存器中传递。

- 动态链接提供了一种扩展 Microsoft 基础类库 (MFC) 类的机制。 可以从现有的 MFC 类派生类，并将它们放在 MFC 扩展 DLL 中供 MFC 应用程序使用。

- 动态链接使创建应用程序的国际版本更容易。 DLL 是一种提供特定于区域设置的资源的便捷方式，使用这种方式创建应用程序的国际版本会更加容易。 你可以将每种语言的字符串和映像放在一个单独的资源 DLL 中，而不是发布应用程序的许多本地化版本。 然后应用程序可以在运行时加载该区域设置的适当资源。

使用 DLL 的潜在缺点是，应用程序不是自包含的。 它依赖于一个独立的 DLL 模块的存在：在安装过程中必须亲自部署或验证的模块。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>关于如何创建和使用 DLL 的详细信息

以下文章提供了有关如何在 Visual Studio 中创建 C/C++ DLL 的详细信息。

[演练：创建和使用动态链接库 (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
介绍如何使用 Visual Studio 创建和使用 DLL。

[DLL 类型](kinds-of-dlls.md)\
提供有关可生成的不同类型的 DLL 的信息。

[DLL 常见问题](dll-frequently-asked-questions.md)\
提供有关 DLL 的常见问题解答。

[将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md)\
描述与 DLL 的显式链接和隐式链接。

[初始化 DLL](run-time-library-behavior.md#initializing-a-dll)\
介绍加载 DLL 时必须执行的 DLL 初始化代码。

[DLL 和 Visual C++ 运行时库行为](run-time-library-behavior.md)\
描述运行库 DLL 启动序列。

[LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
介绍如何在运行时使用 `LoadLibrary` 和 `AfxLoadLibrary` 显式链接到 DLL。

[GetProcAddress](getprocaddress.md)\
介绍如何使用 `GetProcAddress` 获取 DLL 中导出函数的地址。

[FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
介绍当不再需要 DLL 模块时如何使用 `FreeLibrary` 和 `AfxFreeLibrary`。

[动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)\
描述 Windows 操作系统用来定位系统上的 DLL 的搜索路径。

[动态链接到 MFC 的规则 MFC DLL 的模块状态](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
描述动态链接到 MFC 的规则 MFC DLL 的模块状态。

[MFC 扩展 DLL](extension-dlls-overview.md)\
解释通常实现从现有 MFC 类派生的可重用类的 DLL。

[创建纯资源 DLL](creating-a-resource-only-dll.md)\
讨论只包含资源（如图标、位图、字符串和对话框等）的纯资源 DLL。

[MFC 应用程序中已本地化的资源：附属 DLL](localized-resources-in-mfc-applications-satellite-dlls.md)\
提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。

[导入和导出](importing-and-exporting.md)\
描述如何将公共符号导入应用程序或从 DLL 导出函数。

[Active 技术和 DLL](active-technology-and-dlls.md)\
使对象服务器得以在 DLL 内实现。

[DLL 中的自动化](automation-in-a-dll.md)\
描述“MFC DLL 向导”中的“自动化”选项提供的内容。

[MFC DLL 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
讨论 MFC 中包含的 DLL 和库如何遵循结构化命名约定。

[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)\
描述如何从 Visual Basic 应用程序中调用 DLL 函数。

## <a name="related-sections"></a>相关章节

[将 MFC 用作 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
描述使你可以将 MFC 库作为 Windows 动态链接库的一部分来使用的规则 MFC DLL。

[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)\
描述如何将 MFCxx.dll 和 MFCxxD.dll（其中 x 是 MFC 版本号）共享动态链接库用于 MFC 应用程序和 MFC 扩展 DLL。
