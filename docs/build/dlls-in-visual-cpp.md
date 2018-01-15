---
title: "Visual c + + 中的 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed3679d29b8d181e2cbd9896d0322fea634bfbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-in-visual-c"></a>Visual C++ 中的 DLL  
  
在 Windows 中，动态链接库 (DLL) 是一种作为函数和资源的共享库的可执行文件。 动态链接是一项操作系统功能，可执行文件以调用函数，或使用存储在单独的文件的资源。 可从使用这些函数和资源的可执行文件中对其分别进行编译和部署。 DLL 不是独立的可执行文件;它的应用程序调用它的上下文中运行。 到应用程序的内存空间操作系统加载 DLL 加载应用程序时 (*隐式链接*)，或按需在运行时 (*显式链接*)。 DLL 还可以在可执行文件之间轻松共享函数和资源。 多个应用程序可同时访问内存中单个 DLL 副本的内容。  
  
## <a name="differences-between-dynamic-linking-and-static-linking"></a>动态链接与静态链接之间的差异  
  
静态链接将复制所有对象代码中的静态库到生成它们时使用它的可执行文件。 动态链接包括仅在运行时来查找并加载包含数据项或函数的 DLL Windows 所需的信息。 在创建 DLL 时，你还创建导入库，其中包含此信息。 生成调用 DLL 的可执行文件时，链接器会使用的导入库中的导出的符号来存储此信息 Windows 加载程序。 当加载程序加载 DLL 时，该 DLL 会映射到你的应用程序的内存空间。 在 DLL 中，如果存在，函数特殊`DllMain`，调用以执行 DLL 要求的任何初始化。  
  
<a name="differences-between-applications-and-dlls"></a>  
  
## <a name="differences-between-applications-and-dlls"></a>应用程序和 Dll 之间的差异  
  
即使 Dll 和应用程序都是两个可执行模块，它们的区别在于通过多种方式。 向最终用户，最明显的区别是 Dll 不是可直接执行的应用程序。 从系统的角度来看，有两个应用程序和 Dll 之间的基本差异：  
  
-   应用程序可以有多个实例的同时，在系统上运行，而 DLL 只能有一个实例。  
  
-   应用程序可以加载作为等堆栈、 线程执行、 全局内存、 文件句柄和消息队列，都可以拥有的进程，但 DLL 不能。  
  
<a name="advantages-of-using-dlls"></a>  
  
## <a name="advantages-of-using-dlls"></a>使用 Dll 的优点  
  
动态链接代替静态链接到代码和资源有若干优点。 当使用 DLL 时，可以节省内存空间，并减少交换操作。 当多个应用程序可以使用 DLL 的单个副本时，可以节省磁盘空间和下载带宽。 DLL 可单独部署和更新，这可以使你在无需重新生成和发布所有代码的情况下，提供售后支持和软件更新。 DLL 是一种提供特定区域资源的简便方法，可以支持多语言程序，并简化创建国际版本应用程序的过程。 显式链接可以允许你的应用程序能够发现和加载 Dll 在运行时，如提供新功能的扩展。  
  
动态链接具有以下优点：  
  
-   动态链接节省内存，减少交换操作。 多进程可以使用 DLL 同时，共享内存中的 DLL 的只读的组成部分的单个副本。 与此相反，每个应用程序使用静态链接的库生成具有 Windows 必须加载到内存中的库代码的完整副本。  
  
-   动态链接，可以节省磁盘空间和带宽。 许多应用程序可以共享单个 DLL 副本的磁盘上。 与此相反，使用静态链接库生成的每个应用程序链接到其可执行映像，使用更多磁盘空间，而且需要更多的带宽要传输的库代码。  
  
-   维护安全修补程序和升级可能会更加轻松。 当你的应用程序使用在 DLL 中的常见函数时，然后，只要函数自变量和返回值不会更改，您可以实施 bug 修复并将更新部署到该 DLL。 Dll 进行更新后，使用它们的应用程序不需要重新编译或重新链接，并且它们使部署时，就会立即使用新的 DLL。 与此相反，在静态链接的对象代码中所做的修补程序要求您重新链接，并重新部署每个应用程序使用它。  
  
-   Dll 可用于提供售后支持。 例如，可以修改显示驱动程序 DLL，来支持应用程序已发货时没有可显示。 你可以使用显式链接以加载应用程序扩展为 Dll，并将新功能添加到你的应用程序，而无需重新生成或重新部署它。  
  
