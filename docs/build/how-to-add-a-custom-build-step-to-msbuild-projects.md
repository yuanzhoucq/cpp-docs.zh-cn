---
title: 如何：向 MSBuild 项目添加自定义生成步骤
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444915"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>如何：向 MSBuild 项目添加自定义生成步骤

自定义生成步骤是在生成中使用用户定义的步骤。 自定义生成步骤的行为类似于任何其他*命令工具*步骤，如标准编译或链接工具步骤。

在项目文件中指定自定义生成步骤（. .vcxproj）。 步骤可以指定要执行的命令行、任何其他输入文件或输出文件以及要显示的消息。 如果**MSBuild**确定你的输出文件对于输入文件来说已过期，它将显示该消息并执行命令。

若要在生成目标序列中指定自定义生成步骤的位置，请在项目文件中使用 `CustomBuildAfterTargets` 和 `CustomBuildBeforeTargets` XML 元素中的一个或两个。 例如，你可以指定自定义生成步骤在链接工具目标之后以及在清单工具目标之前运行。 实际的可用目标集取决于你的特定生成。

指定 `CustomBuildBeforeTargets` 元素，以在特定目标运行之前执行自定义生成步骤，`CustomBuildAfterTargets` 元素在运行特定目标后执行步骤，或使用这两个元素来执行两个相邻目标之间的步骤。 如果这两个元素均未指定，则您的自定义生成工具会在其默认位置执行，该位置位于**链接**目标之后。

自定义生成步骤和自定义生成工具共享在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 元素中指定的信息。 因此，只需在项目文件中指定这些目标一次。

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>定义自定义生成步骤执行的操作

1. 将属性组添加到项目文件。 在此属性组中，指定命令、其输入和输出以及消息，如下面的示例中所示。 此示例[使用在演练：使用 MSBuild 创建C++项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中创建的主 .cpp 文件创建 .cab 文件。

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>定义在生成中执行自定义生成步骤的位置

1. 将以下属性组添加到项目文件。 您可以指定这两个目标，如果您只想在特定目标之前或之后执行自定义步骤，也可以省略一个目标。 此示例告知**MSBuild**在编译步骤之后但在链接步骤之前执行自定义步骤。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>另请参阅

[演练：使用 MSBuild 创建C++项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)
