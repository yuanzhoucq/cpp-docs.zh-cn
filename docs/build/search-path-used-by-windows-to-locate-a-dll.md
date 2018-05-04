---
title: 搜索 Windows 用来定位 DLL 的路径 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 166b5fccf6dd231029f79fede837909a49e7fc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="search-path-used-by-windows-to-locate-a-dll"></a>Windows 用来定位 DLL 的搜索路径
隐式和显式链接下，Windows 先搜索"已知 Dll"，如 Kernel32.dll 和 User32.dll。 按以下顺序 dll 会搜索 Windows:  
  
1.  当前进程的可执行模块所在的目录。  
  
2.  当前目录中。  
  
3.  Windows 系统目录。 **GetSystemDirectory**函数将检索此目录的路径。  
  
4.  Windows 目录中。 **GetWindowsDirectory**函数将检索此目录的路径。  
  
5.  在 PATH 环境变量中列出的目录中。  
  
    > [!NOTE]
    >  不使用 LIBPATH 环境变量。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [如何将隐式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [如何显式链接到 DLL](../build/linking-an-executable-to-a-dll.md#linking-explicitly)  
  
-   [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)