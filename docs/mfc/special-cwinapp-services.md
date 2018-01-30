---
title: "特殊 CWinApp 服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28a12d9553e1519c158c0a0e9d2fcec6365b65fe
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="special-cwinapp-services"></a>特殊 CWinApp 服务
除了运行消息循环以及支持您初始化应用程序然后清理它， [CWinApp](../mfc/reference/cwinapp-class.md)提供了一些其他服务。  
  
##  <a name="_core_shell_registration"></a>Shell 注册  
 默认情况下，MFC 应用程序向导使用户能够打开您的应用程序已创建的数据文件，方法是在文件资源管理器或文件管理器中打开它们。 如果你的应用程序是 MDI 应用程序和指定应用程序创建的文件扩展名，MFC 应用程序向导将添加到调用[RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes)和[EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)到`InitInstance`它为你编写的替代。  
  
 `RegisterShellFileTypes` 将您的应用程序的文档类型注册到文件资源管理器或文件管理器。 该函数可将项添加到 Windows 保留的注册数据库。 这些项注册每个文档类型、将文件扩展名与文件类型关联、指定用来打开应用程序的命令行并指定用来打开该类型的文档的动态数据交换 (DDE) 命令。  
  
 `EnableShellOpen` 通过以下方式完成这个过程：允许您的应用程序从文件资源管理器或文件管理器接收用来打开用户选择的文件的 DDE 命令。  
  
 `CWinApp` 中的此自动支持使您无需将 .reg 文件附加到您的应用程序或完成特殊安装工作。  
  
 如果你想要为你的应用程序初始化 GDI + (通过调用[GdiplusStartup](https://msdn.microsoft.com/library/ms534077)中你[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)函数)，您必须禁止 GDI + 后台线程。  
  
 你可以执行此操作通过设置**SuppressBackgroundThread**的成员[GdiplusStartupInput](https://msdn.microsoft.com/library/ms534067)结构**TRUE**。 当禁止 GDI + 后台线程， **NotificationHook**和**NotificationUnhook**应进行呼叫之前进入和退出应用程序的消息循环。 有关这些调用的详细信息，请参阅[GdiplusStartupOutput](https://msdn.microsoft.com/library/ms534068)。 因此，调用的良好开端**GdiplusStartup**和挂钩通知函数将中的虚函数重写[cwinapp:: Run](../mfc/reference/cwinapp-class.md#run)，如下所示：  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 如果不禁止后台 GDI+ 线程，DDE 命令可能在其主窗口创建前提前发给应用程序。 shell 发出的 DDE 命令可能提前中止，从而产生错误消息。  
  
##  <a name="_core_file_manager_drag_and_drop"></a>文件管理器拖放  
 可从文件管理器或文件资源管理器中的文件视图将文件拖动到您的应用程序的窗口中。 例如，您可能使一个或多个文件拖动到 MDI 应用程序的主窗口，应用程序可在其中为这些文件检索文件名和打开 MDI 子窗口。  
  
 若要启用文件拖动和删除你的应用程序中，MFC 应用程序向导会将写入调用[CWnd](../mfc/reference/cwnd-class.md)成员函数[DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles)主框架窗口中你`InitInstance`。 如果您不想实现拖放功能，则可以移除该调用。  
  
> [!NOTE]
>  您还可以使用 OLE 实现更常见的拖放功能 — 在文档之间或文档中拖动数据。 有关信息，请参阅文章[拖放 (OLE)](../mfc/drag-and-drop-ole.md)。  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>跟踪的最最近使用的文档  
 当用户打开和关闭文件时，应用程序对象将跟踪四个最近使用的文件。 这些文件的名称将添加到“文件”菜单并在更改时更新。 框架会将这些文件名存储在与您的项目同名的注册表或 .ini 文件中，并在您的应用程序启动时从文件中读取它们。 `InitInstance`重写 MFC 应用程序向导创建包括调用[CWinApp](../mfc/reference/cwinapp-class.md)成员函数[LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings)，这会将信息加载从注册表或.ini文件，包括最近使用的文件的名称。  
  
 这些项按如下方式进行存储：  
  
-   在 Windows NT、Windows 2000 和更高版本中，值存储到注册表项。  
  
-   在 Windows 3.x 中，值存储在 WIN.INI 文件中。  
  
-   在 Windows 95 和更高版本中，值存储在缓存版的 WIN.INI 中。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)