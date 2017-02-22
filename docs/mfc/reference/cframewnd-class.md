---
title: "CFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWnd class"
  - "frame window classes, 基类"
  - "frame windows, 创建"
  - "单文档界面 (SDI), frame windows"
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供的Windows函数单文档界面与管理窗口的成员一起的重叠或弹出框架窗口，\(SDI）。  
  
## 语法  
  
```  
class CFrameWnd : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFrameWnd::CFrameWnd](../Topic/CFrameWnd::CFrameWnd.md)|构造 `CFrameWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFrameWnd::ActivateFrame](../Topic/CFrameWnd::ActivateFrame.md)|具有帧可见并提供给用户。|  
|[CFrameWnd::BeginModalState](../Topic/CFrameWnd::BeginModalState.md)|设置框架窗口到模式。|  
|[CFrameWnd::Create](../Topic/CFrameWnd::Create.md)|调用创建和初始化Windows框架窗口与 `CFrameWnd` 对象。|  
|[CFrameWnd::CreateView](../Topic/CFrameWnd::CreateView.md)|创建在从 `CView`未派生的帧中的视图。|  
|[CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)|停靠控件条。|  
|[CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md)|允许控制条停靠。|  
|[CFrameWnd::EndModalState](../Topic/CFrameWnd::EndModalState.md)|关闭框架窗口的模式状态。  启用 `BeginModalState`禁用所有窗口。|  
|[CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)|浮点控制条。|  
|[CFrameWnd::GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md)|返回有效的 **CDocument** 对象。|  
|[CFrameWnd::GetActiveFrame](../Topic/CFrameWnd::GetActiveFrame.md)|返回有效的 `CFrameWnd` 对象。|  
|[CFrameWnd::GetActiveView](../Topic/CFrameWnd::GetActiveView.md)|返回有效的 `CView` 对象。|  
|[CFrameWnd::GetControlBar](../Topic/CFrameWnd::GetControlBar.md)|检索控件条。|  
|[CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md)|检索框架窗口的停靠状态。|  
|[CFrameWnd::GetMenuBarState](../Topic/CFrameWnd::GetMenuBarState.md)|检索菜单中显示状态在当前MFC应用程序的。|  
|[CFrameWnd::GetMenuBarVisibility](../Topic/CFrameWnd::GetMenuBarVisibility.md)|指示菜单的默认行为在当前MFC应用程序的是否为隐藏或可见。|  
|[CFrameWnd::GetMessageBar](../Topic/CFrameWnd::GetMessageBar.md)|返回指向的指针属于框架窗口的状态栏。|  
|[CFrameWnd::GetMessageString](../Topic/CFrameWnd::GetMessageString.md)|检索消息与命令ID.相应|  
|[CFrameWnd::GetTitle](../Topic/CFrameWnd::GetTitle.md)|检索相关控件条的标题。|  
|[CFrameWnd::InitialUpdateFrame](../Topic/CFrameWnd::InitialUpdateFrame.md)|在将调用框架窗口导致属于所有视图的 `OnInitialUpdate` 成员函数。|  
|[CFrameWnd::InModalState](../Topic/CFrameWnd::InModalState.md)|返回指示框架窗口是否为值在一个模式状态。|  
|[CFrameWnd::IsTracking](../Topic/CFrameWnd::IsTracking.md)|确定拆分栏当前是否正在移动。|  
|[CFrameWnd::LoadAccelTable](../Topic/CFrameWnd::LoadAccelTable.md)|调用加载快捷键对应表。|  
|[CFrameWnd::LoadBarState](../Topic/CFrameWnd::LoadBarState.md)|调用还原控件条的设置。|  
|[CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)|调用动态创建从资源信息的框架窗口。|  
|[CFrameWnd::NegotiateBorderSpace](../Topic/CFrameWnd::NegotiateBorderSpace.md)|协调在框架窗口的边框空间。|  
|[CFrameWnd::OnBarCheck](../Topic/CFrameWnd::OnBarCheck.md)|调用，每当事件在指定的控制条执行。|  
|[CFrameWnd::OnContextHelp](../Topic/CFrameWnd::OnContextHelp.md)|就地项目中处理SHIFT\+F1帮助。|  
|[CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)|设置应用程序的主框架窗口到并在打印预览模式之外。|  
|[CFrameWnd::OnUpdateControlBarMenu](../Topic/CFrameWnd::OnUpdateControlBarMenu.md)|调用由框架，这种关联的菜单更新。|  
|[CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)|重新定位 `CFrameWnd` 对象的控制条。|  
|[CFrameWnd::SaveBarState](../Topic/CFrameWnd::SaveBarState.md)|调用保存控件条的设置。|  
|[CFrameWnd::SetActivePreviewView](../Topic/CFrameWnd::SetActivePreviewView.md)|指定指定的视图是丰富预览的活动视图。|  
|[CFrameWnd::SetActiveView](../Topic/CFrameWnd::SetActiveView.md)|设置活动 `CView` 对象。|  
|[CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md)|调用停靠在主窗口框架窗口。|  
|[CFrameWnd::SetMenuBarState](../Topic/CFrameWnd::SetMenuBarState.md)|将当前MFC应用程序中隐藏或显示的菜单上显示状态。|  
|[CFrameWnd::SetMenuBarVisibility](../Topic/CFrameWnd::SetMenuBarVisibility.md)|设置菜单的默认行为在当前MFC应用程序的是隐藏或可见。|  
|[CFrameWnd::SetMessageText](../Topic/CFrameWnd::SetMessageText.md)|设置标准状态栏的文本。|  
|[CFrameWnd::SetProgressBarPosition](../Topic/CFrameWnd::SetProgressBarPosition.md)|将Windows的当前位置显示的7进度栏在任务栏。|  
|[CFrameWnd::SetProgressBarRange](../Topic/CFrameWnd::SetProgressBarRange.md)|将Windows的范围在任务栏的显示7进度栏。|  
|[CFrameWnd::SetProgressBarState](../Topic/CFrameWnd::SetProgressBarState.md)|设置在任务栏按钮显示的进度指示器的类型和状态。|  
|[CFrameWnd::SetTaskbarOverlayIcon](../Topic/CFrameWnd::SetTaskbarOverlayIcon.md)|已重载。  对复盖率任务栏按钮指示应用程序状态或通知给用户。|  
|[CFrameWnd::SetTitle](../Topic/CFrameWnd::SetTitle.md)|一组相关控件条的标题。|  
|[CFrameWnd::ShowControlBar](../Topic/CFrameWnd::ShowControlBar.md)|调用显示控件条。|  
|[CFrameWnd::ShowOwnedWindows](../Topic/CFrameWnd::ShowOwnedWindows.md)|显示是 `CFrameWnd` 对象的子代的所有窗口。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)|创建框架的客户端窗口。|  
|[CFrameWnd::OnHideMenuBar](../Topic/CFrameWnd::OnHideMenuBar.md)|调用在当前MFC应用程序菜单之前隐藏。|  
|[CFrameWnd::OnShowMenuBar](../Topic/CFrameWnd::OnShowMenuBar.md)|调用在当前MFC应用程序的菜单中显示。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFrameWnd::m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md)|自动的控件启用和禁用菜单项的功能。|  
|[CFrameWnd::rectDefault](../Topic/CFrameWnd::rectDefault.md)|在创建 `CFrameWnd` 对象允许Windows选择窗口的初始大小和位置时，请通过此静态 `CRect` 作为参数。|  
  
