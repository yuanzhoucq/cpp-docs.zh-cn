---
title: "如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 部分受信任的应用程序"
  - "互操作 [C++], 部分受信任的应用程序"
  - "互操作性 [C++], 部分受信任的应用程序"
  - "混合程序集 [C++], 部分受信任的应用程序"
  - "msvcm90[d].dll"
  - "部分受信任的应用程序 [C++]"
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论如何通过使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 移除 msvcm90.dll 上的依赖项来创建部分受信任的公共语言运行时应用程序。  
  
 用 **\/clr** 生成的 Visual C\+\+ 应用程序将在 msvcm90.dll（它是 C 运行库的一部分）上具有依赖项。  当希望您的应用程序在部分信任的环境中使用时，CLR 将强制对您的 DLL 实施特定的代码访问安全规则。  因此，移除此依赖项是必需的，因为 msvcm90.dll 包含本机代码，并且无法在其上强制实现代码访问安全策略。  
  
 如果您的应用程序不使用 C 运行库的任何功能，并且希望从您的代码中移除此库上的依赖项，则将必须使用 **\/NODEFAULTLIB:msvcmrt.lib** 链接器选项，并且使用 ptrustm.lib 或 ptrustmd.lib 进行链接。  这些库包含用于初始化和非初始化应用程序的对象文件、初始化代码所使用的异常类以及托管异常处理代码。  在这些库之一中进行链接将移除 msvcm90.dll. 上的任何依赖项。  
  
> [!NOTE]
>  对于使用 ptrust 库的应用程序，程序集非初始化的顺序可能有所不同。  对于普通的应用程序，通常情况下程序集的卸载顺序与其加载顺序相反，但不总是这样。  对于部分信任的应用程序，通常情况下程序集的卸载顺序与其加载顺序相同。  但也不总是这样。  
  
### 创建部分信任的混合 \(\/clr\) 应用程序  
  
1.  若要移除 msvcm90.dll, 上的依赖项，必须通过使用 **\/NODEFAULTLIB:msvcmrt.lib** 链接器选项指定链接器不要包含此库。  有关如何使用 Visual Studio 开发环境或编程方法完成此操作的信息，请参见 [\/NODEFAULTLIB（忽略库）](../build/reference/nodefaultlib-ignore-libraries.md)。  
  
2.  将 ptrustm 库之一添加到链接器输入依赖项。  如果正在发布模式下生成应用程序，请使用 ptrustm.lib。  对于调试模式，请使用 ptrustmd.lib。  有关如何使用 Visual Studio 开发环境或编程方法完成此操作的信息，请参见 [用作链接器输入的 .Lib 文件](../build/reference/dot-lib-files-as-linker-input.md)。  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)   
 [混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)   
 [混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)   
 [\/link（将选项传递到链接器）](../build/reference/link-pass-options-to-linker.md)   
 [PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/zh-cn/bd61be84-c143-409a-a75a-44253724f784)