---
title: "MFC DLL 向导的应用程序设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.dll.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC DLL 向导，应用程序设置"
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC DLL 向导的应用程序设置
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此 MFC DLL 向导页为新的 MFC DLL 项目设计和添加基本功能。  
  
## DLL 类型  
 选择要创建的 DLL 类型。  
  
 **使用共享 MFC DLL 的规则 DLL**  
 选择此选项将 MFC 库作为共享 DLL 链接到您的程序。  使用此选项不能在 DLL 和调用应用程序之间共享 MFC 对象。  程序在运行时调用 MFC 库。  如果程序由多个使用 MFC 库的执行文件组成，则此选项可降低程序的磁盘和内存需求。  Win32 和 MFC 程序都可调用 DLL 中的函数。  必须将 MFC DLL 与此项目类型一起重新发布。  
  
 **带静态链接 MFC 的规则 DLL**  
 选择此选项在生成时将您的程序静态链接到 MFC 库。  Win32 和 MFC 程序都可调用 DLL 中的函数。  虽然此选项会增加程序的大小，但不必将 MFC DLL 与此项目类型一起重新分布。  不能在 DLL 和调用应用程序之间共享 MFC 对象。  
  
 **MFC 扩展名 DLL**  
 如果希望程序在运行时调用 MFC 库和希望在 DLL 和调用应用程序之间共享 MFC 对象，则选择此选项。  如果程序由多个使用 MFC 库的执行文件组成，则此选项可降低程序的磁盘和内存需求。  只有 MFC 程序可以在 DLL 中调用函数。  必须将 MFC DLL 与此项目类型一起重新发布。  
  
## 附加功能  
 选择 MFC DLL 应支持自动化还是应支持 Windows 套接字。  
  
 **自动化**  
 选择“自动化”使您的程序得以操作在其他程序中实现的对象。  选择“自动化”还会向其他自动化客户公开您的程序。  有关更多信息，请参见[自动化](../../mfc/automation.md)。  
  
 **Windows 套接字**  
 选择此选项以指示程序支持 Windows 套接字。  Windows 套接字允许编写通过 TCP\/IP 网络通信的程序。  
  
 创建具有 Windows 套接字支持的 MFC DLL 时，[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) 初始化套接字支持，而且 MFC 头文件 StdAfx.h 包含 AfxSock.h。  
  
## 请参阅  
 [MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)   
 [创建 MFC DLL 项目](../../mfc/reference/creating-an-mfc-dll-project.md)