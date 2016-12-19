---
title: "如何：对生成文件项目启用 IntelliSense | Microsoft Docs"
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
  - "VC.Project.VCNMakeTool.IntelliSense"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntelliSense, 生成文件项目"
  - "生成文件项目, IntelliSense"
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：对生成文件项目启用 IntelliSense
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于 Visual C\+\+ 生成文件项目来说，如果某些项目设置或编译器选项设置得不正确，IntelliSense 便无法在 IDE 中工作。  使用此过程对 Visual C\+\+ 生成文件项目进行配置，这样，当生成文件项目在 Visual Studio 开发环境中打开时，IntelliSense 便可以工作。  
  
### 在 IDE 中为生成文件项目启用 IntelliSense  
  
1.  打开**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  选择**“NMake”**属性页，然后对**“IntelliSense”**下的属性进行相应的修改。  
  
    -   设置**“预处理器定义”**属性，以定义生成文件项目中的任何预处理器符号。  有关更多信息，请参见 [\/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)。  
  
    -   设置**“包括搜索路径”**属性以指定目录列表，编译器将在您的生成文件项目中搜索这些目录，以解析传递给预处理器指令的文件引用。  有关更多信息，请参见 [\/I（附加包含目录）](../build/reference/i-additional-include-directories.md)。  
  
         对于从命令窗口使用 CL.EXE 生成的项目，设置**“INCLUDE”**环境变量以指定目录，编译器将在您的生成文件项目中搜索这些目录，以解析传递给预处理器指令的文件引用。  
  
    -   设置**“强制包含”**属性，以指定在生成您的生成文件项目时要处理的头文件。  有关更多信息，请参见 [\/FI（命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)。  
  
    -   设置**“程序集搜索路径”**属性以指定目录列表，编译器将在您的项目中搜索这些目录，以解析对 .NET 程序集的引用。  有关更多信息，请参见 [\/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。  
  
    -   设置**“强制使用程序集”**属性，以指定在生成您的生成文件项目时要处理哪些 .NET 程序集。  有关更多信息，请参见 [\/FU（命名强制 \#using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。  
  
    -   设置**“其他选项”**属性以指定在分析 C\+\+ 文件时将由 Intellisense 使用的其他编译器开关。  
  
4.  单击**“确定”**关闭属性页。  
  
5.  使用**“全部保存”**命令保存修改后的项目设置。  
  
 下次在 Visual Studio 开发环境中打开生成文件项目时，对该项目运行**“清理解决方案”**命令，再运行**“生成解决方案”**命令。  IntelliSense 在 IDE 中就应能正常工作了。  
  
## 请参阅  
 [使用 IntelliSense](../Topic/Using%20IntelliSense.md)   
 [NMAKE 参考](../build/nmake-reference.md)   
 [如何：通过现有代码创建 C\+\+ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)