---
title: "MFC DLL 向导的应用程序设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.dll.appset
dev_langs: C++
helpviewer_keywords: MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1851460d5cf9deb8a803b13ec75d92c45c03e607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 向导的应用程序设置
MFC DLL 向导的此页用于设计和添加到新的 MFC DLL 项目的基本功能。  
  
## <a name="dll-type"></a>DLL 类型  
 选择你想要创建的 DLL 的类型。  
  
 **常规 MFC DLL 使用共享 MFC DLL**  
 选择此选项将 MFC 库链接到你的程序作为共享 DLL。 使用此选项，你不能在 DLL 和调用应用程序之间共享 MFC 对象。 你的程序在运行时调用的 MFC 库。 如果它使用 MFC 库的多个执行文件的构成，则此选项可减少你的程序的磁盘和内存要求。 Win32 和 MFC 程序可以在 DLL 中调用函数。 你必须重新分发 MFC DLL 与此类型的项目。  
  
 **常规 MFC DLL 与 MFC 静态链接**  
 选择此选项以程序静态方式链接到 MFC 库在生成时。 Win32 和 MFC 程序可以在 DLL 中调用函数。 虽然此选项会增加你的程序的大小，你不必重新分发 MFC DLL 与此类型的项目。 你无法在 DLL 和调用应用程序之间共享 MFC 对象。  
  
 **MFC 扩展 DLL**  
 如果您希望程序在运行时，可以调用 MFC 库并且你想要共享您的 DLL 和调用应用程序之间的 MFC 对象，请选择此选项。 如果它构成，所有使用 MFC 库的多个可执行文件，此选项可减少你程序的磁盘和内存要求。 仅 MFC 程序可以在 DLL 中调用函数。 你必须重新分发 MFC DLL 与此类型的项目。  
  
## <a name="additional-features"></a>其他功能  
 选择是否 MFC DLL 应支持自动化以及是否它应当支持 Windows 套接字。  
  
 **自动化**  
 选择**自动化**以允许你的程序可以操作在另一个程序中实现的对象。 选择**自动化**还公开其他自动化客户端程序。 请参阅[自动化](../../mfc/automation.md)有关详细信息。  
  
 **Windows 套接字**  
 选择此选项以指示您的程序支持 Windows 套接字。 Windows 套接字，可以编写通过 TCP/IP 网络进行通信的程序。  
  
 MFC DLL 与 Windows 套接字时将创建支持， [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)初始化支持套接字和 MFC 标头文件 StdAfx.h 包括 AfxSock.h。  
  
## <a name="see-also"></a>请参阅  
 [MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)   
 [创建 MFC DLL 项目](../../mfc/reference/creating-an-mfc-dll-project.md)

