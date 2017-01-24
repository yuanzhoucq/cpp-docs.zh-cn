---
title: "使用 C 和 Win32 进行多线程编程 | Microsoft Docs"
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
  - "多线程处理 [C++], C 和 Win32"
  - "线程处理 [C]"
  - "线程处理 [C++], C 和 Win32"
  - "Visual C, 多线程处理"
  - "Win32 [C++], 多线程处理"
  - "Win32 应用程序 [C++], 多线程处理"
  - "Windows API [C++], 多线程处理"
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C 和 Win32 进行多线程编程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ 支持在 Microsoft Windows（Windows XP、Windows 2000、Windows NT、Windows Me 和 Windows 98）下创建多线程应用程序。  如果您的应用程序需要管理多个活动（如同时进行键盘和鼠标输入），则您应当考虑使用多线程。  一个线程可以处理键盘输入，而另一个线程可以筛选鼠标活动。  第三个线程可以根据鼠标和键盘线程的数据更新显示屏幕。  同时，其他线程可以访问磁盘文件或从通信端口获取数据。  
  
 使用 Visual C\+\+ 的多线程编程有两种方式：使用 Microsoft 基础类库 \(MFC\)，或使用 C 运行库和 Win32 API。  有关使用 MFC 创建多线程应用程序的信息，请先阅读以下使用 C 进行多线程处理的主题，再参见[使用 C\+\+ 和 MFC 进行多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
 这些主题介绍 Visual C\+\+ 中支持创建多线程程序的功能。  
  
## 您想进一步了解什么？  
  
-   [关于多线程处理](../parallel/multithread-programs.md)  
  
-   [多线程处理的库支持](../parallel/library-support-for-multithreading.md)  
  
-   [包含用于多线程处理的文件](../parallel/include-files-for-multithreading.md)  
  
-   [线程控制的 C 运行库函数](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [C 语言示例多线程程序](../parallel/sample-multithread-c-program.md)  
  
-   [编写多线程 Win32 程序](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [编译和链接多线程程序](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [避免多线程程序易出现的问题](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [线程本地存储 \(TLS\)](../parallel/thread-local-storage-tls.md)  
  
## 请参阅  
 [针对旧代码的多线程支持 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)