-   动态链接可使更轻松地支持在不同的编程语言中编写的应用程序。 用不同的编程语言编写的程序可以调用相同的 DLL 函数，只要程序遵循函数的调用约定。 程序和 DLL 函数必须通过以下方式兼容： 函数期望其参数被推送到堆栈上，该函数或应用程序是负责清理堆栈，以及任何自变量是否的顺序在寄存器中传递。  
  
-   动态链接提供了一种机制来扩展 MFC 库类。 你可以从现有的 MFC 类派生的类，并将其放在使用 MFC 扩展 DLL 中，由 MFC 应用程序。  
  
-   动态链接使你的应用程序的国际版本创建更容易。 通过将特定于区域设置资源放在 DLL 中，就可以更轻松地创建国际版本应用程序。 传送你的应用程序的许多本地化的版本，你可以将字符串和针对每种语言的图像放在单独的资源 DLL，而非你的应用程序可以然后加载该区域在运行时设置的相应资源。   
  
 使用 Dll 潜在缺点是应用程序不是自包含;它依赖于必须部署或作为安装过程中验证自己的单独 DLL 模块存在。  
  
  
## <a name="more-information-on-how-to-create-and-use-dlls"></a>如何创建和使用 Dll 的详细信息  
  
以下主题提供有关如何的详细的信息，Visual c + + 编程 dll。  
  
 [演练：创建和使用动态链接库 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 介绍如何使用 Visual Studio 创建和使用 DLL。  
  
 [DLL 的类型](../build/kinds-of-dlls.md)  
 提供有关可生成的不同类型的 DLL 的信息。  
  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)  
 提供有关 DLL 的常见问题解答。  
  
 [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)  
 描述与 DLL 的显式链接和隐式链接。  
  
 [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
 讨论当 DLL 加载时必须执行的 DLL 初始化代码。  
  
 [DLL 和 Visual C++ 运行时库行为](../build/run-time-library-behavior.md)  
 描述运行库如何执行 DLL 启动序列。  
  
 [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 讨论如何使用**LoadLibrary**和`AfxLoadLibrary`显式链接到在运行时的 DLL。  
  
 [GetProcAddress](../build/getprocaddress.md)  
 讨论如何使用**GetProcAddress**获取 DLL 中导出的函数的地址。  
  
 [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 讨论如何使用**FreeLibrary**和`AfxFreeLibrary`不再需要 DLL 模块时。  
  
 [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 描述 Windows 操作系统用来定位系统上的 DLL 的搜索路径。  
  
 [动态链接到 MFC 的规则 MFC DLL 的模块状态](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 描述正则表达式 MFC DLL 动态链接到 MFC 模块的状态。  
  
 [MFC 扩展 DLL](../build/extension-dlls-overview.md)  
 解释通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。  
  
 [创建纯资源 DLL](../build/creating-a-resource-only-dll.md)  
 讨论只包含资源（如图标、位图、字符串和对话框等）的纯资源 DLL。  
  
 [MFC 应用程序中已本地化的资源：附属 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。  
  
 [导入和导出](../build/importing-and-exporting.md)  
 描述如何将公共符号导入应用程序或从 DLL 导出函数。  
  
 [Active 技术和 DLL](../build/active-technology-and-dlls.md)  
 使对象服务器得以在 DLL 内实现。  
  
 [DLL 中的自动化](../build/automation-in-a-dll.md)  
 描述“MFC DLL 向导”中的“自动化”选项提供的内容。  
  
 [MFC DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md)  
 讨论 MFC 中包含的 DLL 和库如何遵循结构化命名约定。  
  
 [从 Visual Basic 应用程序调用 DLL 函数](../build/calling-dll-functions-from-visual-basic-applications.md)  
 描述如何从 Visual Basic 应用程序中调用 DLL 函数。  
  
## <a name="related-sections"></a>相关章节  
  
 [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 描述规则的 MFC Dll，它可让你使用 MFC 库作为 Windows 动态链接库的一部分。  
  
 [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
 描述如何可以使用 MFCxx.dll 和 MFCxxD.dll （其中 x 是 MFC 版本号） 共享动态链接库用于 MFC 应用程序和 MFC 扩展 Dll。  
