---
title: "使用 DLL 的优点 | Microsoft Docs"
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
  - "DLL [C++], 优点"
  - "动态链接 [C++]"
  - "动态加载链接 [C++]"
  - "链接 [C++], 动态与静态"
  - "链接 [C++], 动态与静态"
ms.assetid: 8956c8ee-e7b3-446f-a0c6-462381747690
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 DLL 的优点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

动态链接具有下列优点：  
  
-   节省内存和减少交换操作。  很多进程可以同时使用一个 DLL，在内存中共享该 DLL 的一个副本。  相反，对于每个用静态链接库生成的应用程序，Windows 必须在内存中加载库代码的一个副本。  
  
-   节省磁盘空间。  许多应用程序可在磁盘上共享 DLL 的一个副本。  相反，每个用静态链接库生成的应用程序均具有作为单独的副本链接到其可执行图像中的库代码。  
  
-   升级到 DLL 更为容易。  当 DLL 中的函数发生更改时，只要函数的参数和返回值没有更改，就不需重新编译或重新链接使用它们的应用程序。  相反，静态链接的对象代码要求在函数更改时重新链接应用程序。  
  
-   提供售后支持。  例如，可修改显示器驱动程序 DLL 以支持当初交付应用程序时不可用的显示器。  
  
-   支持多语言程序。  只要程序遵循函数的调用约定，用不同编程语言编写的程序就可以调用相同的 DLL 函数。  程序与 DLL 函数在下列方面必须是兼容的：函数期望其参数被推送到堆栈上的顺序，是函数还是应用程序负责清理堆栈，以及寄存器中是否传递了任何参数。  
  
-   提供了扩展 MFC 库类的机制。  可以从现有 MFC 类派生类，并将它们放到 MFC 扩展 DLL 中供 MFC 应用程序使用。  
  
-   使国际版本的创建轻松完成。  通过将资源放到 DLL 中，创建应用程序的国际版本变得容易得多。  可将用于应用程序的每个语言版本的字符串放到单独的 DLL 资源文件中，并使不同的语言版本加载合适的资源。  
  
 使用 DLL 的一个潜在缺点是应用程序不是独立的；它取决于是否存在单独的 DLL 模块。  
  
## 你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)