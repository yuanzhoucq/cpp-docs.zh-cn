---
title: "CFrameWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- frame window classes, base class
- single document interface (SDI), frame windows
- frame windows, creating
- CFrameWnd class
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8df28ed10208973832476b68140594c206bc22b
ms.lasthandoff: 02/24/2017

---
# <a name="cframewnd-class"></a>CFrameWnd 类
提供 Windows 单文档界面 (SDI) 重叠式或弹出框架窗口功能，并提供管理窗口的成员。  
  
## <a name="syntax"></a>语法  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|构造 `CFrameWnd` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|向用户发出框架可见和可用。|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|将模式设置的框架窗口。|  
|[CFrameWnd::Create](#create)|调用创建并初始化与关联的窗口框架窗口`CFrameWnd`对象。|  
|[CFrameWnd::CreateView](#createview)|创建一个视图不源自为内的`CView`。|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|停靠控件条。|  
|[CFrameWnd::EnableDocking](#enabledocking)|允许要停靠控件条。|  
|[CFrameWnd::EndModalState](#endmodalstate)|结束框架窗口模式状态。 通过启用了所有 windows 通过停用`BeginModalState`。|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|浮动的控件条。|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|返回活动**CDocument**对象。|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|返回活动`CFrameWnd`对象。|  
|[CFrameWnd::GetActiveView](#getactiveview)|返回活动`CView`对象。|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|检索控件条。|  
|[CFrameWnd::GetDockState](#getdockstate)|检索框架窗口的停靠状态。|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|检索当前的 MFC 应用程序中的菜单的显示状态。|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|指示当前的 MFC 应用程序中的菜单的默认行为是隐藏还是可见。|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|返回指向状态栏属于框架窗口的指针。|  
|[CFrameWnd::GetMessageString](#getmessagestring)|检索消息对应的命令 id。|  
|[CFrameWnd::GetTitle](#gettitle)|检索相关的控件条的标题。|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|导致`OnInitialUpdate`属于要调用的框架窗口中的所有视图的成员函数。|  
|[CFrameWnd::InModalState](#inmodalstate)|返回一个值，该值指示框架窗口处于模式状态。|  
|[CFrameWnd::IsTracking](#istracking)|确定当前移动拆分器栏。|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|调用以加载快捷键对应表。|  
|[CFrameWnd::LoadBarState](#loadbarstate)|调用它来还原控制条设置。|  
|[CFrameWnd::LoadFrame](#loadframe)|调用，用于动态创建框架窗口中的资源信息。|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|协商在框架窗口的边框空间。|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|只要指定的控件条上执行某个操作调用。|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|处理就地项的 SHIFT + F1 帮助。|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|执行和跳出执行打印预览模式下，将设置应用程序的主框架窗口。|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|更新关联的菜单时，由框架调用。|  
|[CFrameWnd::RecalcLayout](#recalclayout)|重新定位的控件条`CFrameWnd`对象。|  
|[CFrameWnd::SaveBarState](#savebarstate)|调用以保存控件条的设置。|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|指定要用于丰富预览中的活动视图的指定的视图。|  
|[CFrameWnd::SetActiveView](#setactiveview)|设置活动`CView`对象。|  
|[CFrameWnd::SetDockState](#setdockstate)|若要将停靠在主窗口中的框架窗口的调用。|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|将菜单上的显示状态设置为隐藏或显示当前的 MFC 应用程序中。|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|当前的 MFC 应用程序是隐藏还是可见中设置菜单上的默认行为。|  
|[CFrameWnd::SetMessageText](#setmessagetext)|设置标准状态栏的文本。|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|设置 Windows 7 在任务栏上显示的进度栏的当前位置。|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|将 Windows 7 在任务栏上显示的进度栏范围的设置。|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|设置类型和状态的任务栏按钮上显示的进度指示器。|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|已重载。 将一个覆盖区应用到任务栏按钮，以指示应用程序的状态或向用户通知。|  
|[CFrameWnd::SetTitle](#settitle)|设置相关的控件条的标题。|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|调用以显示控件条。|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|显示所有的派生的窗口`CFrameWnd`对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|创建一个客户端窗口的帧。|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|在当前的 MFC 应用程序中的菜单处于隐藏状态之前调用。|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|显示当前的 MFC 应用程序中的菜单前调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|控件自动启用和禁用的菜单项的功能。|  
|[CFrameWnd::rectDefault](#rectdefault)|将此传入静态`CRect`作为参数在创建时`CFrameWnd`对象，以允许 Windows 选择窗口的初始大小和位置。|  
  
## <a name="remarks"></a>备注  
 若要创建您的应用程序的有用的框架窗口，从派生类`CFrameWnd`。 将成员变量添加到派生的类来存储特定于您的应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 有三种方法来构造框架窗口︰  
  
-   直接构造使用[创建](#create)。  
  
-   直接构造使用[LoadFrame](#loadframe)。  
  
-   间接构造它使用文档模板。  
  
 您调用之前**创建**或`LoadFrame`，您必须先构造使用 c + + 堆上的框架窗口对象**新**运算符。 之前，先调用**创建**，也可以注册窗口类[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数可设置的帧图标和类样式。  
  
 使用**创建**成员函数以将为快速参数传递的帧的创建参数。  
  
 `LoadFrame`需要较少的参数比**创建**，并改为从资源，包括框架的标题、 图标、 快捷键对应表和菜单检索大部分其默认值。 可由`LoadFrame`，所有这些资源都必须具有相同的资源 ID (例如， **IDR_MAINFRAME**)。  
  
 当`CFrameWnd`对象包含视图和文档，就会创建间接的框架，而不是直接由程序员。 `CDocTemplate`对象协调的框架的创建、 包含视图的创建和连接到相应的文档的视图。 参数`CDocTemplate`构造函数指定`CRuntimeClass`的三个类涉及 （文档、 框架和视图）。 一个`CRuntimeClass`框架使用对象来动态地创建新帧时由用户指定 （例如，通过使用新建文件命令或多个文档界面 (MDI) 窗口中新建命令）。  
  
 框架窗口类派生自`CFrameWnd`必须使用声明`DECLARE_DYNCREATE`使上述`RUNTIME_CLASS`机制才能正常工作。  
  
 一个`CFrameWnd`包含默认实现为 Windows 中典型的应用程序执行主窗口的下列函数︰  
  
-   一个`CFrameWnd`跟踪当前活动视图独立于 Windows 活动窗口或当前输入的焦点的框架窗口。 活动视图重新激活该框架后，将通过调用通知`CView::OnActivateView`。  
  
-   命令消息并将其多个常见的帧通知消息，包括那些由`OnSetFocus`， `OnHScroll`，和`OnVScroll`函数`CWnd`，通过委派`CFrameWnd`对当前活动视图的框架窗口。  
  
-   当前活动视图 （或对于 MDI 框架当前处于活动状态的 MDI 子框架窗口） 可以确定框架窗口的标题。 可以通过关闭禁用此功能**FWS_ADDTOTITLE**框架窗口的样式位。  
  
-   一个`CFrameWnd`框架窗口管理控件条、 视图和框架窗口的客户端区域内其他子窗口的位置。 框架窗口还执行空闲时间来进行更新的工具栏和其他控件条按钮。 一个`CFrameWnd`框架窗口还具有用于切换打开和关闭工具栏和状态栏的命令的默认实现。  
  
-   一个`CFrameWnd`框架窗口管理主菜单栏。 框架窗口显示一个弹出菜单时，请使用**UPDATE_COMMAND_UI**机制来确定哪些菜单项应启用、 禁用或检查。 当用户选择菜单项时，框架窗口使用该命令的消息字符串更新状态栏。  
  
-   一个`CFrameWnd`框架窗口包含可选的快捷键对应表自动转换键盘快捷键。  
  
-   一个`CFrameWnd`框架窗口具有可选帮助 ID 与设置`LoadFrame`所用的上下文相关帮助。 框架窗口是半模式状态，如上下文相关帮助 (SHIFT + F1) 和打印预览模式的主要 orchestrator。  
  
-   一个`CFrameWnd`框架窗口将打开的文件从文件管理器中拖动并放置在框架窗口上。 如果文件扩展名已注册并与应用程序相关联，框架窗口的请求作出响应动态数据交换 (DDE) 打开，或在用户打开数据文件在文件管理器时出现**ShellExecute**调用 Windows 函数。  
  
-   如果框架窗口是主应用程序窗口 (也就是说， `CWinThread::m_pMainWnd`)，当用户关闭应用程序时，框架窗口会提示用户保存修改后的任何文档 (为`OnClose`和`OnQueryEndSession`)。  
  
-   如果框架窗口是主应用程序窗口，框架窗口是运行 WinHelp 的上下文。 关闭帧窗口将关闭 WINHELP。如果启动此应用程序的帮助的 EXE。  
  
 请不要使用 c + +**删除**要销毁框架窗口的运算符。 请改用 `CWnd::DestroyWindow` 。 `CFrameWnd`实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CFrameWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="activateframe"></a>CFrameWnd::ActivateFrame  
 调用该成员函数以激活并还原框架窗口，以便对用户是可见和可用。  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>参数  
 `nCmdShow`  
 指定要传递给参数[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。 默认情况下，该框架所示，正确还原。  
  
### <a name="remarks"></a>备注  
 通常在诸如 DDE、 OLE 或其他事件。 可能会向用户显示其内容或框架窗口的非用户界面事件后调用此成员函数。  
  
 默认实施激活该框架，再将其带到 Z 顺序的顶层和如有必要，执行应用程序的主框架窗口的相同步骤。  
  
 重写该成员函数以更改激活一个帧的方式。 例如，您可以强制 MDI 子窗口要最大化。 添加适当的功能，然后调用其显式的基类版本`nCmdShow`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&1;](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>CFrameWnd::BeginModalState  
 调用此成员函数以使框架窗口具有模式。  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>CFrameWnd::CFrameWnd  
 构造`CFrameWnd`对象，但不会创建可见的框架窗口。  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 调用**创建**来创建可见的窗口。  
  
##  <a name="create"></a>CFrameWnd::Create  
 调用创建并初始化与关联的窗口框架窗口`CFrameWnd`对象。  
  
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
 `lpszClassName`  
 指向以 null 结尾的字符串名称的 Windows 类 string。 类名可以是任何名称注册`AfxRegisterWndClass`全局函数或**RegisterClass** Windows 函数。 如果**NULL**，使用预定义的默认`CFrameWnd`属性。  
  
 `lpszWindowName`  
 指向以 null 结尾的字符串表示窗口名称。 用作标题栏文本。  
  
 `dwStyle`  
 指定的窗口[样式](../../mfc/reference/window-styles.md)属性。 包括**FWS_ADDTOTITLE** ，如你想要自动显示的名称出现在窗口中的文档的标题栏的样式。  
  
 `rect`  
 指定的大小和窗口的位置。 `rectDefault`值使 Windows 可以指定的大小和新窗口的位置。  
  
 `pParentWnd`  
 指定该框架窗口的父窗口。 此参数应为**NULL**的顶层框架窗口。  
  
 *lpszMenuName*  
 标识要使用与窗口的菜单资源的名称。 使用**MAKEINTRESOURCE**如果的菜单还拥有一个整数 ID，而不是一个字符串。 此参数可以为**NULL**。  
  
 `dwExStyle`  
 指定扩展的窗口[样式](../../mfc/reference/extended-window-styles.md)属性。  
  
 `pContext`  
 指定一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，然后再调用**创建**，它创建 Windows 框架窗口，并将其附加到`CFrameWnd`对象。 **创建**初始化窗口的类名和窗口名称，并注册其样式、 父节点和关联的菜单的默认值。  
  
 使用`LoadFrame`而不是**创建**要从中加载框架窗口而不是指定其参数的资源。  
  
##  <a name="createview"></a>CFrameWnd::CreateView  
 调用`CreateView`创建视图，在范围内的。  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 指定视图和文档的类型。  
  
 `nID`  
 视图的 ID 号。  
  
### <a name="return-value"></a>返回值  
 指向`CWnd`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 使用此成员函数来创建"视图"不`CView`-派生的框架内。 在调用`CreateView`，您必须手动设置为活动状态的视图，并将其设置为可见; 这些任务不会自动执行通过`CreateView`。  
  
##  <a name="dockcontrolbar"></a>CFrameWnd::DockControlBar  
 导致要停靠到框架窗口的控件条。  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pBar`  
 指向要停靠控件条。  
  
 `nDockBarID`  
 确定框架窗口时要考虑的停靠的哪些的边。 它可以是 0，或一个或多项操作︰  
  
- `AFX_IDW_DOCKBAR_TOP`将停靠在框架窗口的顶边。  
  
- **AFX_IDW_DOCKBAR_BOTTOM**停靠到框架窗口的底部。  
  
- `AFX_IDW_DOCKBAR_LEFT`停靠到框架窗口的左侧。  
  
- `AFX_IDW_DOCKBAR_RIGHT`将停靠在框架窗口的右侧。  
  
 如果为 0，任何一侧为停靠在目标框架窗口中启用可停靠控件条。  
  
 `lpRect`  
 确定在屏幕坐标中，将控件条中的目标框架窗口的非工作区中的停靠位置。  
  
### <a name="remarks"></a>备注  
 将到个边的同时调用中指定的框架窗口停靠控件条[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd::EnableDocking](#enabledocking)。 选择的一侧由`nDockBarID`。  
  
##  <a name="enabledocking"></a>CFrameWnd::EnableDocking  
 调用此函数可启用在框架窗口中的可停靠控件条。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwDockStyle`  
 指定的框架窗口的哪些边可以充当以停靠控件条的站点。 它可以是一个或多项操作︰  
  
- `CBRS_ALIGN_TOP`允许在工作区的顶部停靠。  
  
- `CBRS_ALIGN_BOTTOM`允许客户端区域底部的停靠。  
  
- `CBRS_ALIGN_LEFT`允许在客户端区域的左侧停靠。  
  
- `CBRS_ALIGN_RIGHT`允许客户端区域右侧停靠。  
  
- `CBRS_ALIGN_ANY`允许在客户端区域的任何一侧上停靠。  
  
### <a name="remarks"></a>备注  
 框架窗口按以下顺序的一侧将默认情况下，停靠控件条︰ 上、 下、 左、 右。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create)。  
  
##  <a name="endmodalstate"></a>CFrameWnd::EndModalState  
 调用此成员函数以将框架窗口从有模式更改为无模式。  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>备注  
 `EndModalState`通过启用了所有 windows 通过停用[BeginModalState](#beginmodalstate)。  
  
##  <a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar  
 调用此函数可导致以未停靠到框架窗口的控件条。  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>参数  
 `pBar`  
 指向要浮动的控件栏。  
  
 `point`  
 中的位置，屏幕坐标中，将在其中放置控件条的左上的角。  
  
 `dwStyle`  
 指定是否在其新的框架窗口中水平或垂直对齐控件条。 它可以是任何下列选项之一︰  
  
- `CBRS_ALIGN_TOP`垂直排列控件条。  
  
- `CBRS_ALIGN_BOTTOM`垂直排列控件条。  
  
- `CBRS_ALIGN_LEFT`水平排列控件条。  
  
- `CBRS_ALIGN_RIGHT`水平排列控件条。  
  
 如果传递了指定水平和垂直方向的样式，工具栏将是水平方向。  
  
### <a name="remarks"></a>备注  
 通常情况下，这是在应用程序启动时该程序从上一次执行还原设置。  
  
 当用户通过拖动控件条通过不可用于停靠的位置时松开鼠标左键导致拖放操作时，将由框架调用此函数。  
  
##  <a name="getactivedocument"></a>CFrameWnd::GetActiveDocument  
 调用此成员函数以获取指向当前**CDocument**附加到当前活动视图。  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CDocument](../../mfc/reference/cdocument-class.md)。 如果没有当前的文档，将返回**NULL**。  
  
##  <a name="getactiveframe"></a>CFrameWnd::GetActiveFrame  
 调用该成员函数以获取指向活动的多文档界面 (MDI) 子窗口的 MDI 框架窗口。  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>返回值  
 指向活动的 MDI 子窗口的指针。 如果应用程序是 SDI 应用程序，或 MDI 框架窗口具有任何活动文档中，隐式**这**将返回指针。  
  
### <a name="remarks"></a>备注  
 如果没有任何活动 MDI 子窗体或应用程序为单文档界面 (SDI) 的隐式**这**返回指针。  
  
##  <a name="getactiveview"></a>CFrameWnd::GetActiveView  
 调用此成员函数以获取附加到框架窗口的活动视图 （如果有） 的指针 ( `CFrameWnd`)。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CView](../../mfc/reference/cview-class.md)。 如果没有当前的视图，将返回**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数将返回**NULL**为 MDI 主框架窗口调用时 ( `CMDIFrameWnd`)。 在 MDI 应用程序，MDI 主框架窗口没有与其相关联的视图。 相反，每个单独的子窗口 ( `CMDIChildWnd`) 具有一个或多个关联的视图。 可以通过先找到活动的 MDI 子窗口，然后针对该子窗口查找活动视图获取 MDI 应用程序中的活动视图。 通过调用该函数找不到活动的 MDI 子窗口`MDIGetActive`或**GetActiveFrame**在下面的示例所示︰  
  
 [!code-cpp[NVC_MFCWindowing #&2;](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>CFrameWnd::GetControlBar  
 调用`GetControlBar`才能访问与 ID 相关联的控件条  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件条 ID 号。  
  
### <a name="return-value"></a>返回值  
 一个指向与 ID 相关联的控件条  
  
### <a name="remarks"></a>备注  
 `nID`参数是指传递到的唯一标识符**创建**控件条的方法。 有关控件条的详细信息，请参阅标题为主题[控件条](../../mfc/control-bars.md)。  
  
 `GetControlBar`将返回控件条，即使它浮动的因此不是当前帧的子窗口。  
  
##  <a name="getdockstate"></a>CFrameWnd::GetDockState  
 调用此成员函数以存储有关框架窗口的控件条中的状态信息`CDockState`对象。  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>参数  
 `state`  
 包含在返回的框架窗口的控件条的当前状态。  
  
### <a name="remarks"></a>备注  
 然后可以编写的内容`CDockState`存储使用`CDockState::SaveState`或`Serialize`。 如果您以后想要还原到以前的状态的控件条，加载将状态与`CDockState::LoadState`或`Serialize`，然后调用`SetDockState`要应用于框架窗口的控件条的前一状态。  
  
##  <a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState  
 检索当前的 MFC 应用程序中的菜单的显示状态。  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>返回值  
 返回值可以具有以下值︰  
  
-   AFX_MBS_VISIBLE (0x01) – 菜单可见。  
  
-   AFX_MBS_HIDDEN (0x02) – 菜单处于隐藏状态。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility  
 指示当前的 MFC 应用程序中的菜单的默认状态是隐藏还是可见。  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>返回值  
 此方法返回以下值之一︰  
  
-   AFX_MBV_KEEPVISIBLE (0x01) 的菜单显示在所有时间，以及通过默认不具有焦点。  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02)-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 ALT 键显示菜单，然后使其获得焦点。 如果显示菜单上，按 ALT 或 ESC 键可以将其隐藏。  
  
-   AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0x04) （按位组合 (OR)）-默认情况下隐藏菜单。 如果隐藏菜单上，按 F10 键，以显示菜单，然后使其获得焦点。 如果显示菜单上，按 F10 键，以切换焦点打开或关闭菜单。 直到按 ALT 或 ESC 键，以将其隐藏起来，将显示菜单。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmessagebar"></a>CFrameWnd::GetMessageBar  
 调用该成员函数以获取指向状态栏的指针。  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>返回值  
 指针，指向状态栏窗口中。  
  
##  <a name="getmessagestring"></a>CFrameWnd::GetMessageString  
 重写此函数可提供自定义字符串的命令 Id。  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 所需的消息的资源 ID。  
  
 `rMessage`  
 `CString`要将消息放到其中的对象。  
  
### <a name="remarks"></a>备注  
 默认实现只需加载指定的字符串`nID`资源文件中。 在状态栏中的消息字符串需要更新时，将由框架调用此函数。  
  
##  <a name="gettitle"></a>CFrameWnd::GetTitle  
 检索窗口对象的标题。  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它包含窗口对象的当前标题。  
  
##  <a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame  
 调用**IntitialUpdateFrame**创建与新帧后**创建**。  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向以到框架窗口的关联的文档。 可以是**NULL**。  
  
 `bMakeVisible`  
 如果**TRUE**，表示该框架应变得可见并处于活动状态。 如果**FALSE**，没有后代均能看见。  
  
### <a name="remarks"></a>备注  
 这将导致在接收该框架窗口中的所有视图及其`OnInitialUpdate`调用。  
  
 此外，如果没有以前的活动视图，框架窗口的主视图设为活动。 主视图是子 id 为视图**AFX_IDW_PANE_FIRST**。 最后，框架窗口中变为可见如果`bMakeVisible`为非零值。 如果`bMakeVisible`为 0，则当前焦点和框架窗口的可见状态将保持不变。 不需要使用的框架实现文件新建和打开文件时调用此函数。  
  
##  <a name="inmodalstate"></a>CFrameWnd::InModalState  
 调用该成员函数以检查框架窗口是否模式或无模式对话框。  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果是;否则为 0。  
  
##  <a name="istracking"></a>CFrameWnd::IsTracking  
 调用该成员函数以确定当前移动窗口中的拆分器栏。  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行中; 则为非否则为 0。  
  
##  <a name="loadacceltable"></a>CFrameWnd::LoadAccelTable  
 调用以加载指定的快捷键对应表。  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 标识快捷键资源的名称。 使用**MAKEINTRESOURCE**如果该资源标识使用整数 id。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功加载快捷键对应表;否则为 0。  
  
### <a name="remarks"></a>备注  
 只有一个表可以加载一次。  
  
 应用程序终止时，从资源加载的快捷键对应表会被自动释放。  
  
 如果调用`LoadFrame`若要创建框架窗口，框架将加载的菜单和图标资源，以及快捷键对应表，然后不必对此成员函数的后续调用。  
  
##  <a name="loadbarstate"></a>CFrameWnd::LoadBarState  
 调用此函数可还原由框架窗口拥有每个控件条的设置。  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 初始化 (INI) 文件中的节或状态信息都存储的 Windows 注册表中的键的名称。  
  
### <a name="remarks"></a>备注  
 还原的信息包括可见性、 水平/垂直方向、 停靠状态和控件条的位置。  
  
 必须将你想要还原的设置写入到注册表，然后才能调用`LoadBarState`。 通过调用将信息写入到注册表[CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)。 将信息写入 INI 文件通过调用[SaveBarState](#savebarstate)。  
  
##  <a name="loadframe"></a>CFrameWnd::LoadFrame  
 调用，用于动态创建框架窗口中的资源信息。  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nIDResource`  
 与框架窗口关联的共享资源的 ID。  
  
 *dwDefaultStyle*  
 框架的[样式](../../mfc/reference/window-styles.md)。 包括**FWS_ADDTOTITLE** ，如你想要自动显示的名称出现在窗口中的文档的标题栏的样式。  
  
 `pParentWnd`  
 指向框架的父级的指针。  
  
 `pContext`  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为**NULL**。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，然后再调用`LoadFrame`，它将加载 Windows 框架窗口和关联的资源并将附加到框架窗口`CFrameWnd`对象。 `nIDResource`参数指定菜单、 快捷键对应表、 图标和框架窗口的标题的字符串资源。  
  
 使用**创建**成员函数而不是`LoadFrame`如果想要指定所有框架窗口的创建参数。  
  
 框架将调用`LoadFrame`使用文档模板对象的框架窗口在创建时。  
  
 框架将使用`pContext`参数以指定要连接到框架窗口中，包括任何的对象包含的视图对象。 您可以设置`pContext`参数**NULL**当您调用`LoadFrame`。  
  
##  <a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable  
 当启用此数据成员时 （这是默认值） 时，菜单项没有`ON_UPDATE_COMMAND_UI`或`ON_COMMAND`用户会拉取菜单时，处理程序将被自动禁用。  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>备注  
 有的菜单项`ON_COMMAND`处理程序，但无`ON_UPDATE_COMMAND_UI`处理程序将自动启用。  
  
 当设置此数据成员时，菜单项将自动启用与工具栏按钮处于启用状态的方式相同。  
  
> [!NOTE]
> `m_bAutoMenuEnable`具有对顶级菜单项没有影响。  
  
 此数据成员简化了基于当前所选内容的可选命令的实施，可减少需要编写`ON_UPDATE_COMMAND_UI`用于启用和禁用菜单项的处理程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&3;](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace  
 调用此成员函数可在 OLE 就地激活过程中协商边框框架窗口中的空间。  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>参数  
 *nBorderCmd*  
 包含中的以下值之一**枚举 BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定边框的坐标。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是**CFrameWnd** OLE 边框空间协商实现。  
  
##  <a name="onbarcheck"></a>CFrameWnd::OnBarCheck  
 只要指定的控件条上执行某个操作调用。  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 条形图显示控件的 ID。  
  
### <a name="return-value"></a>返回值  
 控件条存在; 如果非零值否则为 0。  
  
##  <a name="oncontexthelp"></a>CFrameWnd::OnContextHelp  
 处理就地项的 SHIFT + F1 帮助。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>备注  
 若要启用区分上下文的帮助，您必须添加  
  
 [!code-cpp[NVC_MFCDocViewSDI #&16;](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 语句与您`CFrameWnd`类消息映射，还将添加一个快捷键对应表项，通常 SHIFT + F1，若要启用此成员函数。  
  
 如果您的应用程序是 OLE 容器，`OnContextHelp`将放到帮助模式包含在框架窗口对象的所有就地项。 然后，光标将变为一个箭头和一个问号，以及用户可以将鼠标指针移动，并按鼠标左键来选择对话框、 窗口、 菜单上或命令按钮。 此成员函数将调用 Windows 函数`WinHelp`光标下的对象的帮助上下文。  
  
##  <a name="oncreateclient"></a>CFrameWnd::OnCreateClient  
 在执行期间由框架调用`OnCreate`。  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 一个指向 Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md)结构*。*  
  
 `pContext`  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构*。*  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 永远不会调用此函数。  
  
 此函数的默认实现将创建`CView`对象中提供的信息从`pContext`，如有可能。  
  
 重写此函数可重写传入的值`CCreateContext`对象或更改创建框架窗口的主工作区中的方式控件。 `CCreateContext`中描述了可以重写的成员[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)类。  
  
> [!NOTE]
>  不会替换传入值`CREATESTRUCT`结构。 它们是仅用于提供信息。 如果您想要重写初始窗口矩形，例如，重写`CWnd`成员函数[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。  
  
##  <a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar  
 当系统即将隐藏菜单栏中当前的 MFC 应用程序时，调用此函数。  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序可以让应用程序可隐藏菜单系统时执行自定义操作。 不能防止菜单中隐藏，但可以例如，调用其他方法来检索的菜单样式或状态。  
  
##  <a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode  
 调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>参数  
 *bPreview*  
 指定将应用程序放置在打印预览模式下。 设置为**TRUE**放置在打印预览中**FALSE**取消预览模式。  
  
 `pState`  
 一个指向**CPrintPreviewState**结构。  
  
### <a name="remarks"></a>备注  
 默认实现将禁用所有的标准工具栏，并在主菜单和客户端主窗口将隐藏。 这将为临时 SDI 框架窗口启用 MDI 框架窗口。  
  
 重写该成员函数以自定义的隐藏和显示的控件条和其他部分，框架窗口在打印预览的过程。 调用基类实现从中重写版本。  
  
##  <a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar  
 当系统即将在当前的 MFC 应用程序中显示的菜单栏时，调用此函数。  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序可以让应用程序将会显示菜单时执行自定义操作。 不能防止菜单上显示，但您可以例如，调用其他方法来检索的菜单样式或状态。  
  
##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu  
 更新关联的菜单时，由框架调用。  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象，表示生成更新命令的菜单。 更新处理程序调用[启用](../../mfc/reference/ccmdui-class.md#enable)成员函数`CCmdUI`对象传递`pCmdUI`来更新用户界面。  
  
##  <a name="recalclayout"></a>CFrameWnd::RecalcLayout  
 当标准控件条切换为打开或关闭时或在框架窗口调整大小时，由框架调用。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bNotify`  
 确定框架窗口的活动中就地项是否接收通知的布局更改。 如果**TRUE**，表明它是通知; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 此成员函数的默认实现调用`CWnd`成员函数`RepositionBars`帧以及与客户端主窗口中重新定位所有控件条 (通常`CView`或**MDICLIENT**)。  
  
 重写该成员函数以框架窗口的布局已发生更改后进行控制的外观和行为的控件条。 例如，调用它时打开或关闭的控件条或添加另一个控件条。  
  
##  <a name="rectdefault"></a>CFrameWnd::rectDefault  
 将此传入静态`CRect`作为参数创建窗口以使 Windows 能够选择窗口的初始大小和位置时。  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>CFrameWnd::SaveBarState  
 调用此函数可存储有关由框架窗口拥有每个控件条的信息。  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 初始化文件中的节或状态信息都存储的 Windows 注册表中的键的名称。  
  
### <a name="remarks"></a>备注  
 此信息可以从初始化文件使用读取[LoadBarState](#loadbarstate)。 存储的信息包括可见性，水平/垂直方向、 停靠状态，以及控件条的位置。  
  
##  <a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView  
 指定要用于丰富预览中的活动视图的指定的视图。  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>参数  
 `pViewNew`  
 指向要激活的视图的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveview"></a>CFrameWnd::SetActiveView  
 调用此成员函数来设置活动的视图。  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pViewNew*  
 指定一个指向[CView](../../mfc/reference/cview-class.md)对象，或**NULL**为不活动状态的视图。  
  
 `bNotify`  
 指定视图是否可以接收通知的激活。 如果**TRUE**，`OnActivateView`称为为新的视图; 如果**FALSE**，它不是。  
  
### <a name="remarks"></a>备注  
 框架将自动调用此函数，因为用户将焦点更改到框架窗口中的视图。 您可以显式调用`SetActiveView`将焦点更改到指定的视图。  
  
##  <a name="setdockstate"></a>CFrameWnd::SetDockState  
 调用此成员函数以将状态信息存储在应用`CDockState`对象传递给框架窗口的控件条。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>参数  
 `state`  
 将存储的状态应用到框架窗口的控件条。  
  
### <a name="remarks"></a>备注  
 若要还原以前的状态的控件条，可以加载使用已存储的状态`CDockState::LoadState`或`Serialize`，然后使用`SetDockState`将其应用于框架窗口的控件条。 以前的状态存储在`CDockState`对象`GetDockState`  
  
##  <a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState  
 将菜单上的显示状态设置为隐藏或显示当前的 MFC 应用程序中。  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nState`|指定是否显示或隐藏菜单。 `nState`参数可以具有以下值︰<br /><br /> -如果它处于隐藏状态，但是如果它是可见的不起作用，AFX_MBS_VISIBLE (0x01) – 显示菜单。<br />-AFX_MBS_HIDDEN (0x02) – 隐藏菜单，如果它是可见的但如果它处于隐藏状态不起作用。|  
  
### <a name="return-value"></a>返回值  
 `true`如果此方法已成功更改菜单状态;，否则为`false`。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility  
 当前的 MFC 应用程序是隐藏还是可见中设置菜单上的默认行为。  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nStyle`|指定菜单是隐藏的默认情况下或可见并具有焦点。 `nStyle`参数可以具有以下值︰<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)-<br />     菜单显示在任何时候，并且默认情况下不具有焦点。<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     默认情况下，菜单处于隐藏状态。 如果菜单处于隐藏状态，请按 ALT 键显示菜单，然后使其获得焦点。 如果显示菜单上，按 ALT 或 ESC 键来隐藏菜单。<br />-AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0X04)<br />     （按位组合 (OR)）-默认情况下隐藏菜单。 如果隐藏菜单上，按 F10 键，以显示菜单，然后使其获得焦点。 如果显示菜单上，按 F10 键，以切换焦点打开或关闭菜单。 直到按 ALT 或 ESC 键，以将其隐藏起来，将显示菜单。|  
  
### <a name="remarks"></a>备注  
 如果值`nStyle`参数不是有效的此方法会断言在调试模式并引发[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)在发布模式下。 在其他运行时错误，此方法在调试模式中断言和将引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
 此方法会影响编写的应用程序中的菜单状态[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]及更高版本。  
  
##  <a name="setmessagetext"></a>CFrameWnd::SetMessageText  
 调用此函数可将字符串放置在具有的 ID 为 0 的状态栏窗格中。  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指向要放置在状态栏上的字符串。  
  
 `nID`  
 字符串的字符串资源 ID 放在状态栏上。  
  
### <a name="remarks"></a>备注  
 这通常是状态栏的最左侧，且最长，窗格。  
  
##  <a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition  
 设置显示在任务栏上的 Windows 7 进度栏的当前位置。  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>参数  
 `nProgressPos`  
 指定要设置的位置。 它必须通过设置范围内`SetProgressBarRange`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange  
 设置显示在任务栏上的 Windows 7 进度栏的范围。  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>参数  
 `nRangeMin`  
 最小值。  
  
 `nRangeMax`  
 最大值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState  
 设置类型和状态的任务栏按钮上显示的进度指示器。  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>参数  
 `tbpFlags`  
 控制进度按钮的当前状态的标志。 指定以下任一标记因为是互相排斥的所有状态︰ TBPF_NOPROGRESS、 TBPF_INDETERMINATE、 TBPF_NORMAL、 TBPF_ERROR、 TBPF_PAUSED。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon  
 已重载。 将一个覆盖区应用到一个任务栏按钮来指示应用程序的状态或通知用户。  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>参数  
 `nIDResource`  
 指定要用作覆盖图标的资源 ID。 请参见说明`hIcon`有关的详细信息。  
  
 `lpcszDescr`  
 指向提供传达覆盖区，供辅助功能的信息的 alt 文本版本的字符串的指针。  
  
 `hIcon`  
 要用作覆盖图标的句柄。 这应该是一个小图标，测量以每英寸点数 (dpi) 96 点 16 x 16 像素。 如果覆盖图标已应用于的任务栏按钮时，将替换该现有的覆盖区。 此值可为 `NULL`。 如何`NULL`处理值取决于任务栏按钮表示单个窗口或 windows 组。 它负责调用应用程序以释放`hIcon`不再需要时。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`如果操作系统版本低于 Windows 7 或设置该图标就会出错。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settitle"></a>CFrameWnd::SetTitle  
 设置窗口对象的标题。  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>参数  
 `lpszTitle`  
 指向包含窗口对象的标题的字符串的指针。  
  
##  <a name="showcontrolbar"></a>CFrameWnd::ShowControlBar  
 调用该成员函数以显示或隐藏控件条。  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>参数  
 `pBar`  
 指向控件条是显示还是隐藏指针。  
  
 `bShow`  
 如果**TRUE**，指定要显示控件条。 如果**FALSE**，指定要将隐藏控件条。  
  
 *bDelay*  
 如果**TRUE**，延迟显示控件条。 如果**FALSE**，显示控制条立即。  
  
##  <a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows  
 调用此成员函数以显示所有的派生的窗口`CFrameWnd`对象。  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 `bShow`  
 指定是否拥有的窗口是显示还是隐藏。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)

