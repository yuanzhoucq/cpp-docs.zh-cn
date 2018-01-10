---
title: "如何： 为生成文件项目启用 IntelliSense |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCNMakeTool.IntelliSense
dev_langs: C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fae3ec35259250f71ad672d9468b991033608ae4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>如何：对生成文件项目启用 IntelliSense
IntelliSense 无法正常工作，某些项目设置或编译器选项时，在 Visual c + + 生成文件项目 IDE 操作的设置不正确。 使用此过程来配置 Visual c + + 生成文件项目，以便在生成文件项目都在 Visual Studio 开发环境中打开时，IntelliSense 可用。  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>若要在 IDE 中生成文件项目启用 IntelliSense  
  
1.  打开**属性页**对话框。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  选择**NMake**属性页上，然后修改属性下的**IntelliSense**根据。  
  
    -   设置**预处理器定义**属性以定义你的生成文件项目中任何预处理器符号。 请参阅[/D （预处理器定义）](../build/reference/d-preprocessor-definitions.md)，有关详细信息。  
  
    -   设置**包含搜索路径**属性指定的编译器将搜索以解析传递给生成文件项目中的预处理器指令的文件引用的目录列表。 请参阅[/I （附加包含目录）](../build/reference/i-additional-include-directories.md)，有关详细信息。  
  
         对于使用 CL 生成的项目。从命令窗口中，EXE 设置**包括**环境变量指定编译器将搜索以解析传递给生成文件项目中的预处理器指令的文件引用的目录。  
  
    -   设置**强制包含**属性来指定在生成你的生成文件项目时要处理的头文件。 请参阅[/FI （命名强制包含文件）](../build/reference/fi-name-forced-include-file.md)，有关详细信息。  
  
    -   设置**程序集搜索路径**属性指定的编译器将搜索以解析对你的项目中的.NET 程序集引用的目录列表。 请参阅[/AI （指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)，有关详细信息。  
  
    -   设置**强制使用程序集**属性来指定在生成生成文件项目时要处理的.NET 程序集。 请参阅[/FU (命名强制 #using 文件)](../build/reference/fu-name-forced-hash-using-file.md)，有关详细信息。  
  
    -   设置**其他选项**属性指定其他编译器开关分析 c + + 文件时要使用 intellisense。  
  
4.  单击**确定**关闭属性页。  
  
5.  使用**保存所有**命令可保存已修改的项目的设置。  
  
 下一次你打开你的生成文件项目在 Visual Studio 开发环境中，运行**清理解决方案**命令，然后**生成解决方案**命令生成文件项目。 IntelliSense 会在 IDE 中正常工作。  
  
## <a name="see-also"></a>请参阅  
 [使用 IntelliSense](/visualstudio/ide/using-intellisense)   
 [NMAKE 参考](../build/nmake-reference.md)   
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)