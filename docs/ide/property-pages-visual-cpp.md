---
title: 属性页 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.NotAProp.Edit
dev_langs:
- C++
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1dc831dff6d1e3dbef4fc762712e8125a5b20e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="property-pages-visual-c"></a>属性页 (Visual C++)

通过使用属性页，可以指定 Visual Studio 项目的设置。 若要打开**属性页**对话框中为 Visual Studio 项目，在**项目**菜单上，选择**属性**。

可以指定项目设置，以便它们应用所有生成配置，也可以为每个生成配置指定不同的项目属性。 例如，你可以为“发布”配置指定某些设置，而为“调试”配置指定其他设置。

并非所有可用页面都一定会显示在**属性页**对话框。 显示哪些页面取决于项目中的文件类型。

有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

对于非 Windows 项目，请参阅[Linux c + + 属性页引用](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="default-properties-vs-modified-properties"></a>默认属性与修改后的属性

当你使用**新项目**对话框中，创建项目，Visual Studio 使用指定的项目模板来初始化项目属性。 因此，可以将模板中的属性值视为该项目类型的默认值。 在其他项目类型中，各属性具有的默认值可能不同。

如果修改了项目属性值，它将显示为粗体。 可出于以下原因修改项目属性：

- 应用程序向导会更改属性，因为它需要与项目模板中指定值不同的属性值。

- 指定不同的属性值中**新项目**对话框。

- 在项目属性页上指定不同的属性值。

> [!TIP]
> 若要查看 MSBuild 用于生成你的项目的属性值的最后一组，检查预处理器输出文件中，您可以通过使用以下命令行生成： **MSBuild / 预处理：** *preprocessor_output_filename*<sub>选择</sub> *project_filename*<sub>选择</sub>

## <a name="resetting-properties"></a>重置属性

当您查看**属性页**中选择一个项目和项目节点的对话框**解决方案资源管理器**，对于许多属性，你可以选择**继承自父级或项目默认值**或修改的值另一种方法。

当您查看**属性页**中选择一个项目和文件的对话框**解决方案资源管理器**，对于许多属性，你可以选择**从父级或项目默认设置继承**或修改的值另一种方法。 但是，如果项目包含许多具有与项目默认值不同的属性值的文件，该项目将花较长时间才能生成。

> [!TIP]
> 若要刷新**属性页**对话框中，使其显示最新的选项中，选择**应用**。

大部分项目默认设置为系统（平台）默认设置。 从更新中的属性时应用的样式表的一些项目默认值派生**项目默认值**部分**常规**项目的配置属性页。 有关详细信息，请参阅[常规属性页 （项目）](../ide/general-property-page-project.md)。

## <a name="specifying-user-defined-values"></a>指定用户定义的值

必须为特定属性定义值。 用户定义的值可以包含一个或多个字母数字字符或项目文件宏名称。 这些属性中的一些只能接受一个用户定义的值，而其他一些则可以接受以分号分隔多个值的列表。

要为属性指定一个用户定义的值或者要在属性可以接受多个用户定义的值时指定一个列表，请在属性名称右侧一列中执行以下操作之一：

- 键入值或值列表。

- 选择下拉箭头。 如果**编辑**不可用，选中它，然后在文本框中键入值列表。 另一种指定列表的方法是：在文本框中键入值，每个值占一行。 在属性页上，值将显示为以分号分隔的列表。

   若要插入项目文件宏作为一个值，请选择**宏**，然后双击宏名称。

- 选择下拉箭头。 如果**浏览**可用，选择它，然后选择一个或多个值。

对于多值属性，**从父级或项目默认设置继承**当你的属性名称右侧列中选择的下拉箭头，然后选择选项才可用**编辑**。 默认情况下，该选项处于选中状态。

请注意，属性页仅显示从另一个级别继承的多值属性在当前级别的设置。 例如，如果中选定一个文件**解决方案资源管理器**和选择 C/c + +**预处理器定义**属性，文件级定义会显示，但继承项目级别的定义不会显示。 若要查看当前级别和继承的值，属性名称右侧列中选择的下拉箭头，然后选择**编辑**。 如果你使用[Visual c + + 项目模型](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine)，此行为也是有效的对象上的文件和项目。 也就是说，当你在文件级别查询某个属性的值时，将不会获取该属性在项目级别的值。 你必须显式获取该属性在项目级别的值。 此外，属性的某些继承值可能来自于无法以编程方式访问的样式表。

## <a name="in-this-section"></a>本节内容

[高级，清单工具，配置属性\<项目名称 > 属性页对话框](../ide/advanced-manifest-tool.md)

[“命令行”属性页](../ide/command-line-property-pages.md)

[“自定义生成步骤”属性页：常规](../ide/custom-build-step-property-page-general.md)

[添加引用](../ide/adding-references-in-visual-cpp-projects.md)

[“常规”属性页（文件）](../ide/general-property-page-file.md)

[常规属性页（项目）](../ide/general-property-page-project.md)

[常规、 清单工具，配置属性\<项目名称 > 属性页对话框](../ide/general-manifest-tool-configuration-properties.md)

[“HLSL”属性页](../ide/hlsl-property-pages.md)

[HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)

[HLSL 属性页：常规](../ide/hlsl-property-pages-general.md)

[HLSL 属性页：输出文件](../ide/hlsl-property-pages-output-files.md)

[输入和输出，清单工具，配置属性\<项目名称 > 属性页对话框](../ide/input-and-output-manifest-tool.md)

[隔离配置属性 COM 清单工具，\<项目名称 > 属性页对话框](../ide/isolated-com-manifest-tool.md)

[“链接器”属性页](../ide/linker-property-pages.md)

[“托管资源”属性页](../ide/managed-resources-property-page.md)

[清单工具属性页](../ide/manifest-tool-property-pages.md)

[“MIDL”属性页](../ide/midl-property-pages.md)

[MIDL 属性页：高级](../ide/midl-property-pages-advanced.md)

[MIDL 属性页：常规](../ide/midl-property-pages-general.md)

[MIDL 属性页：输出](../ide/midl-property-pages-output.md)

[“Nmake”属性页](../ide/nmake-property-page.md)

[“资源”属性页](../ide/resources-property-pages.md)

[“VC++ 目录”属性页](../ide/vcpp-directories-property-page.md)

[“Web 引用”属性页](../ide/web-references-property-page.md)

[“XML 数据生成器工具”属性页](../ide/xml-data-generator-tool-property-page.md)

[“XML 文档生成器工具”属性页](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>请参阅

[如何：创建和删除项目依赖项](/visualstudio/ide/how-to-create-and-remove-project-dependencies)  
[如何：创建和编辑配置](/visualstudio/ide/how-to-create-and-edit-configurations)  
