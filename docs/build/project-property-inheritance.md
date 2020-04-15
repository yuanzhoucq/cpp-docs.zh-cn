---
title: Visual Studio 项目中的属性继承 - C++
description: 属性继承在本机 （MSBuild） 可视化工作室中的工作方式C++项目。
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328480"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Visual Studio 项目中的属性继承

可视化工作室本机项目系统基于 MSBuild。 MSBuild 定义了用于构建任何类型的项目的文件格式和规则。 它管理多个配置和平台构建的大部分复杂性。 你会发现了解它是如何工作的是很有用的。 如果要定义自定义配置，这一点尤其重要。 或者，创建可重用的属性集，可以共享并导入多个项目。

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.vcxproj 文件、.props 文件和 .targets 文件

项目属性直接存储在项目文件 （）*`.vcxproj`* 中，或者存储在项目*`.targets`* 文件*`.props`* 导入和提供默认值的其他或文件中。 对于 Visual Studio 2015，这些文件位于*`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* 中。 对于 Visual Studio 2017，这些文件位于*`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* 的*`<edition>`*，安装的可视化工作室版本在哪里。 在 Visual Studio 2019 中，*`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* 这些文件位于 中。 属性也会存储在可能添加到自己的项目*`.props`* 的任何自定义文件中。 我们强烈建议您不要手动编辑这些文件。 相反，使用 IDE 中的属性页修改所有属性，尤其是参与继承的属性，除非您对 MSBuild 有深刻的理解。

如前面所示，相同配置的同一属性在不同文件中可能分配有不同值。 生成项目时，MSBuild 引擎以明确定义的顺序评估项目文件和所有导入的文件（如下所述）。 在评估每个文件时，该文件中定义的任何属性值都将覆盖现有值。 未指定的任何值都是从之前计算的文件继承的。 当您设置具有属性页的属性时，注意设置属性的位置也很重要。 如果在*`.props`* 文件中将属性设置为"X"，但属性在项目文件中设置为"Y"，则项目将生成属性设置为"Y"。 如果同一属性在项目项（如*`.cpp`* 文件）上设置为"Z"，则 MSBuild 引擎将使用"Z"值。

这是基本的继承树：

1. MSBuild CPP 工具集中的默认设置 （..{程序文件\MSBuild\Microsoft.Cpp_v4.0\Microsoft.Cpp.default.props，该文件导入*`.vcxproj`*。

1. 属性表

1. *`.vcxproj`* 文件。 （可能重写默认设置和属性页设置。）

1. 项元数据

> [!TIP]
> 在属性页上，在当前上下文中定义**粗体**属性。 普通字体的属性将被继承。

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>查看包含所有导入值的已扩展项目文件

有时，通过查看展开的文件来确定给定的属性值如何继承非常有用。 若要查看扩展版本，请在 Visual Studio 命令提示中输入以下命令。 （将占位符文件名称更改为要使用的名称。）

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

扩展的项目文件可能很大，很难理解，除非您熟悉 MSBuild。 这是项目文件的基本结构：

1. 基本项目属性，这些属性未在 IDE 中公开。

1. 导入*`Microsoft.cpp.default.props`*，它定义了一些与工具集无关的基本属性。

1. 全局配置属性在“常规配置”页面上显示为“PlatformToolset”和“项目”默认属性************。 这些属性确定在下一步中*`Microsoft.cpp.props`* 导入了哪些工具集和内部属性表。

1. 导入*`Microsoft.cpp.props`*，它设置大多数项目默认值。

1. 导入所有属性表，包括*`.user`* 文件。 这些属性表可以重写内容，但“PlatformToolset”和“项目”默认属性除外********。

1. 项目配置属性的其余部分。 这些值可以重写属性表中设置的内容。

1. 项（文件）及其元数据。 这些项目始终是 MSBuild 计算规则中的最后一个单词，即使它们发生在其他属性和导入之前也是如此。

有关详细信息，请参阅 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)。

## <a name="build-configurations"></a>生成配置

配置只是给定名称的任意一组属性。 Visual Studio 提供调试和发布配置。 每个属性都适当地为调试生成或发布生成设置各种属性。 您可以使用**配置管理器**定义自定义配置。 它们是为特定版本的特性对属性进行分组的便捷方法。

要更好地了解生成配置，应打开**属性管理器**。 您可以通过选择 **"查看>属性管理器**"或 **>"查看其他 Windows >属性管理器**"来打开它，具体取决于您的设置。 **属性管理器**具有项目中每个配置和平台对的节点。 在每个节点下，都是为该配置设置特定属性*`.props`* 的属性表（文件）的节点。

![属性管理器](media/property-manager.png "“属性管理器”")

例如，您可以转到"属性页"中的"常规"窗格。 将字符集属性更改为"未设置"而不是"使用 Unicode"，然后单击"**确定**"。 属性管理器现在不显示**Unicode 支持**属性表。 它已为当前配置删除，但它仍然存在其他配置。

有关属性管理器和属性表的更多信息，请参阅[共享或重用 Visual Studio C++ 项目设置](create-reusable-property-configurations.md)。

> [!TIP]
> 该文件*`.user`* 是一个旧功能。 我们建议您将其删除，以便根据配置和平台正确分组属性。
