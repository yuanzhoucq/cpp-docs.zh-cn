---
title: "Windows 用来定位 DLL 的搜索路径 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], Windows 搜索路径"
  - "查找 DLL"
  - "已知 DLL 搜索 [C++]"
  - "查找 DLL"
  - "搜索路径 [C++]"
  - "搜索 [C++], DLL"
  - "Windows [C++], DLL 搜索路径"
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows 用来定位 DLL 的搜索路径
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过隐式和显式链接，Windows 首先搜索“已知 DLL”，如 Kernel32.dll 和 User32.dll。  Windows 然后按下列顺序搜索 DLL：  
  
1.  当前进程的可执行模块所在的目录。  
  
2.  当前目录。  
  
3.  Windows 系统目录。  **GetSystemDirectory** 函数检索此目录的路径。  
  
4.  Windows 目录。  **GetWindowsDirectory** 函数检索此目录的路径。  
  
5.  PATH 环境变量中列出的目录。  
  
    > [!NOTE]
    >  未使用 LIBPATH 环境变量。  
  
## 你希望做什么？  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [显式链接](../build/linking-explicitly.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)