## 备注  
 若要创建应用程序的一个有用的框架窗口，从 `CFrameWnd`派生选件类。  添加成员变量添加到派生类来存储数据特定于您的应用程序。  实现消息处理程序成员函数和消息映射在派生类指定发生的情况，在处理消息到windows时。  
  
 有三种构造框架窗口:  
  
-   使用 [创建](../Topic/CFrameWnd::Create.md)，请直接构造它。  
  
-   使用 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md)，请直接构造它。  
  
-   使用文档模板，请取消构造它。  
  
 在调用 **Create** 或 `LoadFrame`之前，使用C\+\+ **new** 运算符，则必须生成堆中的框架窗口对象。  在调用 **Create**之前，可以注册窗口选件类。也将框架的图标和选件类样式的 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全局函数。  
  
 使用 **Create** 成员函数通过帧的创建参数作为即时参数。  
  
 `LoadFrame` 比 **Create**需要的参数和从资源中检索大多数其默认值，包括帧的说明、图标、快捷键对应表和菜单。  若要访问由 `LoadFrame`，所有这些资源必须具有相同的资源ID \(例如，**IDR\_MAINFRAME**）。  
  
 当 `CFrameWnd` 对象包含视图和文档时，它们是间接由框架创建的而不是直接程序员。  `CDocTemplate` 对象协调下帧，包含"视图中创建的创建，因此，视图的连接与相应文档。  `CDocTemplate` 构造函数的参数指定涉及的三选件类的 `CRuntimeClass` \(文档，则框架和视图）。  框架用于 `CRuntimeClass` 对象动态创建新框架，指定由用户\(例如，通过使用文件的命令或多文档界面\(mdi\) \(MDI\)窗口新的命令）。  
  
 必须声明从派生 `CFrameWnd` 框架窗口选件类与 `DECLARE_DYNCREATE` 为上面 `RUNTIME_CLASS` 结构才能正常工作。  
  
 `CFrameWnd` 到Windows的典型的应用程序包含默认实现来执行一个主窗口的以下功能:  
  
-   `CFrameWnd` 框架窗口记录是Windows活动窗口或当前输入焦点的独立的一个当前活动的视图。  这些帧重新激活时，活动视图通过调用 `CView::OnActivateView`通知。  
  
-   命令消息和许多常见帧通知消息，包括 `OnSetFocus`处理的错误，`OnHScroll`和 `CWnd`的 `OnVScroll` 功能，由 `CFrameWnd` 框架窗口委托给为当前活动的视图。  
  
-   为当前活动的视图\(或在MDI框架的当前活动的MDI子框架窗口\)可以确定框架窗口的说明。  此功能可通过关闭 **FWS\_ADDTOTITLE** 样式禁用bit框架窗口。  
  
-   `CFrameWnd` 框架窗口管理确定控制条、视图和其他子窗口在框架窗口的工作区内。  框架窗口还执行闲置时更新工具栏和其他控件条按钮。  `CFrameWnd` 框架窗口还有命令的默认实现打开或关闭的工具栏和状态栏。  
  
-   `CFrameWnd` 框架窗口管理主菜单栏。  当弹出菜单显示时，框架窗口使用 **UPDATE\_COMMAND\_UI** framework确定应启用，禁用或查看哪些菜单项。  当用户选择菜单项时，框架窗口更新消息字符串的状态栏该命令的。  
  
-   `CFrameWnd` 框架窗口将自动转换键盘快捷键的一个选项快捷键对应表。  
  
-   有关上下文相关帮助的 `CFrameWnd` 框架窗口都有一个选项可帮助ID设置为 `LoadFrame`。  框架窗口是semimodal状态的主要管弦乐队例如区分上下文的帮助\(SHIFT\+F1\)和打印预览模式。  
  
-   `CFrameWnd` 框架窗口将打开在框架窗口拖动从文件管理器和删除的文件。  如果文件扩展名并将向应用程序注册，框架窗口回答发生的动态数据交换\(dde\) \(DDE\)打开请求，当用户打开在文件管理器的数据文件，或者 **ShellExecute** Windows函数调用时。  
  
-   如果框架窗口是主应用程序窗口\(即 `CWinThread::m_pMainWnd`\)，那么，当用户关闭应用程序时，框架窗口提示用户保存任何修改文档\(对于 `OnClose` 和 `OnQueryEndSession`）。  
  
-   如果框架窗口是主应用程序窗口，框架窗口是运行的WinHelp上下文。  如果它对于此应用程序，帮助生成已关闭框架窗口将关闭WINHELP.EXE。  
  
 不要使用C\+\+ **delete** 运算符销毁框架窗口。  请改用 `CWnd::DestroyWindow`。  当销毁，`PostNcDestroy` 的 `CFrameWnd` 实现会删除C\+\+对象窗口。  当用户关闭框架窗口，默认 `OnClose` 处理程序将调用 `DestroyWindow`。  
  
 有关 `CFrameWnd`的更多信息，请参见 [Windows框架](../../mfc/frame-windows.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md)