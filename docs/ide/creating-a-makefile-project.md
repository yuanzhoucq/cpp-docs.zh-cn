---
title: "创建生成文件项目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.makefile.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成文件项目, 创建"
  - "项目文件 [C++], 生成文件项目"
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 创建生成文件项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果你的项目是通过生成文件从命令行生成的，Visual Studio 开发环境将无法识别该项目。  若要使用 [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)]、[!INCLUDE[vsPro](../ide/includes/vspro_md.md)] 或 Visual Studio Express for Windows Desktop 打开并生成项目，请首先通过选择生成文件项目模板来创建空项目。  然后可以从 Visual Studio 开发环境中使用该项目生成项目。  
  
 在“解决方案资源管理器”中，项目不显示文件。  项目指定生成设置，这些设置反映在项目的属性页中。  
  
 在项目中指定的输出文件对生成脚本生成的名称无效；它仅声明意图。  
  
### 创建生成文件项目  
  
1.  按照帮助主题[用 Visual C\+\+ 应用程序向导创建项目](../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
2.  在**“新建项目”**对话框中，选择“模板”窗格中的**“生成文件项目”**以打开向导。  
  
3.  在[应用程序设置](../ide/application-settings-makefile-project-wizard.md)页中，提供命令、输出、清除和重新生成信息。  
  
4.  单击**“完成”**关闭向导并在**“解决方案资源管理器”**中打开新创建的项目。  
  
 可以在项目的属性页中查看和编辑项目的属性。  有关如何显示属性页的信息，请参阅[设置 Visual C\+\+ 项目属性](../ide/working-with-project-properties.md)。  
  
## 请参阅  
 [生成文件项目向导](../ide/makefile-project-wizard.md)   
 [生成文件中的特殊字符](../build/special-characters-in-a-makefile.md)   
 [生成文件的内容](../build/contents-of-a-makefile.md)