---
title: 在 Visual Studio 中生成 C++ 项目 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7008e7fe670471301968482fbd4c6c758f0ff5e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340497"
---
# <a name="building-c-projects-in-visual-studio"></a>在 Visual Studio 中生成 C++ 项目
在 Visual Studio 集成开发环境 (IDE) 中，可通过多种方式生成整个解决方案或只在其中生成一个项目。 还可以修改生成设置并指定自定义生成步骤，以使你的部署过程更加高效。  
  
 要生成可在 Visual Studio 中打开并可在“解决方案资源管理器”中选择的解决方案，可以执行以下操作：  
  
-   在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
-   或者，在“解决方案资源管理器”中，打开解决方案的快捷菜单，然后选择“生成解决方案”。  
  
-   或者，按 F7。 （这是 C/C++ 开发设置的默认键盘快捷方式。）  
  
-   或者，在[命令窗口](/visualstudio/ide/reference/command-window)（在菜单栏上，依次选择“视图”、“其他窗口”、“命令窗口”）中，输入 `Build.BuildSolution`。  
  
-   或者，在[快速启动](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box)框中，输入 `build build solution`。  
  
 要生成可在“解决方案资源管理器”中选择的项目，可以执行以下操作：  
  
-   在菜单栏上，依次选择“生成”、“生成 \<项目名称>”。  
  
-   或者，在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“生成”。  
  
-   或者，在“命令窗口”（在菜单栏上，依次选择“视图”、“其他窗口”、“命令窗口”）中，输入 `Build.BuildOnlyProject`。  
  
-   或者，在“快速启动”框中，输入 `build project only build only <project name>`。  
  
 在 Visual Studio 中生成 Visual C++ 应用程序时，可以在项目的“属性页”对话框中修改许多生成设置。 有关如何设置项目属性的信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
 有关如何使用 IDE 来创建、生成和调试 C++ 项目的示例，请参阅[演练：通过 C++ 了解 Visual Studio IDE](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)。 有关如何使用 IDE 来生成 C++/CLR 项目的示例，请参阅[演练：在 Visual Studio 中编译面向 CLR 的 C++ 程序](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。 有关如何使用 IDE 来创建 Windows 运行时应用的示例，请参阅[使用 C++ 创建第一个 Windows 运行时应用](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx)。  
  
 若要阅读有关如何生成、修改生成设置和指定自定义生成步骤的详细信息，请参阅以下文章。  
  
## <a name="in-this-section"></a>本节内容  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)  
 介绍如何在集成开发环境中自定义生成过程。  
  
 [用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)  
 列出在接受字符串的情况下可使用的宏。  
  
 [生成外部项目](../ide/building-external-projects.md)  
 探讨如何生成在集成开发环境之外使用功能的项目。  
  
 [项目文件](../ide/project-files.md)  
 展示 .vcxproj 文件的 XML 结构。  
  
## <a name="related-sections"></a>相关章节  
 [VC++ 目录、项目、“选项”对话框](vcpp-directories-property-page.md)  
 （仅限 MSBuild 项目）探讨如何在生成期间修改可执行文件（包括文件、库文件和源代码文件）的搜索路径。  
  
 [编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 提供有关在 Visual Studio 中生成的信息。  
  
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)  
 提供一些链接，它们指向描述如何从命令行或 Visual Studio 的集成开发环境构建程序的主题。  
  
 [C/C++ 生成参考](../build/reference/c-cpp-building-reference.md)  
 提供指向采用 C++ 生成程序的概述、编译器和链接器选项以及其他生成工具的链接。  
  
 [从 Visual C++ 早期版本升级项目](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 提供涵盖有关将 C++ 项目升级到编译器工具集最新版本时遇到的问题的主题链接。  
  
[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)  
  有关如何升级在早期版本的 Visual Studio 中创建的 C++ 应用程序，以及如何迁移使用 Visual Studio 以外的工具创建的应用程序的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [通用 Windows 应用 (C++)](../windows/universal-windows-apps-cpp.md)