---
title: "在以前版本的运行时上运行 C++ /clr 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "app.config 文件, 指定的运行时版本"
  - "应用程序部署 [C++], 指定的运行时版本"
  - "应用程序 [C++], 指定的运行时版本"
  - "向后兼容性 [C++], 指定的运行时版本"
  - "公共语言运行时 [C++], 指定的版本"
  - "兼容性 [C++], 指定的运行时版本"
  - "部署应用程序 [C++], 指定的运行时版本"
  - "版本 [C++]"
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在以前版本的运行时上运行 C++ /clr 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除非另行说明，否则 Visual C\+\+ .NET framework 应用程序在编译器用于生成应用程序的公共语言运行时 \(CLR\) 版本生成运行。  但是，为某个版本的运行时在其他版本中生成运行提供了所需功能的 .exe 应用程序是可能的。  
  
 为此，请提供在 `supportedRuntime` 标记包含运行时版本信息的一个 app.config 文件。  
  
 运行时，app.config 文件必须具有以下形式 *filename.ext*.config 的名称，其中 *filename.ext* 是启动应用程序的可执行文件的名称，因此，它必须在与可执行文件相同。  例如，因此，如果您的应用程序名为 TestApp.exe，app.config 文件将命名为 TestApp.exe.config。  
  
 如果指定了多个运行时版本和应用程序在具有多个安装的运行时版本的计算机上运行，应用程序使用在设置文件指定以及安装的第一个版本。  
  
 有关更多信息，请参见[How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/zh-cn/5247b307-89ca-417b-8dd0-e8f9bd2f4717)。  
  
 若要在 CLR 版本 1.0 或 1.1 版中运行，由 Visual C\+\+ 编译器生成的应用程序必须使用 [\/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md)生成。  
  
## 请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)