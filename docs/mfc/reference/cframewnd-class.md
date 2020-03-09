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
ms.openlocfilehash: d2e043c8c9f4ad86636cd0e9ea7d695826b6c8fb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866422"
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
|[CFrameWnd：： CFrameWnd](#cframewnd)|构造 `CFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFrameWnd：： ActivateFrame](#activateframe)|使框架对用户可见并可用。|
|[CFrameWnd：： BeginModalState](#beginmodalstate)|将框架窗口设置为模式。|
|[CFrameWnd：： Create](#create)|调用以创建和初始化与 `CFrameWnd` 对象关联的 Windows 框架窗口。|
|[CFrameWnd：： CreateView](#createview)|在不是从 `CView`派生的帧中创建视图。|
|[CFrameWnd：:D ockControlBar](#dockcontrolbar)|停靠控件条。|
|[CFrameWnd：： EnableDocking](#enabledocking)|允许停靠控件条。|
|[CFrameWnd：： EndModalState](#endmodalstate)|结束框架窗口的模式状态。 通过 `BeginModalState`启用所有禁用的窗口。|
|[CFrameWnd：： FloatControlBar](#floatcontrolbar)|将控件条浮动。|
|[CFrameWnd：： GetActiveDocument](#getactivedocument)|返回活动 `CDocument` 对象。|
|[CFrameWnd：： GetActiveFrame](#getactiveframe)|返回活动 `CFrameWnd` 对象。|
|[CFrameWnd：： GetActiveView](#getactiveview)|返回活动 `CView` 对象。|
|[CFrameWnd：： GetControlBar](#getcontrolbar)|检索控件条。|
|[CFrameWnd：： GetDockState](#getdockstate)|检索框架窗口的停靠状态。|
|[CFrameWnd：： GetMenuBarState](#getmenubarstate)|检索当前 MFC 应用程序中的菜单的显示状态。|
|[CFrameWnd：： GetMenuBarVisibility](#getmenubarvisibility)|指示当前 MFC 应用程序中的菜单的默认行为是隐藏还是可见。|
|[CFrameWnd：： GetMessageBar](#getmessagebar)|返回指向属于框架窗口的状态栏的指针。|
|[CFrameWnd：： GetMessageString](#getmessagestring)|检索与命令 ID 相对应的消息。|
|[CFrameWnd：： GetTitle](#gettitle)|检索相关控件条的标题。|
|[CFrameWnd：： InitialUpdateFrame](#initialupdateframe)|导致调用框架窗口中所有视图的 `OnInitialUpdate` 成员函数。|
|[CFrameWnd：： InModalState](#inmodalstate)|返回一个值，该值指示框架窗口是否处于模式状态。|
|[CFrameWnd：： IsTracking](#istracking)|确定当前是否正在移动拆分栏。|
|[CFrameWnd：： LoadAccelTable](#loadacceltable)|调用以加载快捷键对应表。|
|[CFrameWnd：： LoadBarState](#loadbarstate)|调用以还原控制条设置。|
|[CFrameWnd：： LoadFrame](#loadframe)|调用以从资源信息动态创建框架窗口。|
|[CFrameWnd：： NegotiateBorderSpace](#negotiateborderspace)|在框架窗口中协商边框空间。|
|[CFrameWnd：： OnBarCheck](#onbarcheck)|在对指定控件条执行操作时调用。|
|[CFrameWnd：： OnContextHelp](#oncontexthelp)|处理对就地项的 SHIFT + F1 帮助。|
|[CFrameWnd：： OnSetPreviewMode](#onsetpreviewmode)|将应用程序的主框架窗口设置为和外接程序的打印预览模式。|
|[CFrameWnd：： OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|当更新关联的菜单时由框架调用。|
|[CFrameWnd：： RecalcLayout](#recalclayout)|重新定位 `CFrameWnd` 对象的控件条。|
|[CFrameWnd：： SaveBarState](#savebarstate)|调用以保存控制条设置。|
|[CFrameWnd：： SetActivePreviewView](#setactivepreviewview)|指定要作为富预览的活动视图的指定视图。|
|[CFrameWnd：： SetActiveView](#setactiveview)|设置活动 `CView` 对象。|
|[CFrameWnd：： SetDockState](#setdockstate)|调用以将框架窗口停靠在主窗口中。|
|[CFrameWnd：： SetMenuBarState](#setmenubarstate)|将当前 MFC 应用程序中的菜单的显示状态设置为隐藏或显示。|
|[CFrameWnd：： SetMenuBarVisibility](#setmenubarvisibility)|将当前 MFC 应用程序中的菜单的默认行为设置为隐藏或可见。|
|[CFrameWnd：： SetMessageText](#setmessagetext)|设置标准状态栏的文本。|
|[CFrameWnd：： SetProgressBarPosition](#setprogressbarposition)|设置任务栏上显示的 Windows 7 进度栏的当前位置。|
|[CFrameWnd：： SetProgressBarRange](#setprogressbarrange)|设置任务栏上显示的 Windows 7 进度栏的范围。|
|[CFrameWnd：： SetProgressBarState](#setprogressbarstate)|设置任务栏按钮上显示的进度指示器的类型和状态。|
|[CFrameWnd：： SetTaskbarOverlayIcon](#settaskbaroverlayicon)|已重载。 将覆盖应用到任务栏按钮，以指示应用程序状态或用户的通知。|
|[CFrameWnd：： SetTitle](#settitle)|设置相关控件条的标题。|
|[CFrameWnd：： ShowControlBar](#showcontrolbar)|调用以显示控件条。|
|[CFrameWnd：： ShowOwnedWindows](#showownedwindows)|显示作为 `CFrameWnd` 对象的后代的所有窗口。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CFrameWnd：： OnCreateClient](#oncreateclient)|创建框架的客户端窗口。|
|[CFrameWnd：： OnHideMenuBar](#onhidemenubar)|在隐藏当前 MFC 应用程序中的菜单前调用。|
|[CFrameWnd：： OnShowMenuBar](#onshowmenubar)|在显示当前 MFC 应用程序中的菜单前调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFrameWnd：： m_bAutoMenuEnable](#m_bautomenuenable)|控制菜单项的自动启用和禁用功能。|
|[CFrameWnd：： rectDefault](#rectdefault)|创建 `CFrameWnd` 对象时，将此静态 `CRect` 作为参数传递，以允许 Windows 选择窗口的初始大小和位置。|

## <a name="remarks"></a>备注

若要为应用程序创建有用的框架窗口，请从 `CFrameWnd`派生类。 向派生类添加成员变量，以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

可以通过三种方式构造框架窗口：

- 使用[Create](#create)直接构造它。

- 使用[LoadFrame](#loadframe)直接构造它。

- 使用文档模板间接构造它。

在调用 `Create` 或 `LoadFrame`之前，必须使用C++ **new**运算符在堆上构造框架窗口对象。 在调用 `Create`之前，还可以使用[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数注册一个窗口类，以设置该框架的图标和类样式。

使用 `Create` 成员函数将框架的创建参数作为直接参数传递。

`LoadFrame` 所需的参数少于 `Create`，而是从资源中检索其大多数默认值，包括框架的标题、图标、快捷键对应表和菜单。 若要 `LoadFrame`访问，所有这些资源都必须具有相同的资源 ID （例如，IDR_MAINFRAME）。

当 `CFrameWnd` 对象包含视图和文档时，框架会间接创建它们，而不是直接由程序员创建。 `CDocTemplate` 对象将协调框架创建、创建包含视图的过程，以及将视图连接到相应的文档。 `CDocTemplate` 构造函数的参数指定所涉及的三个类的 `CRuntimeClass` （文档、框架和视图）。 当用户指定时，框架使用 `CRuntimeClass` 对象动态创建新帧（例如，通过使用 "文件" "新建" 或 "多文档界面（MDI）" 窗口新建命令）。

必须使用 DECLARE_DYNCREATE 声明派生自 `CFrameWnd` 的框架窗口类，才能正常使用 RUNTIME_CLASS 机制。

`CFrameWnd` 包含用于在 Windows 的典型应用程序中执行主窗口的下列功能的默认实现：

- `CFrameWnd` 框架窗口跟踪与 Windows 活动窗口或当前输入焦点无关的当前活动视图。 重新激活帧后，将通过调用 `CView::OnActivateView`通知活动视图。

- 命令消息和许多常见的帧通知消息（包括由 `CWnd`的 `OnSetFocus`、`OnHScroll`和 `OnVScroll` 函数处理的消息）由 `CFrameWnd` 框架窗口委托给当前活动视图。

- 当前处于活动状态的视图（对于 MDI 框架，则为当前处于活动状态的 MDI 子框架窗口）可以确定框架窗口的标题。 可以通过关闭框架窗口的 FWS_ADDTOTITLE 样式位来禁用此功能。

- `CFrameWnd` 框架窗口管理控件条、视图和框架窗口的工作区中的其他子窗口的位置。 框架窗口还会对工具栏和其他控件栏按钮进行空闲时间更新。 `CFrameWnd` 框架窗口还具有用于在工具栏和状态栏上切换的命令的默认实现。

- `CFrameWnd` 框架窗口管理主菜单栏。 显示弹出菜单时，框架窗口使用 UPDATE_COMMAND_UI 机制来确定应启用、禁用或选中哪些菜单项。 当用户选择菜单项时，框架窗口将使用该命令的消息字符串来更新状态栏。

- `CFrameWnd` 框架窗口具有自动翻译键盘快捷键的可选快捷键对应表。

- `CFrameWnd` 框架窗口包含一个可选的帮助 ID，其中包含用于上下文相关帮助的 `LoadFrame`。 框架窗口是半模式状态的主要协调器，例如上下文相关的帮助（SHIFT + F1）和打印预览模式。

- `CFrameWnd` 框架窗口将打开从文件管理器拖放到框架窗口中的文件。 如果文件扩展名已注册并与应用程序关联，框架窗口将响应在用户在文件管理器中打开数据文件或调用 `ShellExecute` Windows 函数时出现的动态数据交换（DDE）打开请求。

- 如果框架窗口是主应用程序窗口（即 `CWinThread::m_pMainWnd`），则当用户关闭应用程序时，框架窗口将提示用户保存任何修改后的文档（对于 `OnClose` 和 `OnQueryEndSession`）。

- 如果框架窗口是主应用程序窗口，则框架窗口是用于运行 WinHelp 的上下文。 关闭框架窗口将关闭 WINHELP。如果已为此应用程序启动了此应用程序，则为 EXE。

不要使用C++ **delete**运算符来销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 当销毁窗口时，`PostNcDestroy` 的 `CFrameWnd` C++实现将删除该对象。 当用户关闭框架窗口时，默认 `OnClose` 处理程序将调用 `DestroyWindow`。

有关 `CFrameWnd`的详细信息，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="activateframe"></a>CFrameWnd：： ActivateFrame

调用此成员函数以激活并还原框架窗口，使其可见并且可供用户使用。

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>parameters

*nCmdShow*<br/>
指定要传递给[CWnd：： ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)的参数。 默认情况下，将显示并正确还原帧。

### <a name="remarks"></a>备注

此成员函数通常在非用户界面事件（例如 DDE、OLE 或其他可能向用户显示框架窗口或其内容的事件）后调用。

默认实现激活框架，并将其放到 Z 顺序的顶部，并在必要时对应用程序的主框架窗口执行相同的步骤。

重写此成员函数以更改框架的激活方式。 例如，可以强制最大化 MDI 子窗口。 添加适当的功能，然后使用显式*nCmdShow*调用基类版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>CFrameWnd：： BeginModalState

调用此成员函数以使框架窗口具有模式。

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>CFrameWnd：： CFrameWnd

构造 `CFrameWnd` 对象，但不创建可见框架窗口。

```
CFrameWnd();
```

### <a name="remarks"></a>备注

调用 `Create` 以创建可见窗口。

##  <a name="create"></a>CFrameWnd：： Create

调用以创建和初始化与 `CFrameWnd` 对象关联的 Windows 框架窗口。

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

### <a name="parameters"></a>parameters

*lpszClassName*<br/>
指向以 null 结尾的字符串，该字符串对 Windows 类进行命名。 类名称可以是注册到 `AfxRegisterWndClass` 全局函数或 `RegisterClass` Windows 函数的任何名称。 如果为 NULL，则使用预定义的默认 `CFrameWnd` 特性。

*lpszWindowName*<br/>
指向以 null 结尾的字符串，该字符串表示窗口名称。 用作标题栏的文本。

*dwStyle*<br/>
指定窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)特性。 如果希望标题栏自动显示窗口中表示的文档的名称，请包含 FWS_ADDTOTITLE 样式。

*rect*<br/>
指定窗口的大小和位置。 *RectDefault*值允许 Windows 指定新窗口的大小和位置。

*pParentWnd*<br/>
指定此框架窗口的父窗口。 对于顶级框架窗口，此参数应为 NULL。

*lpszMenuName*<br/>
标识要与窗口一起使用的菜单资源的名称。 如果菜单具有整数 ID 而不是字符串，请使用 MAKEINTRESOURCE。 此参数可以为 NULL。

*dwExStyle*<br/>
指定窗口扩展[样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)特性。

*pContext*<br/>
指定指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果初始化成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

通过两个步骤构造一个 `CFrameWnd` 对象。 首先，调用构造函数，该构造函数构造 `CFrameWnd` 对象，然后调用 `Create`，这将创建 Windows 框架窗口并将其附加到 `CFrameWnd` 对象。 `Create` 初始化窗口的类名称和窗口名称，并为其样式、父项和关联菜单注册默认值。

使用 `LoadFrame` 而不是 `Create` 从资源加载框架窗口，而不是指定其参数。

##  <a name="createview"></a>CFrameWnd：： CreateView

调用 `CreateView` 以在框架中创建视图。

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>parameters

*pContext*<br/>
指定视图和文档的类型。

*nID*<br/>
视图的 ID 号。

### <a name="return-value"></a>返回值

如果成功，则为指向 `CWnd` 对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

使用此成员函数可创建在框架中不 `CView`派生的 "视图"。 调用 `CreateView`之后，必须手动将该视图设置为 "活动"，并将其设置为 visible;`CreateView`不会自动执行这些任务。

##  <a name="dockcontrolbar"></a>CFrameWnd：:D ockControlBar

导致控件栏停靠在框架窗口中。

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
指向要停靠的控件条。

*nDockBarID*<br/>
确定要用于停靠的框架窗口的两侧。 它可以为0，也可以为以下一项或多项：

- AFX_IDW_DOCKBAR_TOP 停靠到框架窗口的顶部。

- AFX_IDW_DOCKBAR_BOTTOM 停靠到框架窗口的底部。

- AFX_IDW_DOCKBAR_LEFT 停靠到框架窗口的左侧。

- AFX_IDW_DOCKBAR_RIGHT 停靠到框架窗口的右侧。

如果为0，则可以将控件栏停靠到 "目标框架" 窗口中启用了停靠的任何一侧。

*lpRect*<br/>
确定控件栏在目标框架窗口的非工作区中停靠的位置（以屏幕坐标表示）。

### <a name="remarks"></a>备注

控件条将停靠在对[CControlBar：： EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)和[CFrameWnd：： EnableDocking](#enabledocking)的调用中指定的框架窗口的一侧。 选择的端由*nDockBarID*确定。

##  <a name="enabledocking"></a>CFrameWnd：： EnableDocking

调用此函数可在框架窗口中启用可停靠的控件条。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>parameters

*dwDockStyle*<br/>
指定框架窗口的哪一侧可用作控制条的停靠站点。 它可以是下列一项或多项：

- CBRS_ALIGN_TOP 允许在工作区顶部停靠。

- CBRS_ALIGN_BOTTOM 允许在工作区的底部停靠。

- CBRS_ALIGN_LEFT 允许在工作区的左侧停靠。

- CBRS_ALIGN_RIGHT 允许在客户端区域的右侧停靠。

- CBRS_ALIGN_ANY 允许在客户端区域的任何一侧停靠。

### <a name="remarks"></a>备注

默认情况下，控件条将按以下顺序停靠到框架窗口的一侧：上、下、左、右。

### <a name="example"></a>示例

  请参阅[CToolBar：： Create](../../mfc/reference/ctoolbar-class.md#create)的示例。

##  <a name="endmodalstate"></a>CFrameWnd：： EndModalState

调用此成员函数以将框架窗口从有模式更改为无模式。

```
virtual void EndModalState();
```

### <a name="remarks"></a>备注

`EndModalState` 启用[BeginModalState](#beginmodalstate)禁用的所有窗口。

##  <a name="floatcontrolbar"></a>CFrameWnd：： FloatControlBar

调用此函数可导致控件栏不停靠到框架窗口中。

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
指向要浮动的控件条。

*情况*<br/>
显示控件栏左上角的位置（以屏幕坐标表示）。

*dwStyle*<br/>
指定是否在新的框架窗口内水平或垂直对齐控件条。 它可以是以下任一项：

- CBRS_ALIGN_TOP 垂直方向控制栏。

- CBRS_ALIGN_BOTTOM 垂直方向控制栏。

- CBRS_ALIGN_LEFT 水平方向控制条。

- CBRS_ALIGN_RIGHT 水平方向控制条。

如果同时指定了水平和垂直方向的样式，则将沿水平方向定位工具栏。

### <a name="remarks"></a>备注

通常，这是在应用程序启动时在应用程序启动时执行的

当用户通过释放鼠标左键，同时将控件栏拖到不可用于停靠的位置上时，框架会调用此函数。

##  <a name="getactivedocument"></a>CFrameWnd：： GetActiveDocument

调用此成员函数以获取指向附加到当前活动视图的当前 `CDocument` 的指针。

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>返回值

指向当前[CDocument](../../mfc/reference/cdocument-class.md)的指针。 如果没有当前文档，则返回 NULL。

##  <a name="getactiveframe"></a>CFrameWnd：： GetActiveFrame

调用此成员函数以获取指向 MDI 框架窗口的活动多文档界面（MDI）子窗口的指针。

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>返回值

指向活动的 MDI 子窗口的指针。 如果应用程序是 SDI 应用程序，或 MDI 框架窗口没有活动文档，则将返回隐式**this**指针。

### <a name="remarks"></a>备注

如果没有活动的 MDI 子级，或者应用程序是单文档界面（SDI），则将返回隐式**this**指针。

##  <a name="getactiveview"></a>CFrameWnd：： GetActiveView

调用此成员函数以获取指向附加到框架窗口的活动视图（如果有）的指针（`CFrameWnd`）。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>返回值

指向当前[CView](../../mfc/reference/cview-class.md)的指针。 如果没有当前视图，则返回 NULL。

### <a name="remarks"></a>备注

为 MDI 主框架窗口（`CMDIFrameWnd`）调用此函数时，此函数将返回 NULL。 在 MDI 应用程序中，MDI 主框架窗口没有关联的视图。 相反，每个单独的子窗口（`CMDIChildWnd`）都具有一个或多个关联的视图。 通过首先查找活动的 MDI 子窗口，然后查找该子窗口的活动视图，可以获得 MDI 应用程序中的活动视图。 可以通过调用函数 `MDIGetActive` 或 `GetActiveFrame` 来找到活动 MDI 子窗口，如下所示：

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>CFrameWnd：： GetControlBar

调用 `GetControlBar` 以获取与 ID 关联的控件条的访问权限。

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>parameters

*nID*<br/>
控件条的 ID 号。

### <a name="return-value"></a>返回值

指向与 ID 关联的控件条的指针。

### <a name="remarks"></a>备注

*NID*参数是指传递到控件栏的 `Create` 方法的唯一标识符。 有关控制栏的详细信息，请参阅标题为 "[控制条](../../mfc/control-bars.md)" 的主题。

即使控件栏是浮动的，也不是当前框架的子窗口，`GetControlBar` 将返回控件条。

##  <a name="getdockstate"></a>CFrameWnd：： GetDockState

调用此成员函数以将有关框架窗口的控件条的状态信息存储在 `CDockState` 对象中。

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>parameters

State<br/>
在返回时包含框架窗口的控件条的当前状态。

### <a name="remarks"></a>备注

然后，你可以使用 `CDockState::SaveState` 或 `Serialize`将 `CDockState` 的内容写入存储。 如果以后想要将控件条还原到以前的状态，请使用 `CDockState::LoadState` 或 `Serialize`加载状态，然后调用 `SetDockState` 将以前的状态应用于框架窗口的控件条。

##  <a name="getmenubarstate"></a>CFrameWnd：： GetMenuBarState

检索当前 MFC 应用程序中的菜单的显示状态。

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>返回值

返回值可以具有以下值：

- AFX_MBS_VISIBLE （0x01）-菜单可见。

- AFX_MBS_HIDDEN （0x02）-菜单处于隐藏状态。

### <a name="remarks"></a>备注

如果出现运行时错误，则此方法将在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

##  <a name="getmenubarvisibility"></a>CFrameWnd：： GetMenuBarVisibility

指示当前 MFC 应用程序中的菜单的默认状态是隐藏还是可见。

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>返回值

此方法可返回以下值之一：

- AFX_MBV_KEEPVISIBLE （0x01）-菜单始终显示，并且默认情况下不具有焦点。

- AFX_MBV_DISPLAYONFOCUS （0x02）-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 ALT 键显示菜单，并为其指定焦点。 如果显示菜单，请按 ALT 或 ESC 键将其隐藏。

- AFX_MBV_ DISPLAYONFOCUS （0x02） &#124; AFX_MBV_DISPLAYONF10 （0x04）（按位组合（or））-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 F10 键显示菜单，并为其指定焦点。 如果显示菜单，请按 F10 键，以将焦点切换到菜单。 直到按下 ALT 或 ESC 键将其隐藏后，才会显示菜单。

### <a name="remarks"></a>备注

如果出现运行时错误，则此方法将在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

##  <a name="getmessagebar"></a>CFrameWnd：： GetMessageBar

调用此成员函数以获取指向状态栏的指针。

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>返回值

指向状态栏窗口的指针。

##  <a name="getmessagestring"></a>CFrameWnd：： GetMessageString

重写此函数以为命令 Id 提供自定义字符串。

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>parameters

*nID*<br/>
所需消息的资源 ID。

*rMessage*<br/>
要将消息放入其中的 `CString` 对象。

### <a name="remarks"></a>备注

默认实现只是从资源文件加载*nID*指定的字符串。 当状态栏中的消息字符串需要更新时，框架会调用此函数。

##  <a name="gettitle"></a>CFrameWnd：： GetTitle

检索窗口对象的标题。

```
CString GetTitle() const;
```

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含窗口对象的当前标题。

##  <a name="initialupdateframe"></a>CFrameWnd：： InitialUpdateFrame

使用 `Create`创建新帧后，调用 `IntitialUpdateFrame`。

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>parameters

*pDoc*<br/>
指向框架窗口关联到的文档。 可以为 NULL。

*bMakeVisible*<br/>
如果为 TRUE，则指示帧应变为可见并处于活动状态。 如果为 FALSE，则不显示后代。

### <a name="remarks"></a>备注

这会导致该框架窗口中的所有视图都接收其 `OnInitialUpdate` 调用。

而且，如果以前没有活动的视图，框架窗口的主视图将变为活动状态。 主视图是 AFX_IDW_PANE_FIRST 的子 ID 为的视图。 最后，如果*bMakeVisible*为非零，则使框架窗口可见。 如果*bMakeVisible*为0，则框架窗口的当前焦点和可见状态将保持不变。 使用框架的文件新和打开文件的实现时，不需要调用此函数。

##  <a name="inmodalstate"></a>CFrameWnd：： InModalState

调用此成员函数以检查框架窗口是模式模式还是无模式窗口。

```
BOOL InModalState() const;
```

### <a name="return-value"></a>返回值

如果是，则为非零值;否则为0。

##  <a name="istracking"></a>CFrameWnd：： IsTracking

调用此成员函数以确定当前是否正在移动窗口中的拆分栏。

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>返回值

如果拆分器操作正在进行，则为非零值;否则为0。

##  <a name="loadacceltable"></a>CFrameWnd：： LoadAccelTable

调用以加载指定的快捷键对应表。

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
标识快捷键资源的名称。 如果使用整数 ID 标识资源，请使用 MAKEINTRESOURCE。

### <a name="return-value"></a>返回值

如果快捷键对应表已成功加载，则为非零值;否则为0。

### <a name="remarks"></a>备注

一次只能加载一个表。

当应用程序终止时，将自动释放从资源加载的快捷键对应表。

如果调用 `LoadFrame` 来创建框架窗口，则框架将加载一个快捷方式表以及菜单和图标资源，然后不需要对此成员函数进行后续调用。

##  <a name="loadbarstate"></a>CFrameWnd：： LoadBarState

调用此函数可还原框架窗口拥有的每个控件条的设置。

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
初始化（INI）文件中的部分名称，或 Windows 注册表中存储状态信息的项的名称。

### <a name="remarks"></a>备注

还原的信息包括可见性、水平/垂直方向、停靠状态和控制条位置。

在调用 `LoadBarState`之前，必须将要还原的设置写入注册表。 调用[CWinApp：： SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey)将信息写入注册表。 通过调用[SaveBarState](#savebarstate)将信息写入 INI 文件。

##  <a name="loadframe"></a>CFrameWnd：： LoadFrame

调用以从资源信息动态创建框架窗口。

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>parameters

*nIDResource*<br/>
与框架窗口关联的共享资源的 ID。

*dwDefaultStyle*<br/>
框架的[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 如果希望标题栏自动显示窗口中表示的文档的名称，请包含 FWS_ADDTOTITLE 样式。

*pParentWnd*<br/>
指向框架的父项的指针。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 此参数可以为 NULL。

### <a name="remarks"></a>备注

通过两个步骤构造一个 `CFrameWnd` 对象。 首先，调用构造函数，该构造函数构造 `CFrameWnd` 对象，然后调用 `LoadFrame`，后者加载 Windows 框架窗口和关联的资源，并将框架窗口附加到 `CFrameWnd` 对象。 *NIDResource*参数指定框架窗口标题的菜单、快捷键对应表、图标和字符串资源。

当要指定框架窗口的所有创建参数时，请使用 `Create` 成员函数而不是 `LoadFrame`。

框架在使用文档模板对象创建框架窗口时调用 `LoadFrame`。

框架使用*pContext*参数指定要连接到框架窗口的对象，包括所有包含的视图对象。 调用 `LoadFrame`时，可以将*pContext*参数设置为 NULL。

##  <a name="m_bautomenuenable"></a>CFrameWnd：： m_bAutoMenuEnable

如果启用此数据成员（这是默认值），则当用户下拉菜单时，不会自动禁用 ON_UPDATE_COMMAND_UI 或 ON_COMMAND 处理程序的菜单项。

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>备注

具有 ON_COMMAND 处理程序但不会自动启用 ON_UPDATE_COMMAND_UI 处理程序的菜单项。

设置此数据成员时，将自动启用菜单项，其方式与启用工具栏按钮的方式相同。

> [!NOTE]
> 对于顶级菜单项，`m_bAutoMenuEnable` 不起作用。

此数据成员基于当前所选内容简化了可选命令的实现，并减少了编写用于启用和禁用菜单项 ON_UPDATE_COMMAND_UI 处理程序的需求。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>CFrameWnd：： NegotiateBorderSpace

调用此成员函数以在 OLE 就地激活过程中协商框架窗口中的边框空间。

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>parameters

*nBorderCmd*<br/>
包含 `enum BorderCmd`中的以下值之一：

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针，该对象指定边框的坐标。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是 OLE 边框空间协商的 `CFrameWnd` 实现。

##  <a name="onbarcheck"></a>CFrameWnd：： OnBarCheck

在对指定控件条执行操作时调用。

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>parameters

*nID*<br/>
所显示的控件条的 ID。

### <a name="return-value"></a>返回值

如果控件栏存在，则为非零值;否则为0。

##  <a name="oncontexthelp"></a>CFrameWnd：： OnContextHelp

处理对就地项的 SHIFT + F1 帮助。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>备注

若要启用上下文相关帮助，你必须添加

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

语句添加到 `CFrameWnd` 类消息映射，同时添加快捷键-表项（通常为 SHIFT + F1）来启用此成员函数。

如果你的应用程序是 OLE 容器，`OnContextHelp` 会将框架窗口对象中包含的所有就地项放入帮助模式。 光标更改为箭头和问号，然后用户可以移动鼠标指针并按鼠标左键以选择对话框、窗口、菜单或命令按钮。 此成员函数在光标下的对象的帮助上下文 `WinHelp` 调用 Windows 函数。

##  <a name="oncreateclient"></a>CFrameWnd：： OnCreateClient

在执行 `OnCreate`的过程中由框架调用。

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>parameters

*lpcs*<br/>
指向 Windows [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构的指针。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从不调用此函数。

此函数的默认实现从*pContext*中提供的信息创建 `CView` 对象（如有可能）。

重写此函数以重写在 `CCreateContext` 对象中传递的值，或更改创建框架窗口的主工作区中的控件的方式。 [CCreateContext](../../mfc/reference/ccreatecontext-structure.md)类中描述了可以重写的 `CCreateContext` 成员。

> [!NOTE]
>  请勿替换 `CREATESTRUCT` 结构中传递的值。 它们仅用于提供信息。 例如，如果想要重写初始窗口矩形，请重写 `CWnd` 成员函数[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)。

##  <a name="onhidemenubar"></a>CFrameWnd：： OnHideMenuBar

当系统即将隐藏当前 MFC 应用程序中的菜单栏时，将调用此函数。

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>备注

此事件处理程序使您的应用程序能够在系统即将隐藏菜单时执行自定义操作。 您无法阻止隐藏菜单，但您可以调用其他方法来检索菜单样式或状态。

##  <a name="onsetpreviewmode"></a>CFrameWnd：： OnSetPreviewMode

调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>parameters

*bPreview*<br/>
指定是否将应用程序置于打印预览模式。 如果设置为 TRUE，则在打印预览中设置为 FALSE，则取消预览模式。

*pState*<br/>
指向 `CPrintPreviewState` 结构的指针。

### <a name="remarks"></a>备注

默认实现禁用所有标准工具栏，并隐藏主菜单和主客户端窗口。 这会将 MDI 框架窗口变成临时 SDI 框架窗口。

重写此成员函数可自定义在打印预览期间隐藏和显示控件条和其他框架窗口部分。 从重写的版本中调用基类实现。

##  <a name="onshowmenubar"></a>CFrameWnd：： OnShowMenuBar

当系统将要显示当前 MFC 应用程序中的菜单栏时，将调用此函数。

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>备注

当要显示菜单时，此事件处理程序使您的应用程序能够执行自定义操作。 您无法阻止显示菜单，但您可以调用其他方法来检索菜单样式或状态。

##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd：： OnUpdateControlBarMenu

当更新关联的菜单时由框架调用。

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>parameters

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针，该对象表示生成更新命令的菜单。 更新处理程序通过*pCmdUI*调用 `CCmdUI` 对象的[Enable](../../mfc/reference/ccmdui-class.md#enable)成员函数以更新用户界面。

##  <a name="recalclayout"></a>CFrameWnd：： RecalcLayout

当打开或关闭标准控件条或调整框架窗口大小时，由框架调用。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>parameters

*bNotify*<br/>
确定框架窗口的活动就地项是否收到布局更改的通知。 如果为 TRUE，则通知该项;否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数的默认实现将调用 `CWnd` 成员函数 `RepositionBars` 来重新定位框架中的所有控件条以及主客户端窗口中的所有控件条（通常为 `CView` 或 MDICLIENT）。

重写此成员函数，以控制在框架窗口布局发生更改后控件条的外观和行为。 例如，当您打开或关闭控件条或添加另一个控件条时，请调用它。

##  <a name="rectdefault"></a>CFrameWnd：： rectDefault

创建窗口时，将此静态 `CRect` 作为参数传递，以允许 Windows 选择窗口的初始大小和位置。

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>CFrameWnd：： SaveBarState

调用此函数可存储有关框架窗口所拥有的每个控件条的信息。

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
初始化文件中的节的名称，或存储状态信息的 Windows 注册表中的项的名称。

### <a name="remarks"></a>备注

可以使用[LoadBarState](#loadbarstate)从初始化文件中读取此信息。 存储的信息包括可见性、水平/垂直方向、停靠状态和控制条位置。

##  <a name="setactivepreviewview"></a>CFrameWnd：： SetActivePreviewView

指定要作为富预览的活动视图的指定视图。

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>parameters

*pViewNew*<br/>
指向要激活的视图的指针。

### <a name="remarks"></a>备注

##  <a name="setactiveview"></a>CFrameWnd：： SetActiveView

调用此成员函数以设置活动视图。

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>parameters

*pViewNew*<br/>
指定指向[CView](../../mfc/reference/cview-class.md)对象的指针; 如果没有活动视图，则为 NULL。

*bNotify*<br/>
指定视图是否将被通知激活。 如果为 TRUE，则为新视图调用 `OnActivateView`;如果为 FALSE，则不是。

### <a name="remarks"></a>备注

当用户将焦点更改为框架窗口中的视图时，框架将自动调用此函数。 您可以显式调用 `SetActiveView` 将焦点更改为指定的视图。

##  <a name="setdockstate"></a>CFrameWnd：： SetDockState

调用此成员函数以将 `CDockState` 对象中存储的状态信息应用到框架窗口的控件条。

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>parameters

State<br/>
将存储的状态应用于框架窗口的控件条。

### <a name="remarks"></a>备注

若要还原控件条的先前状态，可以加载具有 `CDockState::LoadState` 或 `Serialize`的存储状态，然后使用 `SetDockState` 将其应用于框架窗口的控件条。 以前的状态存储在 `CDockState` 对象中，其 `GetDockState`

##  <a name="setmenubarstate"></a>CFrameWnd：： SetMenuBarState

将当前 MFC 应用程序中的菜单的显示状态设置为隐藏或显示。

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*nState*|中指定是显示还是隐藏菜单。 *NState*参数可具有以下值：<br /><br />-AFX_MBS_VISIBLE （0x01）-如果菜单处于隐藏状态，则显示菜单，但是如果可见，则不起作用。<br />-AFX_MBS_HIDDEN （0x02）-如果菜单可见，则隐藏菜单; 如果隐藏，则不起作用。|

### <a name="return-value"></a>返回值

如果此方法成功更改菜单状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果出现运行时错误，则此方法将在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

##  <a name="setmenubarvisibility"></a>CFrameWnd：： SetMenuBarVisibility

将当前 MFC 应用程序中的菜单的默认行为设置为隐藏或可见。

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*nStyle*|中指定菜单默认处于隐藏状态还是可见并且具有焦点。 *NStyle*参数可具有以下值：<br /><br />-AFX_MBV_KEEPVISIBLE （0x01）-<br />     菜单始终显示，并且默认情况下不具有焦点。<br />-AFX_MBV_DISPLAYONFOCUS （0x02）-<br />     默认情况下，该菜单处于隐藏状态。 如果菜单处于隐藏状态，请按 ALT 键显示菜单，并为其指定焦点。 如果显示菜单，请按 ALT 或 ESC 键隐藏菜单。<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     （按位组合（OR））-默认情况下隐藏菜单。 如果菜单处于隐藏状态，请按 F10 键显示菜单，并为其指定焦点。 如果显示菜单，请按 F10 键，以将焦点切换到菜单。 直到按下 ALT 或 ESC 键将其隐藏后，才会显示菜单。|

### <a name="remarks"></a>备注

如果*nStyle*参数的值无效，此方法将断言处于调试模式，并在发布模式下引发[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) 。 如果出现其他运行时错误，此方法将在调试模式下断言，并引发从[CException](../../mfc/reference/cexception-class.md)类派生的异常。

此方法影响为 Windows Vista 和更高版本编写的应用程序中菜单的状态。

##  <a name="setmessagetext"></a>CFrameWnd：： SetMessageText

调用此函数可将字符串放在 ID 为0的状态栏窗格中。

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>parameters

*lpszText*<br/>
指向要放置在状态栏上的字符串。

*nID*<br/>
要放置在状态栏上的字符串的字符串资源 ID。

### <a name="remarks"></a>备注

这通常是状态栏最左侧、最长的窗格。

##  <a name="setprogressbarposition"></a>CFrameWnd：： SetProgressBarPosition

设置任务栏上显示的 Windows 7 进度栏的当前位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>parameters

*nProgressPos*<br/>
指定要设置的位置。 它必须位于 `SetProgressBarRange`所设置的范围内。

### <a name="remarks"></a>备注

##  <a name="setprogressbarrange"></a>CFrameWnd：： SetProgressBarRange

设置任务栏上显示的 Windows 7 进度栏的范围。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>parameters

*nRangeMin*<br/>
最小值。

*nRangeMax*<br/>
最大值。

### <a name="remarks"></a>备注

##  <a name="setprogressbarstate"></a>CFrameWnd：： SetProgressBarState

设置任务栏按钮上显示的进度指示器的类型和状态。

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>parameters

*tbpFlags*<br/>
控制进度按钮当前状态的标志。 仅指定下列标志之一，因为所有状态都是互斥的： TBPF_NOPROGRESS、TBPF_INDETERMINATE、TBPF_NORMAL、TBPF_ERROR、TBPF_PAUSED。

### <a name="remarks"></a>备注

##  <a name="settaskbaroverlayicon"></a>CFrameWnd：： SetTaskbarOverlayIcon

已重载。 将覆盖应用到任务栏按钮，以指示应用程序状态或通知用户。

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>parameters

*nIDResource*<br/>
指定要用作覆盖的图标的资源 ID。 有关详细信息，请参阅*hIcon*的说明。

*lpcszDescr*<br/>
一个指向字符串的指针，该字符串为可访问性目的提供覆盖所传达的信息的替换文本版本。

*hIcon*<br/>
用作覆盖的图标的句柄。 这应该是一个小图标，以每英寸96点（dpi）度量16x16 像素。 如果已将覆盖图标应用到任务栏按钮，将替换现有覆盖。 此值可以为 NULL。 处理 NULL 值的方式取决于任务栏按钮表示单个窗口还是窗口组。 调用应用程序负责在不再需要*hIcon*时将其释放。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;如果操作系统版本低于 Windows 7，或在设置图标时出现错误，则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="settitle"></a>CFrameWnd：： SetTitle

设置窗口对象的标题。

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>parameters

*lpszTitle*<br/>
指向字符串的指针，该字符串包含 window 对象的标题。

##  <a name="showcontrolbar"></a>CFrameWnd：： ShowControlBar

调用此成员函数以显示或隐藏控件条。

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>parameters

*pBar*<br/>
指向要显示或隐藏的控件条的指针。

*bShow*<br/>
如果为 TRUE，则指定显示控件条。 如果为 FALSE，则指定隐藏控件条。

*bDelay*<br/>
如果为 TRUE，则延迟显示控件条。 如果为 FALSE，则立即显示控件条。

##  <a name="showownedwindows"></a>CFrameWnd：： ShowOwnedWindows

调用此成员函数以显示 `CFrameWnd` 对象的后代的所有窗口。

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>parameters

*bShow*<br/>
指定是要显示还是隐藏拥有的窗口。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)
