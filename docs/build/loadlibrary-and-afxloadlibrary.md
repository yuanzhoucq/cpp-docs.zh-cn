---
title: "LoadLibrary 和 AfxLoadLibrary | Microsoft Docs"
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
  - "LoadLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxLoadLibrary 方法"
  - "DLL [C++], AfxLoadLibrary"
  - "DLL [C++], LoadLibrary"
  - "显式链接 [C++]"
  - "LoadLibrary 方法"
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LoadLibrary 和 AfxLoadLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

进程调用 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)（或 [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)）以显式链接到 DLL。  如果函数执行成功，它会将指定的 DLL 映射到调用进程的地址空间中并返回该 DLL 的句柄。此句柄可以与其他函数（如 `GetProcAddress` 和 `FreeLibrary`）一起在显式链接中使用。  
  
 `LoadLibrary` 将尝试使用用于隐式链接的相同搜索序列来查找 DLL。  如果系统无法找到所需的 DLL 或者入口点函数返回 FALSE，则 `LoadLibrary` 将返回 NULL。  如果对 `LoadLibrary` 的调用所指定的 DLL 模块已映射到调用进程的地址空间中，则该函数将返回该 DLL 的句柄并递增模块的引用数。  
  
 如果 DLL 具有入口点函数，则操作系统将在调用 `LoadLibrary` 的线程的上下文中调用此函数。  如果由于以前调用了 `LoadLibrary`，但没有相应地调用 `FreeLibrary` 函数，从而导致已经将 DLL 附加到进程，则不会调用此入口点函数。  
  
 对于加载扩展 DLL 的 MFC 应用程序，建议使用 `AfxLoadLibrary`，而不使用 `LoadLibrary`。  在调用 `LoadLibrary` 之前，`AfxLoadLibrary` 处理线程同步。  `AfxLoadLibrary` 的接口（函数原型）与 `LoadLibrary` 相同。  
  
 如果 Windows 无法加载 DLL，则进程会尝试从错误中恢复。  例如，进程会通知用户所发生的错误，并要求用户指定 DLL 的其他路径。  
  
> [!IMPORTANT]
>  如果代码要在 Windows NT 4、Windows 2000 或 Windows XP（SP1 以前的版本）下运行，则请确保为所有 DLL 指定完整路径。  在这些操作系统中，加载文件时会首先搜索当前目录。  如果没有限定文件的路径，则可能会加载不需要的文件。  
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 您想进一步了解什么？  
  
-   [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../Topic/AfxLoadLibrary.md)