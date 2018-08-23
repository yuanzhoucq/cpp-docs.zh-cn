---
title: CFrameWnd 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
dev_langs:
- C++
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 991b8c55c02272613ce329be9a053ff0110f1926
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539198"
---
# <a name="cframewnd-class"></a>CFrameWnd 类
提供 Windows 单文档界面 (SDI) 重叠式或弹出框架窗口功能，并提供管理窗口的成员。  
  
## <a name="syntax"></a>语法  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|构造 `CFrameWnd` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|向用户发出帧可见和可用。|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|设置模式的框架窗口。|  
|[CFrameWnd::Create](#create)|调用以创建并初始化与关联的 Windows 框架窗口`CFrameWnd`对象。|  
|[CFrameWnd::CreateView](#createview)|创建一个视图中不派生自的帧`CView`。|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|将停靠控件条。|  
|[CFrameWnd::EnableDocking](#enabledocking)|允许可停靠控件条。|  
|[CFrameWnd::EndModalState](#endmodalstate)|结束框架窗口的模式状态。 通过启用了所有情况下，禁用 windows `BeginModalState`。|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|浮动的控件条。|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|返回活动`CDocument`对象。|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|返回活动`CFrameWnd`对象。|  
|[CFrameWnd::GetActiveView](#getactiveview)|返回活动`CView`对象。|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|检索控件条。|  
|[CFrameWnd::GetDockState](#getdockstate)|检索框架窗口的停靠状态。|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|检索当前的 MFC 应用程序中的菜单的显示状态。|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|指示当前的 MFC 应用程序中的菜单的默认行为是隐藏还是可见。|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|返回一个指向状态栏属于框架窗口。|  
|[CFrameWnd::GetMessageString](#getmessagestring)|检索消息对应于命令 id。|  
|[CFrameWnd::GetTitle](#gettitle)|检索相关的控件条的标题。|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|导致`OnInitialUpdate`属于框架窗口调用中的所有视图的成员函数。|  
|[CFrameWnd::InModalState](#inmodalstate)|返回一个值，该值指示框架窗口为处于模式状态。|  
|[CFrameWnd::IsTracking](#istracking)|确定拆分条当前正在移动。|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|调用以加载快捷键对应表。|  
|[CFrameWnd::LoadBarState](#loadbarstate)|若要还原控件栏设置的调用。|  
|[CFrameWnd::LoadFrame](#loadframe)|调用以动态创建框架窗口中的资源信息。|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|协商边框空间的框架窗口中。|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|每当在指定的控件栏上执行某个操作时调用。|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|处理的就地项的 SHIFT + F1 帮助。|  
|[Cframewnd:: Onsetpreviewmode](#onsetpreviewmode)|执行和跳出执行打印预览模式下设置应用程序的主框架窗口。|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|更新关联的菜单时由框架调用。|  
|[CFrameWnd::RecalcLayout](#recalclayout)|重新定位的控件条`CFrameWnd`对象。|  
|[CFrameWnd::SaveBarState](#savebarstate)|调用以保存控件栏设置。|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|指定要用于丰富预览的活动视图的指定的视图。|  
|[CFrameWnd::SetActiveView](#setactiveview)|设置活动`CView`对象。|  
|[CFrameWnd::SetDockState](#setdockstate)|若要将停靠在主窗口中的框架窗口的调用。|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|隐藏或显示当前的 MFC 应用程序中设置菜单的显示状态。|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|在当前的 MFC 应用程序是隐藏还是可见设置菜单的默认行为。|  
|[CFrameWnd::SetMessageText](#setmessagetext)|设置标准状态栏的文本。|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|设置为 Windows 7 任务栏上显示的进度栏的当前位置。|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Windows 7 任务栏上显示的进度条的范围设置。|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|设置的类型和任务栏按钮上显示进度指示器的状态。|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|已重载。 适用于任务栏按钮，以指示应用程序状态或向用户通知覆盖。|  
|[CFrameWnd::SetTitle](#settitle)|设置相关的控件条的标题。|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|调用以显示控制条。|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|显示所有的后代的时段`CFrameWnd`对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|创建框架的客户端窗口。|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|在当前的 MFC 应用程序中的菜单处于隐藏状态之前调用。|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|在当前的 MFC 应用程序中的菜单显示之前调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|控件自动启用和禁用的菜单项的功能。|  
|[CFrameWnd::rectDefault](#rectdefault)|将其传递静态`CRect`作为参数创建时`CFrameWnd`对象，以允许 Windows 选择窗口的初始大小和位置。|  
  
## <a name="remarks"></a>备注  
 若要创建你的应用程序有用的框架窗口，从派生类`CFrameWnd`。 将成员变量添加到派生类，以存储特定于你的应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 有三种方法来构造框架窗口：  
  
-   直接构造使用其[创建](#create)。  
  
-   直接构造使用其[LoadFrame](#loadframe)。  
  
-   间接构造它使用文档模板。  
  
 您调用之前`Create`或`LoadFrame`，必须构造上使用 c + + 堆的框架窗口对象**新**运算符。 然后再调用`Create`，您还可以注册窗口类[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数设置的帧的图标和类样式。  
  
 使用`Create`成员函数将为快速参数传递的帧创建参数。  
  
 `LoadFrame` 需要较少的参数，而不是`Create`，并改为从资源，包括帧的标题、 图标、 快捷键对应表和菜单检索大部分其默认值。 可由`LoadFrame`，所有这些资源必须具有相同的资源 ID (例如，IDR_MAINFRAME)。  
  
 当`CFrameWnd`对象包含的视图和文档、 通过的框架，而不是直接由程序员创建间接。 `CDocTemplate`对象协调帧的创建、 包含视图的创建和连接到相应的文档的视图。 参数`CDocTemplate`构造函数指定`CRuntimeClass`的三个类涉及到 （文档、 框架和视图）。 一个`CRuntimeClass`框架使用对象来动态创建新帧时由用户指定 （例如，通过使用新建文件命令或多个文档界面 (MDI) 窗口新命令）。  
  
 框架窗口类派生自`CFrameWnd`必须使用 DECLARE_DYNCREATE 声明使上述的 RUNTIME_CLASS 机制，才能正常工作。  
  
 一个`CFrameWnd`包含默认实现为 Windows 在典型的应用程序中执行的主窗口的以下函数：  
  
-   一个`CFrameWnd`跟踪当前活动视图独立于 Windows 活动窗口或当前输入的焦点的框架窗口。 当重新激活该框架时，通过调用通知的活动视图`CView::OnActivateView`。  
  
-   命令消息和多个常见的帧通知消息，包括那些由处理`OnSetFocus`， `OnHScroll`，并`OnVScroll`函数的`CWnd`，通过委派`CFrameWnd`对当前活动视图的框架窗口。  
  
-   当前活动视图 （或对于 MDI 框架当前处于活动状态的 MDI 子框架窗口） 可以确定框架窗口的标题。 可以通过关闭 FWS_ADDTOTITLE 样式位的框架窗口中禁用此功能。  
  
-   一个`CFrameWnd`框架窗口管理的控件条、 视图和框架窗口的客户端区域内的其他子窗口的位置。 框架窗口也能工具栏和其他控件条按钮的空闲时间更新。 一个`CFrameWnd`框架窗口还具有用于切换打开和关闭工具栏和状态栏的命令的默认实现。  
  
-   一个`CFrameWnd`框架窗口管理主菜单栏。 当显示弹出菜单时，框架窗口使用 UPDATE_COMMAND_UI 机制来确定哪些菜单项应启用、 禁用或检查。 当用户选择菜单项时，框架窗口更新状态栏使用消息字符串，该命令。  
  
-   一个`CFrameWnd`框架窗口包含可选的快捷键对应表，将自动转换键盘快捷键。  
  
-   一个`CFrameWnd`框架窗口具有可选帮助 ID 与设置`LoadFrame`中所用的上下文相关帮助。 框架窗口是半模式状态，如上下文相关帮助 (SHIFT + F1) 和打印预览模式的主要业务流程协调程序。  
  
-   一个`CFrameWnd`框架窗口将打开一个文件从文件管理器拖放到框架窗口上。 如果注册并与应用程序相关联的文件扩展名，框架窗口来响应发生在用户打开数据文件在文件管理器时或时，动态数据交换 (DDE) 打开请求`ShellExecute`调用 Windows 函数。  
  
-   如果框架窗口是主应用程序窗口 (即`CWinThread::m_pMainWnd`)，当用户关闭应用程序，框架窗口会提示用户保存任何已修改的文档 (对于`OnClose`和`OnQueryEndSession`)。  
  
-   如果框架窗口，应用程序主窗口的框架窗口是运行 WinHelp 的上下文。 关闭帧窗口将关闭 WINHELP。如果启动为此应用程序的，EXE。  
  
 不使用 c + +**删除**运算符来销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd`的实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CFrameWnd`，请参阅[帧 Windows](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 调用此成员函数以激活并还原框架窗口，让它对用户是可见和可用。  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>参数  
 *nCmdShow*  
 指定要传递给参数[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。 默认情况下，该框架所示，正确还原。  
  
### <a name="remarks"></a>备注  
 此成员函数通常称为后诸如 DDE、 OLE、 或其他事件，可能会向用户显示其内容或框架窗口的非用户界面事件。  
  
 默认实现激活该框架并将其置于 Z 顺序的顶部和如有必要，执行应用程序的主框架窗口的相同步骤。  
  
 重写此成员函数以更改如何激活一个帧。 例如，可以强制 MDI 子窗口以最大化。 添加适当的功能，然后调用基类版本使用显式*nCmdShow*。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState  
 调用此成员函数以使框架窗口具有模式。  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd  
 构造`CFrameWnd`对象，但不会创建可见的框架窗口。  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 调用`Create`创建可见的窗口。  
  
##  <a name="create"></a>  CFrameWnd::Create  
 调用以创建并初始化与关联的 Windows 框架窗口`CFrameWnd`对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CWnd* pParentWnd = NULL,  
    LPCTSTR lpszMenuName = NULL,  
    DWORD dwExStyle = 0,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszClassName*  
 指向以 null 结尾的字符串命名的 Windows 类。 类名可以是任何名称与注册`AfxRegisterWndClass`全局函数或`RegisterClass`Windows 函数。 如果为 NULL，将使用预定义的默认`CFrameWnd`属性。  
  
 *lpszWindowName*  
 指向以 null 结尾的字符串的字符串表示窗口名称。 用作标题栏文本。  
  
 *dwStyle*  
 指定的窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。 如果你想要自动显示在窗口中显示的文档的名称的标题栏，请包括 FWS_ADDTOTITLE 样式。  
  
 *rect*  
 指定的大小和窗口的位置。 *RectDefault*值，则允许 Windows 指定大小和新窗口的位置。  
  
 *pParentWnd*  
 指定此框架窗口的父窗口。 顶级框架窗口，此参数应为 NULL。  
  
 *lpszMenuName*  
 标识要用于在窗口的菜单资源的名称。 如果菜单还拥有一个整数 ID，而不是一个字符串，请使用 MAKEINTRESOURCE。 此参数可以为 NULL。  
  
 *dwExStyle*  
 指定扩展的窗口[样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)属性。  
  
 *pContext*  
 指定一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，，然后调用`Create`，它创建的 Windows 框架窗口，并将其附加到`CFrameWnd`对象。 `Create` 初始化窗口的类名和窗口名称，并注册其样式、 父级和关联的菜单的默认值。  
  
 使用`LoadFrame`而非`Create`从资源而不是指定其自变量加载框架窗口。  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 调用`CreateView`创建范围内的视图。  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>参数  
 *pContext*  
 指定视图和文档的类型。  
  
 *nID*  
 视图的 ID 号。  
  
### <a name="return-value"></a>返回值  
 指向`CWnd`如果成功，否则该值为 NULL 的对象。  
  
### <a name="remarks"></a>备注  
 使用此成员函数来创建"视图"不是`CView`-在框架内派生。 在调用`CreateView`，你必须手动设置为活动状态的视图，并将其设置为可见; 这些任务不会自动执行通过`CreateView`。  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar  
 导致要停靠到框架窗口的控件条。  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pBar*  
 指向要停靠控件条。  
  
 *nDockBarID*  
 确定要考虑的停靠的框架窗口的哪些边。 它可以是 0，或一个或多个以下：  
  
- AFX_IDW_DOCKBAR_TOP 停靠到顶边的框架窗口。  
  
- AFX_IDW_DOCKBAR_BOTTOM 停靠到框架窗口的底边。  
  
- AFX_IDW_DOCKBAR_LEFT 停靠到左侧和右侧的框架窗口。  
  
- 框架窗口的右侧 AFX_IDW_DOCKBAR_RIGHT 停靠。  
  
 如果为 0，则可以为停靠在目标框架窗口中启用任何端到停靠控件条。  
  
 *lpRect*  
 确定在屏幕坐标，控件条中的目标框架窗口非工作区中的停靠位置。  
  
### <a name="remarks"></a>备注  
 将对两者的调用中指定的框架窗口的方面之一停靠控件条[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)并[CFrameWnd::EnableDocking](#enabledocking)。 由所选的一侧*nDockBarID*。  
  
##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking  
 调用此函数可启用框架窗口中的可停靠控件条。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 *dwDockStyle*  
 指定的框架窗口的哪些边可用作停靠控件条的站点。 它可以是一个或多项操作：  
  
- CBRS_ALIGN_TOP 允许停靠在工作区的顶部。  
  
- CBRS_ALIGN_BOTTOM 允许客户端区域底部的停靠。  
  
- CBRS_ALIGN_LEFT 允许客户端区域的左侧停靠。  
  
- CBRS_ALIGN_RIGHT 允许客户端区域右侧停靠。  
  
- CBRS_ALIGN_ANY 允许任意一侧的客户端区域停靠。  
  
### <a name="remarks"></a>备注  
 将默认情况下，框架窗口按以下顺序的一侧中停靠控件条： 上、 下、 左、 右。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create)。  
  
##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState  
 调用此成员函数以将框架窗口从有模式更改为无模式。  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>备注  
 `EndModalState` 通过启用了所有情况下，禁用 windows [BeginModalState](#beginmodalstate)。  
  
##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar  
 调用此函数可导致控件栏不停靠到框架窗口。  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>参数  
 *pBar*  
 指向控件条以浮动。  
  
 *点*  
 中的位置，屏幕坐标放置控件条的左上的角的位置。  
  
 *dwStyle*  
 指定是否在其新的框架窗口水平或垂直对齐控件条。 它可以是以下之一：  
  
- CBRS_ALIGN_TOP 纵向排列控件条。  
  
- CBRS_ALIGN_BOTTOM 纵向排列控件条。  
  
- CBRS_ALIGN_LEFT 水平排列控件条。  
  
- CBRS_ALIGN_RIGHT 水平排列控件条。  
  
 如果指定水平和垂直方向传递样式，工具栏将是水平方向。  
  
### <a name="remarks"></a>备注  
 通常情况下，这是在应用程序启动时该程序从上一次执行还原设置。  
  
 当用户释放鼠标左键时不可用于停靠的位置上拖动控件条会导致删除操作时，由框架调用此函数。  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 调用此成员函数以获取指向当前`CDocument`附加到当前活动视图。  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CDocument](../../mfc/reference/cdocument-class.md)。 如果没有当前文档，将返回 NULL。  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 调用此成员函数以获取指向活动的 MDI 框架窗口的多文档界面 (MDI) 子窗口。  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>返回值  
 指向活动的 MDI 子窗口的指针。 如果应用程序是 SDI 应用程序，或 MDI 框架窗口包含没有活动文档，隐式**这**将返回指针。  
  
### <a name="remarks"></a>备注  
 如果没有活动 MDI 子窗体或应用程序是单文档界面 (SDI) 的隐式**这**返回指针。  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 调用此成员函数可获取附加到框架窗口的活动视图 （如果有） 的指针 ( `CFrameWnd`)。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CView](../../mfc/reference/cview-class.md)。 如果没有当前视图，返回 NULL。  
  
### <a name="remarks"></a>备注  
 此函数将返回 NULL 时调用的 MDI 主框架窗口 ( `CMDIFrameWnd`)。 在 MDI 应用程序，MDI 主框架窗口不具有与之关联的视图。 相反，每个单独的子窗口 ( `CMDIChildWnd`) 具有一个或多个关联的视图。 可以通过先找到活动的 MDI 子窗口，然后为该子窗口查找活动视图获取 MDI 应用程序中的活动视图。 通过调用该函数找不到活动的 MDI 子窗口`MDIGetActive`或`GetActiveFrame`在下面的示例所示：  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 调用`GetControlBar`来访问与 ID 相关联的控件条  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 控件条 ID 号。  
  
### <a name="return-value"></a>返回值  
 指向与 ID 相关联的控件条的指针  
  
### <a name="remarks"></a>备注  
 *NID*参数引用的唯一标识符传递给`Create`控件条的方法。 有关控件条的详细信息，请参阅标题为主题[控件条](../../mfc/control-bars.md)。  
  
 `GetControlBar` 将返回控件条，即使它浮动的因此不是当前帧的子窗口。  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 调用此成员函数来存储有关框架窗口的控件条中的状态信息`CDockState`对象。  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>参数  
 *state*  
 包含在返回的框架窗口的控件条的当前状态。  
  
### <a name="remarks"></a>备注  
 然后可以写入的内容`CDockState`存储使用`CDockState::SaveState`或`Serialize`。 如果以后想要还原到以前的状态的控件条，加载的状态与`CDockState::LoadState`或`Serialize`，然后调用`SetDockState`要应用于框架窗口的控件条的前一状态。  
  
##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState  
 检索当前的 MFC 应用程序中的菜单的显示状态。  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>返回值  
 返回值可以具有以下值：  
  
-   AFX_MBS_VISIBLE (0x01)-菜单可见。  
  
-   AFX_MBS_HIDDEN (0x02)-菜单处于隐藏状态。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误，此方法在调试模式中断言，并会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility  
 指示当前的 MFC 应用程序中的菜单的默认状态是隐藏还是可见。  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>返回值  
 此方法将返回以下值之一：  
  
-   AFX_MBV_KEEPVISIBLE (0x01)-菜单显示在所有时间和提供的默认不具有焦点。  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02)-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 ALT 键以显示菜单，并为其提供焦点。 如果显示菜单上，则按 ALT 或 ESC 键以隐藏它。  
  
-   AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) （按位组合 (OR)）-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 F10 键，以显示菜单，并为其提供焦点。 如果显示菜单上，则按 F10 键来切换打开或关闭菜单焦点。 直到按下 ALT 或 ESC 键，可以将其隐藏，则会显示菜单。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误，此方法在调试模式中断言，并会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar  
 调用此成员函数可获得到状态栏的指针。  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>返回值  
 到状态栏窗口的指针。  
  
##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString  
 重写此函数可提供自定义字符串的命令 Id。  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 所需的消息的资源 ID。  
  
 *rMessage*  
 `CString` 要将消息放到其中的对象。  
  
### <a name="remarks"></a>备注  
 默认实现只需加载指定的字符串*nID*从资源文件。 当状态栏中的消息字符串需要更新时，由框架调用此函数。  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 检索窗口对象的标题。  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含当前窗口对象的标题。  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 调用`IntitialUpdateFrame`创建具有的新框架后`Create`。  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>参数  
 *来写*  
 文档框架窗口所关联到的点。 可以为 NULL。  
  
 *bMakeVisible*  
 如果为 TRUE，指示在帧应成为可见且处于活动状态。 如果为 FALSE，则没有后代都可见。  
  
### <a name="remarks"></a>备注  
 这将导致在接收该框架窗口中的所有视图及其`OnInitialUpdate`调用。  
  
 此外，如果存在以前不活动的视图，框架窗口的主视图使处于活动状态。 主视图是具有子 AFX_IDW_PANE_FIRST ID 的视图。 最后，框架窗口变为可见如果*bMakeVisible*为非零值。 如果*bMakeVisible*为 0，则当前焦点和框架窗口的可见状态将保持不变。 不需要使用的框架实现的新文件和文件打开时调用此函数。  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 调用此成员函数来检查是否框架窗口为模式对话框或无模式。  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果否。否则为 0。  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 调用此成员函数可确定在窗口中的拆分器栏当前正在移动。  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行中; 为非零值否则为 0。  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 调用以加载指定的快捷键对应表。  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>参数  
 *lpszResourceName*  
 标识加速器资源的名称。 如果使用整数 id。 标识资源，请使用 MAKEINTRESOURCE  
  
### <a name="return-value"></a>返回值  
 非零，如果已成功加载快捷键对应表;否则为 0。  
  
### <a name="remarks"></a>备注  
 只有一个表可以加载一次。  
  
 应用程序终止时，从资源中加载的快捷键对应表会被自动释放。  
  
 如果调用`LoadFrame`若要创建框架窗口，框架将加载快捷键对应表以及菜单和图标资源，然后对此成员函数的后续调用不必要。  
  
##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState  
 调用此函数可还原框架窗口拥有每个控件条的设置。  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 *lpszProfileName*  
 初始化 (INI) 文件中的节或状态信息都存储在 Windows 注册表中的键的名称。  
  
### <a name="remarks"></a>备注  
 还原的信息包括可见性、 水平/垂直方向、 停靠状态和控件条的位置。  
  
 你想要还原的设置必须写入到注册表，然后再调用`LoadBarState`。 通过调用将信息写入到注册表[CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)。 通过调用将信息写入到 INI 文件[SaveBarState](#savebarstate)。  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 调用以动态创建框架窗口中的资源信息。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 *nIDResource*  
 与框架窗口关联的共享资源的 ID。  
  
 *dwDefaultStyle*  
 帧[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果你想要自动显示在窗口中显示的文档的名称的标题栏，请包括 FWS_ADDTOTITLE 样式。  
  
 *pParentWnd*  
 指向帧的父级的指针。  
  
 *pContext*  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为 NULL。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，，然后调用`LoadFrame`，它将加载 Windows 框架窗口和关联的资源并附加到框架窗口`CFrameWnd`对象。 *NIDResource*参数指定的菜单、 快捷键对应表、 图标和框架窗口的标题的字符串资源。  
  
 使用`Create`成员函数而非`LoadFrame`时想要指定所有框架窗口的创建参数。  
  
 框架将调用`LoadFrame`在创建框架窗口使用文档模板对象。  
  
 框架将使用*pContext*参数，以指定的对象以连接到框架窗口，其中包括任何包含的视图对象。 可以设置*pContext*参数为 NULL 时，调用`LoadFrame`。  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 启用此数据成员时 （这是默认值），用户会拉取菜单时，将自动禁用不具有 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 处理程序的菜单项。  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>备注  
 有一个 ON_COMMAND 处理程序，但没有 ON_UPDATE_COMMAND_UI 处理程序的菜单项将自动启用。  
  
 当设置此数据成员时，菜单项会自动启用与工具栏按钮处于启用状态的方式相同。  
  
> [!NOTE]
> `m_bAutoMenuEnable` 具有对顶级菜单项没有影响。  
  
 此数据成员简化了基于当前所选内容的可选命令的实现，而无需编写 ON_UPDATE_COMMAND_UI 用于启用和禁用菜单项的处理程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 调用此成员函数可在 OLE 就地激活过程协商在框架窗口的边框空间。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>参数  
 *nBorderCmd*  
 包含中的以下值之一`enum BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 *lpRectBorder*  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定边框的坐标。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是`CFrameWnd`OLE 边框空间协商的实现。  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 每当在指定的控件栏上执行某个操作时调用。  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 栏显示控件的 ID。  
  
### <a name="return-value"></a>返回值  
 控件条存在; 如果非零值否则为 0。  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 处理的就地项的 SHIFT + F1 帮助。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>备注  
 若要启用上下文相关帮助，必须添加  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 语句在`CFrameWnd`类消息映射，还将添加一个快捷键对应表项，通常 SHIFT + F1，若要启用此成员函数。  
  
 如果你的应用程序的 OLE 容器，`OnContextHelp`将放到帮助模式包含在框架窗口对象中的所有就地项。 然后，光标更改为一个箭头和问号，以及用户可以将鼠标指针移动，并按鼠标左键选择对话框、 窗口、 菜单或命令按钮。 此成员函数将调用 Windows 函数`WinHelp`与光标下的对象的帮助上下文。  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 在执行期间由框架调用`OnCreate`。  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>参数  
 *lpc*  
 指向 Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md)结构。  
  
 *pContext*  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 永远不会调用此函数。  
  
 此函数的默认实现将创建`CView`对象中提供的信息从*pContext*如有可能。  
  
 重写此函数以重写传入的值`CCreateContext`对象或更改创建框架窗口的主工作区中的方式控件。 `CCreateContext`中介绍了可以重写的成员[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)类。  
  
> [!NOTE]
>  将传入的值不为`CREATESTRUCT`结构。 它们仅供参考之用。 如果你想要重写初始窗口矩形，例如，重写`CWnd`成员函数[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 当系统即将隐藏菜单栏中当前的 MFC 应用程序时，调用此函数。  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序使应用程序可以在系统即将隐藏菜单时执行自定义操作。 不能防止菜单上隐藏，但可以例如，调用其他方法来检索菜单样式或状态。  
  
##  <a name="onsetpreviewmode"></a>  Cframewnd:: Onsetpreviewmode  
 调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>参数  
 *bPreview*  
 指定将应用程序放置在打印预览模式下。 设置为 TRUE 以将放在打印预览中，为 FALSE，则取消预览模式。  
  
 *pState*  
 一个指向`CPrintPreviewState`结构。  
  
### <a name="remarks"></a>备注  
 默认实现禁用所有标准工具栏，并在主菜单和客户端主窗口将隐藏。 这会到临时 SDI 框架窗口启用 MDI 框架窗口。  
  
 重写此成员函数以自定义隐藏和显示的控件条和其他框架窗口部分在打印预览的过程。 调用基类实现从中重写版本。  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 当系统即将显示菜单栏中当前的 MFC 应用程序时，调用此函数。  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序可以让应用程序即将显示菜单时执行自定义操作。 不能防止菜单显示，但您可以例如，调用其他方法来检索菜单样式或状态。  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 更新关联的菜单时由框架调用。  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 *pCmdUI*  
 一个指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象，表示生成更新命令的菜单。 更新处理程序调用[启用](../../mfc/reference/ccmdui-class.md#enable)成员函数`CCmdUI`对象，通过*pCmdUI*来更新用户界面。  
  
##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout  
 标准控件条切换打开或关闭时或框架窗口调整大小时，由框架调用。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bNotify*  
 确定框架窗口的活动的就地项是否接收通知的布局更改。 如果为 TRUE，项是收到通知;否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此成员函数的默认实现调用`CWnd`成员函数`RepositionBars`帧以及如主要的客户端窗口中重新定位所有控件条 (通常`CView`或 MDICLIENT)。  
  
 重写此成员函数以框架窗口的布局已发生更改后进行控制的外观和行为的控件条。 例如，调用它时启用或禁用的控件条或添加另一个控件条。  
  
##  <a name="rectdefault"></a>  CFrameWnd::rectDefault  
 将其传递静态`CRect`作为参数创建一个窗口，以允许 Windows 选择窗口的初始大小和位置时。  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState  
 调用此函数可存储有关每个拥有的框架窗口的控件条的信息。  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpszProfileName*  
 初始化文件中的节或状态信息都存储在 Windows 注册表中的键的名称。  
  
### <a name="remarks"></a>备注  
 此信息可以从初始化文件使用读取[LoadBarState](#loadbarstate)。 存储的信息包括可见性水平/垂直方向、 停靠状态和控件条的位置。  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 指定要用于丰富预览的活动视图的指定的视图。  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>参数  
 *pViewNew*  
 指向要激活的视图的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView  
 调用此成员函数可设置的活动视图。  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pViewNew*  
 指定一个指向[CView](../../mfc/reference/cview-class.md)对象或 NULL 表示没有活动的视图。  
  
 *bNotify*  
 指定视图是否为激活接收通知。 如果为 TRUE，`OnActivateView`称为新视图; 如果为 FALSE，不是。  
  
### <a name="remarks"></a>备注  
 框架将自动调用此函数，如用户将焦点更改到框架窗口中的视图。 您可以显式调用`SetActiveView`将焦点更改到指定的视图。  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 调用此成员函数以将状态信息存储在应用`CDockState`到框架窗口的控件条对象。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>参数  
 *state*  
 适用于框架窗口的控件条存储的状态。  
  
### <a name="remarks"></a>备注  
 若要还原以前的状态的控件条，可以加载与存储的状态`CDockState::LoadState`或`Serialize`，然后使用`SetDockState`要应用于框架窗口的控件条。 以前的状态存储在`CDockState`对象 `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 隐藏或显示当前的 MFC 应用程序中设置菜单的显示状态。  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*nState*|指定是否显示或隐藏菜单。 *NState*参数可以具有以下值：<br /><br /> -如果它隐藏的但如果它是可见不起作用，AFX_MBS_VISIBLE (0x01)-显示菜单。<br />-如果可见，但如果它隐藏不起作用，AFX_MBS_HIDDEN (0x02)-隐藏菜单。|  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功更改菜单状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误，此方法在调试模式中断言，并会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 在当前的 MFC 应用程序是隐藏还是可见设置菜单的默认行为。  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*nStyle*|指定菜单是隐藏的默认情况下或可见且具有焦点。 *NStyle*参数可以具有以下值：<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)-<br />     菜单显示在任何时候，并且默认情况下没有焦点。<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 ALT 键以显示菜单，并为其提供焦点。 如果显示菜单上，则按 ALT 或 ESC 键，若要隐藏菜单。<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     （按位组合 (OR)）-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 F10 键，以显示菜单，并为其提供焦点。 如果显示菜单上，则按 F10 键来切换打开或关闭菜单焦点。 直到按下 ALT 或 ESC 键，可以将其隐藏，则会显示菜单。|  
  
### <a name="remarks"></a>备注  
 如果的值*nStyle*参数不是有效的此方法断言在调试模式并引发[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)在发布模式下。 对于其他运行时错误，此方法在调试模式中断言并引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
 此方法会影响编写适用于 Windows Vista 及更高版本的应用程序中的菜单的状态。  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 调用此函数将字符串置于 id 为 0 的状态栏窗格。  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 指向要放置在状态栏上的字符串。  
  
 *nID*  
 字符串的字符串资源 ID 放在状态栏上。  
  
### <a name="remarks"></a>备注  
 这通常是状态栏的最左侧，且最长，窗格。  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 设置显示在任务栏上的 Windows 7 进度栏的当前位置。  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>参数  
 *nProgressPos*  
 指定要设置的位置。 它必须在设置的范围内`SetProgressBarRange`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 设置显示在任务栏上的 Windows 7 进度栏的范围。  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>参数  
 *nRangeMin*  
 最小值。  
  
 *nRangeMax*  
 最大值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 设置的类型和任务栏按钮上显示进度指示器的状态。  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>参数  
 *tbpFlags*  
 控制进度按钮的当前状态的标志。 指定以下任一标记由于所有状态互相都排斥： TBPF_NOPROGRESS、 TBPF_INDETERMINATE、 TBPF_NORMAL、 TBPF_ERROR、 TBPF_PAUSED。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 已重载。 将覆盖应用到一个任务栏按钮，以指示应用程序状态或通知用户。  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>参数  
 *nIDResource*  
 指定要用作覆盖图标的资源 ID。 请参阅说明*hIcon*有关详细信息。  
  
 *lpcszDescr*  
 指向提供可访问性目的的覆盖，传达的信息的 alt 文本版本的字符串的指针。  
  
 *hIcon*  
 要用作在覆盖区上的图标的句柄。 这应该是一个小图标，测量每英寸点数 (dpi) 96 点在 16 x 16 像素。 如果覆盖图标已应用于任务栏按钮，则替换该现有覆盖区。 此值可以为 NULL。 如何处理 NULL 值取决于任务栏按钮表示单个窗口或 windows 组。 它负责调用应用程序来释放*hIcon*不再需要时。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 TRUE如果操作系统版本低于 Windows 7 或出错时设置图标，则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 设置窗口对象的标题。  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>参数  
 *lpszTitle*  
 指向包含标题的窗口对象的字符串的指针。  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 调用此成员函数以显示或隐藏控件条。  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>参数  
 *pBar*  
 指向控件条是显示还是隐藏。  
  
 *bShow*  
 如果为 TRUE，则指定控件条是要显示。 如果为 FALSE，指定控件条是处于隐藏状态。  
  
 *bDelay*  
 如果为 TRUE，延迟显示控件条。 如果为 FALSE，则显示控制条立即。  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 调用此成员函数以显示所有的后代的时段`CFrameWnd`对象。  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 *bShow*  
 指定是否拥有的窗口是显示还是隐藏。  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)
