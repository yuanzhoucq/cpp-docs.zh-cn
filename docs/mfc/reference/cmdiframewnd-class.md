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
ms.openlocfilehash: 321ad0364257d7c20d54f9fdc884073381117c6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222948"
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
|[CMDIFrameWnd：： CMDIFrameWnd](#cmdiframewnd)|构造一个 `CMDIFrameWnd`。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMDIFrameWnd：： CreateClient](#createclient)|为此创建 Windows MDICLIENT 窗口 `CMDIFrameWnd` 。 由的 `OnCreate` 成员函数调用 `CWnd` 。|
|[CMDIFrameWnd：： CreateNewChild](#createnewchild)|创建一个新的子窗口。|
|[CMDIFrameWnd：： GetWindowMenuPopup](#getwindowmenupopup)|返回窗口弹出菜单。|
|[CMDIFrameWnd：： MDIActivate](#mdiactivate)|激活不同的 MDI 子窗口。|
|[CMDIFrameWnd：： MDICascade](#mdicascade)|以层叠格式排列所有子窗口。|
|[CMDIFrameWnd：： MDIGetActive](#mdigetactive)|检索当前处于活动状态的 MDI 子窗口，以及指示是否最大化子窗口的标志。|
|[CMDIFrameWnd：： MDIIconArrange](#mdiiconarrange)|排列所有最小化的文档子窗口。|
|[CMDIFrameWnd：： MDIMaximize](#mdimaximize)|最大化 MDI 子窗口。|
|[CMDIFrameWnd：： MDINext](#mdinext)|激活当前处于活动状态的子窗口之后的子窗口，并将当前处于活动状态的子窗口置于所有其他子窗口之后。|
|[CMDIFrameWnd：： MDIPrev](#mdiprev)|激活上一个子窗口，并紧靠其后放置当前处于活动状态的子窗口。|
|[CMDIFrameWnd：： MDIRestore](#mdirestore)|从最大化或最小化的大小还原 MDI 子窗口。|
|[CMDIFrameWnd：： MDISetMenu](#mdisetmenu)|替换 MDI 框架窗口和/或窗口弹出菜单的菜单。|
|[CMDIFrameWnd：： MDITile](#mditile)|以平铺格式排列所有子窗口。|

## <a name="remarks"></a>备注

若要为应用程序创建有用的 MDI 框架窗口，请从派生一个类 `CMDIFrameWnd` 。 向派生类添加成员变量，以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

可以通过调用的[Create](../../mfc/reference/cframewnd-class.md#create)或[LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)成员函数来构造 MDI 框架窗口 `CFrameWnd` 。

在调用 `Create` 或之前 `LoadFrame` ，必须使用 c + + 运算符在堆上构造框架窗口对象 **`new`** 。 在调用之前 `Create` ，还可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数注册一个窗口类，以设置该框架的图标和类样式。

使用 `Create` 成员函数将框架的创建参数作为直接参数传递。

`LoadFrame`需要的参数少于 `Create` ，而是从资源中检索其大多数默认值，包括框架的标题、图标、快捷键对应表和菜单。 要访问的 `LoadFrame` 所有资源都必须具有相同的资源 ID （例如 IDR_MAINFRAME）。

尽管 `MDIFrameWnd` 派生自 `CFrameWnd` ，但 `CMDIFrameWnd` 不需要使用声明派生自的框架窗口类 `DECLARE_DYNCREATE` 。

`CMDIFrameWnd`类从继承它的很多默认实现 `CFrameWnd` 。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 `CMDIFrameWnd`类具有以下附加功能：

- MDI 框架窗口管理 "MDICLIENT" 窗口，并与控件条一起重新定位。 MDI 客户端窗口是 MDI 子框架窗口的直接父级。 在上指定的 WS_HSCROLL 和 WS_VSCROLL 窗口样式 `CMDIFrameWnd` 应用于 mdi 客户端窗口，而不是主框架窗口，因此用户可以滚动 mdi 工作区（例如，在 Windows 程序管理器中）。

- MDI 框架窗口拥有默认菜单，该菜单在没有活动的 MDI 子窗口时用作菜单栏。 如果有活动的 MDI 子窗口，mdi 框架窗口的菜单栏会自动替换为 MDI 子窗口菜单。

- MDI 框架窗口与当前 MDI 子窗口（如果有）结合使用。 例如，命令消息会委托给 MDI 框架窗口之前的当前活动 MDI 子窗口。

- MDI 框架窗口具有以下标准窗口菜单命令的默认处理程序：

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- MDI 框架窗口还具有 ID_WINDOW_NEW 的实现，这将在当前文档中创建新的框架和视图。 应用程序可以重写这些默认命令实现以自定义 MDI 窗口处理。

不要使用 c + + **`delete`** 运算符销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd` `PostNcDestroy` 当销毁窗口时，的实现将删除 c + + 对象。 当用户关闭框架窗口时，默认 `OnClose` 处理程序将调用 `DestroyWindow` 。

有关的详细信息 `CMDIFrameWnd` ，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd：： CMDIFrameWnd

构造 `CMDIFrameWnd` 对象。

```
CMDIFrameWnd();
```

### <a name="remarks"></a>备注

调用 `Create` 或 `LoadFrame` 成员函数以创建可见的 MDI 框架窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd：： CreateClient

创建用于管理对象的 MDI 客户端窗口 `CMDIChildWnd` 。

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>参数

*lpCreateStruct*<br/>
指向[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构的长指针。

*pWindowMenu*<br/>
指向窗口弹出菜单的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果直接重写成员函数，应调用此成员函数 `OnCreate` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd：： CreateNewChild

创建一个新的子窗口。

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

*nResource*<br/>
与子窗口关联的共享资源的 ID。

*hMenu*<br/>
子窗口的菜单。

*hAccel*<br/>
子窗口的快捷键。

### <a name="remarks"></a>备注

使用此函数可创建 MDI 框架窗口的子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd：： GetWindowMenuPopup

调用此成员函数以获取名为 "Window" 的当前弹出菜单的句柄（弹出菜单，其中包含用于 MDI 窗口管理的菜单项）。

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>参数

*hMenuBar*<br/>
当前菜单栏。

### <a name="return-value"></a>返回值

窗口弹出菜单（如果存在）;否则为 NULL。

### <a name="remarks"></a>备注

默认实现查找包含标准窗口菜单命令（如 ID_WINDOW_NEW 和 ID_WINDOW_TILE_HORZ）的弹出菜单。

如果您有一个不使用标准菜单命令 Id 的窗口菜单，请重写此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd：： MDIActivate

激活不同的 MDI 子窗口。

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>参数

*pWndActivate*<br/>
指向要激活的 MDI 子窗口。

### <a name="remarks"></a>备注

此成员函数将[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)消息发送到正在激活的子窗口，并且子窗口被停用。

如果用户使用鼠标或键盘将焦点更改为 MDI 子窗口，则会发送此消息。

> [!NOTE]
> 将独立于 MDI 框架窗口激活 MDI 子窗口。 当框架变为活动状态时，最后激活的子窗口将发送[WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)消息来绘制活动窗口框架和标题栏，但不会收到另一 WM_MDIACTIVATE 消息。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd：： GetWindowMenuPopup](#getwindowmenupopup)的示例。

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd：： MDICascade

以层叠格式排列所有 MDI 子窗口。

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>参数

nType**<br/>
指定级联标志。 只能指定以下标志： MDITILE_SKIPDISABLED，这会阻止已禁用的 MDI 子窗口进行级联。

### <a name="remarks"></a>备注

的第一个版本 `MDICascade` （没有参数）将所有 MDI 子窗口（包括已禁用的子窗口）进行级联。 如果为*n*参数指定了 MDITILE_SKIPDISABLED，则第二个版本可以选择不级联禁用的 MDI 子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd：： MDIGetActive

检索当前的活动 MDI 子窗口，以及指示子窗口是否最大化的标志。

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>参数

*pbMaximized*<br/>
指向 BOOL 返回值的指针。 如果窗口处于最大化状态，则将设置为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

指向活动的 MDI 子窗口的指针。

### <a name="example"></a>示例

请参阅[CMDIChildWnd：： MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)的示例。

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd：： MDIIconArrange

排列所有最小化的文档子窗口。

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>备注

它不会影响未最小化的子窗口。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd：： MDICascade](#mdicascade)的示例。

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd：： MDIMaximize

最大化指定的 MDI 子窗口。

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向窗口以最大化。

### <a name="remarks"></a>备注

当最大化子窗口时，Windows 会将其调整大小，以使其工作区填充客户端窗口。 Windows 将子窗口的 "控制" 菜单放置在框架的菜单栏中，以便用户可以还原或关闭子窗口。 它还将子窗口的标题添加到框架窗口标题。

如果在当前处于活动状态的 MDI 子窗口处于最大化状态时激活另一个 MDI 子窗口，则 Windows 将还原当前处于活动状态的子窗口并最大化新激活的子窗口。

### <a name="example"></a>示例

请参阅[CMDIChildWnd：： MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)的示例。

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd：： MDINext

激活当前处于活动状态的子窗口之后的子窗口，并将当前处于活动状态的子窗口置于所有其他子窗口之后。

```cpp
void MDINext();
```

### <a name="remarks"></a>备注

如果当前处于活动状态的 MDI 子窗口处于最大化状态，则成员函数将还原当前活动的子窗口并最大化新激活的子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd：： MDIPrev

激活上一个子窗口，并紧靠其后放置当前处于活动状态的子窗口。

```cpp
void MDIPrev();
```

### <a name="remarks"></a>备注

如果当前处于活动状态的 MDI 子窗口处于最大化状态，则成员函数将还原当前活动的子窗口并最大化新激活的子窗口。

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd：： MDIRestore

从最大化或最小化的大小还原 MDI 子窗口。

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要还原的窗口。

### <a name="example"></a>示例

请参阅[CMDIChildWnd：： MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)的示例。

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd：： MDISetMenu

替换 MDI 框架窗口和/或窗口弹出菜单的菜单。

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>参数

*pFrameMenu*<br/>
指定新框架窗口菜单的菜单。 如果为 NULL，则不更改菜单。

*pWindowMenu*<br/>
指定新的窗口弹出菜单的菜单。 如果为 NULL，则不更改菜单。

### <a name="return-value"></a>返回值

指向此消息所替换的框架窗口菜单的指针。 该指针可能是暂时的，不应存储起来供将来使用。

### <a name="remarks"></a>备注

调用后 `MDISetMenu` ，应用程序必须调用的[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成员函数 `CWnd` 以更新菜单栏。

如果此调用替换窗口弹出菜单，则会从上一个窗口菜单中删除 MDI 子窗口菜单项，并将其添加到新的窗口弹出菜单。

如果 MDI 子窗口已最大化并且此调用替换 MDI 框架窗口菜单，则会从上一个框架窗口菜单中删除 "控制" 菜单和 "还原" 控件，并将其添加到 "新建" 菜单。

如果使用框架管理 MDI 子窗口，请不要调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd：： MDITile

以平铺格式排列所有子窗口。

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>参数

nType**<br/>
指定平铺标志。 此参数可以是以下任何一个标志：

- MDITILE_HORIZONTAL 平铺显示 MDI 子窗口，使一个窗口出现在另一个窗口之上。

- MDITILE_SKIPDISABLED 阻止禁用 MDI 子窗口平铺。

- MDITILE_VERTICAL 平铺显示 MDI 子窗口，使一个窗口出现在另一个窗口的旁边。

### <a name="remarks"></a>备注

不带参数的第一个版本 `MDITile` 在 windows 版本3.1 和更高版本下垂直平铺窗口。 第二个版本根据*n*参数的值，垂直或水平平铺窗口。

### <a name="example"></a>示例

请参阅[CMDIFrameWnd：： MDICascade](#mdicascade)的示例。

## <a name="see-also"></a>另请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
