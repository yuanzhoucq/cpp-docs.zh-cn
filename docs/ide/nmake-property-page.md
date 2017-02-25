---
title: "“Nmake”属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.ReBuildCommandLine"
  - "VC.Project.VCNMakeTool.CleanCommandLine"
  - "VC.Project.VCNMakeTool.Output"
  - "VC.Project.VCNMakeTool.BuildCommandLine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“NMake”属性页"
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# “Nmake”属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**“NMake”**属性页使您能够为 NMake 项目指定生成设置。  
  
 有关 NMake 项目的更多信息，请参见[创建生成文件项目](../ide/creating-a-makefile-project.md)。  
  
 **“NMake”**属性页包含下列属性。  
  
## UIElement 列表  
 **生成命令行**  
 指定在**“生成”**菜单中单击**“生成”**时运行的命令。  
  
 **“全部重新生成”命令行**  
 指定在**“生成”**菜单中单击**“全部重新生成”**时运行的命令。  
  
 **“清除”命令行**  
 指定在**“生成”**菜单中单击**“清理”**时运行的命令。  
  
 **Output**  
 指定将包含命令行输出的文件名。  默认情况下，此文件名基于项目名。  
  
 **预处理器定义**  
 指定源文件使用的任何预处理器定义。  默认值由当前平台和配置决定。  
  
 **包含搜索路径**  
 指定编译器搜索包含文件的目录。  
  
 **强制包含**  
 指定预处理器自动处理的文件，即使这些文件不包括在项目文件中。  
  
 **程序集搜索路径**  
 当尝试解析 .NET 程序集时，指定 .NET Framework 要搜索的目录。  
  
 **强制使用程序集**  
 指定 .NET Framework 自动处理的程序集。  
  
 **附加选项**  
 当 IntelliSense 分析 C\+\+ 文件时，指定任何其他的编辑器开关供其使用。  
  
 有关如何访问**“NMake”**属性页的信息，请参见[如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
 有关如何以编程方式访问此对象的成员的信息，请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。  
  
## 请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)   
 [如何：对生成文件项目启用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)