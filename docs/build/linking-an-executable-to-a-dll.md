---
title: "将可执行文件链接到 DLL | Microsoft Docs"
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
  - "DLL [C++], 链接"
  - "动态加载链接 [C++]"
  - "可执行文件 [C++], 链接到 DLL"
  - "显式链接 [C++]"
  - "隐式链接 [C++]"
  - "链接 [C++], DLL"
  - "加载 DLL [C++]"
  - "运行时 [C++], 链接"
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 将可执行文件链接到 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可执行文件以下列两种方式之一链接到（或加载）DLL：  
  
-   [隐式链接](../build/linking-implicitly.md)  
  
-   [显式链接](../build/linking-explicitly.md)  
  
 隐式链接有时称为静态加载或加载时动态链接。  显式链接有时称为动态加载或运行时动态链接。  
  
 在隐式链接下，使用 DLL 的可执行文件链接到该 DLL 的创建者所提供的导入库（.lib 文件）。  使用 DLL 的可执行文件加载时，操作系统加载此 DLL。  客户端可执行文件调用 DLL 的导出函数，就好像这些函数包含在可执行文件内一样。  
  
 在显式链接下，使用 DLL 的可执行文件必须进行函数调用以显式加载和卸载该 DLL，并访问该 DLL 的导出函数。  客户端可执行文件必须通过函数指针调用导出函数。  
  
 可执行文件对两种链接方法可以使用同一个 DLL。  另外，由于一个可执行文件可隐式链接到某个 DLL，而另一个可显式附加到此 DLL，故这些机制不是互斥的。  
  
## 您想进一步了解什么？  
  
-   [处理导入库和导出文件](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [确定要使用的链接方法](../build/determining-which-linking-method-to-use.md)  
  
-   [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)