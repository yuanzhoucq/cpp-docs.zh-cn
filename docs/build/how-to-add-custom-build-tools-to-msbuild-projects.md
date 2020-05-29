---
title: 如何：向 MSBuild 项目添加自定义生成工具
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220716"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>如何：向 MSBuild 项目添加自定义生成工具

自定义生成工具是一种与特定文件关联的用户定义的命令行工具。

对于特定文件，请在项目文件 (.vcxproj) 中指定要执行的命令行、任何其他输入或输出文件，以及要显示的消息。 如果 MSBuild  确定输出文件相对于输入文件而言已过期，则会显示消息并执行命令行工具。

若要指定自定义生成工具的执行时间，请在项目文件中使用 `CustomBuildBeforeTargets` 和/或 `CustomBuildAfterTargets` XML 元素。 例如，可以指定自定义生成工具在 MIDL 编译器之后和 C/C++ 编译器之前运行。 指定 `CustomBuildBeforeTargets` 元素可在特定目标运行之前执行该工具；指定 `CustomBuildAfterTargets` 元素可在特定目标运行之后执行该工具；同时指定这两个元素可在执行两个目标的间隔时间运行该工具。 如果未指定任一元素，则自定义生成工具会在其默认位置（MIDL  目标之前）执行。

自定义生成步骤和自定义生成工具共享在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 元素中指定的信息。 只需在项目文件中指定这些目标一次。

### <a name="to-add-a-custom-build-tool"></a>添加自定义生成工具

1. 向项目文件添加一个项组，并为每个输入文件添加一个项。 指定命令、其他输入、输出和消息作为项元数据，如下所示。 此示例假定“faq.txt”文件与项目位于同一目录中。

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>定义将在生成中的何处执行自定义生成工具

1. 将以下属性组添加到项目文件。 必须至少指定一个目标，但如果只想在特定目标之前（或之后）执行生成步骤，则可以省略另一个目标。 此示例在编译之后但在链接之前执行自定义步骤。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>请参阅

[演练：使用 MSBuild 创建 C++ 项目](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 项目中使用生成事件](how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)
