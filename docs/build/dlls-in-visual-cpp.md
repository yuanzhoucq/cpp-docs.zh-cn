---
title: 创建 C /C++ Visual Studio 中的 Dll
ms.date: 12/10/2018
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 5bd30c84ba202c3f772ad4451368efde10285e6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195457"
---
# <a name="create-cc-dlls-in-visual-studio"></a>创建 C /C++ Visual Studio 中的 Dll

在 Windows 中，动态链接库 (DLL) 是一种作为函数和资源的共享库的可执行文件。 动态链接是操作系统功能，使可执行文件调用的函数或使用存储在单独的文件的资源。 可从使用这些函数和资源的可执行文件中对其分别进行编译和部署。 DLL 不是独立的可执行文件;它在调用它的应用程序的上下文中运行。 操作系统可以将 DLL 加载到应用程序的内存空间时加载该应用程序 (*隐式链接*)，或按需在运行时 (*显式链接*)。 DLL 还可以在可执行文件之间轻松共享函数和资源。 多个应用程序可同时访问内存中单个 DLL 副本的内容。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>动态链接与静态链接之间的差异

静态链接将所有对象代码中的静态库到在生成时使用它的可执行文件。 动态链接包含仅在运行时用于查找和加载包含的数据项或函数的 DLL 所需的 Windows 的信息。 当您创建 DLL 时，还可以创建包含此信息的导入库。 生成调用 DLL 的可执行文件时，链接器会使用在导入库中的导出的符号来存储 Windows 加载程序的此信息。 当加载程序加载 DLL 时，该 DLL 会映射到你的应用程序的内存空间。 如果存在，一个特殊函数，在该 DLL， `DllMain`，调用来执行 DLL 要求的任何初始化。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>应用程序和 Dll 之间的差异

即使 Dll 和应用程序是这两个可执行模块，它们的区别在于通过多种方式。 向最终用户，最明显的区别是 Dll 不是可直接执行的应用程序。 从系统的角度来看，有两个应用程序和 Dll 之间的重要区别：

- 应用程序可以有多个实例的同时，在系统上运行，而 DLL 可以只有一个实例。

- 应用程序可以加载作为进程可以拥有一个堆栈、 执行、 全局内存、 文件句柄和消息队列的线程的事物，但 DLL 不能。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>使用 Dll 的优点

动态链接代替静态链接到代码和资源具有许多优点。 当使用 DLL 时，可以节省内存空间，并减少交换操作。 当多个应用程序可以使用 DLL 的单个副本时，可以节省磁盘空间和下载带宽。 DLL 可单独部署和更新，这可以使你在无需重新生成和发布所有代码的情况下，提供售后支持和软件更新。 DLL 是一种提供特定区域资源的简便方法，可以支持多语言程序，并简化创建国际版本应用程序的过程。 显式链接可以允许你的应用程序能够发现和在运行时，如提供新功能的扩展加载 Dll。

动态链接具有以下优点：

- 动态链接节省内存和减少交换操作。 许多进程可以使用 DLL 同时，共享内存中的 DLL 的只读部分的一个副本。 与此相反，使用静态链接的库生成每个应用程序具有 Windows 必须加载到内存中的库代码的完整副本。

- 动态链接，可以节省磁盘空间和带宽。 许多应用程序可以共享磁盘上的 DLL 的一个副本。 与此相反，使用静态链接库生成的每个应用程序链接到其可执行映像中，使用更多磁盘空间，而且需要更多的带宽要传输的库代码。

- 维护、 安全修补程序和升级可以更轻松。 当你的应用程序 DLL 中使用公共函数时，然后，只要不更改函数参数和返回值，可以实现 bug 修复并将更新部署到该 DLL。 当更新 Dll 时，使用它们的应用程序不需要重新编译或重新链接，并且它们使得新 DLL 的使用，只要它部署。 与此相反，在静态链接的对象代码中所做的修补程序要求您重新链接和重新部署每个应用程序使用它。

- Dll 可用于提供售后支持。 例如，可以修改显示驱动程序 DLL 以支持应用程序已发货时不可用的显示。 可以使用显式链接加载应用程序扩展为 Dll，并将新功能添加到您的应用程序，而无需重新生成或重新部署它。

