---
title: "本机和 .NET 的互操作性 | Microsoft Docs"
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
  - ".NET Framework [C++], 与 Visual C++ 的互操作性"
  - "互操作 [C++]"
  - "互操作 [C++], 关于 .NET 互操作性"
  - "互操作性 [C++]"
  - "互操作性 [C++], 关于 .NET 互操作性"
  - "托管代码 [C++], 互操作性"
  - "MFC [C++], .NET 集成"
  - "本机代码 [C++]"
  - "本机代码 [C++], .NET 互操作性"
  - "托管代码互操作性 [C++]"
  - "Visual C++, 互操作性"
ms.assetid: f3ec6c99-c745-4256-b95b-f1d12ba17a5a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 本机和 .NET 的互操作性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支持互操作性功能，允许托管和非托管构造在同一程序集内甚至同一文件中共存和交互操作。  其他 .NET 语言也支持此功能的一个小的子集（如 P\/Invoke），但是由 Visual C\+\+ 提供的大多数互操作性支持在其他语言中是不可用的。  
  
## 本节内容  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)  
 介绍使用包含托管和非托管功能的 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项生成的程序集。  
  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)  
 讨论如何使用 MFC Windows 窗体支持类以承载 MFC 应用程序内的 Windows 窗体控件。  
  
 [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)  
 介绍在 .NET 应用程序中使用非 CLR DLL 的方式。  
  
## 请参阅  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-cn/0822f806-fa81-4b65-bf0f-1e2921f30c95)