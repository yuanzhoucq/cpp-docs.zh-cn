---
title: CFrameWnd 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 0fd104e377300233ef1526f6c453346555dd27d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373790"
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
|[CFramewnd：CFramewnd](#cframewnd)|构造 `CFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFramewnd：：激活帧](#activateframe)|使帧可见且可供用户使用。|
|[CFramewnd：：开始模式状态](#beginmodalstate)|将框架窗口设置为模态。|
|[CFramewnd：：创建](#create)|调用以创建和初始化与`CFrameWnd`对象关联的 Windows 框架窗口。|
|[CFramewnd：：创建视图](#createview)|在框架中创建未派生自`CView`的视图。|
|[CFramewnd：:Dock控制栏](#dockcontrolbar)|停靠控制栏。|
|[CFramewnd：：启用停靠](#enabledocking)|允许停靠控制栏。|
|[CFramewnd：：结束模式状态](#endmodalstate)|结束帧窗口的模态状态。 启用 由`BeginModalState`禁用的所有窗口。|
|[CFramewnd：：浮动控制栏](#floatcontrolbar)|浮动控制栏。|
|[CFramewnd：获取活动文档](#getactivedocument)|返回活动`CDocument`对象。|
|[CFramewnd：获取活动帧](#getactiveframe)|返回活动`CFrameWnd`对象。|
|[CFramewnd：获取活动视图](#getactiveview)|返回活动`CView`对象。|
|[CFramewnd：：获取控制栏](#getcontrolbar)|检索控制栏。|
|[CFramewnd：：GetDockstate](#getdockstate)|检索框架窗口的停靠状态。|
|[CFramewnd：：获取菜单巴州](#getmenubarstate)|检索当前 MFC 应用程序中菜单的显示状态。|
|[CFramewnd：：获取菜单栏可见性](#getmenubarvisibility)|指示当前 MFC 应用程序中菜单的默认行为是隐藏还是可见。|
|[CFramewnd：：获取消息栏](#getmessagebar)|返回指向属于框架窗口的状态栏的指针。|
|[CFramewnd：：获取消息字符串](#getmessagestring)|检索与命令 ID 对应的消息。|
|[CFramewnd：：获取标题](#gettitle)|检索相关控制栏的标题。|
|[CFramewnd：：初始更新框架](#initialupdateframe)|`OnInitialUpdate`使成员函数属于框架窗口中的所有视图。|
|[Cframewnd：：在莫里状态](#inmodalstate)|返回指示框架窗口是否处于模态状态的值。|
|[CFramewnd：正在跟踪](#istracking)|确定当前是否正在移动拆分条。|
|[CFramewnd：：加载AccelTable](#loadacceltable)|调用以加载加速器表。|
|[CFramewnd：：加载栏](#loadbarstate)|调用以恢复控制栏设置。|
|[CFramewnd：：加载帧](#loadframe)|调用从资源信息动态创建帧窗口。|
|[CFramewnd：：谈判边界空间](#negotiateborderspace)|协商框架窗口中的边框空间。|
|[CFramewnd：：在巴键](#onbarcheck)|每当对指定的控制栏执行操作时，都会调用。|
|[CFramewnd：：在上下文帮助](#oncontexthelp)|处理就地项目 SHIFT_F1 帮助。|
|[CFramewnd：：打开预览模式](#onsetpreviewmode)|将应用程序的主框架窗口设置到打印预览模式和打印预览模式。|
|[CFramewnd：：更新控制栏菜单](#onupdatecontrolbarmenu)|更新关联菜单时由框架调用。|
|[CFramewnd：recalclayout](#recalclayout)|重新定位`CFrameWnd`对象的控制栏。|
|[CFramewnd：：保存巴尔邦](#savebarstate)|调用以保存控制栏设置。|
|[CFramewnd：：设置主动预览视图](#setactivepreviewview)|将指定的视图指定为"富预览"的活动视图。|
|[CFramewnd：：设置活动视图](#setactiveview)|设置活动`CView`对象。|
|[CFramewnd：：SetDockState](#setdockstate)|调用以停靠主窗口中的帧窗口。|
|[CFramewnd：：设置菜单栏](#setmenubarstate)|将当前 MFC 应用程序中菜单的显示状态设置为隐藏或显示。|
|[CFramewnd：：设置菜单栏可见性](#setmenubarvisibility)|将当前 MFC 应用程序中菜单的默认行为设为隐藏或可见。|
|[CFramewnd：：设置消息文本](#setmessagetext)|设置标准状态栏的文本。|
|[CFramewnd：：设置进度栏位置](#setprogressbarposition)|设置任务栏上显示的 Windows 7 进度栏的当前位置。|
|[CFramewnd：：设置进度栏范围](#setprogressbarrange)|设置任务栏上显示的 Windows 7 进度栏的范围。|
|[CFramewnd：：设置进度栏](#setprogressbarstate)|设置任务栏按钮上显示的进度指示器的类型和状态。|
|[CFramewnd：：设置任务栏重叠图标](#settaskbaroverlayicon)|已重载。 将叠加应用于任务栏按钮以指示应用程序状态或通知用户。|
|[CFramewnd：：设置标题](#settitle)|设置相关控制栏的标题。|
|[CFramewnd：：显示控制栏](#showcontrolbar)|呼叫以显示控制栏。|
|[CFramewnd：：显示拥有的窗口](#showownedwindows)|显示`CFrameWnd`对象后代的所有窗口。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CFramewnd：：打开创建客户端](#oncreateclient)|为框架创建客户端窗口。|
|[CFramewnd：：打开隐藏菜单栏](#onhidemenubar)|在当前 MFC 应用程序中的菜单隐藏之前调用。|
|[CFramewnd：：在显示菜单栏](#onshowmenubar)|在当前 MFC 应用程序中的菜单显示之前调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFramewnd：：m_bAutoMenuEnable](#m_bautomenuenable)|控制菜单项的自动启用和禁用功能。|
|[CFramewnd：：重新默认](#rectdefault)|创建`CFrameWnd`对象时`CRect`，将此静态作为参数传递，以允许 Windows 选择窗口的初始大小和位置。|

## <a name="remarks"></a>备注

要为应用程序创建有用的框架窗口，请从`CFrameWnd`派生类。 将成员变量添加到派生类以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

有三种方法可以构造框架窗口：

- 使用 直接构造它使用[创建](#create)。

- 使用[LoadFrame](#loadframe)直接构造它。

- 使用文档模板间接构造它。

在调用 或`Create``LoadFrame`之前，必须使用C++**新**运算符在堆上构造帧窗口对象。 在调用`Create`之前，您还可以使用[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数注册窗口类，以设置框架的图标和类样式。

使用`Create`成员函数将帧的创建参数作为即时参数传递。

`LoadFrame`需要的参数少于`Create`，而是从资源检索其大部分默认值，包括框架的标题、图标、快捷键表和菜单。 要被`LoadFrame`访问，所有这些资源必须具有相同的资源 ID（例如，IDR_MAINFRAME）。

当对象`CFrameWnd`包含视图和文档时，它们由框架间接创建，而不是由程序员直接创建。 该`CDocTemplate`对象协调框架的创建、包含视图的创建以及视图与相应文档的连接。 构造函数的`CDocTemplate`参数指定所涉及的三`CRuntimeClass`个类（文档、框架和视图）的参数。 框架`CRuntimeClass`使用对象在用户指定时动态创建新框架（例如，通过使用 File New 命令或多个文档接口 （MDI） Window New 命令）。

必须用DECLARE_DYNCREATE声明派生的`CFrameWnd`帧窗口类，以便上述RUNTIME_CLASS机制正常工作。

A`CFrameWnd`包含默认实现，用于在 Windows 的典型应用程序中执行主窗口的以下功能：

- `CFrameWnd`框架窗口跟踪独立于 Windows 活动窗口或当前输入焦点的当前活动视图。 重新激活帧时，通过调用`CView::OnActivateView`通知活动视图。

- 命令`OnSetFocus`消息和许多常见的帧通知消息（包括 由 的`OnHScroll``OnVScroll`和 函数处理的消息`CWnd`）由`CFrameWnd`帧窗口委派到当前活动视图。

- 当前活动视图（或当前活动的 MDI 子框架窗口（在 MDI 帧的情况下）可以确定帧窗口的标题。 可以通过关闭框架窗口的FWS_ADDTOTITLE样式位来禁用此功能。

- `CFrameWnd`框架窗口管理控制栏、视图和其他子窗口在框架窗口工作区中的定位。 框架窗口还执行工具栏和其他控制栏按钮的空闲时间更新。 `CFrameWnd`框架窗口还具有用于在工具栏和状态栏上下切换的命令的默认实现。

- `CFrameWnd`框架窗口管理主菜单栏。 显示弹出式菜单时，框架窗口使用UPDATE_COMMAND_UI机制来确定应启用、禁用或检查哪些菜单项。 当用户选择菜单项时，框架窗口会更新具有该命令的消息字符串的状态栏。

- `CFrameWnd`框架窗口具有自动转换键盘快捷键的可选快捷键表。

- `CFrameWnd`框架窗口具有用于上下文相关帮助的可选帮助`LoadFrame`ID 集。 帧窗口是半模态状态的主要协调器，例如上下文敏感的帮助 （SHIFT_F1） 和打印预览模式。

- `CFrameWnd`框架窗口将打开从文件管理器拖动的文件并丢弃在帧窗口中。 如果文件扩展名已注册并与应用程序关联，则帧窗口将响应用户在文件管理器中打开数据文件或调用`ShellExecute`Windows 函数时发生的动态数据交换 （DDE） 打开请求。

- 如果框架窗口是主应用程序窗口（即`CWinThread::m_pMainWnd`），当用户关闭应用程序时，框架窗口会提示用户保存任何修改的文档（for`OnClose`和`OnQueryEndSession`）。

- 如果框架窗口是主应用程序窗口，则框架窗口是运行 WinHelp 的上下文。 关闭帧窗口将关闭 WINHELP。EXE，如果它被启动，以寻求此应用程序的帮助。

请勿使用C++**删除**运算符来破坏框架窗口。 请改用 `CWnd::DestroyWindow`。 当`CFrameWnd`窗口被`PostNcDestroy`破坏时，将删除C++对象。 当用户关闭帧窗口时，默认`OnClose`处理程序将调用`DestroyWindow`。

有关 的详细信息`CFrameWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFramewnd：：激活帧

调用此成员函数以激活和还原框架窗口，以便它可见且可供用户使用。

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>参数

*nCmdShow*<br/>
指定要传递给[CWnd 的参数：：显示窗口](../../mfc/reference/cwnd-class.md#showwindow)。 默认情况下，将显示框架并正确还原。

### <a name="remarks"></a>备注

此成员函数通常在非用户界面事件（如 DDE、OLE 或其他可能向用户显示帧窗口或其内容的事件）之后调用。

默认实现激活帧并将其带到 Z 顺序的顶部，并在必要时对应用程序的主框架窗口执行相同的步骤。

重写此成员函数以更改帧的激活方式。 例如，您可以强制最大化 MDI 子窗口。 添加适当的功能，然后使用显式*nCmdShow*调用基类版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFramewnd：：开始模式状态

调用此成员函数以使框架窗口具有模式。

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFramewnd：CFramewnd

构造`CFrameWnd`对象，但不创建可见的框架窗口。

```
CFrameWnd();
```

### <a name="remarks"></a>备注

调用`Create`以创建可见窗口。

## <a name="cframewndcreate"></a><a name="create"></a>CFramewnd：：创建

调用以创建和初始化与`CFrameWnd`对象关联的 Windows 框架窗口。

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

*lpszClass名称*<br/>
指向命名 Windows 类的 null 端接字符串。 类名称可以是注册到`AfxRegisterWndClass`全局函数或`RegisterClass`Windows 函数的任何名称。 如果为 NULL，则使用预`CFrameWnd`定义的默认属性。

*lpsz窗口名称*<br/>
指向表示窗口名称的 null 端接字符串。 用作标题栏的文本。

*dwStyle*<br/>
指定窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。 如果希望标题栏自动显示窗口中表示的文档的名称，请包括FWS_ADDTOTITLE样式。

*矩形*<br/>
指定窗口的大小和位置。 *rectDefault*值允许 Windows 指定新窗口的大小和位置。

*pparentwnd*<br/>
指定此框架窗口的父窗口。 对于顶级框架窗口，此参数应为 NULL。

*lpszMenu名称*<br/>
标识要与窗口一起使用的菜单资源的名称。 如果菜单具有整数 ID 而不是字符串，请使用 MAKEINTRESOURCE。 此参数可以是 NULL。

*dwExStyle*<br/>
指定窗口扩展[样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)属性。

*pContext*<br/>
指定指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 此参数可以是 NULL。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

分两`CFrameWnd`步构造对象。 首先，调用构造函数，该构造函数构造`CFrameWnd`对象，然后调用`Create`，该构造函数创建 Windows 框架窗口并将其附加到`CFrameWnd`对象。 `Create`初始化窗口的类名称和窗口名称，并注册其样式、父菜单和关联的菜单的默认值。

使用`LoadFrame`而不是`Create`从资源加载帧窗口，而不是指定其参数。

## <a name="cframewndcreateview"></a><a name="createview"></a>CFramewnd：：创建视图

调用`CreateView`以在帧内创建视图。

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>参数

*pContext*<br/>
指定视图和文档的类型。

*nID*<br/>
视图的 ID 号。

### <a name="return-value"></a>返回值

指针指向`CWnd`对象（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

使用此成员函数可以创建框架中未`CView`派生的"视图"。 调用`CreateView`后，必须手动将视图设置为活动视图，并将其设置为可见视图;这些任务不会由`CreateView`自动执行。

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFramewnd：:Dock控制栏

导致控制栏停靠到框架窗口。

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

*pBar*<br/>
指向要停靠的控制栏。

*nDockBarID*<br/>
确定要考虑停靠的帧窗口的哪一侧。 它可以是 0，也可以是以下一个或多个：

- AFX_IDW_DOCKBAR_TOP停靠到框架窗口的顶侧。

- AFX_IDW_DOCKBAR_BOTTOM停靠到框架窗口的底部。

- AFX_IDW_DOCKBAR_LEFT停靠在框架窗口的左侧。

- AFX_IDW_DOCKBAR_RIGHT停靠在框架窗口的右侧。

如果为 0，则控制栏可以停靠到启用的停靠目标帧窗口中的任何一侧。

*lpRect*<br/>
在屏幕坐标中确定控制栏将停靠在目标帧窗口的非工作区中的位置。

### <a name="remarks"></a>备注

控制栏将停靠到调用 CControlBar 时指定的帧窗口的一侧[：：启用停靠](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd：：启用停靠](#enabledocking)。 选择的一侧由*nDockBarID*决定。

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFramewnd：：启用停靠

调用此函数以在框架窗口中启用可停靠的控制栏。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDock风格*<br/>
指定框架窗口的哪一侧可用作控制栏的停靠点。 它可以是以下一个或多个：

- CBRS_ALIGN_TOP 允许在工作区的顶部停靠。

- CBRS_ALIGN_BOTTOM允许在工作区的底部停靠。

- CBRS_ALIGN_LEFT 允许在工作区左侧停靠。

- CBRS_ALIGN_RIGHT允许在工作区的右侧停靠。

- CBRS_ALIGN_ANY 允许在工作区的任何一侧停靠。

### <a name="remarks"></a>备注

默认情况下，控件条将按以下顺序停靠到框架窗口的一侧：顶部、底部、左侧、右侧。

### <a name="example"></a>示例

  请参阅[CToolBar 的示例：：创建](../../mfc/reference/ctoolbar-class.md#create)。

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFramewnd：：结束模式状态

调用此成员函数以将框架窗口从有模式更改为无模式。

```
virtual void EndModalState();
```

### <a name="remarks"></a>备注

`EndModalState`启用[由 BeginModalState](#beginmodalstate)禁用的所有窗口。

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFramewnd：：浮动控制栏

调用此函数可使控制栏不停靠到框架窗口。

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>参数

*pBar*<br/>
指向要浮动的控制栏。

*点*<br/>
控件栏左上角的位置，位于屏幕坐标中。

*dwStyle*<br/>
指定是在其新框架窗口中水平对齐还是垂直对齐控制栏。 它可以是以下任一项：

- CBRS_ALIGN_TOP垂直定向控制条。

- CBRS_ALIGN_BOTTOM垂直定向控制条。

- CBRS_ALIGN_LEFT水平定向控制条。

- CBRS_ALIGN_RIGHT水平定向控制条。

如果传递样式，指定水平和垂直方向，工具栏将水平方向。

### <a name="remarks"></a>备注

通常，当程序从以前的执行还原设置时，在应用程序启动时完成此操作。

当用户通过释放鼠标左键，同时将控制栏拖动到无法停靠的位置，由框架调用此功能。

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFramewnd：获取活动文档

调用此成员函数以获取附加到当前活动视图的电流`CDocument`的指针。

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>返回值

指向当前[CDocument](../../mfc/reference/cdocument-class.md)的指针。 如果没有当前文档，则返回 NULL。

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFramewnd：获取活动帧

调用此成员函数以获取指向 MDI 框架窗口的活动多个文档接口 （MDI） 子窗口的指针。

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>返回值

指向活动 MDI 子窗口的指针。 如果应用程序是 SDI 应用程序，或者 MDI 框架窗口没有活动文档，则将返回隐式**此**指针。

### <a name="remarks"></a>备注

如果没有活动 MDI 子项，或者应用程序是单个文档接口 （SDI），则返回隐式**此**指针。

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFramewnd：获取活动视图

调用此成员函数以获取附加到框架窗口 （）`CFrameWnd`的活动视图（如果有）的指针。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>返回值

指向当前[CView](../../mfc/reference/cview-class.md)的指针。 如果没有当前视图，则返回 NULL。

### <a name="remarks"></a>备注

当调用 MDI 主框架窗口时，`CMDIFrameWnd`此功能将返回 NULL。 在 MDI 应用程序中，MDI 主框架窗口没有与其关联的视图。 相反，每个单独的子窗口`CMDIChildWnd`（ ） 具有一个或多个关联的视图。 可以通过首先查找活动 MDI 子窗口，然后查找该子窗口的活动视图来获取 MDI 应用程序中的活动视图。 可以通过调用函数`MDIGetActive`找到活动 MDI 子窗口，如下`GetActiveFrame`所示：

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFramewnd：：获取控制栏

调用`GetControlBar`以访问与 ID 关联的控制栏。

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
控件栏的 ID 号。

### <a name="return-value"></a>返回值

指向与 ID 关联的控件栏的指针。

### <a name="remarks"></a>备注

*nID*参数是指传递给控制栏`Create`方法的唯一标识符。 有关控制栏的详细信息，请参阅标题为["控制栏](../../mfc/control-bars.md)"的主题。

`GetControlBar`将返回控制栏，即使它是浮动的，因此当前不是框架的子窗口。

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFramewnd：：GetDockstate

调用此成员函数以在`CDockState`对象中存储有关帧窗口控制栏的状态信息。

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>参数

*状态*<br/>
在返回时包含帧窗口控制栏的当前状态。

### <a name="remarks"></a>备注

然后，可以使用`CDockState``CDockState::SaveState`或`Serialize`将 的内容写入存储。 如果以后希望将控制栏还原到以前的状态，请使用`CDockState::LoadState`或`Serialize`加载状态，然后调用`SetDockState`以将以前的状态应用于框架窗口的控制栏。

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFramewnd：：获取菜单巴州

检索当前 MFC 应用程序中菜单的显示状态。

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>返回值

返回值可以具有以下值：

- AFX_MBS_VISIBLE （0x01） - 菜单可见。

- AFX_MBS_HIDDEN （0x02） - 菜单已隐藏。

### <a name="remarks"></a>备注

如果发生运行时错误，此方法在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFramewnd：：获取菜单栏可见性

指示当前 MFC 应用程序中菜单的默认状态是隐藏还是可见。

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>返回值

此方法可返回以下值之一：

- AFX_MBV_KEEPVISIBLE （0x01） - 菜单随时显示，默认情况下没有焦点。

- AFX_MBV_DISPLAYONFOCUS （0x02） - 默认情况下，菜单处于隐藏状态。 如果菜单处于隐藏状态，请按 ALT 键显示菜单并赋予其焦点。 如果显示菜单，请按 ALT 或 ESC 键将其隐藏。

- AFX_MBV_ DISPLAYONFOCUS （0x02） &#124;AFX_MBV_DISPLAYONF10 （0x04） （位组合 （OR） - 默认情况下，菜单是隐藏的。 如果菜单处于隐藏状态，请按 F10 键显示菜单并赋予其焦点。 如果显示菜单，请按 F10 键切换菜单上或菜单外的焦点。 菜单将显示，直到您按 ALT 或 ESC 键来隐藏它。

### <a name="remarks"></a>备注

如果发生运行时错误，此方法在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFramewnd：：获取消息栏

调用此成员函数以获取指向状态栏的指针。

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>返回值

指向状态栏窗口的指针。

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFramewnd：：获取消息字符串

重写此函数以为命令指示指示提供自定义字符串。

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
所需消息的资源 ID。

*rMessage*<br/>
`CString`要将消息放入的对象。

### <a name="remarks"></a>备注

默认实现只需从资源文件加载*nID*指定的字符串。 当状态栏中的消息字符串需要更新时，框架将调用此功能。

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFramewnd：：获取标题

检索窗口对象的标题。

```
CString GetTitle() const;
```

### <a name="return-value"></a>返回值

包含窗口对象的当前标题的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFramewnd：：初始更新框架

使用`IntitialUpdateFrame``Create`创建新帧后调用 。

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
指向框架窗口关联的文档。 可以为 NULL。

*b使可见*<br/>
如果为 TRUE，则指示帧应变为可见且处于活动状态。 如果 FALSE，则不使后代可见。

### <a name="remarks"></a>备注

这将导致该帧窗口中的所有视图接收其`OnInitialUpdate`呼叫。

此外，如果以前没有活动视图，则框架窗口的主视图将变为活动状态。 主视图是具有 AFX_IDW_PANE_FIRST 子 ID 的视图。 最后，如果*bMakeVisible*是非零，则帧窗口变得可见。 如果*bMakeVisible*为 0，则帧窗口的当前焦点和可见状态将保持不变。 使用框架的"文件新建"和"文件打开"实现时，不必调用此功能。

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>Cframewnd：：在莫里状态

调用此成员函数以检查帧窗口是模态还是无模式。

```
BOOL InModalState() const;
```

### <a name="return-value"></a>返回值

如果是则非零;否则 0。

## <a name="cframewndistracking"></a><a name="istracking"></a>CFramewnd：正在跟踪

调用此成员函数以确定窗口中的拆分器条当前是否正在移动。

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>返回值

如果拆分器操作正在进行，则非零;否则 0。

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFramewnd：：加载AccelTable

调用以加载指定的加速器表。

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
标识加速器资源的名称。 如果资源使用整数 ID 标识，请使用 MAKEINTRESOURCE。

### <a name="return-value"></a>返回值

如果已成功加载加速器表，则非零;否则 0。

### <a name="remarks"></a>备注

一次只能加载一个表。

当应用程序终止时，从资源加载的加速器表将自动释放。

如果调用`LoadFrame`以创建框架窗口，框架将加载一个快捷键表以及菜单和图标资源，然后不需要随后调用此成员函数。

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFramewnd：：加载栏

调用此函数以还原帧窗口拥有的每个控制栏的设置。

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
初始化 （INI） 文件中的节的名称或存储状态信息的 Windows 注册表中的键的名称。

### <a name="remarks"></a>备注

恢复的信息包括可见性、水平/垂直方向、停靠状态和控制栏位置。

在调用`LoadBarState`之前，必须将要还原的设置写入注册表。 通过调用[CWinApp：：setRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)将信息写入注册表。 通过调用[SaveBarState](#savebarstate)将信息写入 INI 文件。

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFramewnd：：加载帧

调用从资源信息动态创建帧窗口。

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*nID资源*<br/>
与框架窗口关联的共享资源的 ID。

*dwDefault样式*<br/>
框架[的风格](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果希望标题栏自动显示窗口中表示的文档的名称，请包括FWS_ADDTOTITLE样式。

*pparentwnd*<br/>
指向帧父级的指针。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 此参数可以是 NULL。

### <a name="remarks"></a>备注

分两`CFrameWnd`步构造对象。 首先，调用构造函数，该构造函数构造`CFrameWnd`对象，然后调用`LoadFrame`，该构造函数加载 Windows 框架窗口和相关资源，并将框架窗口附加到`CFrameWnd`对象。 *nIDResource*参数指定框架窗口标题的菜单、快捷键表、图标和字符串资源。

使用`Create`成员函数，而不是`LoadFrame`指定帧窗口的所有创建参数时。

当框架使用`LoadFrame`文档模板对象创建框架窗口时，它将调用它。

框架使用*pContext*参数指定要连接到框架窗口的对象，包括任何包含的视图对象。 调用`LoadFrame`时，可以将*pContext*参数设置为 NULL。

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFramewnd：：m_bAutoMenuEnable

启用此数据成员（默认值）时，当用户拉下菜单时，将会自动禁用没有ON_UPDATE_COMMAND_UI或ON_COMMAND处理程序的菜单项。

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>备注

将自动启用具有ON_COMMAND处理程序但没有ON_UPDATE_COMMAND_UI处理程序的菜单项。

设置此数据成员时，菜单项将自动启用，其方式与启用工具栏按钮的方式相同。

> [!NOTE]
> `m_bAutoMenuEnable`对顶级菜单项没有影响。

此数据成员简化了基于当前选择的可选命令的实现，并减少了编写ON_UPDATE_COMMAND_UI处理程序以启用和禁用菜单项的需要。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFramewnd：：谈判边界空间

调用此成员函数以在 OLE 就地激活期间协商框架窗口中的边框空间。

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>参数

*nBorderCmd*<br/>
包含 以下值之一： `enum BorderCmd`

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lprect边框*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或指定边框坐标的[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是`CFrameWnd`实现 OLE 边界空间协商。

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFramewnd：：在巴键

每当对指定的控制栏执行操作时，都会调用。

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
显示的控制栏的 ID。

### <a name="return-value"></a>返回值

如果存在控制条，则非零;否则 0。

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFramewnd：：在上下文帮助

处理就地项目 SHIFT_F1 帮助。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>备注

要启用上下文相关的帮助，必须添加

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

语句到`CFrameWnd`类消息映射，并添加一个快捷表条目（通常 SHIFT_F1）以启用此成员函数。

如果应用程序是 OLE 容器，`OnContextHelp`则将帧窗口对象中包含的所有就地项目放入帮助模式。 光标将变为箭头和问号，然后用户可以移动鼠标指针并按鼠标左键选择对话框、窗口、菜单或命令按钮。 此成员函数使用光标下对象的`WinHelp`帮助上下文调用 Windows 函数。

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFramewnd：：打开创建客户端

在执行 期间由框架调用`OnCreate`。

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>参数

*lpcs*<br/>
指向 Windows [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构的指针。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

切勿调用此函数。

如果可能，此函数的默认实现`CView`将创建一个对象，该消息来自*pContext*中提供的信息。

重写此函数以覆盖`CCreateContext`对象中传递的值或更改框架窗口主工作区中的控件的创建方式。 可以`CCreateContext`重写的成员在[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)类中描述。

> [!NOTE]
> 不要替换结构中`CREATESTRUCT`传递的值。 它们仅供参考使用。 例如，如果要覆盖初始窗口矩形，请重写`CWnd`成员函数[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFramewnd：：打开隐藏菜单栏

当系统要隐藏当前 MFC 应用程序中的菜单栏时，将调用此功能。

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>备注

此事件处理程序使应用程序能够在系统要隐藏菜单时执行自定义操作。 不能阻止菜单被隐藏，但例如，您可以调用其他方法来检索菜单样式或状态。

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFramewnd：：打开预览模式

调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>参数

*b预览*<br/>
指定是否将应用程序置于打印预览模式。 设置为 TRUE 以放置在打印预览中，FALSE 设置为取消预览模式。

*pState*<br/>
指向结构的`CPrintPreviewState`指针。

### <a name="remarks"></a>备注

默认实现禁用所有标准工具栏并隐藏主菜单和主客户端窗口。 这将将 MDI 框架窗口转换为临时 SDI 框架窗口。

覆盖此成员功能以自定义打印预览期间控制栏和其他框架窗口部件的隐藏和显示。 从重写版本内调用基类实现。

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFramewnd：：在显示菜单栏

当系统要在当前 MFC 应用程序中显示菜单栏时，将调用此功能。

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>备注

此事件处理程序使应用程序能够在菜单即将显示时执行自定义操作。 不能阻止显示菜单，但例如，您可以调用其他方法来检索菜单样式或状态。

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFramewnd：：更新控制栏菜单

更新关联菜单时由框架调用。

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向表示生成更新命令的菜单的[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。 更新处理程序通过*pCmdUI*调用`CCmdUI`对象的[启用](../../mfc/reference/ccmdui-class.md#enable)成员函数以更新用户界面。

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFramewnd：recalclayout

当标准控制栏打开或关闭或调整框架窗口大小时，由框架调用。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

*b 通知*<br/>
确定框架窗口的活动就地项目是否接收布局更改通知。 如果为 TRUE，则会通知该项目;如果为 TRUE，则通知该项目。否则 FALSE。

### <a name="remarks"></a>备注

此成员函数的默认实现调用`CWnd`成员函数`RepositionBars`重新定位帧和主客户端窗口中的所有控制栏（通常为 a`CView`或 MDICLIENT）。

重写此成员函数以在帧窗口布局更改后控制控制栏的外观和行为。 例如，在打开或关闭控制栏或添加其他控制栏时调用它。

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFramewnd：：重新默认

创建窗口时`CRect`，将此静态作为参数传递，以允许 Windows 选择窗口的初始大小和位置。

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFramewnd：：保存巴尔邦

调用此函数以存储有关帧窗口拥有的每个控制栏的信息。

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
初始化文件中的节的名称或存储状态信息的 Windows 注册表中的键的名称。

### <a name="remarks"></a>备注

此信息可以使用[LoadBarState](#loadbarstate)从初始化文件中读取。 存储的信息包括可见性、水平/垂直方向、停靠状态和控制栏位置。

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFramewnd：：设置主动预览视图

将指定的视图指定为"富预览"的活动视图。

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>参数

*pView New*<br/>
指向要激活的视图的指针。

### <a name="remarks"></a>备注

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFramewnd：：设置活动视图

调用此成员函数以设置活动视图。

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

*pView New*<br/>
指定指向[CView](../../mfc/reference/cview-class.md)对象的指针，为无活动视图指定 NULL。

*b 通知*<br/>
指定是否通知视图激活。 如果为`OnActivateView`TRUE，则调用新视图;如果为"TRUE"，则为 "TRUE"，则为"TRUE"，为"TRUE"请求如果 FALSE，则不是。

### <a name="remarks"></a>备注

当用户将焦点更改为框架窗口中的视图时，框架将自动调用此函数。 您可以显式调用`SetActiveView`以将焦点更改为指定的视图。

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFramewnd：：SetDockState

调用此成员函数将存储在对象中`CDockState`的状态信息应用于帧窗口的控制栏。

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>参数

*状态*<br/>
将存储的状态应用于框架窗口的控制栏。

### <a name="remarks"></a>备注

要还原控件栏的先前状态，可以使用`CDockState::LoadState`或`Serialize`加载存储的状态，然后使用它`SetDockState`将其应用于框架窗口的控制栏。 以前的状态存储在对象中`CDockState`，`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFramewnd：：设置菜单栏

将当前 MFC 应用程序中菜单的显示状态设置为隐藏或显示。

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*n州*|[在]指定是显示还是隐藏菜单。 *nState*参数可以具有以下值：<br /><br />- AFX_MBS_VISIBLE （0x01） - 如果菜单处于隐藏状态，则显示该菜单，但如果菜单可见，则无效果。<br />- AFX_MBS_HIDDEN （0x02） - 如果菜单可见，则隐藏菜单，但如果该菜单隐藏，则无效。|

### <a name="return-value"></a>返回值

如果此方法成功更改菜单状态，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果发生运行时错误，此方法在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFramewnd：：设置菜单栏可见性

将当前 MFC 应用程序中菜单的默认行为设为隐藏或可见。

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*nStyle*|[在]指定菜单在默认情况下是隐藏的，还是可见的，并且具有焦点。 *nStyle*参数可以具有以下值：<br /><br />- AFX_MBV_KEEPVISIBLE （0x01） -<br />     菜单随时显示，默认情况下没有焦点。<br />- AFX_MBV_DISPLAYONFOCUS （0x02） -<br />     默认情况下，菜单处于隐藏状态。 如果菜单处于隐藏状态，请按 ALT 键显示菜单并赋予其焦点。 如果显示菜单，请按 ALT 或 ESC 键隐藏菜单。<br />- AFX_MBV_显示器（0x02）&#124;AFX_MBV_DISPLAYONF10 （0x04）<br />     （位组合 （OR）） - 默认情况下，菜单是隐藏的。 如果菜单处于隐藏状态，请按 F10 键显示菜单并赋予其焦点。 如果显示菜单，请按 F10 键切换菜单上或菜单外的焦点。 菜单将显示，直到您按 ALT 或 ESC 键来隐藏它。|

### <a name="remarks"></a>备注

如果*nStyle*参数的值无效，则此方法在调试模式下断言，并在释放模式下引发[CInvalidArgexception。](../../mfc/reference/cinvalidargexception-class.md) 如果出现其他运行时错误，此方法在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

此方法会影响为 Windows Vista 和更高版本的应用程序中菜单的状态。

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFramewnd：：设置消息文本

调用此函数以在 ID 为 0 的状态栏窗格中放置字符串。

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向要放置在状态栏上的字符串。

*nID*<br/>
要放置在状态栏上的字符串资源 ID。

### <a name="remarks"></a>备注

这通常是状态栏中最左侧且最长的窗格。

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFramewnd：：设置进度栏位置

设置任务栏上显示的 Windows 7 进度栏的当前位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>参数

*n 进步Pos*<br/>
指定要设置的位置。 它必须在 设置`SetProgressBarRange`的范围内。

### <a name="remarks"></a>备注

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFramewnd：：设置进度栏范围

设置任务栏上显示的 Windows 7 进度栏的范围。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>参数

*恩朗明*<br/>
最小值。

*nRangeMax*<br/>
最大值。

### <a name="remarks"></a>备注

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFramewnd：：设置进度栏

设置任务栏按钮上显示的进度指示器的类型和状态。

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>参数

*tbpFlags*<br/>
控制进度按钮的当前状态的标志。 只指定以下标志之一，因为所有状态都是互斥的：TBPF_NOPROGRESS、TBPF_INDETERMINATE、TBPF_NORMAL、TBPF_ERRORTBPF_PAUSED。

### <a name="remarks"></a>备注

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFramewnd：：设置任务栏重叠图标

已重载。 将叠加应用于任务栏按钮以指示应用程序状态或通知用户。

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>参数

*nID资源*<br/>
指定要用作叠加的图标的资源 ID。 有关详细信息，请参阅*hIcon*的说明。

*lpcszDescr*<br/>
指向字符串的指针，该字符串提供叠加所传达的信息的 alt 文本版本，用于辅助功能。

*hIcon*<br/>
用作叠加的图标的句柄。 这应该是一个小图标，每英寸 96 点（dpi）测量 16x16 像素。 如果叠加图标已应用于任务栏按钮，则替换现有叠加。 此值可以是 NULL。 NULL 值的处理方式取决于任务栏按钮是表示单个窗口还是一组窗口。 调用应用程序有责任在不再需要*hIcon*时释放它。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;如果操作系统版本小于 Windows 7 或出现错误，则设置图标。

### <a name="remarks"></a>备注

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFramewnd：：设置标题

设置窗口对象的标题。

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>参数

*lpszTitle*<br/>
指向包含窗口对象标题的字符串的指针。

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFramewnd：：显示控制栏

调用此成员函数以显示或隐藏控制栏。

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>参数

*pBar*<br/>
指向要显示或隐藏的控制栏的指针。

*b显示*<br/>
如果为 TRUE，则指定要显示控制栏。 如果 FALSE，则指定要隐藏控制栏。

*bDelay*<br/>
如果为 TRUE，则延迟显示控制条。 如果 FALSE，则立即显示控制栏。

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFramewnd：：显示拥有的窗口

调用此成员函数以显示`CFrameWnd`对象后代的所有窗口。

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
指定是显示还是隐藏拥有的窗口。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)
