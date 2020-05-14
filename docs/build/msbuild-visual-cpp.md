---
title: 命令行上的 MSBuild - C++
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
# <a name="msbuild-on-the-command-line---c"></a>命令行上的 MSBuild - C++

一般而言，建议使用 Visual Studio 设置项目属性和调用 MSBuild 系统。 但是，可以直接从命令提示符使用 MSBuild  工具。 生成过程由可以创建和编辑的项目文件 (.vcxproj) 中的信息控制。 项目文件基于生成阶段、条件和事件指定生成选项。 此外，可以指定零个或多个命令行选项  参数。

> msbuild.exe [ project_file ] [ options ]   

使用 /target（或 /t）和 /property（或 /p）命令行选项可替代项目文件中指定的特定属性和目标     。

项目文件的基本功能是指定目标  （应用于项目的特定操作）以及执行该操作所需的输入和输出。 项目文件可以指定一个或多个目标，这些目标可以包含默认目标。

每个目标都由一个或多个  任务组成。 每个任务由包含一个可执行命令的 .NET Framework 类表示。 例如，[CL 任务](/visualstudio/msbuild/cl-task)包含 [cl.exe](reference/compiling-a-c-cpp-program.md) 命令。

任务参数  是类任务的属性，通常表示可执行命令的命令行选项。 例如，`CL` 任务的 `FavorSizeOrSpeed` 参数对应于 /Os  和 /Ot  编译器选项。

其他任务参数支持 MSBuild 基础结构。 例如，`Sources` 任务参数指定可由其他任务使用的一组任务。 有关 MSBuild 任务的详细信息，请参阅[任务参考](/visualstudio/msbuild/msbuild-task-reference)。

大多数任务都需要输入和输出，如文件名、路径、字符串、数字或布尔参数。 例如，一个常用输入是要编译的 .cpp 源文件的名称。 一个重要输入参数是指定生成配置和平台的字符串，例如“Debug\|Win32”。 输入和输出由一个或多个用户定义的 XML `Item` 元素（包含在 `ItemGroup` 元素中）指定。

项目文件还可以指定用户定义的属性  和 `ItemDefinitionGroup` 项  。 属性和项组成可在生成中用作变量的名称/值对。 对的名称组成部分定义宏  ，值组成部分声明宏值  。 属性宏使用 $(name  ) 表示法进行访问，而项宏使用 %(name  ) 表示法进行访问。

项目文件中的其他 XML 元素可以测试宏，然后有条件地设置任何宏的值或控制生成的执行。 宏名称和文本字符串可以进行连接，以生成构造（如路径和文件名）。 在命令行中，/property  选项设置或替代项目属性。 不能在命令行上引用项。

MSBuild 系统可以有条件地在另一个目标之前或之后执行一个目标。 此外，系统可以基于目标使用的文件是否比它发出的文件更新而生成目标。

有关 MSBuild 的详细信息，请参阅：

- [MSBuild](/visualstudio/msbuild/msbuild) MSBuild 概念概述。

- [MSBuild 参考](/visualstudio/msbuild/msbuild-reference) 有关 MSBuild 系统的参考信息。

- [项目文件架构参考](/visualstudio/msbuild/msbuild-project-file-schema-reference) 列出 MSBuild XML 架构元素及其特性以及父元素和子元素。 特别要注意 [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)、[PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)、[Target](/visualstudio/msbuild/target-element-msbuild) 和 [Task](/visualstudio/msbuild/task-element-msbuild) 元素。

- [命令行参考](/visualstudio/msbuild/msbuild-command-line-reference) 介绍可用于 msbuild.exe 的命令行参数和选项。

- [任务参考](/visualstudio/msbuild/msbuild-task-reference) 介绍 MSBuild 任务。 特别要注意特定于 Visual C++ 的以下任务：[BscMake 任务](/visualstudio/msbuild/bscmake-task)、[CL 任务](/visualstudio/msbuild/cl-task)、[CPPClean 任务](/visualstudio/msbuild/cppclean-task)、[LIB 任务](/visualstudio/msbuild/lib-task)、[Link 任务](/visualstudio/msbuild/link-task)、[MIDL 任务](/visualstudio/msbuild/midl-task)、[MT 任务](/visualstudio/msbuild/mt-task)、[RC 任务](/visualstudio/msbuild/rc-task)、[SetEnv 任务](/visualstudio/msbuild/setenv-task)、[VCMessage 任务](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>本节内容

|术语|定义|
|----------|----------------|
|[演练：使用 MSBuild 创建 C++ 项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|演示如何使用 MSBuild  创建 Visual Studio C++ 项目。|
|[如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)|演示如何指定在生成中的特定阶段发生的操作：生成开始之前；链接步骤开始之前；或生成结束之后。|
|[如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)|演示如何将用户定义的阶段添加到生成序列。|
|[如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)|演示如何将生成工具与特定文件相关联。|
|[如何：将自定义工具集成到项目属性中](how-to-integrate-custom-tools-into-the-project-properties.md)|演示如何将自定义工具的选项添加到项目属性。|
|[如何：修改目标框架和平台工具集](how-to-modify-the-target-framework-and-platform-toolset.md)|演示如何针对多个框架或工具集编译项目。|

## <a name="see-also"></a>请参阅

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)
