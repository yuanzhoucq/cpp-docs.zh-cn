---
title: "MFC 程序或控件的源文件和头文件 | Microsoft Docs"
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
  - "文件类型 [C++], MFC 源和头"
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 程序或控件的源文件和头文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual Studio 中创建 MFC 项目时将创建下列文件，具体视为所创建项目选择的选项而不同。  例如，仅当创建基于对话框的项目或类时，项目才包含 *Projname*dlg.cpp 和 *Projname*dlg.h 文件。  
  
 所有这些文件都位于 *Projname* 目录中，而且位于解决方案资源管理器中的头文件（.h 文件）文件夹中或源文件（.cpp 文件）文件夹中。  
  
|文件名|说明|  
|---------|--------|  
|*Projname*.h|程序或 DLL 的主包含文件。  它包含其他头文件的所有全局符号和 `#include` 指令。  它从 `CWinApp` 导出 `CPrjnameApp` 类并声明 `InitInstance` 成员函数。  对于控件，`CPrjnameApp` 类从 `COleControlModule` 导出。|  
|*Projname*.cpp|主程序源文件。  它创建从`CWinApp` 导出的 `CPrjnameApp` 类的一个对象，并重写 `InitInstance` 成员函数。<br /><br /> 对于可执行文件，`CPrjnameApp::InitInstance` 完成以下几件事。  它注册文档模板，以用作文档和视窗之间的连接；创建主框架窗口；以及创建空文档（如果有一个文档被指定为应用程序的命令行参数，则打开此文档）。<br /><br /> 对于 DLL 和 ActiveX（原为 OLE）控件，`CProjNameApp::InitInstance` 通过调用 `COleObjectFactory::RegisterAll` 向 OLE 注册控件的对象工厂，然后调用 `AfxOLEInit`。  另外，`CProjNameApp::ExitInstance` 成员函数用于通过 **AfxOleTerm** 调用从内存中卸载控件。<br /><br /> 此文件也通过实现 `DllRegisterServer` 和 `DllUnregisterServer` 函数，在 Windows 注册数据库中注册和注销控件。|  
|*Projname*ctrl.h、*Projname*ctrl.cpp|声明并实现 `CProjnameCtrl` 类。  从 `COleControl` 派生 `CProjnameCtrl`，并且定义一些用于初始化、描绘和序列化（加载和保存）控件的成员函数的主干实现。  也定义消息、事件和调度映射。|  
|*Projname*dlg.cpp、*Projname*dlg.h|选择基于对话框的应用程序时创建。  此文件导出和实现名为 `CProjnameDlg` 的对话框类，并且包含初始化对话框和执行对话框数据交换 \(DDX\) 的主干成员函数。  “关于”对话框类也放在这些文件中，而不是放在 *Projname*.cpp 中。|  
|Dlgproxy.cpp、Dlgproxy.h|在基于对话框的程序中，主对话框的项目自动化代理类的实现和头文件。  仅当选择了自动化支持时才使用它。|  
|*Projname*doc.cpp、*Projname*doc.h|导出和实现名为 `CProjnameDoc` 的文档类，并且包含初始化文档、序列化（加载和保存）文档和实现调试诊断的主干成员函数。|  
|*Projname*set.h\/.cpp|创建支持数据库且包含记录集类的程序时创建。|  
|*Projname*view.cpp、*Projname*view.h|导出并实现名为 `CProjnameView` 的视图类，该类用于显示和打印文档数据。  `CProjnameView` 类从下列 MFC 类之一导出：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 项目的视图类包含描述视图和实现调试诊断的主干成员函数。  如果启用了打印支持，则还添加打印、打印设置和打印预览命令消息的消息映射项。  这些项调用基视图类中的相应成员函数。|  
|*Projname*PropPage.h、*Projname*PropPage.cpp|声明并实现 `CProjnamePropPage` 类。  从 `COlePropertyPage` 派生 `CProjnamePropPage`，并且提供实现数据交换和验证的主干成员函数 `DoDataExchange`。|  
|IPframe.cpp、IPframe.h|在应用程序向导的“自动化选项”页（六个步骤中的第三步）中，如果选定了“袖珍服务器”\(Mini\-Server\) 或“完全服务器”\(Full\-Server\) 选项，则创建它们。  这些文件导出并实现名为 **CInPlaceFrame** 的就地框架窗口类，该类在容器程序就地激活服务器时使用。|  
|Mainfrm.cpp、Mainfrm.h|从 [CFrameWnd](../mfc/reference/cframewnd-class.md)（对于 SDI 应用程序）或 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)（对于 MDI 应用程序）导出 **CMainFrame** 类。  如果在应用程序向导的“应用程序选项”页（六个步骤中的第四步）中选定了相应的选项，则 **CMainFrame** 类处理工具栏按钮和状态栏的创建。  有关使用 **CMainFrame** 的信息，请参见[应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|  
|Childfrm.cpp、Childfrm.h|从 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 导出 **CChildFrame** 类。  **CChildFrame** 类用于 MDI 文档框架窗口。  如果选定了 MDI 选项，则总是创建这些文件。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [ATL 程序或控件的源文件和头文件](../ide/atl-program-or-control-source-and-header-files.md)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)