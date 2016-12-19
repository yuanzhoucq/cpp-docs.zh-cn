---
title: "Visual C++ 中的 DLL | Microsoft Docs"
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
  - "DLL [C++]"
  - "DLL [C++], 关于 DLL"
  - "动态链接 [C++]"
  - "可执行文件 [C++]"
  - "链接 [C++], 动态与静态"
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 中的 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

动态链接库 \(DLL\) 是作为函数和资源的共享库的可执行文件。  动态链接可使执行文件调用函数或使用存储在单独文件中的资源。  可从使用这些函数和资源的可执行文件中对其分别进行编译和部署。  操作系统可在已加载可执行文件时或在运行时按需将 DLL 加载到可执行的内存空间中。  DLL 还可以在可执行文件之间轻松共享函数和资源。  多个应用程序可同时访问内存中单个 DLL 副本的内容。  
  
 静态链接会将 .lib 文件中所有对象代码复制到可执行文件中。  动态链接仅包括在运行时用于查找和加载含有数据项或函数的 DLL 所需的信息。  在创建 DLL 时，还会创建一个包含此信息的 .lib 文件。  生成调用 DLL 的可执行文件时，链接器会使用 .lib 文件中的导出符号来为加载程序存储此信息。  当加载程序加载 DLL 时，该 DLL 会映射到你的可执行文件的内存空间中。  将调用 DLL 中的特殊函数 `DllMain` 来执行 DLL 要求的任何初始化。  
  
 使用动态链接代替静态链接有若干优点。  当使用 DLL 时，可以节省内存空间，并减少交换操作。  当多个应用程序可以使用 DLL 的单个副本时，可以节省磁盘空间和下载带宽。  DLL 可单独部署和更新，这可以使你在无需重新生成和发布所有代码的情况下，提供售后支持和软件更新。  DLL 是一种提供特定区域资源的简便方法，可以支持多语言程序，并简化创建国际版本应用程序的过程。  
  
 下列主题提供有关如何编程 DLL 的详细信息。  
  
## 本节内容  
 [演练：创建和使用动态链接库 \(C\+\+\)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 介绍如何使用 Visual Studio 创建和使用 DLL。  
  
 [应用程序和 DLL 之间的区别](../build/differences-between-applications-and-dlls.md)  
 描述应用程序和 DLL 之间的基本区别。  
  
 [使用 DLL 的优点](../build/advantages-of-using-dlls.md)  
 描述动态链接的优点。  
  
 [DLL 的类型](../build/kinds-of-dlls.md)  
 提供有关可生成的不同类型的 DLL 的信息。  
  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)  
 提供有关 DLL 的常见问题解答。  
  
 [将可执行文件链接到 DLL](../build/linking-an-executable-to-a-dll.md)  
 描述与 DLL 的显式链接和隐式链接。  
  
 [初始化 DLL](../build/initializing-a-dll.md)  
 讨论当 DLL 加载时必须执行的 DLL 初始化代码（如分配内存）。  
  
 [运行库行为](../build/run-time-library-behavior.md)  
 描述运行库如何执行 DLL 启动序列。  
  
 [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 讨论如何在运行时使用 **LoadLibrary** 和 `AfxLoadLibrary` 显式链接到 DLL。  
  
 [GetProcAddress](../build/getprocaddress.md)  
 讨论如何使用 **GetProcAddress** 获取 DLL 中导出函数的地址。  
  
 [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 讨论当不再需要 DLL 模块时如何使用 **FreeLibrary** 和 `AfxFreeLibrary`。  
  
 [Windows 用来定位 DLL 的搜索路径](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 描述 Windows 操作系统用来定位系统上的 DLL 的搜索路径。  
  
 [动态链接到 MFC 的规则 DLL 的模块状态](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 描述动态链接到 MFC 的规则 DLL 的模块状态。  
  
 [扩展 DLL](../build/extension-dlls-overview.md)  
 解释通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。  
  
 [创建纯资源 DLL](../build/creating-a-resource-only-dll.md)  
 讨论只包含资源（如图标、位图、字符串和对话框等）的纯资源 DLL。  
  
 [MFC 应用程序中已本地化的资源：附属 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。  
  
 [导入和导出](../build/importing-and-exporting.md)  
 描述如何将公共符号导入应用程序或从 DLL 导出函数。  
  
 [Active 技术和 DLL](../build/active-technology-and-dlls.md)  
 使对象服务器得以在 DLL 内实现。  
  
 [DLL 中的自动化](../build/automation-in-a-dll.md)  
 描述“MFC DLL 向导”中的“自动化”选项提供的内容。  
  
 [MFC DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md)  
 讨论 MFC 中包含的 DLL 和库如何遵循结构化命名约定。  
  
 [从 Visual Basic 应用程序调用 DLL 函数](../build/calling-dll-functions-from-visual-basic-applications.md)  
 描述如何从 Visual Basic 应用程序中调用 DLL 函数。  
  
## 相关章节  
 [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 描述使你可以将 MFC 库作为 Windows 动态链接库的一部分来使用的规则 DLL。  
  
 [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
 描述如何将 MFCxx.dll 和 MFCxxD.dll（其中 x 是 MFC 版本号）共享动态链接库用于 MFC 应用程序和扩展 DLL。  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-cn/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 提供描述有关 Visual C\+\+ 库的概念信息和讨论各种编码技术和方法的主题的链接。