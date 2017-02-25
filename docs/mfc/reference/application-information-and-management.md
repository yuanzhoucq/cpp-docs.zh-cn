---
title: "应用程序信息和管理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], 管理"
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# 应用程序信息和管理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在使用编写应用程序时，则可对创建唯一 [CWinApp](../../mfc/reference/cwinapp-class.md)派生的对象。  通常，可能需要从 `CWinApp`之外获得有关该对象派生的对象的信息。  
  
 Microsoft 基础类 \(MFC\) 库提供以下全局函数来帮助您完成以下任务：  
  
### 应用程序信息和管理功能  
  
|||  
|-|-|  
|[AfxBeginThread](../Topic/AfxBeginThread.md)|创建新线程。|  
|[AfxEndThread](../Topic/AfxEndThread.md)|终止当前线程。|  
|[AfxFreeLibrary](../Topic/AfxFreeLibrary.md)|递减加载的动态链接库 \(DLL\) \(DLL\) 模块的引用数；当引用计数达到零时，该模块未映射。|  
|[AfxGetApp](../Topic/AfxGetApp.md)|返回指向应用程序的 `CWinApp` 对象。|  
|[AfxGetAppName](../Topic/AfxGetAppName.md)|返回包含应用程序名称的字符串。|  
|[AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)|返回表示该应用程序实例的 `HINSTANCE`。|  
|[AfxGetMainWnd](../Topic/AfxGetMainWnd.md)|返回指向 OLE 非应用程序的当前“master”窗口或服务器应用的就地框架窗口。|  
|[AfxGetPerUserRegistration](../Topic/AfxGetPerUserRegistration.md)|使用此函数来确定应用程序是否重定向到 **HKEY\_CURRENT\_USER** \(**HKCU**\) 注册表节点的访问。|  
|[AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md)|返回 `HINSTANCE` 设置为应用程序的默认资源的源。  使用此直接访问应用程序的资源。|  
|[AfxGetThread](../Topic/AfxGetThread.md)|检索指向当前对象。[CWinThread](../../mfc/reference/cwinthread-class.md)|  
|[AfxInitRichEdit](../Topic/AfxInitRichEdit.md)|初始化应用程序的 1.0 版提供编辑控件。|  
|[AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md)|初始化和应用程序版本 2.0 的最新 Rich Edit 控件。|  
|[AfxLoadLibrary](../Topic/AfxLoadLibrary.md)|将 DLL 模块映射并返回可用来获取 DLL 函数的地址分配的句柄。|  
|[AfxRegisterClass](../Topic/AfxRegisterClass.md)|注册使用 MFC DLL 中的窗口类。|  
|[AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md)|Windows 注册窗口类添加 MFC 自动注册的。|  
|[AfxSetPerUserRegistration](../Topic/AfxSetPerUserRegistration.md)|设置应用程序是否重定向到 **HKEY\_CURRENT\_USER** \(**HKCU**\) 注册表节点的访问。|  
|[AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md)|设置应用程序的默认资源加载的 `HINSTANCE` 处理。|  
|[AfxSocketInit](../Topic/AfxSocketInit.md)|调用在 `CWinApp::InitInstance` 重写初始化 Windows 套接字。|  
|[AfxWinInit](../Topic/AfxWinInit.md)|调用按逐个 MFC 提供的 `WinMain` 函数，作为基于 GUI 的应用程序 [CWinApp](../../mfc/reference/cwinapp-class.md) 初始化的一部分，MFC 初始化。  必须直接用于使用 MFC 的控制台应用程序。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)