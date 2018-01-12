---
title: "VC + + 目录属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c92a97ccd28a1bc7d1fae518cf499b45d339dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vc-directories-property-page-windows"></a>VC + + 目录属性页 (Windows)

此属性页用于告知 Visual Studio 生成当前所选项目时要使用的目录。 若要在解决方案中设置为多个项目的目录，使用自定义属性表中所述[创建可重用的属性配置](working-with-project-properties.md#bkmkPropertySheets)。

有关此页的 Linux 版本，请参阅[VC + + 目录 （Linux c + +）](../linux/prop-pages/directories-linux.md)。   

访问**VC + + 目录**属性页：

1. 在主菜单中选择**视图 |解决方案资源管理器**
1. 右键单击项目节点 （不是顶级解决方案），然后选择**属性**
1. 在左窗格中**属性页**对话框框中，展开**配置属性**和选择**VC + + 目录**。  

VC + + 目录属性适用于一个项目，不是顶级解决方案节点：

![选择项目节点](media/vcppdir.png "选择项目节点，以查看 VC + + 目录属性")

如果看不到属性页，请确保已在中选择项目节点**解决方案资源管理器**。 请注意， **VC + + 目录**跨平台项目中的属性页的外观。 对于非 Windows 项目，请参阅[VC + + 目录 （Linux c + +）](../linux/prop-pages/directories-linux.md)或。 
 
如果你不熟悉*项目属性*在 Visual Studio 中，你可能会发现它对第一次读取帮助[使用项目属性](working-with-project-properties.md)。 
 
VC + + 目录的默认设置取决于项目类型。 对于桌面项目中，它们包括特定的平台工具集的 VC + + 工具位置和为 Windows SDK 的位置。 你可以更改**平台工具集**和**Windows SDK 版本**上**配置属性-常规**页。 若要查看的任何目录的值：

1. 在右窗格中**VC + + 目录**页上，选择一行。 例如，**库目录**
1. 选择右侧的向下箭头按钮
1. 选择**编辑**。

![编辑库目录](media/vcppdir_libdir_edit.png "对话框编辑库路径")

现在，你将看到如下对话框： 

![显示库目录](media/vcppdir_libdir.png "对话框添加或删除库路径")

使用此对话框可以查看当前目录。 但是，如果你想要更改或添加一个目录，则最好使用**属性管理器**创建属性表或修改默认用户属性页。 有关详细信息，请参阅[创建可重用的属性配置](working-with-project-properties.md#bkmkPropertySheets)。

如上所示，作为宏提供许多的继承路径。  若要检查宏的当前值，请选择**宏**对话框右下角中的按钮。 请注意，许多宏取决于配置类型。 在调试版本的宏可能计算结果为发布版本中的相同宏以外的其他路径。 

你可以搜索的部分或完全匹配项的编辑框中。 下图显示了包含字符串"WindowsSDK"的所有宏和它还都显示当前路径宏计算结果为：

![请参阅宏值](media/vcppdir_libdir_macros.png "对话框编辑宏")

注意： 您键入时，将填充列表。 不要按**Enter**。

有关宏和为何应而不是硬编码路径尽可能使用它们的详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

常用的宏的列表，请参阅[用于生成命令和属性的公共宏](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties)。

你可以通过两种方式来定义您自己的宏：
-   在开发人员命令提示中设置环境变量。 所有环境变量将被都视为 MSBuild 属性/宏。
-   在.props 文件中定义用户宏。 有关详细信息，请参阅[属性页宏](working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

有关详细信息，请参阅以下博客帖子： [VC + + 目录](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[继承属性和属性表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010 c + + 项目升级指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
## <a name="directory-types"></a>目录类型

你还可以指定其他目录，如下所示。  
  
**可执行目录**  
在其中搜索可执行文件的目录。 对应于**路径**环境变量。

**包含目录**  
在其中搜索源代码中所引用的包含文件的目录。 对应于**包括**环境变量。

**引用目录**  
 要在其中搜索程序集和通过的源代码中引用的模块 （元数据） 文件的目录[#using](../preprocessor/hash-using-directive-cpp.md)指令。 对应于**LIBPATH**环境变量。

**库目录**  
在其中搜索库 (.lib) 文件的目录；其中包括运行库。 对应于**LIB**环境变量。 此设置不适用于.obj 文件;若要链接到.obj 文件中，在[链接器](../ide/linker-property-pages.md)**常规**属性页上，选择**其他库依赖项**，然后指定文件的相对路径。

**源目录**  
在其中搜索用于 IntelliSense 的源文件的目录。

**排除目录**  
检查生成依赖项时不搜索的目录。

## <a name="sharing-the-settings"></a>共享设置

你可以与其他用户或在多台计算机上共享项目属性。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。
