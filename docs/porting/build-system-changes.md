---
title: Visual Studio 2010 中的生成系统更改
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
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828167"
---
# <a name="build-system-changes"></a>有关生成系统的更改

MSBuild 系统用于生成 Visual C++ 项目。 但是，在 Visual Studio 2008 和早期版本中，使用了 VCBuild 系统。 依赖 VCBuild 的某些文件类型和概念在当前系统中不存在或表示方式不同。 本文档讨论了当前生成系统的差异。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 现在是 .vcxproj

项目文件不再使用 .vcproj 文件扩展名。 Visual Studio 自动将由早期版本的 Visual C++ 创建的项目文件转换为当前系统使用的格式。 有关如何手动升级项目的详细信息，请参阅 [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。

在最新版本中，项目文件的文件扩展名为 .vcxproj。

## <a name="vsprops-is-now-props"></a>.vsprops 现在是 .props

在早期版本中，项目属性表是基于 XML 的文件，其文件扩展名为 .vsprops。 项目属性表可以为生成工具（如编译器或链接器）指定开关和创建用户定义的宏。

在最新版本中，项目属性表的文件扩展名为 .props。

## <a name="custom-build-rules-and-rules-files"></a>自定义生成规则和 .rules 文件

在早期版本中，规则文件是基于 XML 的文件，其文件扩展名为 .rules。 规则文件可以定义自定义生成规则并将其合并到 Visual C++ 项目的生成过程中。 可以与一个或多个文件扩展名关联的自定义生成规则可以将输入文件传递到创建一个或多个输出文件的工具。

在此版本中，自定义生成规则由三种文件类型（.xml、.props 和 .targets）表示，而不是由 .rules 文件表示。 使用早期版本的 Visual C++ 创建的 .rules 文件迁移到最新版本时，创建等效的 .xml、.props和 .targets 文件，并将其与原始 .rules 文件一起存储在项目中。

> [!IMPORTANT]
>  在最新版本中，IDE 不支持创建新规则。 因此，若要使用通过早期版本的 Visual C++ 创建的项目中的规则文件，最简单的方法是将该项目迁移到最新版本。

## <a name="inheritance-macros"></a>继承宏

在早期版本中，$(Inherit) 宏指定了继承属性在由项目生成系统组成的命令行中的显示顺序。 $(NoInherit) 导致任何出现的 $(Inherit) 都被忽略，并导致任何本来可以继承的属性不被继承。 例如，默认情况下，$(Inherit) 宏导致通过使用 [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) 编译器选项指定的文件被追加到命令行。

在最新版本中，通过将属性的值指定为一个或多个文本值和属性宏的串联来支持继承。 $(Inherit) 和 $(NoInherit) 宏不受支持。

在以下示例中，以分号分隔的列表被分配盗属性页上的属性。 该列表包含 \<value> 文本和 `MyProperty` 属性值的串联，可通过使用宏表示法 $(<em>MyProperty</em>) 访问。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj.user 文件

用户文件 (.vcxproj.user) 存储特定于用户的属性，例如调试和部署设置。 vcxproj.user 文件适用于特定用户的所有项目。

## <a name="vcxprojfilters-file"></a>.vcxproj.filters 文件

解决方案资源管理器用于将文件添加到项目时，筛选器文件 (.vcxproj.filters) 定义在解决方案资源管理器树状视图中添加文件（基于其文件扩展名）的位置。

## <a name="vc-directories-settings"></a>VC++ 目录设置

Visual C++ 目录设置在[“VC++ 目录”属性页](../ide/vcpp-directories-property-page.md)上指定。 在早期版本的 Visual Studio 中，目录设置适用于每个用户，并且在 sysincl.dat 文件中指定了已排除的目录列表。

如果在命令行上运行 [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)，则无法更改 VC++ 目录设置。 如果打开“工具”菜单，单击“导入和导出设置”，然后选择“重置所有设置”选项，同样无法更改设置。

从由早期版本的 Visual C++ 创建的 .vssettings 文件迁移 VC++ 目录设置。 打开“工具”菜单，单击“导入和导出设置”，选择“导入选定的环境设置”，然后按照向导中的说明进行操作。 或者，当第一次启动 Visual Studio 时，在“选择默认环境设置”对话框中，选择“除了下面所选的默认设置以外，从早期版本中迁移并应用合格的设置”。

## <a name="see-also"></a>请参阅

[命令行上的 MSBuild - C++](../build/msbuild-visual-cpp.md)
