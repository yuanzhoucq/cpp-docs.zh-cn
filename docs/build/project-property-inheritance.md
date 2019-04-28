---
title: 在 Visual Studio 项目中的属性继承C++
ms.date: 12/10/2018
helpviewer_keywords:
- Visual C++ projects, property inheritance
ms.openlocfilehash: edd6d3bf82f7a13cf6687abeba3758dcceca5e84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295434"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>在 Visual Studio 项目中的属性继承

Visual Studio 项目系统基于 MSBuild，定义文件格式和生成项目的任何类型的规则。 MSBuild 承应生成多个配置和平台的复杂性，但你需要了解一些 MSBuild 的工作原理。 如果想要定义自定义配置，或者创建可共享和导入多个项目的可重用的属性集，这一点尤为重要。

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.Vcxproj 文件、.props 文件和.targets 文件

直接在项目文件 (*.vcxproj) 或其他项目文件导入和其提供的默认值的.targets 或.props 文件中存储项目属性。 对于 Visual Studio 2015，这些文件位于\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140。 对于 Visual Studio 2017，这些文件位于 \\Program Files (x86)\\Microsoft Visual Studio\\2017\\edition\\Common7\\IDE\\VC\\VCTargets，其中“edition”是已安装的 Visual Studio 版本。 属性也存储在可能想要添加到自己项目的任何自定义 .props 文件中。 我们强烈建议不要手动编辑这些文件，而是使用 IDE 中的属性页来更改所有属性，特别是参与继承的属性，除非你非常了解 MSBuild。

如前面所示，这些不同文件中不同的值可能会分配的同一属性进行相同的配置。 生成项目时，MSBuild 引擎以明确定义的顺序评估项目文件和所有导入的文件（如下所述）。 在评估每个文件时，该文件中定义的任何属性值都将覆盖现有值。 未指定的任何值都从之前已评估的文件继承。 因此，使用属性页设置属性时，也请务必注意设置它的位置。 如果在 .props 文件中将属性设置为“X”，但该属性在项目文件中已设为“Y”，然后将在属性设为“Y”的情况下生成项目。 如果在项目项（例如 .cpp 文件）上，相同的属性已设为“Z”，然后 MSBuild 引擎将使用“Z”值。 

这是基本的继承树：

1. 来自 MSBuild CPP 工具集的默认设置（..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props，由 .vcxproj 文件导入。）

2. 属性表

3. .vcxproj 文件。 （可能重写默认设置和属性页设置。）

4. 项元数据

> [!TIP]
> 在属性页中，`bold` 的属性在当前上下文中定义。 普通字体的属性将被继承。

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>查看所有导入的值的已展开的项目文件

有时，通过查看展开的文件来确定给定的属性值如何继承非常有用。 若要查看扩展版本，请在 Visual Studio 命令提示中输入以下命令。 （将占位符文件名称更改为要使用的名称。）

**msbuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

除非你十分熟悉 MSBuild，否则展开的项目文件可能会很大并且难以理解。 这是项目文件的基本结构：

1. 基本项目属性，不在 IDE 中显示。

2. 导入 Microsoft.cpp.default.props，该文件定义了一些基本的、不依赖于工具集的属性。

3. 全局配置属性在“常规配置”页面上显示为“PlatformToolset”和“项目”默认属性。 这些属性决定下一步将哪个工具集和内部属性表导入 Microsoft.cpp.props 中。

4. 导入 Microsoft.cpp.props，该文件设置大多数项目默认值。

5. 导入所有属性表，包括 .user 文件。 这些属性表可以重写内容，但“PlatformToolset”和“项目”默认属性除外。

6. 项目配置属性的其余部分。 这些值可以重写属性表中设置的内容。

7. 项（文件）及其元数据。 这些始终是 MSBuild 评估规则的最后一项，即使它们出现在其他属性和导入之前仍是如此。

有关详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。

## <a name="build-configurations"></a>生成配置

配置只是给定名称的任意一组属性。 Visual Studio 提供“调试”和“发布”配置，并且每个配置都相应地为调试版本和发布版本设置各种属性。 可以使用 Configuration Manager 来定义自定义配置，提供一种简单的方法来组合属性获得特定风格的版本。 

若要获取更好地了解生成配置，请打开**属性管理器**通过选择**视图&#124;属性管理器**或**视图&#124;其他 Windows&#124;属性管理器**具体取决于你的设置。 **属性管理器**项目中已配置/平台对每个节点。 这些节点的每个节点下都是属性表（.props 文件）的节点，为该配置设置某些特定属性。

![属性管理器](media/property-manager.png "属性管理器")

如果转到属性页中的常规窗格和字符集属性设置为"未设置"而不是"使用 Unicode"，再单击**确定**，将显示属性管理器没有**Unicode 支持**属性表当前配置，但它仍会出现的其他配置。

有关属性管理器和属性表的详细信息，请参阅[共享或重新 Visual StudioC++项目设置](create-reusable-property-configurations.md)。

> [!TIP]
> .user 文件是一项旧功能，我们建议将其删除以便根据配置/平台正确地对属性分组。



