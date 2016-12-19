---
title: "“从现有代码文件创建新项目”向导 -&gt;“指定项目设置” | Microsoft Docs"
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
  - "vc.appwiz.importwiz.appsettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“从现有代码文件创建新项目”向导，项目设置"
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “从现有代码文件创建新项目”向导 -&gt;“指定项目设置”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用“从现有代码文件创建新项目”向导的此页可以指定：  
  
-   新项目的生成环境  
  
-   与要生成的特定类型的新项目相匹配的生成设置  
  
## 任务列表  
 [如何：通过现有代码创建 C\+\+ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## UIElement 列表  
 **使用 Visual Studio**  
 指定使用 Visual Studio 中包含的生成工具生成新项目。  默认情况下此选项处于选中状态。  
  
 **项目类型**  
 指定向导将生成的项目类型。  
  
 **Windows 应用程序项目**  
 指示向导将为可执行的 Windows 应用程序生成一个项目。  此选项可从**“项目类型”**下拉列表框中获得。  
  
 **控制台应用程序项目**  
 指示向导将为控制台应用程序生成一个项目。  此选项可从**“项目类型”**下拉列表框中获得。  
  
 **动态链接库\(DLL\)项目**  
 指示向导将为空动态链接库应用程序生成一个项目。  此选项可从**“项目类型”**下拉列表框中获得。  
  
 **静态库\(LIB\)项目**  
 指示向导将为静态库应用程序生成一个项目。  此选项可从**“项目类型”**下拉列表框中获得。  
  
 **添加对 ATL 的支持**  
 向新项目中添加 ATL 支持。  
  
 **添加对 MFC 的支持**  
 向新项目中添加 MFC 支持。  
  
 **添加对公共语言运行时的支持**  
 向新项目中添加 CLR 编程支持。  
  
 **公共语言运行时**  
 指定新项目要与 CLR 功能兼容。  
  
 **公共语言运行时（旧语法）**  
 指定要符合 C\+\+ 托管扩展语法（在 Visual C\+\+ 2005 之前为 CLR 编程语法）的新项目。  
  
 **使用外部生成系统**  
 指定使用未包含在 Visual Studio 中的生成工具生成新项目。  选择此选项时，可以在**“指定调试配置设置”**和**“指定发布配置设置”**页上指定生成命令行。  
  
> [!NOTE]
>  选中**“使用外部生成系统”**选项时，IDE 不会生成新项目，因此编译时不需要 \/D、\/I、\/FI、\/AI 或 \/FU 选项。  但是，为使 IntelliSense 能够正常工作，必须正确设置这些选项。  
  
## 请参阅  
 [“从现有代码文件创建新项目”向导 \-\>“指定调试配置设置”](../ide/specify-debug-configuration-settings.md)   
 [“从现有代码文件创建新项目”向导 \-\>“指定发布配置设置”](../ide/specify-release-configuration.md)