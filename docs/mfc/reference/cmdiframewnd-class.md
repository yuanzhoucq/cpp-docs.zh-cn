---
title: CMDIFrameWnd 类
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: a6e68f6368a7b45e0a566a7d2d12f23a9cd62b12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370062"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 类

提供 Windows 多文档界面 (MDI) 框架窗口功能，并提供管理窗口的成员。

## <a name="syntax"></a>语法

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMDIFramewnd：：CMDIFramewnd](#cmdiframewnd)|构造一个 `CMDIFrameWnd`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMDIFramewnd：：创建客户端](#createclient)|为此`CMDIFrameWnd`创建一个 Windows MDICLIENT 窗口。 由 的成员`OnCreate`函数调用`CWnd`。|
|[CMDIFramewnd：：创建新儿童](#createnewchild)|创建新的子窗口。|
|[CMDIFramewnd：：获取窗口菜单弹出](#getwindowmenupopup)|返回"窗口"弹出式菜单。|
|[CMDIFramewnd：：MDIActivate](#mdiactivate)|激活其他 MDI 子窗口。|
|[CMDIFramewnd：：MDICascade](#mdicascade)|以级联格式排列所有子窗口。|
|[CMDIFramewnd：MDIGetactive](#mdigetactive)|检索当前活动的 MDI 子窗口，以及指示子项是否最大化的标志。|
|[CMDIFramewnd：：MDIIcon排列](#mdiiconarrange)|排列所有最小化的文档子窗口。|
|[CMDIFramewnd：：MDI最大化](#mdimaximize)|最大化 MDI 子窗口。|
|[CMDIFramewnd：：MDINext](#mdinext)|立即激活当前活动子窗口后面的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口后面。|
|[CMDIFramewnd：：MDIPrev](#mdiprev)|激活以前的子窗口，并将当前处于活动状态的子窗口立即放在窗口后面。|
|[CMDIFramewnd：：MDI还原](#mdirestore)|从最大大小或最小化大小还原 MDI 子窗口。|
|[CMDIFramewnd：：MDISetMenu](#mdisetmenu)|替换 MDI 框架窗口的菜单、窗口弹出窗口菜单或两者。|
|[CMDIFramewnd：：MDITile](#mditile)|以平铺格式排列所有子窗口。|

## <a name="remarks"></a>备注

要为应用程序创建有用的 MDI 框架窗口，请从`CMDIFrameWnd`派生类。 将成员变量添加到派生类以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

可以通过调用 的["创建](../../mfc/reference/cframewnd-class.md#create)"或["LoadFrame"](../../mfc/reference/cframewnd-class.md#loadframe)成员函数来构造 MDI 帧窗口`CFrameWnd`。

在调用`Create`或`LoadFrame`之前，必须**使用新运算符**C++在堆上构造帧窗口对象。 在调用`Create`之前，您还可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数注册窗口类，以设置框架的图标和类样式。

使用`Create`成员函数将帧的创建参数作为即时参数传递。

`LoadFrame`需要的参数少于`Create`，而是从资源检索其大部分默认值，包括框架的标题、图标、快捷键表和菜单。 要由`LoadFrame`访问，所有这些资源必须具有相同的资源 ID（例如，IDR_MAINFRAME）。

尽管`MDIFrameWnd`派生自`CFrameWnd`，但不需要使用`CMDIFrameWnd``DECLARE_DYNCREATE`声明派生的帧窗口类。

类`CMDIFrameWnd`从`CFrameWnd`继承其大部分默认实现。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 该`CMDIFrameWnd`类具有以下附加功能：

- MDI 框架窗口管理 MDICLIENT 窗口，将其与控制栏一起重新定位。 MDI 客户端窗口是 MDI 子框架窗口的直接父级。 在 DDI 客户端窗口而不是主`CMDIFrameWnd`框架窗口上指定的WS_HSCROLL和WS_VSCROLL窗口样式，以便用户可以滚动 MDI 工作区（例如，如 Windows 程序管理器中所示）。

- MDI 框架窗口具有默认菜单，当没有活动 MDI 子窗口时，该菜单用作菜单栏。 当存在活动 MDI 子项时，MDI 框架窗口的菜单栏将自动替换为 MDI 子窗口菜单。

- MDI 框架窗口与当前 MDI 子窗口（如果有）配合使用。 例如，命令消息在 MDI 帧窗口之前委派给当前活动的 MDI 子级。

- MDI 框架窗口具有以下标准窗口菜单命令的默认处理程序：

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- MDI 框架窗口还具有ID_WINDOW_NEW的实现，从而在当前文档上创建新的帧和视图。 应用程序可以重写这些默认命令实现以自定义 MDI 窗口处理。

请勿使用C++**删除**运算符来破坏框架窗口。 请改用 `CWnd::DestroyWindow`。 当`CFrameWnd`窗口被`PostNcDestroy`破坏时，将删除C++对象。 当用户关闭帧窗口时，默认`OnClose`处理程序将调用`DestroyWindow`。

有关 的详细信息`CMDIFrameWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFramewnd：：CMDIFramewnd

构造 `CMDIFrameWnd` 对象。

```
CMDIFrameWnd();
```

### <a name="remarks"></a>备注

调用`Create`或`LoadFrame`成员函数以创建可见的 MDI 帧窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFramewnd：：创建客户端

创建管理`CMDIChildWnd`对象的 MDI 客户端窗口。

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>参数

*lpCreatestruct*<br/>
指向[CREATESTRUCT 结构](/windows/win32/api/winuser/ns-winuser-createstructw)的长指针。

*pWindowMenu*<br/>
指向窗口弹出菜单的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果直接重写成员函数，`OnCreate`则应调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFramewnd：：创建新儿童

创建新的子窗口。

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>参数

*pClass*<br/>
要创建的子窗口的运行时类。

*n资源*<br/>
与子窗口关联的共享资源的 ID。

*hMenu*<br/>
子窗口的菜单。

*哈克尔*<br/>
子窗口的加速器。

### <a name="remarks"></a>备注

使用此函数可以创建 MDI 框架窗口的子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFramewnd：：获取窗口菜单弹出

调用此成员函数以获取当前名为"窗口"的弹出式菜单（包含 MDI 窗口管理的菜单项的弹出菜单）的句柄。

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>参数

*hMenuBar*<br/>
当前菜单栏。

### <a name="return-value"></a>返回值

窗口弹出菜单（如果存在）;否则 NULL。

### <a name="remarks"></a>备注

默认实现查找包含标准窗口菜单命令（如ID_WINDOW_NEW和ID_WINDOW_TILE_HORZ）的弹出菜单。

如果窗口菜单不使用标准菜单命令"指示"，则覆盖此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFramewnd：：MDIActivate

激活其他 MDI 子窗口。

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>参数

*pWndActivate*<br/>
指向要激活的 MDI 子窗口。

### <a name="remarks"></a>备注

此成员函数向正在激活的子窗口和正在停用的子窗口发送[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)消息。

如果用户使用鼠标或键盘将焦点更改为 MDI 子窗口，则发送的消息与发送的消息相同。

> [!NOTE]
> 独立于 MDI 框架窗口激活 MDI 子窗口。 当帧变为活动状态时，上次激活的子窗口将发送[一条WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)消息以绘制活动窗口框和标题栏，但不会收到另一WM_MDIACTIVATE消息。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd 的示例：获取窗口菜单弹出](#getwindowmenupopup)。

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFramewnd：：MDICascade

以级联格式排列所有 MDI 子窗口。

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>参数

nType**<br/>
指定级联标志。 只能指定以下标志：MDITILE_SKIPDISABLED，以防止禁用的 MDI 子窗口被级联。

### <a name="remarks"></a>备注

第一个版本`MDICascade`没有参数，级联所有 MDI 子窗口，包括禁用的。 如果为*nType*参数指定MDITILE_SKIPDISABLED，则第二个版本可选地不会级联禁用的 MDI 子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFramewnd：MDIGetactive

检索当前活动 MDI 子窗口，以及指示子窗口是否最大化的标志。

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>参数

*pb 最大化*<br/>
指向 BOOL 返回值的指针。 如果窗口最大化，则在返回时设置为 TRUE;如果窗口最大化，则设置为 TRUE。否则 FALSE。

### <a name="return-value"></a>返回值

指向活动 MDI 子窗口的指针。

### <a name="example"></a>示例

请参阅[CMDIChildwnd 的示例：：MDI最大化](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFramewnd：：MDIIcon排列

排列所有最小化的文档子窗口。

```
void MDIIconArrange();
```

### <a name="remarks"></a>备注

它不会影响未最小化的子窗口。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd 的示例：：MDICascade](#mdicascade)。

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFramewnd：：MDI最大化

最大化指定的 MDI 子窗口。

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向窗口以最大化。

### <a name="remarks"></a>备注

最大化子窗口时，Windows 会调整其大小，使其工作区填充客户端窗口。 Windows 将子窗口的"控件"菜单放在框架的菜单栏中，以便用户可以还原或关闭子窗口。 它还将子窗口的标题添加到框架窗口标题。

如果在最大化当前活动的 MDI 子窗口时激活另一个 MDI 子窗口，Windows 将恢复当前处于活动状态的子窗口并最大化新激活的子窗口。

### <a name="example"></a>示例

请参阅[CMDIChildwnd 的示例：：MDI最大化](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFramewnd：：MDINext

立即激活当前活动子窗口后面的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口后面。

```
void MDINext();
```

### <a name="remarks"></a>备注

如果当前活动的 MDI 子窗口最大化，则成员函数将恢复当前处于活动状态的子级并最大化新激活的子级。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFramewnd：：MDIPrev

激活以前的子窗口，并将当前处于活动状态的子窗口立即放在窗口后面。

```
void MDIPrev();
```

### <a name="remarks"></a>备注

如果当前活动的 MDI 子窗口最大化，则成员函数将恢复当前处于活动状态的子级并最大化新激活的子级。

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFramewnd：：MDI还原

从最大大小或最小化大小还原 MDI 子窗口。

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向要还原的窗口。

### <a name="example"></a>示例

请参阅[CMDIChildwnd 的示例：：MDI 还原](../../mfc/reference/cmdichildwnd-class.md#mdirestore)。

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFramewnd：：MDISetMenu

替换 MDI 框架窗口的菜单、窗口弹出窗口菜单或两者。

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>参数

*pFrameMenu*<br/>
指定新框架窗口菜单的菜单。 如果为 NULL，则菜单不会更改。

*pWindowMenu*<br/>
指定新窗口弹出式菜单的菜单。 如果为 NULL，则菜单不会更改。

### <a name="return-value"></a>返回值

指向由此消息替换的框架窗口菜单的指针。 该指针可能是暂时的，不应存储起来供将来使用。

### <a name="remarks"></a>备注

调用`MDISetMenu`后，应用程序必须调用 的`CWnd` [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成员函数来更新菜单栏。

如果此调用替换窗口弹出窗口菜单，则 MDI 子窗口菜单项将从上一个窗口菜单中删除，并添加到新的窗口弹出窗口菜单中。

如果最大化 MDI 子窗口，并且此调用替换 MDI 框架窗口菜单，则"控制"菜单和还原控件将从以前的框架窗口菜单中删除并添加到新菜单。

如果使用框架管理 MDI 子窗口，请不要调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFramewnd：：MDITile

以平铺格式排列所有子窗口。

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>参数

nType**<br/>
指定平铺标志。 此参数可以是以下标志之一：

- MDITILE_HORIZONTAL磁贴 MDI 子窗口，以便一个窗口显示在另一个窗口的上方。

- MDITILE_SKIPDISABLED防止禁用的 MDI 子窗口被平铺。

- MDITILE_VERTICAL磁贴 MDI 子窗口，以便一个窗口出现在另一个窗口旁边。

### <a name="remarks"></a>备注

第一个版本`MDITile`没有参数，在 Windows 版本 3.1 和更高版本下垂直放置窗口。 第二个版本垂直或水平地放置窗口，具体取决于*nType*参数的值。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd 的示例：：MDICascade](#mdicascade)。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
