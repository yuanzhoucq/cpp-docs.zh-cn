---
title: 特殊 CWinApp 服务
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
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
ms.openlocfilehash: e96753a5dbc77fdc7aab365439e997585e00f43b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511333"
---
# <a name="special-cwinapp-services"></a>特殊 CWinApp 服务

除了运行消息循环，并为你提供初始化应用程序并进行清理的机会外， [CWinApp](../mfc/reference/cwinapp-class.md)还提供了一些其他服务。

##  <a name="_core_shell_registration"></a>Shell 注册

默认情况下，MFC 应用程序向导使用户能够打开您的应用程序已创建的数据文件，方法是在文件资源管理器或文件管理器中打开它们。 如果你的应用程序是一个 MDI 应用程序，并且你为应用程序创建的文件指定了扩展，则 MFC 应用程序向导会将对[CWinApp](../mfc/reference/cwinapp-class.md)的[RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes)和[EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)成员函数的调用添加到它为您写入的重写。`InitInstance`

`RegisterShellFileTypes` 将您的应用程序的文档类型注册到文件资源管理器或文件管理器。 该函数可将项添加到 Windows 保留的注册数据库。 这些项注册每个文档类型、将文件扩展名与文件类型关联、指定用来打开应用程序的命令行并指定用来打开该类型的文档的动态数据交换 (DDE) 命令。

`EnableShellOpen` 通过以下方式完成这个过程：允许您的应用程序从文件资源管理器或文件管理器接收用来打开用户选择的文件的 DDE 命令。

`CWinApp` 中的此自动支持使您无需将 .reg 文件附加到您的应用程序或完成特殊安装工作。

如果要为应用程序初始化 GDI + （通过在[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)函数中调用[GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) ），则必须取消 gdi + 后台线程。

为此，可以将[GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput)结构`SuppressBackgroundThread`的成员设置为**TRUE**。 当禁止 gdi + 后台线程时， `NotificationHook`应`NotificationUnhook`刚好在进入和退出应用程序的消息循环之前执行和调用。 有关这些调用的详细信息，请参阅[GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput)。 因此，有一个很好的`GdiplusStartup`调用位置，挂钩通知函数将位于虚拟函数[CWinApp：： Run](../mfc/reference/cwinapp-class.md#run)的重写中，如下所示：

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

如果不禁止后台 GDI+ 线程，DDE 命令可能在其主窗口创建前提前发给应用程序。 shell 发出的 DDE 命令可能提前中止，从而产生错误消息。

##  <a name="_core_file_manager_drag_and_drop"></a>文件管理器拖放

可从文件管理器或文件资源管理器中的文件视图将文件拖动到您的应用程序的窗口中。 例如，您可能使一个或多个文件拖动到 MDI 应用程序的主窗口，应用程序可在其中为这些文件检索文件名和打开 MDI 子窗口。

若要在应用程序中启用文件拖放功能，MFC 应用程序向导会在的主框架`InitInstance`窗口中写入[CWnd](../mfc/reference/cwnd-class.md)成员函数[DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles)的调用。 如果您不想实现拖放功能，则可以移除该调用。

> [!NOTE]
>  您还可以使用 OLE 实现更常见的拖放功能 — 在文档之间或文档中拖动数据。 有关信息，请参阅[拖放（OLE）](../mfc/drag-and-drop-ole.md)一文。

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>跟踪最近使用的文档

当用户打开和关闭文件时，应用程序对象将跟踪四个最近使用的文件。 这些文件的名称将添加到“文件”菜单并在更改时更新。 框架会将这些文件名存储在与您的项目同名的注册表或 .ini 文件中，并在您的应用程序启动时从文件中读取它们。 MFC 应用程序向导为您创建的 `InitInstance`替代包括对[CWinApp](../mfc/reference/cwinapp-class.md)成员函数[LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings)的调用，该函数从注册表或.ini文件（包括最近使用的文件）加载信息人名.

这些项按如下方式进行存储：

- 在 Windows NT、Windows 2000 和更高版本中，值存储到注册表项。

- 在 Windows 3.x 中，值存储在 WIN.INI 文件中。

- 在 Windows 95 和更高版本中，值存储在缓存版的 WIN.INI 中。

## <a name="see-also"></a>请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
