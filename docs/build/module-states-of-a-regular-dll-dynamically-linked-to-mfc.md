---
title: "动态链接到 MFC 的规则 DLL 的模块状态 | Microsoft Docs"
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
  - "DLL [C++], 模块状态"
  - "MFC DLL [C++], 规则 DLL"
  - "模块状态 [C++]"
  - "模块状态 [C++], 规则 DLL 动态链接到"
  - "规则 DLL [C++], 动态链接到 MFC"
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 动态链接到 MFC 的规则 DLL 的模块状态
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果能够将规则 DLL 动态链接到 MFC DLL，就可以进行一些非常复杂的配置。  例如，规则 DLL 和使用它的可执行文件可同时动态链接到 MFC DLL 和任何扩展 DLL。  
  
 此配置会引起一个与 MFC 全局数据（如指向当前 `CWinApp` 对象的指针以及句柄映射）有关的问题。  
  
 在 MFC 4.0 版之前，此全局数据驻留在 MFC DLL 本身中并由进程中的所有模块共享。  由于每个使用 Win32 DLL 的进程均获取自己的 DLL 数据副本，因此，本方案提供了一种简单的方法来跟踪每个进程的数据。  此外，由于 AFXDLL 模型假定进程中只有一个 `CWinApp` 对象并且仅有一组句柄映射，因此可以在 MFC DLL 本身中跟踪这些项。  
  
 但具有了将规则 DLL 动态链接到 MFC DLL 的能力后，现在一个进程中可以有两个或更多的 `CWinApp` 对象，以及两组或更多组句柄映射。  这时 MFC 如何跟踪它应使用的对象和句柄映射呢？  
  
 解决方案是赋予每个模块（应用程序或规则 DLL）自己的此全局状态信息副本。  这样，对规则 DLL 中 **AfxGetApp** 的调用所返回的指针指向的将是 DLL 中的 `CWinApp` 对象，而不是可执行文件中的该对象。  此 MFC 全局数据的每个模块的副本都称作“模块状态”，详见 [MFC 技术说明 58](../mfc/tn058-mfc-module-state-implementation.md) 中的描述。  
  
 MFC 的通用窗口过程会自动切换到正确的模块状态，因此您无需担心在规则 DLL 中实现的任何消息处理程序中的模块状态。  但当可执行文件调用到规则 DLL 中时，确实需要将当前模块状态显式设置为 DLL 的模块状态。  为此，请在从 DLL 导出的每个函数中使用 **AFX\_MANAGE\_STATE** 宏。  为此，需将下列代码行添加到从 DLL 导出的函数的开始处：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## 您想进一步了解什么？  
  
-   [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL](../build/extension-dlls-overview.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)