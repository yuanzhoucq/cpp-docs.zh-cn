---
title: 有关生成系统的更改
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 742b018ae96ff706336a81b49e1d8e5fb954d9b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425440"
---
# <a name="build-system-changes"></a>有关生成系统的更改

MSBuild 系统用于生成 Visual C++ 项目。 但是，在 Visual Studio 2008 和早期版本中，使用了 VCBuild 系统。 某些文件类型和依赖 VCBuild 的概念不存在，或在当前系统中以不同的方式表示。 本文档讨论在当前的生成系统中的差异。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 现.vcxproj

项目文件不能再使用.vcproj 文件扩展名。 Visual Studio 会自动转换项目文件创建的早期版本的 Visual c + + 为当前系统使用的格式。 有关如何将项目手动升级的详细信息，请参阅[/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。

在当前版本中，项目文件的文件扩展名为.vcxproj。

## <a name="vsprops-is-now-props"></a>.vsprops 现.props

在早期版本中，*项目属性表*是具有.vsprops 文件扩展名的基于 XML 的文件。 项目属性表可让你指定的生成工具，例如编译器或链接器开关并创建用户定义的宏。

在当前版本中，项目属性表的文件扩展名为.props。

## <a name="custom-build-rules-and-rules-files"></a>自定义生成规则和.rules 文件

在早期版本中，*规则文件*是扩展名为.rules 文件名称的基于 XML 的文件。 规则文件，可以定义自定义生成规则，并将其合并到 Visual c + + 项目的生成过程。 一个自定义生成规则，其中可以与一个或多个文件扩展名相关联，可以将输入的文件传递到一种工具，将创建一个或多个输出文件。

在此版本中，由三个文件类型、.xml、.props 和.targets，而不是.rules 文件表示自定义生成规则。 在已通过使用早期版本的 Visual c + + 的.rules 文件迁移到当前版本，等效的.xml、.props 和.targets 文件创建和存储在你的项目与原始的.rules 文件中。

> [!IMPORTANT]
>  在当前版本中，IDE 不支持创建新规则。 因此，若要使用通过早期版本的 Visual C++ 创建的项目中的规则文件，最简单的方法是将该项目迁移到最新版本。

## <a name="inheritance-macros"></a>继承宏

在早期版本中， **$ （inherit)** 宏指定继承的属性的显示的顺序由项目生成系统的命令行上。 **$ （noinherit)** 宏 $ （inherit） 被忽略的任何匹配项，并折叠要的任何属性将被继承，不被继承。 例如，默认情况下 $ （inherit） 宏会导致通过使用指定的文件[/I （附加包含目录）](../build/reference/i-additional-include-directories.md)编译器选项追加到命令行。

在当前版本中，通过指定属性的值的串联的一个或多个文本值和属性宏支持继承。 **$ （inherit)** 并 **$ （noinherit)** 宏不受支持。

在以下示例中，以分号分隔的列表被分配给属性页上的属性。 列表包含的串联*\<值 >* 文字和的值`MyProperty`属性，它通过使用宏表示法访问时， **$(** <em>MyProperty</em>**)**。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>。 vcxproj.user 文件

用户文件 (。 vcxproj.user) 存储特定于用户的属性，例如，调试和部署设置。 Vcxproj.user 文件适用于特定用户的所有项目。

## <a name="vcxprojfilters-file"></a>。 vcxproj.filters 文件

当**解决方案资源管理器**用于将文件添加到项目中，筛选器文件 (。 vcxproj.filters) 定义中的位置**解决方案资源管理器**树的视图添加文件时，基于其文件扩展名。

## <a name="vc-directories-settings"></a>VC + + 目录设置

Visual c + + 目录设置在指定[VC + + Directories Property Page](../ide/vcpp-directories-property-page.md)。 在早期版本的 Visual Studio 中，目录设置应用每个用户和 sysincl.dat 文件中指定的已排除的目录列表。

如果您运行，不能更改 VC + + 目录设置[devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)在命令行。 您还不能更改设置如果您打开**工具**菜单上，单击**导入和导出设置**，然后选择**重置所有设置**选项。

从早期版本的 Visual c + + 创建的.vssettings 文件迁移 VC + + 目录设置。 打开**工具**菜单上，单击**导入和导出设置**，选择**导入选定的环境设置**，然后按照向导中的说明进行操作。 当您按或启动 Visual Studio 第一次**选择默认环境设置**对话框中，选择**迁移合格的设置从以前的版本并将其应用除了默认设置下面所选**。

## <a name="see-also"></a>请参阅

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
