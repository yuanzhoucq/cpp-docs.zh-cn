---
title: Visual Studio 项目中的属性继承 - C++
description: 属性继承在本机（MSBuild） Visual Studio C++项目中的工作方式。
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 2032ab63c7d278a080742dba8d8d0c6c3ed7a094
ms.sourcegitcommit: 9a63e9b36d5e7fb13eab15c2c35bedad4fb03ade
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600018"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Visual Studio 项目中的属性继承

Visual Studio 本机项目系统基于 MSBuild。 MSBuild 定义用于生成任何类型项目的文件格式和规则。 它管理着构建多个配置和平台的大多数复杂性。 你会发现，了解它的工作原理很有用。 如果要定义自定义配置，这一点特别重要。 或创建可重用的属性集，这些属性可共享并导入到多个项目中。

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.vcxproj 文件、.props 文件和 .targets 文件

项目属性要么直接存储在项目文件（ *`.vcxproj`* ）中，要么存储在项目文件导入的其他 *`.targets`* 或 *`.props`* 文件中，后者提供默认值。 对于 Visual Studio 2015，这些文件位于 *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* 。 对于 Visual Studio 2017，这些文件位于 *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* 中，其中 *`<edition>`* 是安装的 Visual studio 版本。 在 Visual Studio 2019 中，这些文件位于 *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* 。 属性还存储在可添加到自己的项目中的任何自定义 *`.props`* 文件中。 我们强烈建议你不要手动编辑这些文件。 请改用 IDE 中的属性页来修改所有属性，尤其是参与继承的属性，除非您深入了解 MSBuild。

如前面所示，相同配置的同一属性在不同文件中可能分配有不同值。 生成项目时，MSBuild 引擎以明确定义的顺序评估项目文件和所有导入的文件（如下所述）。 在评估每个文件时，该文件中定义的任何属性值都将覆盖现有值。 未指定的任何值都将继承自之前计算的文件。 使用属性页设置属性时，请注意您设置它的位置。 如果在 *`.props`* 文件中将属性设置为 "X"，但在项目文件中将属性设置为 "y"，则将生成项目，并将属性设置为 "y"。 如果项目项（如 *`.cpp`* 文件）中的同一属性设置为 "z"，则 MSBuild 引擎将使用 "z" 值。

这是基本的继承树：

1. MSBuild CPP 工具集（.. 中的默认设置\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props，由 *`.vcxproj`* 文件导入。）

1. 属性表

1. *`.vcxproj`* 文件。 （可能重写默认设置和属性页设置。）

1. 项元数据

> [!TIP]
> 在属性页上，以**粗体显示**的属性在当前上下文中定义。 普通字体的属性将被继承。

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>查看包含所有导入值的已扩展项目文件

有时，通过查看展开的文件来确定给定的属性值如何继承非常有用。 若要查看扩展版本，请在 Visual Studio 命令提示中输入以下命令。 （将占位符文件名称更改为要使用的名称。）

> **msbuild/pp：** **.vcxproj**

除非你熟悉 MSBuild，否则展开的项目文件可能会很大并且难以理解。 这是项目文件的基本结构：

1. 基本项目属性，不在 IDE 中公开。

1. 导入 *`Microsoft.cpp.default.props`* ，它定义了一些与工具集无关的基本属性。

1. 全局配置属性在“常规配置”页面上显示为“PlatformToolset”和“项目”默认属性。 这些属性决定下一步中 *`Microsoft.cpp.props`* 导入的工具集和内部属性表。

1. 导入 *`Microsoft.cpp.props`* ，这将设置大多数项目默认值。

1. 导入所有属性表（包括 *`.user`* 文件）。 这些属性表可以重写内容，但“PlatformToolset”和“项目”默认属性除外。

1. 项目配置属性的其余部分。 这些值可以重写属性表中设置的内容。

1. 项（文件）及其元数据。 这些项始终是 MSBuild 计算规则中的最后一个单词，即使它们出现在其他属性和导入之前也是如此。

有关详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。

## <a name="build-configurations"></a>生成配置

配置只是给定名称的任意一组属性。 Visual Studio 提供调试和发布配置。 每个为调试版本或发布版本设置相应的属性。 您可以使用**Configuration Manager**来定义自定义配置。 它们是一种为特定风格的版本分组属性的简便方法。

为了更好地了解生成配置，请打开**属性管理器**。 您可以通过选择 "**查看 > 属性管理器**或 **> 其他 Windows > 属性管理器**来打开它，具体取决于您的设置。 对于项目中的每个配置和平台对，**属性管理器**都有相应的节点。 在每个节点下，都是属性表（ *`.props`* 文件）的节点，用于设置该配置的特定属性。

![属性管理器](media/property-manager.png "属性管理器")

例如，可以在属性页中转到 "常规" 窗格。 将 "字符集" 属性更改为 "未设置" 而不是 "使用 Unicode"，然后单击 **"确定**"。 属性管理器现在未显示 " **Unicode 支持**" 属性表。 对于当前配置，它将被删除，但仍存在其他配置。

有关属性管理器和属性表的更多信息，请参阅[共享或重用 Visual Studio C++ 项目设置](create-reusable-property-configurations.md)。

> [!TIP]
> *`.user`* 文件是一项旧功能。 建议删除该属性，使其根据配置和平台正确地进行分组。
