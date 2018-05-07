---
title: NMake 属性页 (Windows c + +) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs:
- C++
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f156d69467f00c4c4a62ec84d3b870e2999d7115
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-property-page"></a>“NMake”属性页
**NMake**属性页可以指定 NMake 项目的生成设置。  
  
 有关 NMake 项目的详细信息，请参阅[创建生成文件项目](../ide/creating-a-makefile-project.md)。 Non_Windows 生成文件项目，请参阅[生成文件项目属性 （Linux c + +）](../linux/prop-pages/makefile-linux.md)，[常规项目属性 （Android c + + 生成文件）](/visualstudio/cross-platform/general-makefile-android-prop-page)或[NMake 属性 （Android c + +）](/visualstudio/cross-platform/nmake-android-prop-page).
  
 **NMake**属性页包含以下属性。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **生成命令行**  
 指定要运行时的命令**生成**上单击**生成**菜单。  
  
 **重新生成所有命令行**  
 指定要运行时的命令**全部重新生成**上单击**生成**菜单。  
  
 **清除命令行**  
 指定要运行时的命令**清理**上单击**生成**菜单。  
  
 **输出**  
 指定将包含命令行的输出文件的名称。 默认情况下，此文件名基于项目名称。  
  
 **预处理器定义**  
 指定源文件使用任何预处理器定义。 默认值是由当前平台和配置确定的。  
  
 **包括搜索路径**  
 指定编译器搜索包含文件的目录。  
  
 **强制包括**  
 指定预处理器自动处理即使它们不包括在项目文件中的文件。  
  
 **程序集搜索路径**  
 指定.NET Framework 搜索时的位置的目录它尝试解决.NET 程序集。  
  
 **强制使用程序集**  
 指定.NET Framework 自动处理的程序集。  
  
 **附加选项**  
 指定 IntelliSense 分析 c + + 文件时要使用任何其他编译器开关。  
  
 有关如何访问**NMake**属性页中，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
 有关如何以编程方式访问此对象的成员的信息，请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)   
 [如何：对生成文件项目启用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)