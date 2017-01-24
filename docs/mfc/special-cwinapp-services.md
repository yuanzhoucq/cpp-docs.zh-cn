---
title: "特殊 CWinApp 服务 | Microsoft Docs"
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
  - "LoadStdProfileSettings"
  - "EnableShellOpen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序对象 [C++], 服务"
  - "CWinApp 类, 文件管理器拖放"
  - "CWinApp 类, 初始化 GDI+"
  - "CWinApp 类, 最近使用的文档"
  - "CWinApp 类, 服务"
  - "CWinApp 类, shell 注册"
  - "拖放 [C++], 文件"
  - "DragAcceptFiles 方法"
  - "EnableShellOpen 方法"
  - "文件 [C++], 拖放"
  - "文件 [C++], 最近使用的"
  - "GDI+, 针对 MFC 初始化"
  - "GDI+, 取消后台线程 [MFC]"
  - "LoadStdProfileSettings 方法"
  - "MFC [C++], 文件操作"
  - "MFC [C++], 最近使用的文件列表"
  - "MFC [C++], shell 注册"
  - "MRU 列表"
  - "注册文件类型"
  - "RegisterShellFileTypes 方法"
  - "注册 [C++], shell"
  - "注册表 [C++], 最近使用的文件"
  - "服务, 由 CWinApp 提供"
  - "shell, 注册文件类型"
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 特殊 CWinApp 服务
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了运行消息外请循环，您可以利用这一机会初始化应用程序和。后清理，[CWinApp](../mfc/reference/cwinapp-class.md) 提供若干其他服务。  
  
##  <a name="_core_shell_registration"></a> Shell 注册  
 默认情况下， MFC 应用程序向导"使您能够为用户到数据文件应用程序通过双击控件来创建文件资源管理器或文件管理器。  如果应用程序比较 MDI 应用程序，而您为应用程序创建的文件指定扩展名，MFC 应用程序向导添加调用 [RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md) [EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md) [CWinApp](../mfc/reference/cwinapp-class.md) 的成员，并且函数对 `InitInstance` 的重写它为您编写。  
  
 `RegisterShellFileTypes` 注册文件管理器或文件管理器的应用程序关联的文档类型。  函数输入添加到 Windows 注册数据库的维护。  输入注册每个文档类型，将文件扩展名的文件类型，指定打开命令行应用程序，并指定一个动态数据交换 \(DDE\) \(DDE\) 命令打开相应类型的文档。  
  
 `EnableShellOpen` 方法允许应用程序完成过程接收文件管理器或文件管理器的 DDE 命令打开用户选定的文件。  
  
 `CWinApp` 中自动的不再需要此注册支持提供与应用程序的一 .reg 文件或完成特定安装工作。  
  
 如果要初始化应用程序的 GDI\+ \(通过调用在 [InitInstance](../Topic/CWinApp::InitInstance.md) 函数的 [GdiplusStartup](_gdiplus_FUNC_GdiplusStartup_token_input_output_) \)，您必须禁止 GDI\+ 后台线程。  
  
 您可以通过 [GdiplusStartupInput](_gdiplus_STRUC_GdiplusStartupInput) 设置结构的 **SuppressBackgroundThread** 成员执行为 **TRUE**。  当取消 GDI\+ 后台线程时，应在进入和退出应用程序的消息循环之前调用 **NotificationHook** 和 **NotificationUnhook** 调用 \(请参见 [GdiplusStartupOutput](_gdiplus_STRUC_GdiplusStartupOutput)\)。  因此，适合放置调用 **GdiplusStartup** 的和通知挂钩函数在虚拟函数 [CWinApp::Run](../Topic/CWinApp::Run.md)的重写，如下所示：  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/CPP/special-cwinapp-services_1.cpp)]  
  
 如果不显示后台 GDI\+ 线程，DDE 命令可以提前地发出到应用程序，它在主窗口之前创建的。  shell 发出的 DDE 命令可以提前地被中止，导致错误消息。  
  
##  <a name="_core_file_manager_drag_and_drop"></a> 文件管理器的拖放  
 文件可从文件中的文件或文件管理器窗口资源管理器拖动到应用程序的窗口。  可能，例如，用于启用要拖动的一个或多个文件到 MDI 应用程序的主窗口，则应用程序可以检索文件名并打开这些文件的 MDI 子窗口。  
  
 若要在应用程序中使用的文件拖放，MFC 应用程序向导编写对 [CWnd](../mfc/reference/cwnd-class.md) 成员函数 [DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md) 在 `InitInstance`的主框架窗口。  如果不想实现拖放功能，则可以移除该调用。  
  
> [!NOTE]
>  您还可以实现更为一般性的拖放功能将的数据之间文档或中与 OLE。  有关信息，请参见 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)文章。  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> 记录最新使用过的文档  
 因为用户打开和关闭文件，应用程序对象记录四最近使用的文件。  这些文件名称添加到"菜单并更新它们发生更改。  当应用程序启动时，框架将这些文件名在注册表中或 .ini 文件，名称与项目同名并从磁盘读取文件。  MFC 应用程序向导为您创建的 `InitInstance` 重写包括对包括最新使用的文件名的 [CWinApp](../mfc/reference/cwinapp-class.md) 成员函数 [LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)，从注册表或 .ini 文件加载信息。  
  
 这些输入存储方式如下：  
  
-   在 Windows NT 中，Windows 2000，然后再存储，值写入注册表项。  
  
-   在 Windows 3.x，可以在 WIN.INI 文件中。  
  
-   在 Windows 95 和更高版本，可以在 WIN.INI 一缓存版本的存储。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)