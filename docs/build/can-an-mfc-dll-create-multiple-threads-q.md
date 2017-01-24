---
title: "MFC DLL 是否能创建多线程？ | Microsoft Docs"
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
  - "DLL [C++], 多线程处理"
  - "MFC DLL [C++], 多线程处理"
  - "多线程处理 [C++], DLL"
  - "线程处理 [MFC], DLL"
ms.assetid: 41d5b5e6-a7d3-42bf-b641-f1245abd1c59
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MFC DLL 是否能创建多线程？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了在初始化过程中，只要 MFC DLL 使用 **TlsAlloc** 这样的 Win32 线程本地存储区 \(TLS\) 函数来分配线程本地存储区，就可以安全地创建多线程。  但是，如果 MFC DLL 是使用 **\_\_declspec\(thread\)** 分配线程本地存储区，客户端应用程序必须隐式链接到 DLL。  如果客户端应用程序显式链接到 DLL，对 **LoadLibrary** 的调用将不会成功加载此 DLL。  有关在 MFC DLL 内创建多线程的更多信息，请参见知识库文章 Q118816“PRB: Calling LoadLibrary\(\) to Load a DLL That Has Static TLS”（PRB：调用 LoadLibrary\(\) 以加载具有静态 TLS 的 DLL）。  
  
 启动期间创建新 MFC 线程的 MFC DLL 在由应用程序加载时将停止响应。  每当在下列对象内部通过调用 `AfxBeginThread` 或 `CWinThread::CreateThread` 创建线程时，就会发生这种情况：  
  
-   规则 DLL 中 `CWinApp` 派生对象的 `InitInstance`。  
  
-   规则 DLL 中提供的 `DllMain` 或 **RawDllMain** 函数。  
  
-   扩展 DLL 中提供的 `DllMain` 或 **RawDllMain** 函数。  
  
 有关如何在初始化期间创建线程的更多信息，请参见知识库文章“PRB: Cannot Create an MFC Thread During DLL Startup”\(Q142243\)。  
  
## 请参阅  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)