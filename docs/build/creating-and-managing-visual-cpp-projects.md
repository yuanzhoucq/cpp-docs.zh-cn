---
title: Visual Studio Projects - C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 3694478e22bfd2a3c58a72ba0c3ad2d15351bc9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078692"
---
# <a name="visual-studio-projects---c"></a>Visual Studio projects - C++

Visual Studio 项目是基于 MSBuild 生成系统的项目。 MSBuild 是 Visual Studio 的本机生成系统，通常是适用于 Windows 特定程序的最佳生成系统。 MSBuild 与 Visual Studio 紧密集成，但也可从命令行使用它。 对于跨平台项目或使用开放源代码库的项目，我们建议使用 visual studio 2017 和更高版本的[Visual studio 中的 CMake 项目](cmake-projects-in-visual-studio.md)。 有关从早期版本的 Visual Studio 升级 MSBuild 项目的信息，请参阅[Microsoft C++移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)。

## <a name="create-a-project"></a>创建一个项目

::: moniker range="vs-2019"

可通过选择“文件” **“新建”** “项目”，然后将“语言”设为 C++，创建 C++ 项目 >  > 。 在结果列表中，可看到项目模板列表，可通过设置“平台”或“项目类型”以及通过在搜索框中键入关键字进行筛选。

   ![Visual Studio 2019 项目模板](../build/media/vs2019-choose-console-app.png "Visual Studio 2019“新建项目”对话框")

::: moniker-end

::: moniker range="vs-2017"

可通过选择“文件” **“新建”** “项目”，然后选择左侧窗格中的 C++，创建 C++ 项目 >  > 。 可在中心窗格中看到项目模板列表：

   ![项目模板](../overview/media/vs2017-new-project.png "Visual Studio 2017“新建项目”对话框")

::: moniker-end

有关 Visual Studio 中包含的所有默认项目模板的详细信息，请参阅 [Visual Studio 中的 C++ 项目模板](reference/visual-cpp-project-types.md)。 可以创建自己的项目模板。 有关详细信息，请参阅[如何：创建项目模板](/visualstudio/ide/how-to-create-project-templates)。

创建项目后，它会显示在[解决方案资源管理器](/visualstudio/ide/solutions-and-projects-in-visual-studio)窗口中：

   ![解决方案资源管理器](media/mathlibrary-solution-explorer-153.png)

创建新项目时，还会创建解决方案文件 (.sln)。 可通过在“解决方案资源管理器”中右键单击该解决方案，将其他项目添加到该解决方案。 具有多个相关项目时，解决方案文件用于协调生成依赖项，但除此之外不执行任何操作。 所有编译器选项都在项目级别进行设置。

## <a name="add-items"></a>添加项

通过右键单击“解决方案资源管理器”中的项目并选择“添加”>“新建”或“添加”>“现有”，将源代码文件、图标或任何其他项添加到项目中。

## <a name="add-third-party-libraries"></a>添加第三方库

若要添加第三方库，请使用 [vcpkg](vcpkg.md) 包管理器。 运行 Visual Studio 集成步骤，以设置从任何 Visual Studio 项目引用该库时，该库的路径。

## <a name="set-compiler-options-and-other-build-properties"></a>设置编译器选项和其他生成属性

若要配置项目的生成设置，请右键单击“解决方案资源管理器”中的项目，然后选择“属性”。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](working-with-project-properties.md)。

## <a name="compile-and-run"></a>编译和运行

若要编译和运行新项目，请按 F5 或在主工具栏上单击带有绿色箭头的“调试下拉列表”。 请在“配置下拉列表”中选择是执行“调试”还是“发布”（或一些其他自定义配置）生成。

编译新项目时未发生错误。 添加自己的代码时，可能有时会引发错误或触发警告。 错误会导致无法完成生成；警告不会。 生成项目时，所有错误和警告会显示在“输出窗口”和“错误列表”中。

   ![输出窗口和错误列表](../overview/media/vs2017-output-error-list.png)

在“错误列表”中，可以按突出显示的错误上的 F1，以转到其文档主题。

## <a name="in-this-section"></a>本节内容

[在 Visual Studio 中设置 C++ 编译器并生成属性](working-with-project-properties.md)<br/>
如何使用属性页和属性表来指定项目设置。

[在生成时引用库和组件](adding-references-in-visual-cpp-projects.md)<br/>
如何在项目中包含库、DLL、COM 和 .NET 组件。

[整理项目输出文件](how-to-organize-project-output-files-for-builds.md)<br/>
如何自定义生成过程中创建的可执行文件的位置。

[自定义生成步骤和生成事件](understanding-custom-build-steps-and-build-events.md)<br/>
如何在指定点将任意命令添加到生成过程。

[通过现有代码创建项目](how-to-create-a-cpp-project-from-existing-code.md)<br/>
如何从松散的源文件集合中创建新的 Visual Studio 项目。

## <a name="see-also"></a>另请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)<br>
[Microsoft C++移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)
