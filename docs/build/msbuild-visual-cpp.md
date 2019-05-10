---
title: 在命令行中的 MSBuildC++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220575"
---
# <a name="msbuild-on-the-command-line---c"></a>在命令行中的 MSBuildC++

一般情况下，我们建议使用 Visual Studio 设置项目属性以及调用 MSBuild 系统。 但是，可以使用**MSBuild**直接从命令提示符工具。 您可以创建和编辑的项目文件 (.vcxproj) 中的信息由控制生成过程。 项目文件指定生成选项基于生成阶段、 条件和事件。 此外，可以指定零或多个命令行*选项*参数。

> **msbuild.exe** [ *project_file* ] [ *options* ]

使用 **/target** (或 **/t**) 和 **/property** (或 **/p**) 用于重写特定属性和目标的命令行选项项目文件中指定。

项目文件的基本功能是指定*目标*，这是应用于你的项目，并输入和输出执行该操作所需的某一特定操作。 项目文件可以指定一个或多个目标，可以包含默认目标。

每个目标包含的一个或多个序列*任务*。 每个任务由包含一个可执行命令的.NET Framework 类表示。 例如， [CL 任务](/visualstudio/msbuild/cl-task)包含[cl.exe](reference/compiling-a-c-cpp-program.md)命令。

一个*任务参数*是类任务的属性，通常表示可执行命令的命令行选项。 例如，`FavorSizeOrSpeed`的参数`CL`任务对应于 **/Os**并 **/Ot**编译器选项。

其他任务参数支持 MSBuild 基础结构。 例如，`Sources`任务参数指定一组可供其他任务的任务。 有关 MSBuild 任务的详细信息，请参阅[任务参考](/visualstudio/msbuild/msbuild-task-reference)。

大多数任务要求输入和输出，如文件名、 路径和字符串、 数值或布尔参数。 例如，常见的输入是要编译的.cpp 源文件的名称。 一个重要的输入的参数是一个字符串，指定生成配置和平台，例如，"调试\|Win32"。 一个或多个用户定义的 XML 指定输入和输出`Item`中所含元素`ItemGroup`元素。

项目文件还可以指定用户定义*属性*并`ItemDefinitionGroup`*项*。 属性和项形成可用作生成中的变量的名称/值对。 一对的名称部分定义*宏*，，值部分声明*宏值*。 使用 $ 访问属性宏 (*名称*) 表示法和的项宏可通过 %(*名称*) 表示法。

项目文件中的其他 XML 元素可以测试宏，然后进行有条件地设置任何宏的值或控制生成的执行。 宏名称和文字字符串可以串联来生成构造，例如路径和文件名的名称。 在命令行 **/property**选项设置或重写项目属性。 不能在命令行上引用项。

之前或之后另一个目标，MSBuild 系统可以有条件地执行目标。 此外，系统可以生成基于目标使用的文件是否比它发出的文件的目标。

有关 MSBuild 的详细信息，请参阅：

- [MSBuild](/visualstudio/msbuild/msbuild)概述的 MSBuild 概念。

- [MSBuild 参考](/visualstudio/msbuild/msbuild-reference)引用 MSBuild 系统的信息。

- [项目文件架构引用](/visualstudio/msbuild/msbuild-project-file-schema-reference)列出 MSBuild XML 架构元素，以及其属性和父和子元素。 尤其注意[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)， [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)，[目标](/visualstudio/msbuild/target-element-msbuild)，以及[任务](/visualstudio/msbuild/task-element-msbuild)元素。

- [命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)介绍的命令行参数和可用于 msbuild.exe 的选项。

- [任务参考](/visualstudio/msbuild/msbuild-task-reference)介绍 MSBuild 任务。 尤其注意这些任务，特定于视觉对象C++:[BscMake 任务](/visualstudio/msbuild/bscmake-task)， [CL 任务](/visualstudio/msbuild/cl-task)， [CPPClean 任务](/visualstudio/msbuild/cppclean-task)， [LIB 任务](/visualstudio/msbuild/lib-task)，[链接任务](/visualstudio/msbuild/link-task)， [MIDL 任务](/visualstudio/msbuild/midl-task)， [MT 任务](/visualstudio/msbuild/mt-task)， [RC 任务](/visualstudio/msbuild/rc-task)， [SetEnv 任务](/visualstudio/msbuild/setenv-task)， [VCMessage 任务](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>本节内容

|术语|定义|
|----------|----------------|
|[演练：使用 MSBuild 创建 C++ 项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|演示如何创建 Visual StudioC++使用项目**MSBuild**。|
|[如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)|演示如何指定在生成中的某个特定阶段发生的操作： 在生成开始前;之前在链接步骤开始;或在生成结束之后。|
|[如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)|演示如何将用户定义的阶段添加到生成序列。|
|[如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)|演示如何将生成工具关联与特定文件。|
|[如何：将自定义工具集成到项目属性中](how-to-integrate-custom-tools-into-the-project-properties.md)|演示如何将自定义工具的选项添加到项目属性。|
|[如何：修改目标框架和平台工具集](how-to-modify-the-target-framework-and-platform-toolset.md)|演示如何为多个框架或工具集的某个项目进行编译。|

## <a name="see-also"></a>请参阅

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)
