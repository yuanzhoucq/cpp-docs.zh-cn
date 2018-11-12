---
title: 用于 Visual C++ 开发的 IDE 和工具
description: Visual Studio IDE 支持在 Windows、Linux、Android 和 iOS 上通过代码编辑器、调试程序、测试框架、静态诊断分析器以及其他编程工具进行 C++ 开发。
ms.date: 09/27/2018
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
ms.openlocfilehash: e24ba58cf0cf94f1505adaf056f64580b8f7829e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473354"
---
# <a name="ide-and-compiler-tools-for-visual-c-development"></a>用于 Visual C++ 开发的 IDE 和编译器工具

作为 Visual Studio 集成开发环境 (IDE) 的一部分，Microsoft Visual C++ (MSVC) 共享许多与其他语言相同的窗口和工具。 其中许多窗口和工具（包括“解决方案资源管理器”、“代码编辑器”和“调试器”）都记录在 [Visual Studio IDE](/visualstudio/ide/visual-studio-ide) 下。 通常，相比为 .NET 语言或 JavaScript 提供的功能集，共享的工具或窗口为 C++ 提供的功能集略有不同。 一些窗口或工具仅在 Visual StudioProfessional 或 Visual Studio Enterprise 版本中可用。

除了 Visual Studio IDE 中的共享工具之外，MSVC 还有几种专门用于本机代码开发的工具。 这些工具也会在本文中列出。 有关每个版本的 Visual Studio 可用的工具列表，请参阅 [Visual Studio 版本中的 Visual C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="create-projects"></a>创建项目

一个项目基本上就是一组植入进可执行文件的源代码文件和资源（例如图像或数据文件）。

Visual Studio 2015 提供对 MSBuild 项目的支持。 可下载适用于其他生成系统（例如 Qt 或 CMake）的 Visual Studio 扩展。

Visual Studio 2017 可支持要使用的任何生成系统或自定义生成工具，且完全支持 IntelliSense、浏览和调试：

- MSBuild 是 Visual Studio 的本机生成系统。 从主菜单中选择“文件” > “新建” > “项目”时，你可以看到多种 MSBuild 项目模板，可帮助你快速开始开发不同类型的 C++ 应用程序。

   ![项目模板](media/vs2017-new-project.png "Visual Studio 2017 新建项目对话框")

   一般情况下，请为新项目使用这些模板，除非有特定原因要使用 CMake 或其他项目系统。 有些项目会提供向导来帮助你逐步完成创建新项目的过程。 有关详细信息，请参阅[创建和管理基于 MSBuild 的项目](creating-and-managing-visual-cpp-projects.md)。

- CMake 是一个跨平台生成系统，在安装使用 C++ 的桌面开发负载时集成在 Visual Studio IDE 中。 有关详细信息，请参阅 [Visual C++ 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。
- 通过“打开文件夹”功能，支持任何其他 C++ 生成系统，包括松散的文件集合。 创建简单的 JSON 文件来调用生成程序并配置调试会话。 有关详细信息，请参阅 [Visual C++ 中的“打开文件夹”项目](non-msbuild-projects.md)。

## <a name="add-to-source-control"></a>添加到源控件

通过源控件，可让你协调多个开发人员的工作，将正在进行中的工作与生产代码隔离并备份源代码。 Visual Studio 通过其“团队资源管理器”窗口支持 Git 和 [Team Foundation 版本控制 \(TFVC\)](/azure/devops/repos/tfvc/)。

![团队资源管理器](media/vs2017-team-explorer.png "Visual Studio 2017 团队资源管理器")

有关 Azure 中 Git 与存储库集成的详细信息，请参阅[与 Visual Studio 2017 和 Azure Repos Git 共享代码](/azure/devops/repos/git/share-your-code-in-git-vs-2017)。 有关 Git 与 GitHub 集成的信息，请参阅[适用于 Visual Studio 的 GitHub 扩展](https://visualstudio.github.com/)。

## <a name="create-user-interfaces-with-designers"></a>使用设计器创建用户界面

如果你的程序包含用户界面，则可以使用设计器为其快速填充按钮和列表框等控件。 从工具箱窗口拖动控件并将其放到设计图面上时，Visual Studio 会生成使其正常运行所需的资源和代码。 然后，你编写代码来自定义外观和行为。

![设计器和工具箱](media/vs2017-toolbox-designer.png "Visual Studio 2017 工具箱和设计器")

有关设计通用 Windows 平台应用用户界面的详细信息，请参阅[设计和 UI](https://developer.microsoft.com/windows/design)。

有关为 MFC 应用程序创建用户界面的详细信息，请参阅 [MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)。 有关 Win32 Windows 程序的信息，请参阅 [Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)。

## <a name="write-code"></a>编写代码

创建项目后，所有项目文件将都显示在“解决方案资源管理器”窗口中。 （解决方案是用于一个或多个相关项目的逻辑容器。）单击解决方案资源管理器中的 .h 或 .cpp 文件时，该文件将在代码编辑器中打开。

![解决方案资源管理器和代码编辑器](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 解决方案资源管理器和代码编辑器")

代码编辑器是专用于 C++ 源代码的字处理器。 它会以不同的颜色标记语言关键字、方法和变量名以及代码的其他元素，使代码更具可读性且更易于理解。

有关详细信息，请参阅[编写和重构代码](writing-and-refactoring-code-cpp.md)。

## <a name="add-and-edit-resources"></a>添加和编辑资源

“资源”一词包括许多内容，例如对话框、图标、图像、可本地化的字符串、初始屏幕、数据库连接字符串，或想要包含在可执行文件中的任意数据。

有关添加和编辑本机桌面 C++ 项目中的资源的详细信息，请参阅[使用资源文件](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>生成（编译和链接）

要编译和链接项目，请在菜单栏选择“生成” > “生成解决方案”，或按组合键 Ctrl+Shift+B。 将在“错误列表”中报告生成错误和警告（Ctrl+\\、Ctrl+E）。 “输出”窗口 (Alt+2) 显示生成过程的相关信息。

![输出窗口和错误列表](media/vs2017-output-error-list.png "Visual Studio 2017 输出窗口和错误列表") 有关 MSBuild 配置的详细信息，请参阅[使用项目属性](working-with-project-properties.md)和[在 Visual Studio 中生成 C++ 项目](building-cpp-projects-in-visual-studio.md)。

还可以直接从命令行使用编译器 (cl.exe) 和许多其他与生成相关的独立工具（如 NMAKE 和 LIB）。 有关详细信息，请参阅[在命令行上生成 C/C++ 代码](../build/building-on-the-command-line.md)以及 [C/C++ 生成参考](../build/reference/c-cpp-building-reference.md)。

## <a name="debug"></a>调试

你可以通过按 F5 键开始调试。 执行会在你设置的任何断点暂停。 你也可以一次一行地逐步执行代码、查看变量或寄存器的值，某些情况下甚至可在代码中进行更改并继续调试，而无需重新编译。 下图显示了一个在断点处停止执行的调试会话。 数据结构成员的值显示在“监视窗口”中。

![调试会话](media/vs2017-debug-watch.png "Visual Studio 2017 调试会话")

有关详细信息，请参阅[使用 Visual Studio 进行调试](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="test"></a>测试

Visual Studio 包含用于本机 C++ 和 C++/CLI 的单元测试框架。 此外还支持 Boost.Test、Google Test 和 CTest。 从“测试资源管理器”窗口运行测试：

![测试资源管理器](media/cpp-test-explorer-passed.png "Visual Studio 2017 测试资源管理器")

有关详细信息，请参阅[使用单元测试验证代码](/visualstudio/test/unit-test-your-code)和[在 Visual Studio 中为 C/C++ 编写单元测试](/visualstudio/test/writing-unit-tests-for-c-cpp)。

## <a name="analyze"></a>分析

Visual Studio 包含可以在源代码中检测潜在问题的静态代码分析工具。 这些工具包括 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 规则检查器的实现。 有关详细信息，请参阅 [C/C++ 代码分析概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="deploy-completed-applications"></a>部署已完成的应用程序

你可以通过 Microsoft Store 将传统桌面应用程序和 UWP 应用部署到客户。 将在后台自动处理 CRT 的部署。 有关详细信息，请参阅[发布 Windows 应用和游戏](/windows/uwp/publish/)。

此外，还可以将本机 C++ 桌面部署到另一台计算机。有关详细信息，请参阅[部署桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)。

有关部署 C++/CLI 程序的详细信息，请参阅[面向开发人员的部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。

## <a name="related-articles"></a>相关文章

|||
|-|-|
|[Visual Studio 版本中的 Visual C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)|显示各种版本的 Visual Studio 中提供的功能。|
|[创建和管理基于 MSBuild 的项目](creating-and-managing-visual-cpp-projects.md)|概述了 Visual Studio 中基于 MSBuild 的 C++ 项目和指向其他介绍如何创建和管理它们的文章的链接。|
|[Visual C++ 中的 CMake 项目](cmake-tools-for-visual-cpp.md)。|介绍如何生成 Visual C++ 中的 CMake 项目或其他非 MSBuild 项目。|
|[生成 C/C++ 程序](../build/building-c-cpp-programs.md)|介绍如何生成 C++ 项目。|
|[部署桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)|对 C++ 应用的部署和指向其他详细介绍部署的文章的链接进行了概述。|
|[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)|有关如何升级在早期版本的 Visual Studio 中创建的 C++ 应用程序，以及如何迁移使用 Visual Studio 以外的工具创建的应用程序的详细信息。|
|[Visual C++](../visual-cpp-in-visual-studio.md)|描述 Visual C++ 在 Visual Studio 中的主要功能，并链接到 Visual C++ 文档的剩余部分。|
