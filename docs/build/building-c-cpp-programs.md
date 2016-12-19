---
title: "生成 C/C++ 程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vcbuilding"
  - "buildingaprogramVC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "builds [C++]"
  - "builds [C++], 选项"
  - "项目 [C++], 生成"
  - "Visual C++ 项目, 生成"
  - "Visual C++, build options"
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成 C/C++ 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以在 Visual Studio 中或命令行上生成 Visual C\+\+ 项目。  Visual Studio IDE 使用 [MSBuild](../build/msbuild-visual-cpp.md) 来构建项目和解决方案。  可以在命令行使用 C\/C\+\+ 编译器 \(cl.exe\) 和链接器 \(link.exe\) 来生成简单项目。  若要在命令行上生成更复杂的项目，你可以使用 MSBuild 或 [NMAKE](../build/nmake-reference.md)。  若要获得如何使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 生成项目和解决方案的相关概述，请参阅[在 Visual Studio 中构建应用程序](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)。  
  
## 本节内容  
 [在 Visual Studio 中生成 C\+\+ 项目](../ide/building-cpp-projects-in-visual-studio.md)  
 讨论如何使用 Visual Studio IDE 来生成 C\/C\+\+ 项目。  
  
 [在命令行上生成](../build/building-on-the-command-line.md)  
 讨论如何使用 C\/C\+\+ 命令行编译器和 Visual Studio 中所包含的生成工具。  
  
 [生成 C\/C\+\+ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
 描述了适用于 Windows 桌面应用程序的部署模型，这一模型的理论基础是独立应用程序和并行程序集。  
  
 [C\/C\+\+ 生成参考](../build/reference/c-cpp-building-reference.md)  
 提供指向有关使用 C\+\+ 生成程序、编译器和链接器选项以及各种生成工具的参考文章的链接。  
  
 [配置 64 位的程序](../build/configuring-programs-for-64-bit-visual-cpp.md)  
 介绍如何将 Visual Studio 和命令行配置为使用 64 位工具集以及如何面向 64 位体系结构，还讨论了在将代码移到 64 位体系结构时常见的迁移问题。  
  
 [配置 ARM 处理器的程序](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
 描述了 ARM 处理器使用的约定，并讨论了在代码移动到 ARM 体系结构时常见的迁移问题。  
  
 [配置适用于 Windows XP 的 C\+\+ 11 程序](../build/configuring-programs-for-windows-xp.md)  
 描述如何将平台工具集设置为面向 Windows XP 开发。  
  
## 相关章节  
 [NIB: Samples Included in Visual C\+\+](http://msdn.microsoft.com/zh-cn/c9ec56b3-2bbd-49b4-8a4c-9ed4b78b7a84)  
 提供一些代码示例链接，这些示例演示 Visual C\+\+ 的功能以及它支持的库和技术。  
  
 [在 Visual Studio 中构建应用程序](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 介绍 Visual Studio 生成系统和工具。