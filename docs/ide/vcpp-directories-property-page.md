---
title: VC + + 目录属性页 |Microsoft 文档
ms.custom: ''
ms.date: 04/26/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs:
- C++
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8931ecd34acfa1aba0287274acb45d362bdec2cf
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="vc-directories-property-page-windows"></a>VC + + 目录属性页 (Windows)

此属性页用于告知 Visual Studio 生成当前所选项目时要使用的目录。 若要在解决方案中设置为多个项目的目录，使用自定义属性表中所述[创建可重用的属性配置](working-with-project-properties.md#bkmkPropertySheets)。

有关此页的 Linux 版本，请参阅[VC + + 目录 （Linux c + +）](../linux/prop-pages/directories-linux.md)。   

访问**VC + + 目录**属性页：

1. 如果**解决方案资源管理器**窗口不可见，然后在主菜单上选择**视图** > **解决方案资源管理器**。
1. 右键单击项目节点 （不是顶级解决方案），然后选择**属性**。
1. 在左窗格中**属性页**对话框中，选择**配置属性** > **VC + + 目录**。  

VC + + 目录属性适用于一个项目，而不是顶级解决方案节点。 如果看不到**VC + + 目录**下**配置属性**，选择中的 c + + 项目节点**解决方案资源管理器**窗口： 

![选择项目节点](media/vcppdir.png "选择项目节点，以查看 VC + + 目录属性")

请注意， **VC + + 目录**跨平台项目中的属性页的外观。 特定于 Linux c + + 项目的信息，请参阅[VC + + 目录 （Linux c + +）](../linux/prop-pages/directories-linux.md)。 
 
如果你不熟悉*项目属性*在 Visual Studio 中，你可能会发现它对第一次读取帮助[使用项目属性](working-with-project-properties.md)。 
 
默认设置**VC + + 目录**属性取决于项目类型。 对于桌面项目中，它们包括特定的平台工具集的 c + + 工具位置和为 Windows SDK 的位置。 你可以更改**平台工具集**和**Windows SDK 版本**上**配置属性** > **常规**页。 

若要查看的任何目录的值：

1. 选择中的属性之一**VC + + 目录**页。 例如，选择**库目录**。
1. 选择向下箭头按钮在属性值字段的末尾。
1. 在下拉列表菜单中，选择**编辑**。

![编辑库目录](media/vcppdir_libdir_edit.png "对话框编辑库路径")

现在，你将看到如下对话框： 

![显示库目录](media/vcppdir_libdir.png "对话框添加或删除库路径")

使用此对话框可以查看当前目录。 但是，如果你想要更改或添加一个目录，则最好使用**属性管理器**创建属性表或修改默认用户属性页。 有关详细信息，请参阅[创建可重用的属性配置](working-with-project-properties.md#bkmkPropertySheets)。

如上所示，作为宏提供许多的继承路径。  若要检查宏的当前值，请选择**宏**对话框右下角中的按钮。 请注意，许多宏取决于配置类型。 在调试版本的宏可能计算结果为发布版本中的相同宏以外的其他路径。 

你可以搜索的部分或完全匹配项的编辑框中。 下图显示了包含字符串"WindowsSDK"的所有宏和它还都显示当前路径宏计算结果为：

![请参阅宏值](media/vcppdir_libdir_macros.png "对话框编辑宏")

注意： 您键入时，会填充列表。 不要按**Enter**。

有关宏和为何应而不是硬编码路径尽可能使用它们的详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

常用的宏的列表，请参阅[用于生成命令和属性的公共宏](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties)。

你可以通过两种方式来定义您自己的宏：
-   在开发人员命令提示中设置环境变量。 所有环境变量将被都视为 MSBuild 属性/宏。
-   在.props 文件中定义用户宏。 有关详细信息，请参阅[属性页宏](working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

有关详细信息，请参阅以下博客帖子： [VC + + 目录](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[继承属性和属性表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010 c + + 项目升级指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
## <a name="directory-types"></a>目录类型

你还可以指定其他目录，如下所示。  
  
**可执行目录**<br/>
在其中搜索可执行文件的目录。 对应于**路径**环境变量。

**包含目录**<br/>
在其中搜索源代码中所引用的包含文件的目录。 对应于**包括**环境变量。

**引用目录**<br/>
 要在其中搜索程序集和通过的源代码中引用的模块 （元数据） 文件的目录[#using](../preprocessor/hash-using-directive-cpp.md)指令。 对应于**LIBPATH**环境变量。

**库目录**<br/>
在其中搜索库 (.lib) 文件的目录；其中包括运行库。 对应于**LIB**环境变量。 此设置不适用于.obj 文件;若要链接到.obj 文件中，在**配置属性** > **链接器** > **常规**属性页上，选择**其他库依赖项**，然后指定文件的相对路径。 有关详细信息，请参阅[链接器属性页](../ide/linker-property-pages.md)。

**库 WinRT 目录**<br/>
在通用 Windows 平台 (UWP) 应用中使用目录以便搜索 WinRT 库文件。 

**源目录**<br/>
在其中搜索用于 IntelliSense 的源文件的目录。

**排除目录**<br/>
在每次编译之前 Visual Studio 查询上所有文件，以确定是否修改了任何自以前编译以来的时间戳。 如果你的项目具有大型稳定库，你可能通过可以加快生成时间的时间戳检查从中排除这些目录。

## <a name="sharing-the-settings"></a>共享设置

你可以与其他用户或在多台计算机上共享项目属性。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。
