---
title: "创建和管理 Visual c + + 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vcprojects
- creatingmanagingVC
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c38f4c75a41de8b2f2b494941c6a52b1ff46fa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>创建和管理基于 MSBuild 的 Visual c + + 项目
MSBuild 是 Visual c + + 本机生成系统，并通常是最佳生成系统，用于 UWP 应用，以及使用 MFC 或 ATL 库的桌面应用程序。 MSBuild 与 Visual Studio IDE 和项目系统紧密集成，但你还可以从命令行使用它。 从 Visual Studio 2017 年 1 开始，Visual c + + 支持[CMake 和其他非 MSBuild 系统通过打开文件夹功能](non-msbuild-projects.md)。

一个基于 MSBuild 的项目具有指定编译该程序，以及其他配置设置，例如目标平台 (x 86、 x64 或 ARM） 以及生成时所需的所有文件和资源的 XML 格式 (.vcxproj) 中一个项目文件发行版本或调试版本的程序。 一个项目（或多个项目）包含在一个 *解决方案*中；例如，一个解决方案可能包含多个 Win32 DLL 项目和一个使用这些 DLL 的 Win32 控制台应用程序。 生成项目时，MSBuild 引擎将使用项目文件并生成可执行文件和/或你指定的任何其他自定义输出。

你可以通过选择创建 Visual c + + 项目**文件 &#124;新 &#124;项目**，确保选中了 Visual c + + 的左窗格中，然后从中间窗格中的项目模板列表中选择。 当你单击模板时，在许多情况下会出现一个向导，可用于创建项目之前设置各种项目属性。 您可以查看和修改这些属性更高版本通过使用项目的属性页 (**项目 &#124;属性**)。  
  
 你还可以创建新项目：  
  
-   选择**文件 &#124;新 &#124;从现有代码项目**并按照提示添加现有的源代码文件。 此选项最适合相对小型简单的项目，或许是具有少量或没有复杂依赖关系的 25 个或以下数量的源代码文件。  
  
-   以生成文件开始，选择“常规”选项卡下的“生成文件项目”模板。  
  
-   创建一个空项目 (下**常规**选项卡) 并右键单击解决方案资源管理器中的项目节点并选择手动添加源代码文件**添加 &#124;现有项**。  
  
-   using the [Win32 Application Wizard](../windows/win32-application-wizard.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [Visual C++ 项目类型](../ide/visual-cpp-project-types.md)  
 介绍 Visual c + + 中可用的、 基于 MSBuild 的项目类型。  
  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)  
 描述类型的与各种 MSBuild 项目类型一起使用的文件。  
  
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 如何使用向导来借助 Visual C++ 创建项目。  
  
 [使用项目属性](../ide/working-with-project-properties.md)  
 描述如何使用属性页和属性表来指定项目设置。  
  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)  
 描述如何向项目添加类、方法、变量和其他元素，以便增添功能。  
  
 [如何：组织生成的项目输出文件](../ide/how-to-organize-project-output-files-for-builds.md)  
 描述如何组织项目输出文件。  
  
## <a name="related-sections"></a>相关章节  
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)  
 提供一些链接，它们指向描述如何从命令行或 Visual Studio 的集成开发环境构建程序的主题。  
  
 [Visual C++ 引用](http://msdn.microsoft.com/en-us/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 提供一些链接，它们指向描述 C 和 C++ 语言参考、Visual C++ 随附的库、Visual C++ 扩展性对象模型和 Microsoft 宏汇编 (MASM) 的主题。  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio SDK](http://msdn.microsoft.com/vstudio/extend)
