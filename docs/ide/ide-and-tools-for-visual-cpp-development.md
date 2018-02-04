---
title: "IDE 和 Visual c + + 开发工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01d4898b2d67de4b23d31227e572c0f270aa6f37
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="ide-and-tools-for-visual-c-development"></a>用于 Visual C++ 开发的 IDE 和工具

作为一部分的 Visual Studio 集成开发环境 (IDE)，Microsoft Visual c + + (MSVC) 共享许多窗口和工具与其他语言相同。 其中包括许多**解决方案资源管理器**，代码编辑器中和调试器，都记录在[Visual Studio IDE](/visualstudio/ide/visual-studio-ide)。 通常，共享的工具或窗口为 C++ 提供的功能集与为 .NET 语言或 Javascript 提供的功能集略有不同。 某些窗口或工具仅在 Visual Studio Pro 或 Visual Studio Enterprise 中可用。

除了 Visual Studio IDE 中的共享工具，MSVC 还具有几种专门用于本机代码开发工具。 这些工具也会在本文中列出。 有关工具的每个版本的 Visual Studio 中提供的列表，请参阅[Visual c + + 工具和 Visual Studio 版本中的功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="creating-a-solution-and-projects"></a>创建解决方案和项目

A*项目*基本上是一套源代码文件和资源如图像或数据文件中的内置的可执行文件。 Visual Studio 2017 可以支持的任何生成系统或你想要使用 intellisense，浏览和调试的完全支持带有自定义生成工具：

- MSBuild 是 Visual Studio 的本机生成系统和通常是最佳选择的通用 Windows 平台 (UWP) 应用或旧 Windows 桌面应用程序使用 MFC 或 atl。 有关基于 MSBuild 的 c + + 项目的详细信息，请参阅[创建和管理基于 MSBuild 的项目](creating-and-managing-visual-cpp-projects.md)。
- CMake 是跨平台生成已集成到 Visual Studio IDE 中，当你安装桌面开发与 c + + 工作负荷时的系统。 有关详细信息，请参阅 [Visual C++ 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。
- 支持的任何其他 c + + 生成系统，包括松散文件的集合，通过打开文件夹功能。 创建简单的 JSON 文件，以调用生成程序并配置调试会话。 有关详细信息，请参阅[到 Visual Studio 将你的 c + + 代码](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/)。

### <a name="project-templates-msbuild"></a>项目模板 (MSBuild)

Visual Studio 附带了几个模板为基于 MSBuild 的项目;这些模板包含起始代码和多种基本程序类型所需的设置。 通常，首先通过选择**文件** > **新项目**从项目模板创建项目，然后将新的源代码文件添加到该项目，或提供的文件中开始编码。 特定于 c + + 项目和项目向导的信息，请参阅[创建和管理 Visual c + + 项目](../ide/creating-and-managing-visual-cpp-projects.md)。

### <a name="application-wizards-msbuild"></a>应用程序向导 (MSBuild)

Visual Studio 为某些 MSBuild 项目类型提供向导，当你选择**文件** > **新项目**。 向导将指导你逐步完成创建一个新项目的过程。 这对于具有许多选项和设置的项目类型很有用。 有关详细信息，请参阅[创建桌面项目通过使用应用程序向导](../ide/creating-desktop-projects-by-using-application-wizards.md)。

## <a name="creating-user-interfaces-with-designers-msbuild"></a>使用设计器 (MSBuild) 创建用户界面

如果你的程序包含用户界面，则首要任务之一是使用控件（如按钮和列表框等）对其进行填充。 Visual Studio 包括一个可视化设计图面和工具箱，可创建各种风格的 C++ 应用程序。 无论正在创建哪种类型的应用，基本理念都是相同的：从工具箱窗口拖动控件，将其放置到设计图面上的所需位置。 Visual Studio 将在后台生成使所有应用都正常运行所需的资源和代码。 然后，你编写代码以填充数据的控件或自定义其外观和行为。

有关设计通用 Windows 平台应用的用户界面的详细信息，请参阅[设计和 UI](https://developer.microsoft.com/en-us/windows/design)。

有关创建 MFC 应用程序的用户界面的详细信息，请参阅[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)。 有关 Win32 Windows 程序的信息，请参阅[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)。

## <a name="writing-and-editing-code"></a>编写和编辑代码

### <a name="semantic-colorization"></a>语义着色

创建项目后，所有项目文件将都显示在**解决方案资源管理器**窗口。 当你单击的.h 或.cpp 文件中**解决方案资源管理器**，文件将打开代码编辑器中。 代码编辑器是专用于 C++ 源代码的字处理器。 它会以不同的颜色标记语言关键字、方法和变量名以及代码的其他元素，使代码更具可读性且更易于理解。

### <a name="intellisense"></a>Intellisense

代码编辑器还支持几个功能，这些功能组合在一起被称为 Intellisense。 可以将鼠标悬停在某种方法上，并查看该方法的一些相关基本文档。 键入类变量名称以及 . 或 -> 后，将显示该类的实例成员列表。 如果键入一个类名，然后键入 ::，则将显示静态成员列表。 当开始键入类名或方法名时，代码编辑器中将提供完成语句的建议。 有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

### <a name="code-snippets"></a>代码片段

可以使用 Intellisense 代码片段，通过快捷方式击键生成常用的或复杂的代码构造。 有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。

## <a name="navigating-code"></a>导航代码

**视图**菜单提供对许多窗口和工具用于在你的代码文件中导航的访问。 有关这些时窗口的详细信息，请参阅[查看代码结构](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="solution-explorer"></a>“解决方案资源管理器”

在所有版本的 Visual Studio 中，使用**解决方案资源管理器**窗格在项目中的文件之间导航。 展开 .h 或 .cpp 文件图标，查看文件中的类。 展开某个类，以查看其成员。 双击某个成员，以导航到其在文件中的定义或实现。

### <a name="class-view-and-code-definition-window"></a>类视图和代码定义窗口

使用**类视图**窗格以查看所有文件，包括分部类中的命名空间和类。 展开每个命名空间或类可查看其成员，而双击成员可导航到源文件中的该位置。 如果你打开**代码定义窗口**，你可以定义或实现的类型选择时，查看在**类视图**。

### <a name="object-browser"></a>对象浏览器

使用**对象浏览器**浏览 Windows 运行时组件 （.winmd 文件） 中的类型信息，.NET 程序集和 COM 类型库。 它不与 Win32 DLL 一起使用。

### <a name="go-to-definitiondeclaration"></a>转到定义/声明

在任何 API 名称或成员变量上按 F12，以转到其定义。 如果定义位于.winmd 文件 （适用于 UWP 或 Windows 8.x 应用商店应用），则将在对象浏览器中显示类型信息。 你还可以选择**转到定义**或**转到声明**通过右键单击变量或类型名称，并从上下文菜单中选择的选项。

### <a name="find-all-references"></a>查找所有引用

在源代码文件中，右键单击将鼠标光标置于类型、 方法或变量的名称并选择**查找所有引用**以返回的每个位置的列表中的文件、 项目或解决方案中使用类型。 **查找所有引用**十分智能，仅返回同一变量的实例，即使其他作用域中的其他变量具有相同的名称。

## <a name="add-and-edit-resources--msbuild"></a>添加和编辑资源 (MSBuild)

术语*资源*桌面项目在 Visual Studio 的上下文中包括如对话框、 图标、 可本地化的字符串、 初始屏幕、 数据库连接字符串或你想要在中包含的任意数据的内容可执行文件。

有关添加和编辑本机桌面 c + + 项目中的资源的详细信息，请参阅[使用资源文件](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>生成 （编译和链接）

选择**生成** > **生成解决方案**在菜单栏，或输入 Ctrl + Shift + B 组合键，编译并链接一个项目。 若要创建可执行代码，Visual Studio 将使用[MSBuild](/visualstudio/msbuild/msbuild1)或 CMake 或任何构建环境，你将设置为通过**打开文件夹**。 对于 MSBuild 项目，设置下的常规生成选项**工具** > **选项** > **项目和解决方案**还可以设置属性对于下的特定项目**项目** > **属性**。 错误列表中报告生成错误和警告 (Ctrl +\\，E)。 非 MSBuild 项目配置与你在解决方案资源管理器中创建的 JSON 文件中。 任何生成的系统使用，**输出**窗口 (Alt + 2) 将显示有关生成过程的信息。 有关 MSBuild 配置的详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)和[Visual Studio 中生成 c + + 项目](../ide/building-cpp-projects-in-visual-studio.md)。

你还可以使用编译器 (cl.exe) 和许多其他与生成相关的独立工具如 NMAKE 和 LIB 直接从命令行。 有关详细信息，请参阅[命令行上的生成 C/c + + 代码](../build/building-on-the-command-line.md)和[C/c + + 生成参考](../build/reference/c-cpp-building-reference.md)。

## <a name="test"></a>测试

Visual Studio 包含一个用于本机 C++ 和 C++/CLI 的单元测试框架。 有关详细信息，请参阅[使用单元测试验证代码](/visualstudio/test/unit-test-your-code)和[编写 C/c + + 的 Microsoft 单元测试框架适用于单元测试 c + +](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="debug"></a>调试

你可以通过按调试程序**F5**当你的项目配置设置为调试。 调试你可以通过按设置断点时**F9**，按逐步执行代码**F10**、 查看指定的变量或寄存器的值和甚至在某些情况下在代码中进行更改并继续调试而无需重新编译。 有关详细信息，请参阅[使用 Visual Studio 进行调试](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="deploy-completed-applications"></a>部署已完成应用程序

UWP 应用部署到通过 Windows 应用商店客户**项目** > **存储**菜单选项。 将在后台自动处理 CRT 的部署。 有关更多信息，请参阅 [将你的应用投入市场](http://go.microsoft.com/fwlink/p/?LinkId=262280)。

将本机 C++ 桌面应用程序部署到另一台计算机时，必须安装该应用程序及其依赖的任何库文件。 有三种方法来部署通用 c + + 运行时 (UCRT) 与应用程序： 集中部署、 本地部署或静态链接。 有关详细信息，请参阅[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)。

有关部署 C + + /cli 程序，请参阅[开发人员部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)，

## <a name="related-articles"></a>相关文章

|||
|-|-|
|[Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|显示各种版本的 Visual Studio 中提供的功能。|
|[创建和管理基于 MSBuild 的项目](../ide/creating-and-managing-visual-cpp-projects.md)|概述在 Visual Studio 和指向其他介绍如何创建和管理它们的文章基于 c + + MSBuild 的项目。|
|[Visual c + + 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。|介绍如何构建 CMake 或 Visual c + + 中的其他非 MSBuild 项目。|
|[生成 C/C++ 程序](../build/building-c-cpp-programs.md)|介绍如何生成 C++ 项目。|
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|对 C++ 应用的部署和指向其他详细介绍部署的文章的链接进行了概述。|
|[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)|有关如何升级在 Visual Studio 的早期版本中创建的 c + + 应用程序以及如何将应用程序使用工具而非 Visual Studio 创建的迁移的详细的信息。|
|[Visual C++](../top/visual-cpp-in-visual-studio.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，并链接到 Visual C++ 文档的剩余部分。|
