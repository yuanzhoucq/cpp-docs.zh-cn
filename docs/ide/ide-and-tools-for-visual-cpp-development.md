---
title: 用于 Visual C++ 开发的 IDE 和工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4e7742afd3fecc4dd115624da0c1650dc662004
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412517"
---
# <a name="ide-and-tools-for-visual-c-development"></a>用于 Visual C++ 开发的 IDE 和工具

作为 Visual Studio 集成开发环境 (IDE) 的一部分，Microsoft Visual C++ (MSVC) 共享许多与其他语言相同的窗口和工具。 其中许多窗口和工具（包括“解决方案资源管理器”、“代码编辑器”和“调试器”）都记录在 [Visual Studio IDE](/visualstudio/ide/visual-studio-ide) 下。 通常，共享的工具或窗口为 C++ 提供的功能集与为 .NET 语言或 Javascript 提供的功能集略有不同。 某些窗口或工具仅在 Visual Studio Pro 或 Visual Studio Enterprise 中可用。

除了 Visual Studio IDE 中的共享工具之外，MSVC 还有几种专门用于本机代码开发的工具。 这些工具也会在本文中列出。 有关每个版本的 Visual Studio 可用的工具列表，请参阅 [Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="creating-a-solution-and-projects"></a>创建解决方案和项目

一个项目基本上就是一组植入进可执行文件的源代码文件和资源（例如图像或数据文件）。

Visual Studio 2015 提供对 MSBuild 项目的支持。 可下载适用于其他生成系统（例如 Qt 或 CMake）的 Visual Studio 扩展。

Visual Studio 2017 可支持要使用的任何生成系统或自定义生成工具，且完全支持 IntelliSense、浏览和调试：

- MSBuild 是 Visual Studio 的本机生成系统，通常是使用 MFC 或 ATL 的通用 Windows 平台 (UWP) 应用或旧版 Windows 桌面应用程序的最佳选择。 有关基于 MSBuild 的 C++ 项目的详细信息，请参阅[创建并管理基于 MSBuild 的项目](creating-and-managing-visual-cpp-projects.md)。
- CMake 是一个跨平台生成系统，在安装使用 C++ 的桌面开发时集成在 Visual Studio IDE 中。 有关详细信息，请参阅 [Visual C++ 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。
- 通过“打开文件夹”功能，支持任何其他 C++ 生成系统，包括松散的文件集合。 创建简单的 JSON 文件来调用生成程序并配置调试会话。 有关详细信息，请参阅 [Bring your C++ code to Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/)（向 Visual Studio 引入 C++ 代码）。

### <a name="project-templates-msbuild"></a>项目模板 (MSBuild)

Visual Studio 附带了几个模板，用于基于 MSBuild 的项目，其中包含多种基本程序类型所需的起始代码和设置。 通常，首先选择“文件” > “新建项目”，基于项目模板创建一个项目，然后向该项目添加新的源代码文件，或在提供的文件中开始编码。 有关特定于 C++ 项目和项目向导的信息，请参阅[创建和管理 Visual C++ 项目](../ide/creating-and-managing-visual-cpp-projects.md)。

### <a name="application-wizards-msbuild"></a>应用程序向导 (MSBuild)

选择“文件” > “新建项目”时，Visual Studio 为部分 MSBuild 项目类型提供向导。 向导将指导你逐步完成创建一个新项目的过程。 这对于具有许多选项和设置的项目类型很有用。 有关详细信息，请参阅[使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)。

## <a name="creating-user-interfaces-with-designers-msbuild"></a>使用设计器创建用户界面 (MSBuild)

如果你的程序包含用户界面，则首要任务之一是使用控件（如按钮和列表框等）对其进行填充。 Visual Studio 包括一个可视化设计图面和工具箱，可创建各种风格的 C++ 应用程序。 无论正在创建哪种类型的应用，基本理念都是相同的：从工具箱窗口拖动控件，将其放置到设计图面上的所需位置。 Visual Studio 将在后台生成使所有应用都正常运行所需的资源和代码。 然后编写代码，用数据填充控件，或者自定义控件的外观和行为。

有关设计通用 Windows 平台应用用户界面的详细信息，请参阅[设计和 UI](https://developer.microsoft.com/en-us/windows/design)。

有关为 MFC 应用程序创建用户界面的详细信息，请参阅 [MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)。 有关 Win32 Windows 程序的信息，请参阅 [Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)。

## <a name="writing-and-editing-code"></a>编写和编辑代码

### <a name="semantic-colorization"></a>语义着色

创建项目后，所有项目文件将都显示在“解决方案资源管理器”窗口中。 单击解决方案资源管理器中的 .h 或 .cpp 文件时，该文件将在代码编辑器中打开。 代码编辑器是专用于 C++ 源代码的字处理器。 它会以不同的颜色标记语言关键字、方法和变量名以及代码的其他元素，使代码更具可读性且更易于理解。

### <a name="intellisense"></a>IntelliSense

代码编辑器还支持几个功能，这些功能组合在一起被称为 IntelliSense。 可以将鼠标悬停在某种方法上，并查看该方法的一些相关基本文档。 键入类变量名称以及 . 或 -> 后，将显示该类的实例成员列表。 如果键入一个类名，然后键入 ::，则将显示静态成员列表。 当开始键入类名或方法名时，代码编辑器中将提供完成语句的建议。 有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

### <a name="code-snippets"></a>代码片段

可以使用 IntelliSense 代码片段，通过快捷方式击键生成常用的或复杂的代码构造。 有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。

## <a name="navigating-code"></a>导航代码

“视图”菜单提供对多个窗口和工具的访问，以便在代码文件中进行导航。 有关这些窗口的详细信息，请参阅[查看代码结构](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="solution-explorer"></a>“解决方案资源管理器”

在所有版本的 Visual Studio 中，使用“解决方案资源管理器”窗格在项目中的文件之间导航。 展开 .h 或 .cpp 文件图标，查看文件中的类。 展开某个类，以查看其成员。 双击某个成员，以导航到其在文件中的定义或实现。

### <a name="class-view-and-code-definition-window"></a>类视图和代码定义窗口

使用“类视图”窗格，可查看所有文件中的命名空间和类（包括分部类）。 展开每个命名空间或类可查看其成员，而双击成员可导航到源文件中的该位置。 如果打开“代码定义”窗口，则在类视图中选择类型时，可以查看该类型的定义或实现。

### <a name="object-browser"></a>对象浏览器

使用“对象浏览器”浏览 Windows 运行时组件（.winmd 文件）、.NET 程序集和 COM 类型库中的类型信息。 它不与 Win32 DLL 一起使用。

### <a name="go-to-definitiondeclaration"></a>转到定义/声明

在任何 API 名称或成员变量上按 F12，以转到其定义。 如果定义位于 .winmd 文件（对于 UWP 或 Windows 8.x Store 应用）中，则将在对象浏览器中显示类型信息。 还可右键单击变量名或类型名称，并从上下文菜单中选择相应选项，以选择“转到定义”或“转到声明”。

### <a name="find-all-references"></a>查找所有引用

在源代码文件中，将鼠标光标置于类型、方法或变量的名称上，右键单击，并选择“查找所有引用”，以返回文件、项目或解决方案中使用该类型的每个位置的列表。 “查找所有引用”十分智能，仅返回同一变量的实例，即使其他作用域中的其他变量具有相同的名称。

## <a name="add-and-edit-resources--msbuild"></a>添加和编辑资源 (MSBuild)

Visual Studio 桌面项目上下文中的术语“资源”包括许多内容，例如对话框、图标、可本地化的字符串、初始屏幕、数据库连接字符串或想要包含在可执行文件中的任意数据。

有关添加和编辑本机桌面 C++ 项目中的资源的详细信息，请参阅[使用资源文件](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>生成（编译和链接）

要编译和链接项目，请在菜单栏选择“生成” > “生成解决方案”，或按组合键 Ctrl+Shift+B。 为了创建可执行代码，Visual Studio 使用 [MSBuild](/visualstudio/msbuild/msbuild1)CMake 或任何通过“打卡文件夹”功能设置的生成环境。 对于 MSBuild 项目，可在“工具” > “选项” > “项目和解决方案”下设置常规生成选项，还可在“项目” > “属性”下为特定项目设置属性。 将在“错误列表”中报告生成错误和警告（Ctrl+\\、Ctrl+E）。 非 MSBuild 项目使用在解决方案资源管理器中创建的 JSON 文件配置。 无论所使用何种生成系统，“输出”窗口 (Alt+2) 都显示生成过程的相关信息。 有关 MSBuild 配置的详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)和[在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)。

还可以直接从命令行使用编译器 (cl.exe) 和许多其他与生成相关的独立工具（如 NMAKE 和 LIB）。 有关详细信息，请参阅[在命令行上生成 C/C++ 代码](../build/building-on-the-command-line.md)以及 [C/C++ 生成参考](../build/reference/c-cpp-building-reference.md)。

## <a name="test"></a>测试

Visual Studio 包含一个用于本机 C++ 和 C++/CLI 的单元测试框架。 有关详细信息，请参阅[使用单元测试验证代码](/visualstudio/test/unit-test-your-code)和[用适用于 C++ 的 Microsoft 单元测试框架编写 C/C++ 单元测试](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="analyze"></a>分析

Visual Studio 包含用于 C++ 的静态代码分析工具，包括 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 规则检查器的实现。 有关详细信息，请参阅 [C/C++ 代码分析概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="debug"></a>调试

将项目配置设置为“调试”时，按 F5 即可调试程序。 在调试期间，可通过按 F9 设置断点、按 F10 逐步执行代码、查看指定变量或寄存器的值，甚至还可在某些情况下在代码中进行更改并继续调试，而无需重新编译。 有关详细信息，请参阅[使用 Visual Studio 进行调试](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="deploy-completed-applications"></a>部署已完成的应用程序

使用“项目” > “Microsoft Store”菜单选项，可通过 Microsoft Store 向客户部署 UWP 应用。 将在后台自动处理 CRT 的部署。 有关详细信息，请参阅[发布 Windows 应用和游戏](/windows/uwp/publish/)。

将本机 C++ 桌面应用程序部署到另一台计算机时，必须安装该应用程序及其依赖的任何库文件。 可通过三种方式使用应用程序部署通用 C++ 运行时 (UCRT)：集中部署、本地部署或静态链接。 有关详细信息，请参阅[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)。

有关部署 C++/CLI 程序的详细信息，请参阅[面向开发人员的部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。

## <a name="related-articles"></a>相关文章

|||
|-|-|
|[Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|显示各种版本的 Visual Studio 中提供的功能。|
|[创建和管理基于 MSBuild 的项目](../ide/creating-and-managing-visual-cpp-projects.md)|概述了 Visual Studio 中基于 MSBuild 的 C++ 项目和指向其他介绍如何创建和管理它们的文章的链接。|
|[Visual C++ 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。|介绍如何生成 Visual C++ 中的 CMake 项目或其他非 MSBuild 项目。|
|[生成 C/C++ 程序](../build/building-c-cpp-programs.md)|介绍如何生成 C++ 项目。|
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|对 C++ 应用的部署和指向其他详细介绍部署的文章的链接进行了概述。|
|[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)|有关如何升级在早期版本的 Visual Studio 中创建的 C++ 应用程序，以及如何迁移使用 Visual Studio 以外的工具创建的应用程序的详细信息。|
|[Visual C++](../visual-cpp-in-visual-studio.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，并链接到 Visual C++ 文档的剩余部分。|
