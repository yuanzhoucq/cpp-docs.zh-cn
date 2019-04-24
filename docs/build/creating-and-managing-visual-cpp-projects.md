---
title: Visual Studio 项目的C++
ms.date: 12/12/2018
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
ms.openlocfilehash: b4772b9bd625a542a18039386fefe42840ab65b1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038033"
---
# <a name="visual-studio-projects---c"></a>Visual Studio 项目的C++

一个*Visual Studio 项目*项目基于 MSBuild 生成系统。 MSBuild 是 Visual Studio 的本机生成系统，并通常是最佳的生成系统用于 UWP 应用，以及使用 MFC 或 ATL 库、 COM 组件和其他特定于 Windows 的程序的桌面应用程序。 MSBuild 与 Visual Studio 中，紧密集成，但你也可以从命令行使用它。 

## <a name="create-a-project"></a>创建项目

您可以创建C++通过选择项目**文件&#124;新建&#124;项目**，然后选择视觉对象C++的左窗格中。 在中心窗格中可以看到项目模板的列表： 

   ![项目模板](../overview/media/vs2017-new-project.png "Visual Studio 2017 新建项目对话框")

有关 Visual Studio 中包含的所有默认项目模板的详细信息，请参阅[C++项目模板在 Visual Studio](reference/visual-cpp-project-types.md)。 可以创建自己的项目模板。 有关详细信息，请参阅[如何：创建项目模板](/visualstudio/ide/how-to-create-project-templates)。

创建项目后，它将出现在[解决方案资源管理器](/visualstudio/ide/solutions-and-projects-in-visual-studio)窗口：

   ![“解决方案资源管理器”](media/mathlibrary-solution-explorer-153.png)

时创建新项目时，将创建解决方案文件 (.sln)。 可以通过右键单击它中向解决方案中添加其他项目**解决方案资源管理器**。 解决方案文件用于协调生成依赖项时有多个相关的项目，但不会完成比这更多。 在项目级别来设置所有编译器选项。

## <a name="add-items"></a>添加项

右键单击项目中添加到项目的源代码文件、 图标或任何其他项**解决方案资源管理器**，然后选择**添加 > 新建**或**添加 > 现有**。

## <a name="add-third-party-libraries"></a>添加第三方库

若要添加第三方库，请使用[vcpkg](vcpkg.md)包管理器。 运行 Visual Studio 集成步骤，若要从任何 Visual Studio 项目引用时设置此库的路径。 

## <a name="set-compiler-options-and-other-build-properties"></a>设置编译器选项和其他生成属性

若要配置项目的生成设置，请右键单击中的项目**解决方案资源管理器**，然后选择**属性**。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](working-with-project-properties.md)。

## <a name="compile-and-run"></a>编译并运行

若要编译并运行新的项目，按**F5**或单击*调试下拉列表中*与主工具栏上的绿色箭头。 *配置下拉列表中*是你在其中选择是否执行*调试*或*发行*生成 （或某些其他自定义配置）。

新的项目编译时没有错误。 在添加你自己的代码时，你偶尔可能会引入错误或触发警告。 错误导致生成无法完成;警告却没有。 所有错误和警告时将都显示在输出窗口和错误列表中生成项目。 

   ![输出窗口和错误列表](../overview/media/vs2017-output-error-list.png)

在错误列表可以按**F1**突出显示错误时要转到其文档主题。

## <a name="in-this-section"></a>本节内容

[在 Visual Studio 中设置 C++ 编译器并生成属性](working-with-project-properties.md)<br/>
如何使用属性页和属性表来指定项目设置。

[在生成时引用库和组件](adding-references-in-visual-cpp-projects.md)<br/>
如何在项目中包括库、 Dll、 COM 和.NET 组件。
 
[整理项目输出文件](how-to-organize-project-output-files-for-builds.md)<br/>
如何自定义生成过程中创建的可执行文件的位置。

[自定义生成步骤和生成事件](understanding-custom-build-steps-and-build-events.md)<br/>
如何将任何命令添加到生成过程在指定的点。

[通过现有代码创建项目](how-to-create-a-cpp-project-from-existing-code.md)<br/>
如何从一系列松散源文件创建新的 Visual Studio 项目。

## <a name="see-also"></a>请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)<br>
