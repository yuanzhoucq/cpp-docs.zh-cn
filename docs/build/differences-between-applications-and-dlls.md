---
title: "应用程序和 DLL 之间的区别 | Microsoft Docs"
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
  - "应用程序 [C++], 与 DLL"
  - "DLL [C++], 与应用程序"
  - "可执行文件 [C++], DLL 与应用程序"
ms.assetid: 8f271523-d8d0-4ad1-84d2-0c5645d7fd5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 应用程序和 DLL 之间的区别
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尽管 DLL 和应用程序都是可执行的程序模块，但它们之间有若干不同之处。  对于最终用户来说，最明显的差异在于 DLL 不是可直接执行的程序。  从系统角度讲，应用程序和 DLL 之间有两个基本差异：  
  
-   应用程序可有多个同时在系统上运行的实例，而 DLL 只能有一个实例。  
  
-   应用程序可以拥有堆栈、共用内存、文件句柄、消息队列这样的事物，而 DLL 不能。  
  
## 你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [使用 DLL 的好处](../build/advantages-of-using-dlls.md)  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)