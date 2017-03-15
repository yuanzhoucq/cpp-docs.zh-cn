---
title: "链接器的延迟加载 DLL 支持 | Microsoft Docs"
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
  - "DLL 的延迟加载, 链接器支持"
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 链接器的延迟加载 DLL 支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 链接器现在支持 DLL 的延迟加载。  这使您不必再用 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 函数 **LoadLibrary** 和 **GetProcAddress** 来实现 DLL 延迟加载。  
  
 在 Visual C\+\+ 6.0 版之前，在运行时加载 DLL 的唯一办法是使用 **LoadLibrary** 和 **GetProcAddress** 函数；当使用操作系统的可执行文件或 DLL 被加载之后，操作系统才加载 DLL。  
  
 从 Visual C\+\+ 6.0 开始，与 DLL 静态链接时，链接器提供了一些选项，将 DLL 的加载延迟到程序调用该 DLL 中的函数时才进行。  
  
 应用程序可以使用具有 Helper 函数的 [\/DELAYLOAD（延迟加载导入）](../../build/reference/delayload-delay-load-import.md)链接器选项延迟加载 DLL（Visual C\+\+ 提供的默认实现）。  Helper 函数将在运行时通过调用 **LoadLibrary** 和 **GetProcAddress** 为您加载 DLL。  
  
 在下列情况下，应考虑延迟加载 DLL：  
  
-   程序可能不调用 DLL 中的函数。  
  
-   可能直到程序执行后期才调用 DLL 中的函数。  
  
 可在 .EXE 或 .DLL 项目生成过程中指定延迟加载 DLL。  延迟加载一个或多个 DLL 的 DLL 项目本身不应调用 Dllmain 中的延迟加载入口点。  
  
 下列主题描述延迟加载 DLL：  
  
-   [指定要延迟加载的 DLL](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [显式卸载延迟加载的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [加载被延迟加载的 DLL 的所有导入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [绑定导入](../../build/reference/binding-imports.md)  
  
-   [错误处理和通知](../../build/reference/error-handling-and-notification.md)  
  
-   [转储延迟加载的导入](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [延迟加载 DLL 的约束](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [了解 Helper 函数](http://msdn.microsoft.com/zh-cn/6279c12c-d908-4967-b0b3-cabfc3e91d3d)  
  
-   [开发您自己的 Helper 函数](../../build/reference/developing-your-own-helper-function.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)   
 [链接](../../build/reference/linking.md)