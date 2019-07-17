---
title: “VC++ 目录”属性页
ms.date: 10/09/2018
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
ms.openlocfilehash: aff143fca47cb5958b90e4a3f4c7ec284f2129f5
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861047"
---
# <a name="vc-directories-property-page-windows"></a>“VC++ 目录”属性页 (Windows)

使用此属性页告知 Visual Studio 在生成当前所选项目时要使用的目录。 若要在解决方案中设置多个项目的目录，请使用自定义属性表中所述[共享或重用 Visual StudioC++项目设置](../create-reusable-property-configurations.md)。

若需要此页的 Linux 版本，请参阅 [VC++ 目录 (Linux C++)](../../linux/prop-pages/directories-linux.md)。

要访问“VC++ 目录”属性页，请执行以下操作  ：

1. 如果“解决方案资源管理器”窗口不可见，请在主菜单上选择“视图” > “解决方案资源管理器”    。
1. 右键单击某个项目节点（而不是顶级解决方案）并选择“属性”  。
1. 在“属性页”对话框的左窗格中，选择“配置属性” > “VC++ 目录”    。

VC++ 目录属性适用于项目，而不是顶级解决方案节点。 如果在“配置属性”下未看到“VC++ 目录”，请在“解决方案资源管理器”窗口中选择一个 C++ 项目节点    ：

![选择项目节点](../media/vcppdir.png "选择项目节点以查看 VC++ 目录属性")

请注意，跨平台项目的“VC++ 目录”属性页看起来会有所不同  。 若要了解 Linux C++ 项目的特定信息，请参阅 [VC++ 目录 (Linux C++)](../../linux/prop-pages/directories-linux.md)。

如果您不熟悉*项目属性*在 Visual Studio 中，您可能会有所它到第一次读取[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

“VC++ 目录”属性的默认设置取决于项目类型  。 对于桌面项目，它们包括特定平台工具集的 C++ 工具位置以及 Windows SDK 位置。 可更改“配置属性” > “常规”页上的“平台工具集”和“Windows SDK 版本”     。

要查看任一目录的这些值，请执行以下操作：

1. 选择“VC++ 目录”页中的其中一个属性  。 例如选择“库目录”  。
1. 选择属性值字段末尾的向下箭头按钮。
1. 在下拉菜单中选择“编辑”  。

![编辑库目录](../media/vcppdir_libdir_edit.png "用于编辑库路径的对话框")

此时会看到如下所示的对话框：

![显示库目录](../media/vcppdir_libdir.png "用于添加或删除库路径的对话框")

使用此对话框查看当前目录。 不过如果希望更改或添加目录，最好使用“属性管理器”创建属性表或修改默认用户属性表  。 有关详细信息，请参阅[共享或重用 Visual StudioC++项目设置](../create-reusable-property-configurations.md)。

如上所述，很多继承路径都以宏的形式提供。  若要检查某个宏的当前值，请选择对话框右下角中的“宏”按钮  。 请注意，很多宏都取决于配置类型。 同样的宏在调试生成和版本生成中得出的路径可能会有所不同。

可以在编辑框中搜索部分或完全匹配项。 下图显示了包含字符串“WindowsSDK”的所有宏，并且还显示了这些宏计算出的当前路径：

![查看宏的值](../media/vcppdir_libdir_macros.png "用于编辑宏的对话框")

注意:键入时，会填充列表。 请勿按 Enter  。

有关宏以及为什么应而不是硬编码路径尽可能使用它们的详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

有关常用宏的列表，请参阅[用于常见宏生成命令和属性](common-macros-for-build-commands-and-properties.md)。

可以通过两种方式来定义自己的宏：

- 在开发人员命令提示符处设置环境变量。 所有环境变量都将被视为 MSBuild 属性/宏。

- 在 .props 文件中定义用户宏。 有关详细信息，请参阅[属性页宏](../working-with-project-properties.md)。

有关详细信息，请参阅以下博客文章：[VC + + 目录](https://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[继承属性和属性表](https://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010C++项目升级指南](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/)。

## <a name="directory-types"></a>目录类型

你还可以指定其他目录，如下所示。

**可执行目录**<br/>
在其中搜索可执行文件的目录。 对应于 PATH 环境变量  。

**包含目录**<br/>
在其中搜索源代码中所引用的包含文件的目录。 对应于 INCLUDE 环境变量  。

**引用目录**<br/>
通过 [#using](../../preprocessor/hash-using-directive-cpp.md) 指令在其中搜索源代码中所引用的程序集和模块（元数据）文件的目录。 对应于 LIBPATH 环境变量  。

**库目录**<br/>
在其中搜索库 (.lib) 文件的目录；其中包括运行库。 对应于 LIB 环境变量  。 该设置不适用于 .obj 文件，若要链接到 .obj 文件，请在“配置属性” > “链接器” > “常规”属性页上选择“其他库依赖项”，然后指定文件的相对路径     。 有关详细信息，请参阅[链接器属性页](linker-property-pages.md)。

**库 WinRT 目录**<br/>
搜索用于通用 Windows 平台(UWP) 应用的 WinRT 目录文件的目录。

**源目录**<br/>
在其中搜索用于 IntelliSense 的源文件的目录。

**排除目录**<br/>
Visual Studio 在每次编译之前都会查询所有文件上的时间戳，确定自上次编译后是否修改过任何内容。 如果项目具备一些大型且稳定的库，则通过从时间戳检查中排除这些库，可以潜在地加快生成时间。

## <a name="sharing-the-settings"></a>共享设置

你可以与其他用户或在多台计算机上共享项目属性。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。
