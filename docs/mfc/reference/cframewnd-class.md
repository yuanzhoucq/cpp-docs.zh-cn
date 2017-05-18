---
title: "CFrameWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 06becdd593028e02d45ed68fb8fa5687e1e2dbd1
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|使帧可见且可用于用户。|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|将框架窗口设置为模式。|  
|[CFrameWnd::Create](#create)|调用创建并初始化与关联的 Windows 框架窗口`CFrameWnd`对象。|  
|[CFrameWnd::CreateView](#createview)|创建在不派生自的范围内的视图`CView`。|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|停靠控件条。|  
|[CFrameWnd::EnableDocking](#enabledocking)|允许要停靠的控件条。|  
|[CFrameWnd::EndModalState](#endmodalstate)|结束框架窗口的模式状态。 使所有 windows 通过停用`BeginModalState`。|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|浮动的控件条。|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|返回活动**CDocument**对象。|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|返回活动`CFrameWnd`对象。|  
|[CFrameWnd::GetActiveView](#getactiveview)|返回活动`CView`对象。|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|检索控件条。|  
|[CFrameWnd::GetDockState](#getdockstate)|检索框架窗口的停靠状态。|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|检索当前的 MFC 应用程序中的菜单的显示状态。|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|指示当前的 MFC 应用程序中的菜单的默认行为是否隐藏还是可见。|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|返回指向状态栏属于框架窗口的指针。|  
|[CFrameWnd::GetMessageString](#getmessagestring)|检索消息对应于命令 id。|  
|[CFrameWnd::GetTitle](#gettitle)|检索相关的控件条的标题。|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|导致`OnInitialUpdate`属于框架窗口调用中的所有视图的成员函数。|  
|[CFrameWnd::InModalState](#inmodalstate)|返回一个值，该值指示框架窗口处于模式状态。|  
|[CFrameWnd::IsTracking](#istracking)|确定当前移动拆分栏。|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|调用以加载快捷键对应表。|  
|[CFrameWnd::LoadBarState](#loadbarstate)|若要还原控件栏设置的调用。|  
|[CFrameWnd::LoadFrame](#loadframe)|调用动态地创建框架窗口中的资源信息。|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|协商框架窗口中的边框空间。|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|每当在指定的控件条上执行操作时调用。|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|处理的就地项的 SHIFT + F1 帮助。|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|执行和跳出执行打印预览模式，请设置应用程序的主框架窗口。|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|更新关联的菜单时由框架调用。|  
|[CFrameWnd::RecalcLayout](#recalclayout)|将重新定位的控件条`CFrameWnd`对象。|  
|[CFrameWnd::SaveBarState](#savebarstate)|若要保存控件栏设置的调用。|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|指定要用于丰富预览的活动视图，指定的视图。|  
|[CFrameWnd::SetActiveView](#setactiveview)|设置活动`CView`对象。|  
|[CFrameWnd::SetDockState](#setdockstate)|若要将停靠在主窗口中的框架窗口的调用。|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|隐藏或显示当前的 MFC 应用程序中设置菜单的显示状态。|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|在当前的 MFC 应用程序，可隐藏还是可见设置菜单的默认行为。|  
|[CFrameWnd::SetMessageText](#setmessagetext)|设置标准状态栏的文本。|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|设置显示在任务栏上的 Windows 7 进度栏的当前位置。|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|设置 Windows 7 进度栏在任务栏上显示的范围。|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|设置的类型和状态任务栏按钮上显示的进度指示器。|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|已重载。 将一个覆盖区应用到任务栏按钮，以指示应用程序状态或向用户通知。|  
|[CFrameWnd::SetTitle](#settitle)|设置相关的控件条的标题。|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|调用以显示控件条。|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|显示所有的派生的窗口`CFrameWnd`对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|创建一个客户端窗口框架。|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|隐藏在当前的 MFC 应用程序中的菜单之前调用。|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|在显示的菜单中当前的 MFC 应用程序之前调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|控件自动启用和禁用的菜单项的功能。|  
|[CFrameWnd::rectDefault](#rectdefault)|将此传递静态`CRect`作为参数创建时`CFrameWnd`对象，以使 Windows 能够选择窗口的初始大小和位置。|  
  
## <a name="remarks"></a>备注  
 若要创建你的应用程序有用的框架窗口，从派生类`CFrameWnd`。 将成员变量添加到派生的类，以存储特定于你的应用程序数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 有三种方法来构造框架窗口︰  
  
-   直接构造它使用[创建](#create)。  
  
-   直接构造它使用[LoadFrame](#loadframe)。  
  
-   间接构造使用的文档模板。  
  
 你调用之前**创建**或`LoadFrame`，您必须先构造使用 c + + 堆上的框架窗口对象**新**运算符。 之前调用**创建**，还可以注册窗口类[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数，若要设置帧的图标和类样式。  
  
 使用**创建**成员函数将为快速的自变量传递帧的创建参数。  
  
 `LoadFrame`需要更少的自变量比**创建**，并改为从资源，包括帧的标题、 图标、 快捷键对应表和菜单中检索大多数其默认值。 可以访问`LoadFrame`，所有这些资源必须具有相同的资源 ID (例如， **IDR_MAINFRAME**)。  
  
 当`CFrameWnd`对象包含视图和文档，就会创建间接的框架，而不是直接由程序员。 `CDocTemplate`对象安排帧的创建、 创建所包含的视图和连接到适当的文档的视图。 参数`CDocTemplate`构造函数指定`CRuntimeClass`的三个类涉及到 （文档、 框架和视图）。 A`CRuntimeClass`对象由框架用于动态创建新帧时指定用户 （例如，通过使用新建文件命令或多个文档界面 (MDI) 窗口新命令）。  
  
 框架窗口类派生自`CFrameWnd`必须使用声明`DECLARE_DYNCREATE`顺序上述`RUNTIME_CLASS`机制才能正常工作。  
  
 A`CFrameWnd`包含默认实现为 Windows 在典型的应用程序中执行主窗口的下列函数︰  
  
-   A`CFrameWnd`框架窗口用于跟踪的独立于 Windows 的活动窗口或当前输入的焦点的当前处于活动状态视图。 重新激活的帧后，通过调用通知活动视图`CView::OnActivateView`。  
  
-   命令消息和许多常见的帧通知消息，包括那些由`OnSetFocus`， `OnHScroll`，和`OnVScroll`函数的`CWnd`，通过委派`CFrameWnd`对当前活动视图的框架窗口。  
  
-   当前处于活动状态的视图 （或当前活动 MDI 子框架窗口的 MDI 框架对于） 可以确定框架窗口的标题。 可以通过关闭来禁用此功能**FWS_ADDTOTITLE**框架窗口的样式位。  
  
-   A`CFrameWnd`框架窗口管理控件条、 视图和框架窗口的客户端区域内的其他子窗口的位置。 框架窗口还执行更新的工具栏和其他控件栏按钮的空闲时间。 A`CFrameWnd`框架窗口还具有用于切换打开和关闭工具栏和状态栏的命令的默认实现。  
  
-   A`CFrameWnd`框架窗口管理主菜单栏。 当显示弹出菜单时，框架窗口使用**UPDATE_COMMAND_UI**机制来确定哪些菜单项应启用、 禁用，或检查。 当用户选择菜单项时，则框架窗口更新状态栏使用该命令的消息字符串。  
  
-   A`CFrameWnd`框架窗口具有可选的快捷键对应表进行自动转换的键盘快捷键。  
  
-   A`CFrameWnd`框架窗口具有可选帮助 ID 与设置`LoadFrame`用于区分上下文的帮助。 框架窗口是半模式状态，如上下文相关帮助 (SHIFT + F1) 和打印预览模式的主要 orchestrator。  
  
-   A`CFrameWnd`框架窗口将打开一个文件从文件管理器拖放框架窗口。 如果文件扩展名已注册并与应用程序关联，框架窗口的请求作出响应动态数据交换 (DDE) 打开发生在用户打开数据文件在文件管理器时或当**ShellExecute**调用 Windows 函数。  
  
-   如果框架窗口是主应用程序窗口 (即， `CWinThread::m_pMainWnd`)，当用户关闭应用程序时，框架窗口将提示用户保存任何已修改的文档 (有关`OnClose`和`OnQueryEndSession`)。  
  
-   如果框架窗口是主应用程序窗口，框架窗口是运行 WinHelp 的上下文。 关闭帧窗口将关闭 WINHELP。如果它对此应用程序的帮助启动，EXE。  
  
 不使用 c + +**删除**运算符销毁框架窗口。 请改用 `CWnd::DestroyWindow` 。 `CFrameWnd`实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CFrameWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="activateframe"></a>CFrameWnd::ActivateFrame  
 调用此成员函数以激活并还原框架窗口，以便它向用户是可见的且可用。  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>参数  
 `nCmdShow`  
 指定要传递给参数[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)。 默认情况下，框架显示，并且正确还原。  
  
### <a name="remarks"></a>备注  
 非用户界面事件，如 DDE、 OLE 或可能向用户显示框架窗口或其内容的其他事件之后通常调用此成员函数。  
  
 默认实现激活该框架和将其带到 Z 顺序的顶层而且，如果有必要，将执行应用程序的主框架窗口的相同步骤。  
  
 重写该成员函数以更改激活某个帧的方式。 例如，你可以强制 MDI 子窗口，以最大化。 添加适当的功能，然后调用基类版本的显式`nCmdShow`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing # 1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>CFrameWnd::BeginModalState  
 调用此成员函数以使框架窗口具有模式。  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>CFrameWnd::CFrameWnd  
 构造`CFrameWnd`对象，但不会创建可见框架窗口。  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 调用**创建**创建可见的窗口。  
  
##  <a name="create"></a>CFrameWnd::Create  
 调用创建并初始化与关联的 Windows 框架窗口`CFrameWnd`对象。  
  
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
 指向以 null 结尾的字符串名称的 Windows 类。 类名称可以是与注册的任何名称`AfxRegisterWndClass`全局函数或**RegisterClass** Windows 函数。 如果**NULL**，使用预定义的默认`CFrameWnd`属性。  
  
 `lpszWindowName`  
 指向以 null 结尾的字符串表示的窗口名称。 用作标题栏的文本。  
  
 `dwStyle`  
 指定的窗口[样式](../../mfc/reference/window-styles.md)属性。 包括**FWS_ADDTOTITLE** ，如你想要自动显示的名称出现在窗口中的文档的标题栏的样式。  
  
 `rect`  
 指定的大小和窗口的位置。 `rectDefault`值允许 Windows 指定的大小和位置的新窗口。  
  
 `pParentWnd`  
 指定此框架窗口的父窗口。 此参数应为**NULL**的顶级框架窗口。  
  
 *lpszMenuName*  
 标识要使用与窗口的菜单资源的名称。 使用**MAKEINTRESOURCE**如果的菜单还拥有整数 ID 而不是字符串。 此参数可以为**NULL**。  
  
 `dwExStyle`  
 指定扩展的窗口[样式](../../mfc/reference/extended-window-styles.md)属性。  
  
 `pContext`  
 指定指向的指针[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，，然后调用**创建**，它创建 Windows 框架窗口，并将其附加到`CFrameWnd`对象。 **创建**初始化窗口的类名称和窗口名称并注册其样式、 父级和关联的菜单的默认值。  
  
 使用`LoadFrame`而非**创建**从而不是指定其自变量的资源加载框架窗口。  
  
##  <a name="createview"></a>CFrameWnd::CreateView  
 调用`CreateView`创建在范围内的视图。  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 指定的视图和文档的类型。  
  
 `nID`  
 视图的 ID 号。  
  
### <a name="return-value"></a>返回值  
 指向`CWnd`对象成功; 否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 使用此成员函数来创建"视图"不是`CView`-框架内派生。 在调用`CreateView`，你必须手动设置为活动状态的视图，并将其设置为可见; 这些任务不会自动执行通过`CreateView`。  
  
##  <a name="dockcontrolbar"></a>CFrameWnd::DockControlBar  
 将导致控件栏停靠到框架窗口。  
  
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
 确定框架窗口停靠考虑哪些边。 它可以是 0，或一个或多个以下︰  
  
- `AFX_IDW_DOCKBAR_TOP`将停靠到框架窗口的顶部。  
  
- **AFX_IDW_DOCKBAR_BOTTOM**停靠到框架窗口的底部。  
  
- `AFX_IDW_DOCKBAR_LEFT`停靠到框架窗口的左侧。  
  
- `AFX_IDW_DOCKBAR_RIGHT`停靠框架窗口的右侧。  
  
 如果为 0，为在目标框架窗口停靠启用任何端可停靠控件条。  
  
 `lpRect`  
 确定在屏幕坐标中，控件条将停靠在目标框架窗口的非工作区中的位置。  
  
### <a name="remarks"></a>备注  
 将对两者的调用中指定在框架窗口的侧之一停靠控件条[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd::EnableDocking](#enabledocking)。 选择端由`nDockBarID`。  
  
##  <a name="enabledocking"></a>CFrameWnd::EnableDocking  
 调用此函数可启用框架窗口中的可停靠控件条。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwDockStyle`  
 指定的框架窗口的哪些边可用作停靠控件条的站点。 它可以是一个或多个以下︰  
  
- `CBRS_ALIGN_TOP`允许在客户端区域的顶部停靠。  
  
- `CBRS_ALIGN_BOTTOM`允许在工作区底部停靠。  
  
- `CBRS_ALIGN_LEFT`允许客户端区域的左侧停靠。  
  
- `CBRS_ALIGN_RIGHT`允许客户端区域右侧停靠。  
  
- `CBRS_ALIGN_ANY`允许在客户端区域的任何一侧上停靠。  
  
### <a name="remarks"></a>备注  
 将默认情况下，框架窗口按以下顺序的一侧中停靠控件条︰ 上、 下、 左、 右。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create)。  
  
##  <a name="endmodalstate"></a>CFrameWnd::EndModalState  
 调用此成员函数以将框架窗口从有模式更改为无模式。  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>备注  
 `EndModalState`使所有 windows 通过停用[BeginModalState](#beginmodalstate)。  
  
##  <a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar  
 调用此函数可导致控件栏不停靠到框架窗口。  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>参数  
 `pBar`  
 指向控件条以浮动。  
  
 `point`  
 中的位置，屏幕坐标，在其中放置控件条的左上的角。  
  
 `dwStyle`  
 指定是否在其新的框架窗口内水平或垂直对齐控件条。 它可以是以下之一︰  
  
- `CBRS_ALIGN_TOP`纵向排列控件条。  
  
- `CBRS_ALIGN_BOTTOM`纵向排列控件条。  
  
- `CBRS_ALIGN_LEFT`水平排列控件条。  
  
- `CBRS_ALIGN_RIGHT`水平排列控件条。  
  
 如果指定水平和垂直方向传递样式，工具栏将为水平方向。  
  
### <a name="remarks"></a>备注  
 通常情况下，这是在应用程序启动时该程序从上一次执行还原设置。  
  
 当用户释放鼠标左键拖动控件条通过也无法供停靠的位置时来导致放操作时，将由框架调用此函数。  
  
##  <a name="getactivedocument"></a>CFrameWnd::GetActiveDocument  
 调用此成员函数以获取指向当前的**CDocument**附加到当前活动视图。  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CDocument](../../mfc/reference/cdocument-class.md)。 如果不不存在任何当前的文档，返回**NULL**。  
  
##  <a name="getactiveframe"></a>CFrameWnd::GetActiveFrame  
 调用此成员函数以获取指向活动的多文档界面 (MDI) 子窗口的 MDI 框架窗口。  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>返回值  
 指向活动的 MDI 子窗口的指针。 如果应用程序是 SDI 应用程序，或 MDI 框架窗口包含任何活动文档时，隐式**这**将返回指针。  
  
### <a name="remarks"></a>备注  
 如果没有任何活动的 MDI 子或应用程序为单文档界面 (SDI) 的隐式**这**指针会返回。  
  
##  <a name="getactiveview"></a>CFrameWnd::GetActiveView  
 调用此成员函数可获取附加到框架窗口的活动视图 （如果有） 的指针 ( `CFrameWnd`)。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前[CView](../../mfc/reference/cview-class.md)。 如果没有当前视图，将返回**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数将返回**NULL**调用 MDI 主框架窗口 ( `CMDIFrameWnd`)。 在 MDI 应用程序，MDI 主框架窗口没有与它关联的视图。 相反，每个单独的子窗口 ( `CMDIChildWnd`) 具有一个或多个关联的视图。 可以通过首先查找活动的 MDI 子窗口，然后为该子窗口查找活动视图获取 MDI 应用程序中的活动视图。 通过调用函数找不到活动的 MDI 子窗口`MDIGetActive`或**GetActiveFrame**在下面的示例所示︰  
  
 [!code-cpp[NVC_MFCWindowing # 2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>CFrameWnd::GetControlBar  
 调用`GetControlBar`来访问与 ID 相关联的控件条  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 控件条 ID 号。  
  
### <a name="return-value"></a>返回值  
 指向控件条 id 相关联的指针  
  
### <a name="remarks"></a>备注  
 `nID`参数引用传递到的唯一标识符**创建**控件条的方法。 有关控件条的详细信息，请参阅标题为主题[控件条](../../mfc/control-bars.md)。  
  
 `GetControlBar`将返回控件条，即使它浮动的因此不是当前帧的子窗口。  
  
##  <a name="getdockstate"></a>CFrameWnd::GetDockState  
 调用此成员函数以存储有关框架窗口的控件条中的状态信息`CDockState`对象。  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>参数  
 `state`  
 包含返回后的框架窗口的控件条的当前状态。  
  
### <a name="remarks"></a>备注  
 然后，便可以编写的内容`CDockState`到存储使用`CDockState::SaveState`或`Serialize`。 如果你以后想要还原到以前的状态的控件条，加载将状态与`CDockState::LoadState`或`Serialize`，然后调用`SetDockState`要应用于框架窗口的控件条的前一状态。  
  
##  <a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState  
 检索当前的 MFC 应用程序中的菜单的显示状态。  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>返回值  
 返回值可以具有以下值︰  
  
-   AFX_MBS_VISIBLE (0x01)-菜单是可见的。  
  
-   AFX_MBS_HIDDEN (0x02)-隐藏菜单。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility  
 指示当前的 MFC 应用程序中的菜单的默认状态是隐藏还是可见。  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>返回值  
 此方法返回以下值之一︰  
  
-   AFX_MBV_KEEPVISIBLE (0x01) 的菜单将显示在所有时间，以及通过默认不具有焦点。  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02)-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 ALT 键来显示菜单并授予它焦点。 如果显示菜单上，则按 ALT 或 ESC 键，可以将其隐藏。  
  
-   AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0x04) （按位组合 (OR)）-默认情况下隐藏菜单。 如果菜单处于隐藏状态，按 F10 键，以显示的菜单，然后使其获得焦点。 如果显示菜单上，则按 F10 键，以切换焦点打开或关闭菜单。 直到按 ALT 或 ESC 键，以隐藏它，将显示菜单。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="getmessagebar"></a>CFrameWnd::GetMessageBar  
 调用此成员函数可获取对状态栏的指针。  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>返回值  
 指向状态栏窗口的指针。  
  
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
 `CString`要将该消息放到其中的对象。  
  
### <a name="remarks"></a>备注  
 默认实现只需加载指定的字符串`nID`使用资源文件。 当状态栏中的消息字符串需要更新时，将由框架调用此函数。  
  
##  <a name="gettitle"></a>CFrameWnd::GetTitle  
 检索窗口对象的标题。  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含的窗口对象的当前标题。  
  
##  <a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame  
 调用**IntitialUpdateFrame**创建具有的新帧之后**创建**。  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向框架窗口所关联到的文档。 可以是**NULL**。  
  
 `bMakeVisible`  
 如果**TRUE**，表示框架应变得可见并处于活动状态。 如果**FALSE**，没有后代进行可见。  
  
### <a name="remarks"></a>备注  
 这将导致在接收该框架窗口中的所有视图其`OnInitialUpdate`调用。  
  
 此外，如果存在不是以前的活动视图，框架窗口的主视图设为活动。 主视图是使用子 ID 的视图**AFX_IDW_PANE_FIRST**。 最后，框架窗口均可见如果`bMakeVisible`为非零值。 如果`bMakeVisible`为 0，则当前焦点和框架窗口的可见状态将保持不变。 不需要使用框架的实现的新文件和文件打开时调用此函数。  
  
##  <a name="inmodalstate"></a>CFrameWnd::InModalState  
 调用此成员函数以检查框架窗口是模式还是无模式。  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果否。否则为 0。  
  
##  <a name="istracking"></a>CFrameWnd::IsTracking  
 调用此成员函数可确定当前移动窗口中的拆分栏。  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行; 则为非 0否则为 0。  
  
##  <a name="loadacceltable"></a>CFrameWnd::LoadAccelTable  
 调用以加载指定的快捷键对应表。  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 标识快捷键资源的名称。 使用**MAKEINTRESOURCE**如果资源标识使用整数 id。  
  
### <a name="return-value"></a>返回值  
 如果已成功加载的快捷键对应表; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 只有一个表可以加载一次。  
  
 当在应用程序终止时，从资源加载的快捷键对应表将自动释放。  
  
 如果调用`LoadFrame`若要创建框架窗口，框架将加载快捷键对应表以及菜单和图标的资源，而此成员函数的后续调用即不必要。  
  
##  <a name="loadbarstate"></a>CFrameWnd::LoadBarState  
 调用此函数可还原拥有框架窗口的每个控件条的设置。  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 初始化 (INI) 文件中的节或 Windows 注册表状态信息的存储位置中的键的名称。  
  
### <a name="remarks"></a>备注  
 还原的信息包括可见性、 水平/垂直方向、 停靠状态和控件条的位置。  
  
 你想要还原的设置必须写入注册表，然后才能调用`LoadBarState`。 将信息写入注册表通过调用[CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)。 将信息写入 INI 文件通过调用[SaveBarState](#savebarstate)。  
  
##  <a name="loadframe"></a>CFrameWnd::LoadFrame  
 调用动态地创建框架窗口中的资源信息。  
  
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
 帧的[样式](../../mfc/reference/window-styles.md)。 包括**FWS_ADDTOTITLE** ，如你想要自动显示的名称出现在窗口中的文档的标题栏的样式。  
  
 `pParentWnd`  
 指向帧的父的指针。  
  
 `pContext`  
 指向的指针[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为**NULL**。  
  
### <a name="remarks"></a>备注  
 构造`CFrameWnd`两个步骤中的对象。 首先，调用构造函数构造`CFrameWnd`对象，，然后调用`LoadFrame`，它将加载 Windows 框架窗口和关联的资源并将附加到框架窗口`CFrameWnd`对象。 `nIDResource`参数指定菜单、 快捷键对应表、 图标和框架窗口的标题的字符串资源。  
  
 使用**创建**成员函数而不是`LoadFrame`如果想要指定所有框架窗口的创建参数。  
  
 框架调用`LoadFrame`使用文档模板对象的框架窗口在创建时。  
  
 框架将使用`pContext`自变量以指定要连接到框架窗口中，包括所有的对象包含的视图对象。 你可以设置`pContext`参数**NULL**当调用`LoadFrame`。  
  
##  <a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable  
 启用此数据成员时 （这是默认值），菜单项没有`ON_UPDATE_COMMAND_UI`或`ON_COMMAND`用户会拉取菜单时，处理程序将被自动禁用。  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>备注  
 菜单项具有`ON_COMMAND`处理程序但不是`ON_UPDATE_COMMAND_UI`处理程序将自动启用。  
  
 当设置此数据成员时，菜单项会自动启用与工具栏按钮处于启用状态的方式相同。  
  
> [!NOTE]
> `m_bAutoMenuEnable`具有对顶级菜单项没有影响。  
  
 此数据成员简化了基于当前所选内容的可选命令的实现，而无需编写`ON_UPDATE_COMMAND_UI`用于启用和禁用菜单项的处理程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing # 3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace  
 调用此成员函数可在 OLE 就地激活过程协商框架窗口中的边框空间。  
  
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
 每当在指定的控件条上执行操作时调用。  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 栏显示控件的 ID。  
  
### <a name="return-value"></a>返回值  
 如果控件条存在; 则为非 0否则为 0。  
  
##  <a name="oncontexthelp"></a>CFrameWnd::OnContextHelp  
 处理的就地项的 SHIFT + F1 帮助。  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>备注  
 若要启用上下文相关帮助，你必须添加  
  
 [!code-cpp[NVC_MFCDocViewSDI # 16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 语句与你`CFrameWnd`类消息映射，还将添加一个快捷键对应表条目，通常 SHIFT + F1，若要启用此成员函数。  
  
 如果你的应用程序是 OLE 容器，`OnContextHelp`放入框架窗口对象中包含到帮助模式的所有现有项。 然后，光标更改为一个箭头和问号，以及用户可以将鼠标指针移动，并按鼠标左键以选择对话框中，窗口、 菜单上或命令按钮。 此成员函数将调用 Windows 函数`WinHelp`光标下的对象的帮助上下文。  
  
##  <a name="oncreateclient"></a>CFrameWnd::OnCreateClient  
 在执行期间由框架调用`OnCreate`。  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 指向 Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md)结构。  
  
 `pContext`  
 指向的指针[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 永远不会调用此函数。  
  
 此函数的默认实现将创建`CView`从中提供的信息的对象`pContext`如果可能。  
  
 重写此函数可重写传入值`CCreateContext`对象或更改创建框架窗口的主要工作区中的方式控件。 `CCreateContext`可以重写的成员中所述[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)类。  
  
> [!NOTE]
>  不将值传入`CREATESTRUCT`结构。 它们是仅用于提供信息。 如果你想要重写初始窗口矩形，例如，重写`CWnd`成员函数[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。  
  
##  <a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar  
 当系统以隐藏在当前的 MFC 应用程序的菜单栏时调用此函数。  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序使应用程序将要隐藏菜单系统时执行自定义操作。 不能防止菜单隐藏，但可以例如，调用其他方法来检索的菜单样式或状态。  
  
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
 指向的指针**CPrintPreviewState**结构。  
  
### <a name="remarks"></a>备注  
 默认实现禁用所有标准工具栏，并隐藏在主菜单和客户端主窗口。 这将转换临时 SDI 框架窗口的 MDI 框架窗口。  
  
 重写该成员函数以自定义的隐藏和显示的控件条和其他帧窗口部分在打印预览的过程。 调用基类实现从中重写版本。  
  
##  <a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar  
 当系统即将在当前的 MFC 应用程序中显示的菜单栏时调用此函数。  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>备注  
 此事件处理程序使应用程序将要显示的菜单时执行自定义操作。 不能防止菜单显示，但你可以例如，调用其他方法来检索的菜单样式或状态。  
  
##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu  
 更新关联的菜单时由框架调用。  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针[CCmdUI](../../mfc/reference/ccmdui-class.md)表示生成更新命令的菜单对象。 更新处理程序调用[启用](../../mfc/reference/ccmdui-class.md#enable)成员函数`CCmdUI`对象通过`pCmdUI`若要更新的用户界面。  
  
##  <a name="recalclayout"></a>CFrameWnd::RecalcLayout  
 标准控件条打开或关闭时或在框架窗口调整大小时，由框架调用。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bNotify`  
 确定框架窗口的活动的就地项是否接收通知的布局更改。 如果**TRUE**，表明它是通知; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 此成员函数的默认实现调用`CWnd`成员函数`RepositionBars`来重新定位在框架也如主要的客户端窗口中的所有控件条 (通常`CView`或**MDICLIENT**)。  
  
 重写该成员函数以后已更改的框架窗口的布局进行控制的外观和行为的控件条。 例如，调用它时打开或关闭的控件条或添加另一个控件条。  
  
##  <a name="rectdefault"></a>CFrameWnd::rectDefault  
 将此传递静态`CRect`作为参数创建一个窗口，以使 Windows 能够选择窗口的初始大小和位置时。  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>CFrameWnd::SaveBarState  
 调用此函数可存储有关拥有框架窗口的每个控件条的信息。  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszProfileName`  
 初始化文件中的节或 Windows 注册表状态信息的存储位置中的键的名称。  
  
### <a name="remarks"></a>备注  
 从初始化文件使用可以读取此信息[LoadBarState](#loadbarstate)。 存储的信息包括可见性，水平/垂直方向、 停靠状态和控件条的位置。  
  
##  <a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView  
 指定要用于丰富预览的活动视图，指定的视图。  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>参数  
 `pViewNew`  
 指向要激活的视图的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveview"></a>CFrameWnd::SetActiveView  
 调用此成员函数可设置活动的视图。  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pViewNew*  
 指定指向的指针[CView](../../mfc/reference/cview-class.md)对象，或**NULL**没有活动的视图。  
  
 `bNotify`  
 指定视图是否接收通知的激活。 如果**TRUE**，`OnActivateView`称为新视图; 如果**FALSE**，它不是。  
  
### <a name="remarks"></a>备注  
 框架将自动调用此函数，如用户将焦点更改到在框架窗口内的视图。 你可以明确地调用`SetActiveView`要将焦点更改到指定的视图。  
  
##  <a name="setdockstate"></a>CFrameWnd::SetDockState  
 调用此成员函数可将状态信息存储在应用`CDockState`到框架窗口的控件条对象。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>参数  
 `state`  
 将存储的状态应用到框架窗口的控件条。  
  
### <a name="remarks"></a>备注  
 若要还原以前的状态的控件条，可以加载带的存储的状态`CDockState::LoadState`或`Serialize`，然后使用`SetDockState`以将其应用到框架窗口的控件条。 以前的状态存储在`CDockState`对象`GetDockState`  
  
##  <a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState  
 隐藏或显示当前的 MFC 应用程序中设置菜单的显示状态。  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nState`|指定是否显示或隐藏菜单。 `nState`参数可以具有以下值︰<br /><br /> -如果它处于隐藏状态，但如果它是可见不起作用，AFX_MBS_VISIBLE (0x01)-显示菜单。<br />-AFX_MBS_HIDDEN (0x02)-隐藏菜单上，如果它可见，但如果它隐藏不起作用。|  
  
### <a name="return-value"></a>返回值  
 `true`如果此方法已成功更改菜单状态;，否则为`false`。  
  
### <a name="remarks"></a>备注  
 如果出现运行时错误时，此方法在调试模式中断言，并且会引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
##  <a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility  
 在当前的 MFC 应用程序，可隐藏还是可见设置菜单的默认行为。  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nStyle`|指定是否菜单默认情况下隐藏的或者是可见的具有焦点。 `nStyle`参数可以具有以下值︰<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)-<br />     菜单会显示在所有时间，并默认情况下不具有焦点。<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     默认情况下，菜单处于隐藏状态。 如果菜单处于隐藏状态，请按 ALT 键来显示菜单并授予它焦点。 如果显示菜单上，则按 ALT 或 ESC 键，若要隐藏菜单。<br />-AFX_MBV_ DISPLAYONFOCUS (0X02) |AFX_MBV_DISPLAYONF10 (0X04)<br />     （按位组合 (OR)）-默认情况下隐藏菜单。 如果菜单处于隐藏状态，按 F10 键，以显示的菜单，然后使其获得焦点。 如果显示菜单上，则按 F10 键，以切换焦点打开或关闭菜单。 直到按 ALT 或 ESC 键，以隐藏它，将显示菜单。|  
  
### <a name="remarks"></a>备注  
 如果值`nStyle`参数不是有效的此方法会断言在调试模式并引发[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)在发布模式下。 在其他运行时错误，此方法在调试模式中断言和引发异常派生自[CException](../../mfc/reference/cexception-class.md)类。  
  
 此方法会影响为编写的应用程序中的菜单状态[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]及更高版本。  
  
##  <a name="setmessagetext"></a>CFrameWnd::SetMessageText  
 调用此函数可将字符串放置在状态栏窗格中具有的 ID 为 0。  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指向要将放置在状态栏上的字符串。  
  
 `nID`  
 字符串的字符串资源 ID 放在状态栏。  
  
### <a name="remarks"></a>备注  
 这通常是状态栏的最左侧，且最长，窗格。  
  
##  <a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition  
 设置显示在任务栏上的 Windows 7 进度栏的当前位置。  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>参数  
 `nProgressPos`  
 指定要设置的位置。 它必须位于设置的范围内`SetProgressBarRange`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange  
 设置 Windows 7 进度栏显示在任务栏上的范围。  
  
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
 设置的类型和状态任务栏按钮上显示的进度指示器。  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>参数  
 `tbpFlags`  
 控制进度按钮的当前状态的标志。 指定以下之一标记的所有状态都是互相排斥，因为︰ TBPF_NOPROGRESS、 TBPF_INDETERMINATE、 TBPF_NORMAL、 TBPF_ERROR、 TBPF_PAUSED。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon  
 已重载。 将一个覆盖区应用到任务栏按钮，以指示应用程序状态，或者通知用户。  
  
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
 指定要用作在覆盖区上图标的资源 ID。 请参阅说明`hIcon`有关详细信息。  
  
 `lpcszDescr`  
 指向提供传达在覆盖区上，供辅助功能的信息的替换文字版本的字符串的指针。  
  
 `hIcon`  
 要用作在覆盖区上的图标的句柄。 这应该是一个小图标，测量每英寸点数 (dpi) 96 点在 16 x 16 像素。 如果覆盖图标已应用于任务栏按钮时，将替换该现有覆盖区。 此值可为 `NULL`。 如何`NULL`处理值取决于任务栏按钮表示单个窗口或 windows 组。 要释放的调用应用程序负责`hIcon`不再需要时。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`如果操作系统版本低于 Windows 7 或设置图标就会出错。  
  
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
 调用此成员函数可显示或隐藏控件条。  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>参数  
 `pBar`  
 指向控件条是显示还是隐藏。  
  
 `bShow`  
 如果**TRUE**，指定要显示控件条。 如果**FALSE**，指定要隐藏控件条。  
  
 *bDelay*  
 如果**TRUE**，延迟显示控件条。 如果**FALSE**，显示栏立即的控件。  
  
##  <a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows  
 调用此成员函数，以显示所有的派生的窗口`CFrameWnd`对象。  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 `bShow`  
 指定是否拥有的 windows 的是显示还是隐藏。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)

