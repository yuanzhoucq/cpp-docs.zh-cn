---
title: "Linking to the CRT in Your ATL Project | Microsoft Docs"
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
  - "DllMainCRTStartup"
  - "wWinMainCRTStartup"
  - "WinMainCRTStartup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, C Run-Time library (CRT)"
  - "CRT, linking with ATL"
  - "DllMainCRTStartup method"
  - "WinMainCRTStartup method"
  - "wWinMainCRTStartup method"
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Linking to the CRT in Your ATL Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[C运行库](../c-runtime-library/crt-library-features.md) \(crt\)提供在ATL开发过程中，可以通过编程变得更容易的许多有用的功能。  所有ATL项目链接到CRT库。  您可以查看链接在 [使用的方法的优点和权衡若要链接到CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)的方法的优点和缺点。  
  
## 链接的效果CRT到您的程序图像  
 如果使用CRT静态链接，从CRT的代码在可执行图像放置，不需要具有CRT DLL在运行您的图形系统。  如果使用CRT动态链接，在您的图像，但是，不是代码对CRT DLL的代码放置。  为了将图像可以运行在特定系统，CRT DLL必须存在该系统。  即使您使用CRT动态链接，您可能会发现一些代码可以静态链接\(例如，**DllMainCRTStartup**）。  
  
 当您链接到的图像时，您显式或隐式指定入口点操作系统将调用在加载图像之后。  为DLL，默认入口点是 **DllMainCRTStartup**。  对于EXE，它是 **WinMainCRTStartup**。  您可以重写与\/ENTRY链接器选项的默认值。  CRT为 **DllMainCRTStartup**提供的实现，**WinMainCRTStartup**和 **wWinMainCRTStartup** \(Unicode为EXE入口点）。  这些CRT提供的入口点调用全局对象的构造函数并初始化某些CRT函数使用的其他数据结构。  则，静态链接到此启动代码添加有关25K到您的图像。  如果该动态链接，大多数代码在DLL，因此，您的图像大小保持小。  
  
 有关更多信息，请参见链接器主题 [\/ENTRY \(将入口点符号\)](../build/reference/entry-entry-point-symbol.md)。  
  
## 优化选项  
 使用链接器选项\/OPT: NOWIN98能由10K进一步减少默认ATL控件，从而牺牲在Windows 98系统的增强加载时间。  有关链接选项的更多信息，请参见 [\/OPT \(优化\)](../build/reference/opt-optimizations.md)。  
  
## 请参阅  
 [使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)   
 [运行库行为](../build/run-time-library-behavior.md)