- 动态链接，可以更轻松地支持在不同的编程语言编写的应用程序。 只要程序遵循函数的调用约定，用不同的编程语言编写的程序可以调用相同的 DLL 函数。 程序和 DLL 函数必须是兼容的以下方面： 该函数需要其自变量推送到堆栈上、 函数或应用程序是负责清理堆栈，以及任何自变量是中的顺序在寄存器中传递。

- 动态链接提供了一种机制来扩展 MFC 库类。 可以从现有的 MFC 类派生的类，并将其放置在使用的 MFC 扩展 DLL 的 MFC 应用程序。

- 动态链接可以更轻松的应用程序的国际版本的创建。 通过将特定于区域设置的资源放在 DLL 中，是创建国际版本的应用程序容易得多。 而不是传送许多本地化的版本的应用程序，可以将字符串和每种语言的映像放置在单独的资源 DLL，和你的应用程序然后将相应的资源对该区域设置在运行时加载。

使用 Dll 的一个潜在缺点是应用程序不是自包含;它依赖于单独的 DLL 模块，必须部署或作为在安装过程中验证自己存在。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>如何创建和使用 Dll 的详细信息

以下主题提供有关如何的详细的信息为视觉对象中的程序 Dll C++。

[演练：创建和使用动态链接库 (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
介绍如何使用 Visual Studio 创建和使用 DLL。

[DLL 的类型](kinds-of-dlls.md)<br/>
提供有关可生成的不同类型的 DLL 的信息。

[DLL 常见问题](dll-frequently-asked-questions.md)<br/>
提供有关 DLL 的常见问题解答。

[将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md)<br/>
描述与 DLL 的显式链接和隐式链接。

[初始化 DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
讨论当 DLL 加载时必须执行的 DLL 初始化代码。

[DLL 和 Visual C++ 运行时库行为](run-time-library-behavior.md)<br/>
描述运行库如何执行 DLL 启动序列。

[LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
讨论如何使用**LoadLibrary**和`AfxLoadLibrary`显式链接到在运行时的 DLL。

[GetProcAddress](getprocaddress.md)<br/>
讨论如何使用**GetProcAddress**获取 DLL 中导出函数的地址。

[FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
讨论如何使用**FreeLibrary**和`AfxFreeLibrary`当不再需要 DLL 模块。

[动态链接库搜索顺序](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
描述 Windows 操作系统用来定位系统上的 DLL 的搜索路径。

[动态链接到 MFC 的规则 MFC DLL 的模块状态](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
描述正则表达式 MFC DLL 动态链接到 MFC 模块的状态。

[MFC 扩展 DLL](extension-dlls-overview.md)<br/>
解释通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。

[创建纯资源 DLL](creating-a-resource-only-dll.md)<br/>
讨论只包含资源（如图标、位图、字符串和对话框等）的纯资源 DLL。

[MFC 应用程序中已本地化的资源：附属 DLL](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。

[导入和导出](importing-and-exporting.md)<br/>
描述如何将公共符号导入应用程序或从 DLL 导出函数。

[Active 技术和 DLL](active-technology-and-dlls.md)<br/>
使对象服务器得以在 DLL 内实现。

[DLL 中的自动化](automation-in-a-dll.md)<br/>
描述“MFC DLL 向导”中的“自动化”选项提供的内容。

[MFC DLL 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
讨论 MFC 中包含的 DLL 和库如何遵循结构化命名约定。

[从 Visual Basic 应用程序调用 DLL 函数](calling-dll-functions-from-visual-basic-applications.md)<br/>
描述如何从 Visual Basic 应用程序中调用 DLL 函数。

## <a name="related-sections"></a>相关章节

[将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
描述规则 MFC Dll，它可让你使用 MFC 库作为 Windows 动态链接库的一部分。

[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)<br/>
描述你将 mfcxx.dll 和 MFCxxD.dll （其中 x 是 MFC 版本号） 共享动态链接库与 MFC 应用程序和 MFC 扩展 Dll 的方式。
