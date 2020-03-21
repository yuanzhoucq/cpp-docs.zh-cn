---
title: VCBuild 与 MSBuild
description: Visual Studio C++生成系统已从 VCBuild 更改为 visual studio 2010 中的 MSBuild。
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: ce3eb9e51a103aa54b74c7b5b4f775eb402269f1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076956"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild 与 MSBuild：在 Visual Studio 2010 中生成系统更改

C++项目的 MSBuild 系统是在 Visual Studio 2010 中引入的。 在 Visual Studio 2008 及更早版本中，使用了 VCBuild 系统。 依赖于 VCBuild 的某些文件类型和概念在 MSBuild 中不存在或以不同的方式表示。 本文档讨论了当前生成系统的差异。 若要将 Visual Studio 2008 项目转换为 MSBuild，必须使用 Visual Studio 2010。 转换项目后，应使用最新版本的 Visual Studio 升级到当前 IDE 和编译器工具集。 有关详细信息，包括如何获取 Visual Studio 2010，请参阅[Visual studio 2008 的说明](use-native-multi-targeting.md#instructions-for-visual-studio-2008)。

以下各节汇总了从 VCBuild 到 MSBuild 的更改。 如果 VCBuild 项目具有 MSBuild 无法识别的自定义生成规则或宏，请参阅[Visual Studio 项目- C++ ](../build/creating-and-managing-visual-cpp-projects.md)了解如何将这些指令转换为 msbuild 系统。 从 VCBuild 到 MSBuild 的初始转换只是一个中间步骤。 不需要完全正确地获取项目文件或使程序编译时不会出错。 仅使用 Visual Studio 2010 将项目转换为 MSBuild 格式，以便使项目在最新版本的 Visual Studio 中运行。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 现在是 .vcxproj

项目文件不再使用 .vcproj 文件扩展名。 Visual Studio 2010 会将 Visual C++ Studio 早期版本创建的项目文件自动转换为 MSBuild 格式，该格式使用项目文件的 .vcxproj 扩展名。

## <a name="vsprops-is-now-props"></a>.vsprops 现在是 .props

在 Visual Studio 2008 及更早版本中，*项目属性表*是基于 XML 的文件，文件扩展名为 vsprops。 项目属性表可以为生成工具（如编译器或链接器）指定开关和创建用户定义的宏。 在 MSBuild 中，项目属性表的文件扩展名为属性。

## <a name="custom-build-rules-and-rules-files"></a>自定义生成规则和. 规则文件

在 Visual Studio 2008 及更早版本中，*规则文件*是基于 XML 的文件，其文件扩展名为。 借助规则文件，可定义自定义生成规则并将其合并到 Visual Studio C++ 项目的生成过程中。 可以与一个或多个文件扩展名关联的自定义生成规则可以将输入文件传递到创建一个或多个输出文件的工具。

在 MSBuild 系统中，自定义生成规则由三个文件类型（.xml、. 属性和 .targets）表示，而不是由 rules 文件表示。 当使用 Visual C++ Studio 的早期版本创建的. 规则文件迁移到 visual Studio 2010 时，会创建属性文件，并将它们与原始 rules 文件一起存储在您的项目中。

> [!IMPORTANT]
> 在 Visual Studio 2010 中，IDE 不支持创建新规则。 出于此原因，使用 Visual C++ Studio 早期版本创建的项目中的规则文件的最简单方法是将项目迁移到 visual Studio 2010。

## <a name="inheritance-macros"></a>继承宏

在 Visual Studio 2008 及更早版本中， **$ （Inherit）** 宏指定继承的属性在项目生成系统所撰写的命令行上的显示顺序。 $(NoInherit) 导致任何出现的 $(Inherit) 都被忽略，并导致任何本来可以继承的属性不被继承。 例如，默认情况下，$(Inherit) 宏导致通过使用 [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) 编译器选项指定的文件被追加到命令行。

在 Visual Studio 2010 中，通过将属性的值指定为一个或多个文本值和属性宏的连接，支持继承。 $(Inherit) 和 $(NoInherit) 宏不受支持。

在以下示例中，以分号分隔的列表被分配盗属性页上的属性。 该列表包含 *value> 文本和 \< 属性值的串联，可通过使用宏表示法 $(* MyProperty`MyProperty`) 访问。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj 文件

用户文件 (.vcxproj.user) 存储特定于用户的属性，例如调试和部署设置。 *.Vcxproj*文件适用于特定用户的所有项目。

## <a name="vcxprojfilters-file"></a>.vcxproj 文件

当使用**解决方案资源管理器**将文件添加到项目时，筛选器文件（ *. .vcxproj*）根据文件扩展名定义在**解决方案资源管理器**树视图中添加文件的位置。

## <a name="vc-directories-settings"></a>VC + + 目录设置

Visual C++ 目录设置在[“VC++ 目录”属性页](../ide/vcpp-directories-property-page.md)上指定。 在 Visual Studio 2008 及更早版本中，目录设置应用于每个用户，并在*sysincl*文件中指定排除目录的列表。

如果在命令行上运行 [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)，则无法更改 VC++ 目录设置。 如果打开“工具”菜单，单击“导入和导出设置”，然后选择“重置所有设置”选项，同样无法更改设置。

若要从 Visual Studio 早期版本创建的 *.vssettings*文件迁移 VC + + 目录设置，请执行以下操作：

1. 打开 "**工具**" 菜单，单击 "**导入和导出设置**"
2. 选择 "**导入选定的环境设置**"
3. 按照向导中的说明操作。

## <a name="see-also"></a>另请参阅

[命令行上的 MSBuild - C++](../build/msbuild-visual-cpp.md)
