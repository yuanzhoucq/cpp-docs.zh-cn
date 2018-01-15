---
title: "多线程处理使用 C 和 Win32 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30c7833a4df80669b6223f1fe6b1ccceed0257cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-win32"></a>使用 C 和 Win32 进行多线程编程
Microsoft Visual c + + 用于与 Microsoft Windows 一起创建多线程应用程序提供支持： Windows XP、 Windows 2000、 Windows NT、 Windows Me，和 Windows 98。 你应考虑使用多个线程，如果你的应用程序需要管理多个活动，如同时键盘和鼠标输入。 一个线程可以处理键盘输入，而第二个线程筛选鼠标活动。 第三个线程可以更新显示屏幕基于数据的鼠标和键盘线程。 同时，其他线程可以访问磁盘文件或从通信端口中获取数据。  
  
 使用 Visual c + + 中，有两个程序与多个线程的方法： 使用 Microsoft 基础类 (MFC) 库或 C 运行时库和 Win32 API。 有关使用 MFC 创建多线程应用程序的信息，请参阅[与 c + + 和 MFC 的多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)之后读取以下有关 C 中的多线程处理的主题  
  
 这些主题说明了支持创建多线程程序中 Visual c + + 的功能。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [什么多线程处理即将](../parallel/multithread-programs.md)  
  
-   [库支持多线程处理](../parallel/library-support-for-multithreading.md)  
  
-   [包含文件中的多线程处理](../parallel/include-files-for-multithreading.md)  
  
-   [线程控制的 C 运行时库函数](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [示例在 C 中的多线程程序](../parallel/sample-multithread-c-program.md)  
  
-   [编写多线程 Win32 程序](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [编译和链接多线程程序](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [避免与多线程程序问题](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [线程本地存储区 (TLS)](../parallel/thread-local-storage-tls.md)  
  
## <a name="see-also"></a>请参阅  
 [针对旧代码的多线程支持 (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)