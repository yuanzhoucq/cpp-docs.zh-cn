---
title: 如何：修改目标框架和平台工具集
ms.custom: conceptual
ms.date: 05/06/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: c3d6b50a57cab9cc63657949fceccebf4ea6b8c9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220673"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>如何：修改目标框架和平台工具集

您可以更改 Visual StudioC++项目设置以面向不同版本的.NET framework 并使用不同的平台工具集。 默认情况下，项目系统将使用对应于你用于创建该项目的 Visual Studio 版本的 .NET Framework 版本和工具集版本。 可以通过修改项目属性来更改目标平台工具集。 可以通过修改项目 (.vcxproj) 文件来更改目标框架。 不必为每个编译目标都维护一个单独的基本代码。

> [!IMPORTANT]
>  某些版本可能不支持修改过的目标 Framework 或平台工具集。 有关兼容性信息，请参阅[端口、 迁移和升级 Visual Studio 项目](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)。

在更改目标 Framework 时，也要将平台工具集更改为支持该 Framework 的版本。 例如，要面向 .NET Framework 4.5，你必须使用兼容平台工具集，例如 Visual Studio 2015 (v140)、Visual Studio 2013 (v120) 或 Visual Studio 2012 (v110)。 可以使用 **“Windows7.1SDK”** 平台工具集将 .NET Framework 2.0、3.0、3.5 和 4 以及 x86、Itanium 和 x64 平台作为目标。

> [!NOTE]
>  若要更改目标平台工具集，你必须安装相关版本的 Visual Studio 或 Windows Platform SDK。 例如，要面向具有“Windows7.1SDK”  平台工具集的 Itanium 平台，你必须安装 [适用于 Windows 7 的 Microsoft Windows SDK 和 .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279) ；但是，只要面向正确的 Framework 版本和平台工具集，你就可以使用 Visual Studio 的其他兼容版本来完成开发工作。

可以通过创建自定义平台工具集来扩展目标平台。 有关详细信息，请参见 Visual C++ 博客上的 [C++ 本机多目标](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) 。

### <a name="to-change-the-target-framework"></a>更改目标框架

1. 在 Visual Studio 中，在“解决方案资源管理器” 中，选择你的项目。 在菜单栏上，打开“项目”  菜单并选择“卸载项目” 。 这将为你的项目卸载项目文件 (.vcxproj)。

    > [!NOTE]
    >  C++ 项目文件正在 Visual Studio 中修改时无法加载该项目。 但是，当项目加载到 Visual Studio 中时，你可以使用另一个编辑器（如记事本）来修改项目文件。 Visual Studio 会检测到项目文件的更改并提示你重新加载项目。

1. 在菜单栏上，依次选择 **“文件”**、 **“打开”**、 **“文件”**。 在 **“打开文件”** 对话框中，导航到项目文件夹，然后打开项目文件 (.vcxproj)。

1. 在项目文件中，找到目标 Framework 版本的条目。 例如，如果你的项目设计为使用 .NET Framework 4.5，请在 `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` 元素的 `<PropertyGroup Label="Globals">` 元素中找到 `<Project>` 。 如果 `<TargetFrameworkVersion>` 元素不存在，你的项目不使用 .NET Framework，也无需进行更改。

1. 将值更改为需要的 Framework 版本，例如 v3.5 或 v4.6。

1. 保存更改并关闭编辑器。

1. 在 **“解决方案资源管理器”** 中，打开项目的快捷菜单，然后选择 **“重新加载项目”**。

1. 若要验证更改，在“解决方案资源管理器” 中，右键单击打开你的项目（不适用于解决方案）的快捷菜单，然后选择“属性”  以打开项目“属性页”  对话框。 在对话框的左窗格中，展开 **“配置属性”** ，然后选择 **“常规”**。 验证“.NET 目标 Framework 版本”  是否显示了新的 Framework 版本。

### <a name="to-change-the-project-toolset"></a>更改项目工具集

1. 在 Visual Studio 中，在 **解决方案资源管理器**中，打开您的项目（不适用于您的解决方案）的快捷菜单，然后选择 **属性** 可打开 **项目属性页** 对话框。

1. 在 **“属性页”** 对话框中，打开 **“配置”** 下拉列表，然后选择 **“所有配置”**。

1. 在对话框的左窗格中，展开 **“配置属性”** ，然后选择 **“常规”**。

1. 在右窗格中，选择 **“平台工具集”** ，然后从下拉列表中选择需要的工具集。 例如，如果已安装 Visual Studio 2010 工具集，则选择**Visual Studio 2010 (v100)** 要用于你的项目。

1. 选择“确定”  按钮。

## <a name="see-also"></a>请参阅

[在命令行中的 MSBuildC++](msbuild-visual-cpp.md)
