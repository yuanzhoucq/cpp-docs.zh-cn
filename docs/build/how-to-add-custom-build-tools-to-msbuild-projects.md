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

自定义生成工具是与特定文件关联的用户定义的命令行工具。

对于特定的文件，请指定要执行的项目文件 (.vcxproj) 命令行中，任何其他输入或输出文件和要显示的消息中。 如果**MSBuild**确定输出文件已过期的相对于输入文件而言，它将显示该消息并执行命令行工具。

若要指定自定义生成工具的执行时，使用一个或两个`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`项目文件中的 XML 元素。 例如，可以指定自定义生成工具运行之后 MIDL 编译器和 C 之前 /C++编译器。 指定`CustomBuildBeforeTargets`元素来执行该工具之前运行的特定目标;`CustomBuildAfterTargets`元素后要执行该工具的特定目标; 或这两个元素执行的两个目标之间运行该工具。 如果指定两个元素中，将在其默认位置，即之前执行自定义生成工具**MIDL**目标。

自定义生成工具和自定义生成步骤共享中指定的信息`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 元素。 在项目文件中指定这些目标一次。

### <a name="to-add-a-custom-build-tool"></a>若要添加自定义生成工具

1. 将一个项组添加到项目文件并添加一个项的每个输入文件。 指定该命令、 其他输入、 输出和消息为项元数据，如下所示。 此示例假定在你的项目所在的目录中存在的"faq.txt"文件。

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>若要定义在生成中的自定义生成工具将执行位置

1. 将以下属性组添加到项目文件。 你必须指定至少一个目标，但是您可以忽略另，如果只希望生成步骤之前 （或之后） 执行特定的目标。 此示例将在编译之后但在链接之前执行自定义步骤。

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
