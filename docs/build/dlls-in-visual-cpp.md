---
title: 在 Visual StudioC++中创建 C/dll
description: 概述C++在 Visual Studio 中创建和使用 dll 的原因和方式。
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821416"
---
# <a name="create-cc-dlls-in-visual-studio"></a>在 Visual StudioC++中创建 C/dll

在 Windows 中，动态链接库（DLL）是作为函数和资源的共享库的一种可执行文件。 动态链接是操作系统功能。 它使可执行文件可以调用函数或使用存储在单独文件中的资源。 可从使用这些函数和资源的可执行文件中对其分别进行编译和部署。

DLL 不是独立的可执行文件。 Dll 在调用它们的应用程序的上下文中运行。 操作系统将该 DLL 加载到应用程序的内存空间中。 这是在应用程序加载时（*隐式链接*）或在运行时按需运行（*显式链接*）完成的。 DLL 还可以在可执行文件之间轻松共享函数和资源。 多个应用程序可同时访问内存中单个 DLL 副本的内容。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>动态链接和静态链接之间的差异

静态链接将静态库中的所有对象代码复制到生成时使用它的可执行文件。 动态链接只包含 Windows 在运行时查找并加载包含数据项或函数的 DLL 所需的信息。 创建 DLL 时，还将创建包含此信息的导入库。 当你生成调用 DLL 的可执行文件时，链接器将使用导入库中的已导出符号存储 Windows 加载程序的此信息。 当加载程序加载 DLL 时，DLL 映射到您的应用程序的内存空间中。 如果存在，则调用 DLL 中的特殊函数 `DllMain`，以执行 DLL 所需的任何初始化。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>应用程序和 Dll 之间的差异

即使 Dll 和应用程序都是可执行的模块，它们也有多种不同之处。 最明显的区别在于不能运行 DLL。 从系统的角度来看，应用程序和 Dll 之间有两个基本差异：

- 应用程序可以同时在系统中运行多个实例。 一个 DLL 只能有一个实例。

- 应用程序可以作为进程加载。 它可以拥有一些功能，如堆栈、执行线程、全局内存、文件句柄和消息队列。 DLL 不能拥有这些项。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>使用 Dll 的优点

与静态链接相比，动态链接到代码和资源具有多项优势：

- 动态链接可节省内存，减少交换。 许多进程可以同时使用 DLL，在内存中共享 DLL 的只读部分的单个副本。 与此相反，使用静态链接库生成的每个应用程序都有一个完整的库代码副本，Windows 必须将其加载到内存中。

- 动态链接节省了磁盘空间和带宽。 许多应用程序可以在磁盘上共享 DLL 的单个副本。 与此相反，使用静态链接库生成的每个应用程序都具有链接到其可执行映像的库代码。 这会占用更多的磁盘空间，并需要更多的带宽来传输。

- 维护、安全修补程序和升级会比较容易。 当应用程序在 DLL 中使用常见函数时，可以实现 bug 修复和将更新部署到 DLL。 更新 Dll 时，无需重新编译或重新链接使用它们的应用程序。 它们可以在部署后立即利用新的 DLL。 与此相反，当您在静态链接的对象代码中进行修复时，您必须重新链接和重新部署使用它的每个应用程序。

- 您可以使用 Dll 提供上市后支持。 例如，可以修改显示驱动程序 DLL 以支持在交付应用程序时不可用的显示。

- 可以在运行时使用显式链接来发现和加载 Dll。 例如，向应用程序添加新功能而不重新生成或重新部署的应用程序扩展。

- 动态链接使支持用不同编程语言编写的应用程序更加容易。 只要程序遵循函数的调用约定，用不同编程语言编写的程序就可以调用相同的 DLL 函数。 程序和 DLL 函数必须通过以下方式兼容：函数预期其参数被推送到堆栈上的顺序。 函数或应用程序是否负责清理堆栈。 和，是否在寄存器中传递任何参数。

- 动态链接提供了一种扩展 Microsoft 基础类库（MFC）类的机制。 可以从现有的 MFC 类派生类，并将它们放在 MFC 扩展 DLL 中以供 MFC 应用程序使用。

- 动态链接使你可以更轻松地创建应用程序的国际版本。 Dll 是提供特定于区域设置的资源的一种简便方法，这使创建应用程序的国际版本变得更加容易。 你可以将每种语言的字符串和图像放在单独的资源 DLL 中，而不是提供应用程序的多个本地化版本。 然后，应用程序可以在运行时为该区域设置加载相应的资源。

使用 Dll 的潜在缺点是，应用程序不是自包含的。 这取决于是否存在单独的 DLL 模块：一个是您在安装过程中必须部署或验证自己的。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>有关如何创建和使用 Dll 的详细信息

以下文章提供了有关如何在 Visual Studio 中创建 CC++ /dll 的详细信息。

[演练：创建和使用动态链接库（C++）](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
介绍如何使用 Visual Studio 创建和使用 DLL。

[Dll 的类型](kinds-of-dlls.md)\
提供有关可生成的不同类型的 DLL 的信息。

[DLL 常见问题](dll-frequently-asked-questions.md)\
提供有关 DLL 的常见问题解答。

将[可执行文件链接到 DLL](linking-an-executable-to-a-dll.md)\
描述与 DLL 的显式链接和隐式链接。

[初始化 DLL](run-time-library-behavior.md#initializing-a-dll)\
讨论当 DLL 加载时必须执行的 DLL 初始化代码。

[Dll 和 Visual C++运行时库行为](run-time-library-behavior.md)\
描述运行时库 DLL 启动序列。

[LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
讨论使用 `LoadLibrary` 和 `AfxLoadLibrary` 在运行时显式链接到 DLL。

[GetProcAddress](getprocaddress.md)\
讨论如何使用 `GetProcAddress` 获取 DLL 中导出函数的地址。

[FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
讨论在不再需要 DLL 模块时使用 `FreeLibrary` 和 `AfxFreeLibrary`。

[动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)\
描述 Windows 操作系统用来定位系统上的 DLL 的搜索路径。

[动态链接到 mfc 的规则 MFC DLL 的模块状态](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
描述动态链接到 MFC 的规则 MFC DLL 的模块状态。

[MFC 扩展 dll](extension-dlls-overview.md)\
介绍通常实现从现有 MFC 类派生的可重用类的 Dll。

[创建纯资源 DLL](creating-a-resource-only-dll.md)\
讨论只包含资源（如图标、位图、字符串和对话框等）的纯资源 DLL。

[MFC 应用程序中已本地化的资源：附属 dll](localized-resources-in-mfc-applications-satellite-dlls.md)\
提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。

[导入和导出](importing-and-exporting.md)\
描述如何将公共符号导入应用程序或从 DLL 导出函数。

[活动技术和 dll](active-technology-and-dlls.md)\
使对象服务器得以在 DLL 内实现。

[DLL 中的自动化](automation-in-a-dll.md)\
描述“MFC DLL 向导”中的“自动化”选项提供的内容。

[MFC dll 的命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
讨论 MFC 中包含的 DLL 和库如何遵循结构化命名约定。

[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)\
描述如何从 Visual Basic 应用程序中调用 DLL 函数。

## <a name="related-sections"></a>相关章节

[使用 MFC 作为 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
介绍用于将 MFC 库作为 Windows 动态链接库的一部分的规则 MFC Dll。

[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)\
介绍如何将 Mfcxx.dll 和 Mfcxxd.dll （其中 x 是 MFC 版本号）共享动态链接库与 MFC 应用程序和 MFC 扩展 Dll 结合使用。
