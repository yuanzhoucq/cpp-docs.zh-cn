---
title: 如何：向 MSBuild 项目添加自定义生成步骤
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: d70f145a9d43463266a9c0bbff68e8e7f36ef2c6
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220726"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>如何：向 MSBuild 项目添加自定义生成步骤

自定义生成步骤是在生成中的用户定义的步骤。 自定义生成步骤的行为类似于任何其他*命令工具*步骤，例如标准编译或链接工具步骤。

在项目文件 (.vcxproj) 中指定的自定义生成步骤。 该步骤可以指定要执行的任何其他输入或输出文件和要显示的消息的命令行。 如果**MSBuild**确定输出文件已过时相对于输入文件而言，它显示的消息并执行的命令。

若要指定自定义生成的位置的生成目标序列中的步骤，使用一个或两个`CustomBuildAfterTargets`和`CustomBuildBeforeTargets`项目文件中的 XML 元素。 例如，可以指定自定义生成步骤运行之后链接工具目标和之前的清单工具的目标。 实际的可用目标集取决于您的特定生成。

指定`CustomBuildBeforeTargets`元素之前的特定目标运行时，执行自定义生成步骤`CustomBuildAfterTargets`元素后要执行该步骤运行时特定的目标或这两个元素执行两个相邻目标之间的步骤。 如果指定两个元素中，将在其默认位置，即后执行自定义生成工具**链接**目标。

自定义生成工具和自定义生成步骤共享中指定的信息`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 元素。 因此，指定这些目标只需一次在项目文件中。

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>若要定义由自定义生成步骤执行的内容

1. 将属性组添加到项目文件。 在此属性组中，指定命令、 其输入和输出和消息，如下面的示例中所示。 此示例创建一个.cab 文件中创建的 main.cpp 文件从[演练：使用 MSBuild 创建C++项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>若要定义自定义生成步骤，在生成中将执行

1. 将以下属性组添加到项目文件。 可以指定这两个目标，或者如果你只是想要执行之前或之后的特定目标的自定义步骤，可以忽略其中一个。 此示例会告知**MSBuild**后编译步骤，但在链接步骤之前执行的自定义步骤。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>请参阅

[演练：使用 MSBuild 创建 C++ 项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)
