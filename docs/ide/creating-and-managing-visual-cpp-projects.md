---
title: 创建和管理 Visual C++ 项目
ms.date: 11/04/2016
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 2c3722fe9da764a578c255e50120fa2770555665
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553174"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>创建和管理基于 MSBuild 的 Visual C++ 项目

MSBuild 是 Visual C++ 的本机生成系统，通常非常适合用于 UWP 应用以及使用 MFC 或 ATL 库的桌面应用程序。 MSBuild 与 Visual Studio IDE 和项目系统紧密集成，但也可从命令行使用它。 自 Visual Studio 2017 起，Visual C++ [通过“打开文件夹”功能支持 CMake 和其他非 MSBuild 系统](non-msbuild-projects.md)。

基于 MSBuild 的项目具有一个 XML 格式的项目文件 (.vcxproj)，它指定了编译程序所需的所有文件和资源，同时指定了其他配置设置，例如目标平台（x86、x64 或 ARM）以及生成的是程序的发布版本还是调试版本。 一个项目（或多个项目）包含在一个 *解决方案*中；例如，一个解决方案可能包含多个 Win32 DLL 项目和一个使用这些 DLL 的 Win32 控制台应用程序。 生成项目时，MSBuild 引擎将使用项目文件并生成可执行文件和/或你指定的任何其他自定义输出。

可使用以下方式来创建 Visual C++ 项目：选择“文件”|“新建”|“项目”，确保在左侧窗格中勾选 Visual C++，然后从中间窗格的项目模板列表中进行选择。 单击模板时，通常会出现一个向导，让你能在创建项目前设置各种项目属性。 稍后可使用项目的属性页（“项目”|“属性”）查看和修改这些属性。

还可通过以下方式创建新项目：

- 选择“文件”|“新建”|“从现有代码创建项目”，并按照提示添加现有的源代码文件。 此选项最适合相对小型简单的项目，或许是具有少量或没有复杂依赖关系的 25 个或以下数量的源代码文件。

- 以生成文件开始，选择“常规”选项卡下的“生成文件项目”模板。

- 创建一个空项目（在“常规”选项卡下），然后通过在解决方案资源管理器中右键单击项目节点并选择“添加”|“现有项”来手动添加源代码文件。

- using the [Win32 Application Wizard](../windows/win32-application-wizard.md)。

## <a name="in-this-section"></a>本节内容

[Visual C++ 项目类型](../ide/visual-cpp-project-types.md)<br>
介绍 Visual C++ 中基于 MSBuild 的可用项目类型。

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
介绍可与各种 MSBuild 项目类型一起使用的文件类型。

[使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
如何使用向导来借助 Visual C++ 创建项目。

[使用项目属性](../ide/working-with-project-properties.md)<br>
描述如何使用属性页和属性表来指定项目设置。

[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
描述如何向项目添加类、方法、变量和其他元素，以便增添功能。

[如何：组织生成的项目输出文件](../ide/how-to-organize-project-output-files-for-builds.md)<br>
描述如何组织项目输出文件。

## <a name="related-sections"></a>相关章节

[生成 C/C++ 程序](../build/building-c-cpp-programs.md)<br>
提供一些链接，它们指向描述如何从命令行或 Visual Studio 的集成开发环境构建程序的主题。

## <a name="see-also"></a>请参阅

[Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
