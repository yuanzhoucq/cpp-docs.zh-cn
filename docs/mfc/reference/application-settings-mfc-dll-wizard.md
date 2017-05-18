---
title: "MFC DLL 向导的应用程序设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: df1e3de3e1548fe4c4c340a30127d9916998ba64
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 向导的应用程序设置
MFC DLL 向导的此页用于设计和添加到新的 MFC DLL 项目的基本功能。  
  
## <a name="dll-type"></a>DLL 类型  
 选择你想要创建的 DLL 的类型。  
  
 **使用共享的 MFC DLL 的规则 DLL**  
 选择此选项可以链接到您的程序作为共享 DLL 的 MFC 库。 使用此选项时，不能在 DLL 和调用应用程序之间共享 MFC 对象。 您的程序在运行时调用的 MFC 库。 如果它组成使用 MFC 库的多个执行文件，此选项可减少您的程序的磁盘和内存要求。 Win32 和 MFC 程序可以在您的 DLL 中调用函数。 您必须重新分发 MFC DLL 与此类型的项目。  
  
 **与静态链接的 MFC 的规则 DLL**  
 选择此选项以您的程序静态方式链接到 MFC 库在生成时。 Win32 和 MFC 程序可以在您的 DLL 中调用函数。 虽然此选项会增加您的程序的大小，您不必重新分发 MFC DLL 与此类型的项目。 无法在 DLL 和调用应用程序之间共享 MFC 对象。  
  
 **MFC 扩展 DLL**  
 如果您希望程序在运行时，进行到 MFC 库的调用，并且您想要共享您的 DLL 和调用应用程序之间的 MFC 对象，请选择此选项。 如果它组成，所有使用 MFC 库的多个可执行文件，此选项可减少您的程序的磁盘和内存要求。 仅 MFC 程序可以在您的 DLL 中调用函数。 您必须重新分发 MFC DLL 与此类型的项目。  
  
## <a name="additional-features"></a>其他功能  
 选择 MFC DLL 应支持自动化以及是否有它应该支持 Windows 套接字。  
  
 **自动化**  
 选择**自动化**以便程序可以操作在其他程序中实现的对象。 选择**自动化**还会公开给其他自动化客户端程序。 请参阅[自动化](../../mfc/automation.md)有关详细信息。  
  
 **Windows 套接字**  
 选择此选项以指示您的程序支持 Windows 套接字。 Windows 套接字，可以编写通过 TCP/IP 网络进行通信的程序。  
  
 在 MFC DLL 与 Windows 套接字将创建支持， [cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)初始化为套接字支持，MFC 标头文件 StdAfx.h 包括 AfxSock.h。  
  
## <a name="see-also"></a>另请参阅  
 [MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)   
 [创建 MFC DLL 项目](../../mfc/reference/creating-an-mfc-dll-project.md)


