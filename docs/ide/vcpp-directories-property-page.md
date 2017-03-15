---
title: "“VC++ 目录”属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDirectories.IncludePath"
  - "VC.Project.VCDirectories.ReferencePath"
  - "VC.Project.VCDirectories.SourcePath"
  - "VC.Project.VCDirectories.LibraryWPath"
  - "VC.Project.VCDirectories.ExecutablePath"
  - "VC.Project.VCDirectories.LibraryPath"
  - "VS.ToolsOptionsPages.Projects.VCDirectories"
  - "VC.Project.VCDirectories.ExcludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“VC++ 目录”属性页"
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “VC++ 目录”属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定你希望 Visual Studio 用于生成项目的目录。  若要访问该属性页，请在**“解决方案资源管理器”**中打开项目的快捷菜单并选择**“属性”**，然后在**“属性页”**对话框的左窗格中，展开**“配置属性”**并选择**“VC\+\+ 目录”**。  
  
 使用 Visual Studio 创建项目时，会继承某些目录。  其中许多都以宏的形式提供。  若要检查宏的当前值，请在**“VC\+\+ 目录”**页面的右窗格中选择一行（例如**“包含目录”**），选择右侧的向下箭头按钮，再选择**“编辑”**，然后在显示的对话框中选择**“宏”**按钮。  有关详细信息，请参阅以下博客文章：[VC\+\+ Directories](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)（VC\+\+ 目录）、[Inherited Properties and Property Sheets](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)（继承的属性和属性表）和 [Visual Studio 2010 C\+\+ Project Upgrade Guide](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)（Visual Studio 2010 C\+\+ 项目升级指南）。  
  
## 目录类型  
 你还可以指定其他目录，如下所示。  
  
 **可执行目录**  
 在其中搜索可执行文件的目录。  对应于 **PATH** 环境变量。  
  
 **包含目录**  
 在其中搜索源代码中所引用的包含文件的目录。  对应于 **INCLUDE** 环境变量。  
  
 **引用目录**  
 通过 [\#using](../preprocessor/hash-using-directive-cpp.md) 指令在其中搜索源代码中所引用的程序集和模块（元数据）文件的目录。  对应于 **LIBPATH** 环境变量。  
  
 **库目录**  
 在其中搜索库 \(.lib\) 文件的目录；其中包括运行库。  对应于 **LIB** 环境变量。  该设置不适用于 .obj 文件；若要链接到 .obj 文件，请在[“链接器”](../ide/linker-property-pages.md)\-\>**“常规”**属性页中，选择**“其他库依赖项”**，然后指定文件的相对路径。  
  
 **源目录**  
 在其中搜索用于 IntelliSense 的源文件的目录。  
  
 **排除目录**  
 检查生成依赖项时不搜索的目录。  
  
#### 指定或修改目录设置  
  
1.  在**“解决方案资源管理器”**中，打开要更改的项目的快捷菜单，然后选择**“属性”**。  
  
2.  在**“属性页”**对话框的左窗格中，展开**“配置属性”**，然后选择**“VC\+\+ 目录”**。  
  
3.  若要修改一个目录列表，请选择它，再选择右侧的向下箭头按钮，然后选择**“编辑”**。  
  
     在显示的对话框中的框内，你可以添加或删除值，并可以重新排列值的显示顺序。  你还可以通过选中或清除**“从父级或项目默认设置继承”**，更改项目是否继承任何设置。  
  
## 共享设置  
 你可以与其他用户或在多台计算机上共享项目属性。  有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
## 请参阅  
 [使用项目属性](../ide/working-with-project-properties.md)