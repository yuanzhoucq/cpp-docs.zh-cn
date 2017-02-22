---
title: "CWinApp：应用程序类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序类"
  - "CWinApp 类, CWinThread"
  - "CWinApp 类, 多线程处理"
  - "CWinApp 类, WinMain"
  - "CWinThread 类, 和 CWinApp"
  - "InitApplication 方法"
  - "MFC [C++], WinMain 和"
  - "WinMain 方法"
  - "WinMain 方法, 在 MFC 中"
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CWinApp：应用程序类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 中的主应用类封装的应用程序初始化、运行和终止适用于 Windows 操作系统。  框架上生成的应用程序必须具有来自 [CWinApp](../mfc/reference/cwinapp-class.md)派生的类仅有一个对象。  在创建窗口之前，此构造对象。  
  
 `CWinApp` 派生自 `CWinThread`，表示主执行线程应用程序，可能具有一个或多个线程。  MFC 在最新版本中，`InitInstance`、**运行**、`ExitInstance`和 `OnIdle` 成员函数实际上是 `CWinThread`类。  此处讨论这些函数，如同它们是 `CWinApp` 成员，因为对象的应用程序，讨论相关角色作为对象 \(而不是主线程。  
  
> [!NOTE]
>  应用程序类构成执行应用程序的主线程。  使用 Win32 API 函数，还可以创建辅助线程执行。  这些线程可以将 MFC 库。  （有关详细信息，请参阅[多线程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 与 Windows 操作系统的所有程序，框架应用程序有 `WinMain` 函数。  在框架应用程序，但是，不为 `WinMain`。  当应用程序启动时，库提供类并调用。  `WinMain` 运行标准服务 \(如注册一个窗口类。  DllEntryPoint 随后调用应用程序对象的成员函数中以初始化并运行应用程序。\(可以通过重写 `CWinApp` 成员自定义 `WinMain` 函数调用 `WinMain`。\)  
  
 若要初始化应用程序，`WinMain` 调用 `InitApplication` 和应用程序对象的 `InitInstance` 成员函数。  若要运行应用程序的消息循环，`WinMain` 调用 **运行** 成员函数。  在停止，`WinMain` 调用应用程序对象的 `ExitInstance` 成员函数。  
  
> [!NOTE]
>  在此文档的 **加粗** 显示的名称表示 Microsoft 基础类 \(MFC\) 库和 Visual C\+\+ 提供的元素。  在 `monospaced` 类型显示的名称指示所创建或重写的元素。  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CWinApp 和 MFC 应用程序向导](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊 CWinApp 服务](../mfc/special-cwinapp-services.md)