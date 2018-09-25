---
title: MFC 程序或控件的源文件和头文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cb9518f60db98bd590cecdffa09ee7d814241ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447903"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC 程序或控件的源文件和头文件

根据为创建的项目选择的选项，在 Visual Studio 中创建 MFC 项目时会创建以下文件。 例如，仅当创建基于对话框的项目或类时，项目才包含 Projnamedlg.cpp 和 Projnamedlg.h 文件。

所有这些文件都位于 Projname 目录中，并位于解决方案资源管理器中的头文件（.h 文件）文件夹或源文件（.cpp 文件）文件夹中。

|文件名|描述|
|---------------|-----------------|
|projname.h|程序或 DLL 的主包含文件。 它包含其他头文件的所有全局符号和 `#include` 指令。 它从 `CWinApp` 派生 `CPrjnameApp` 类并声明 `InitInstance` 成员函数。 对于控件，`CPrjnameApp` 类派生自 `COleControlModule`。|
|Projname.cpp|主程序源文件。 它创建一个派生自 `CWinApp` 的 `CPrjnameApp` 类的对象，并替代 `InitInstance` 成员函数。<br /><br /> 对于可执行文件，可使用 `CPrjnameApp::InitInstance` 执行多项操作。 可注册作为文档和视图之间的连接的文档模板；创建主框架窗口；创建一个空文档（如果已将一个文档指定为应用程序的命令行参数，则打开一个文档）。<br /><br /> 对于 DLL 和 ActiveX（以前称为 OLE）控件，`CProjNameApp::InitInstance` 通过调用 `COleObjectFactory::RegisterAll` 向 OLE 注册控件的对象工厂，并调用 `AfxOLEInit`。 此外，成员函数 `CProjNameApp::ExitInstance` 还可用于通过调用 AfxOleTerm 从内存卸载控件。<br /><br /> 该文件还通过实现 `DllRegisterServer` 和 `DllUnregisterServer` 函数在 Windows 注册数据库中注册和取消注册该控件。|
|Projnamectrl.h, Projnamectrl.cpp|声明并实现 `CProjnameCtrl` 类。 `CProjnameCtrl` 派生自 `COleControl`，并定义某些成员函数的框架实现，这些函数用于初始化、绘制和序列化（加载和保存）控件。 还定义消息、事件和调度映射。|
|Projnamedlg.cpp, Projnamedlg.h|选择基于对话框的应用程序时创建。 文件派生并实现名为 `CProjnameDlg` 的对话框类，并包括用于初始化对话框和执行对话框数据交换 (DDX) 的框架成员函数。 “关于”对话框类也位于这些文件中，而不是位于 Projname.cpp 中。|
|Dlgproxy.cpp, Dlgproxy.h|在基于对话框的程序中，主对话框的项目自动化代理类的实现和头文件。 仅当选择了“自动化支持”时才使用此选项。|
|Projnamedoc.cpp, Projnamedoc.h|派生和实现名为 `CProjnameDoc` 的文档类，并包括用于初始化文档、序列化（保存和加载）文档以及实现调试诊断的骨框架成员函数。|
|Projnameset.h/.cpp|创建的程序支持数据库并包含记录集类时创建。|
|Projnameview.cpp, Projnameview.h|派生并实现名为 `CProjnameView` 的视图类，该类用于显示和打印文档数据。 `CProjnameView` 类派生自以下任一 MFC 类：<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> 项目的视图类包含用于绘制视图和实现调试诊断的框架成员函数。 如果启用了打印支持，则会为打印、打印设置和打印预览命令消息添加消息映射项。 这些项在基视图类中调用相应的成员函数。|
|ProjnamePropPage.h, ProjnamePropPage.cpp|声明并实现 `CProjnamePropPage` 类。 `CProjnamePropPage` 派生自 `COlePropertyPage`，并提供一个框架成员函数 `DoDataExchange` 来实现数据交换和验证。|
|IPframe.cpp, IPframe.h|在应用程序向导的“自动化选项”页中选择了“微型服务器”或“全服务器”选项时创建（第 3 步，共 6 步）。 文件派生并实现名为 CInPlaceFrame 的就地框架窗口类，容器程序就地激活服务器时使用。|
|Mainfrm.cpp, Mainfrm.h|从 [CFrameWnd](../mfc/reference/cframewnd-class.md)（针对 SDI 应用程序）或 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)（针对 MDI 应用程序）派生 CMainFrame 类。 如果在应用程序向导的“应用程序选项”页中选择了相应的选项，CMainFrame 类将处理工具栏按钮和状态栏的创建（第 4 步，共 6 步）。 有关使用 CMainFrame 的信息，请参阅[应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)。|
|Childfrm.cpp, Childfrm.h|从 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 派生 CChildFrame 类。 CChildFrame 类用于 MDI 文档框架窗口。 如果选择 MDI 选项，则始终创建这些文件。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[ATL 程序或控件的源文件和头文件](../ide/atl-program-or-control-source-and-header-files.md)<br>
[CLR 项目](../ide/files-created-for-clr-projects.md)