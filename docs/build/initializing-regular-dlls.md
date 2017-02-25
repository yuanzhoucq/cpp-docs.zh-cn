---
title: "初始化规则 DLL | Microsoft Docs"
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
  - "DLL [C++], 规则"
  - "初始化 DLL"
  - "规则 DLL [C++], 初始化"
ms.assetid: f1f091d1-bb91-468a-94f4-3c554657b8fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化规则 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于规则 DLL 具有 `CWinApp` 对象，故它们执行初始化和终止任务的位置应与 MFC 应用程序相同：在 DLL 的 `CWinApp` 派生类的 `InitInstance` 和 **ExitInstance** 成员函数中。  MFC 为 **PROCESS\_ATTACH** 和 **PROCESS\_DETACH** 提供了由 **\_DllMainCRTStartup** 调用的 `DllMain` 函数，因此您不应编写自己的 `DllMain` 函数。  MFC 提供的 `DllMain` 函数在 DLL 被加载时调用 `InitInstance`，并在 DLL 被卸载之前调用 `ExitInstance`。  
  
 规则 DLL 可通过在自己的 `InitInstance` 函数中调用 [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) 和 [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) 来跟踪多线程。  这些函数允许 DLL 跟踪线程特定的数据。  
  
 在动态链接到 MFC 的规则 DLL 中，如果使用了任何 MFC OLE、MFC 数据库（或 DAO）或 MFC 套接字支持，则将分别自动链接 MFC 调试扩展 DLL MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll（其中 xx 是版本号）。  对于在规则 DLL 的 `CWinApp::InitInstance` 中使用的上述每个 DLL，必须调用下列预定义的初始化函数之一。  
  
|MFC 类型支持|要调用的初始化函数|  
|--------------|---------------|  
|MFC OLE \(MFCOxxD.dll\)|`AfxOleInitModule`|  
|MFC 数据库 \(MFCDxxD.dll\)|`AfxDbInitModule`|  
|MFC 套接字 \(MFCNxxD.dll\)|`AfxNetInitModule`|  
  
## 你希望做什么？  
  
-   [初始化扩展 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [C 运行库行为和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="704731be78a1b2b43311fed62656e454" class\="tgtSentence"\>进程和线程 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
-   [线程本地存储区包装（MFC 技术说明 58）](../mfc/tn058-mfc-module-state-implementation.md)  
  
## 请参阅  
 [初始化 DLL](../build/initializing-a-dll.md)