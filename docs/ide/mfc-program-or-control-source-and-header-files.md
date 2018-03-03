---
title: "MFC 程序或控件的源文件和头文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adb4ba4fdcc141438b2eeb87b4e3c9151bb9a5c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC 程序或控件的源文件和头文件
MFC 项目在 Visual Studio 中，根据你为创建的项目选择的选项创建时创建以下文件。 例如，你的项目包含*Projname*dlg.cpp 和*Projname*dlg.h 文件仅当你创建的、 基于对话框的项目或类。  
  
 所有这些文件位于*Projname*目录中，而且标头文件 （.h 文件） 文件夹或解决方案资源管理器中的源代码文件 （.cpp 文件） 文件夹中。  
  
|文件名|描述|  
|---------------|-----------------|  
|*Projname*.h|程序或 DLL 主要包含文件。 它包含所有全局符号和`#include`指令的其他标头文件。 它派生`CPrjnameApp`类`CWinApp`并声明`InitInstance`成员函数。 用于控件，`CPrjnameApp`类派生自`COleControlModule`。|  
|*Projname*.cpp|主程序源文件。 它将创建一个类对象`CPrjnameApp`，该类派生自`CWinApp`，并重写`InitInstance`成员函数。<br /><br /> 对可执行文件，`CPrjnameApp::InitInstance`执行多项操作。 它注册文档模板，以用作文档和视图; 之间的连接创建一个主框架窗口;并创建空文档 （或打开文档，如果作为应用程序的命令行参数指定的一个）。<br /><br /> 对于 Dll 和 ActiveX (以前称为 OLE) 控件，`CProjNameApp::InitInstance`注册 OLE 通过调用控件的对象工厂`COleObjectFactory::RegisterAll`和调用`AfxOLEInit`。 此外，成员函数`CProjNameApp::ExitInstance`用于卸载从内存通过调用控件**AfxOleTerm**。<br /><br /> 此文件还注册和注销 Windows 注册数据库中的控件，通过实现`DllRegisterServer`和`DllUnregisterServer`函数。|  
|*Projname*ctrl.h， *Projname*ctrl.cpp|声明和实现`CProjnameCtrl`类。 `CProjnameCtrl`派生自`COleControl`，某些成员函数的主干实现定义用于初始化、 绘制，和序列化 （加载和保存） 控件。 此外定义了消息、 事件和调度映射。|  
|*Projname*dlg.cpp， *Projname*dlg.h|如果你选择基于对话框的应用程序，创建。 文件派生和实现名为的对话框类`CProjnameDlg`，并且包括主干成员函数来初始化的对话框和执行对话框数据交换 (DDX)。 有关对话框类还放置在这些文件而不是在*Projname*.cpp。|  
|Dlgproxy.cpp Dlgproxy.h|基于对话框的程序、 实现和标头文件中的主对话框的项目的自动化的代理类。 仅当选择了自动化的支持，才使用此选项。|  
|*Projname*doc.cpp， *Projname*doc.h|派生和实现名为的文档类`CProjnameDoc`，并包括主干成员函数初始化文档、 序列化 （保存和加载） 文档和调试诊断的实现。|  
|*Projname*set.h/.cpp|如果你创建一个程序，它支持数据库包含的记录集类，创建。|  
|*Projname*view.cpp， *Projname*view.h|派生和实现名为的视图类`CProjnameView`，用于显示和打印的文档数据。 `CProjnameView`类派生自以下的 MFC 类之一：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [Ctreeview 类](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 项目的视图类包含用于绘制的视图和实现调试诊断的主干成员函数。 如果已启用对打印的支持，消息映射条目会添加用于打印、 打印设置，并在打印预览命令消息。 这些项的基的 view 类中调用相应的成员函数。|  
|*Projname*PropPage.h， *Projname*PropPage.cpp|声明和实现`CProjnamePropPage`类。 `CProjnamePropPage`派生自`COlePropertyPage`与主干成员函数， `DoDataExchange`，用于实现数据交换和验证。|  
|IPframe.cpp IPframe.h|如果在应用程序向导中选择最小化服务器或完全服务器选项创建**自动化选项**页 （步骤 3 的 6）。 文件派生和实现就地框架窗口类，名为**CInPlaceFrame**，就地激活的容器程序服务器时使用。|  
|Mainfrm.cpp Mainfrm.h|派生**CMainFrame**类从[CFrameWnd](../mfc/reference/cframewnd-class.md) （对于 SDI 应用程序） 或[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) （对于 MDI 应用程序）。 **CMainFrame**类处理创建工具栏按钮和状态栏中，如果在应用程序向导中选择相应选项**应用程序选项**页 （步骤 4 的 6）。 有关使用信息**CMainFrame**，请参阅[框架窗口类创建的应用程序向导](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|  
|Childfrm.cpp Childfrm.h|派生**CChildFrame**类[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。 **CChildFrame**类用于 MDI 文档框架窗口。 如果你选择 MDI 选项始终创建这些文件。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [ATL 程序或控件的源文件和头文件](../ide/atl-program-or-control-source-and-header-files.md)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)