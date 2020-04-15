---
title: CMDIChildWnd 类
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 0fbcb47f3148b72a3155e7c17cc913d652c70c2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370084"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 类

提供 Windows 多文档界面 (MDI) 子窗口功能，并提供管理窗口的成员。

## <a name="syntax"></a>语法

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMDIChildwnd：CMDIChildwnd](#cmdichildwnd)|构造 `CMDIChildWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMDIChildwnd：创建](#create)|创建与`CMDIChildWnd`对象关联的 Windows MDI 子窗口。|
|[CMDIChildwnd：：GetMDIFrame](#getmdiframe)|返回 MDI 客户端窗口的父 MDI 帧。|
|[CMDIChildwnd：MDIActivate](#mdiactivate)|激活此 MDI 子窗口。|
|[CMDIChildwnd：MDI销毁](#mdidestroy)|销毁此 MDI 子窗口。|
|[CMDIChildwnd：：MDI最大化](#mdimaximize)|最大化此 MDI 子窗口。|
|[CMDIChildwnd：：MDI恢复](#mdirestore)|从最大大小或最小化大小还原此 MDI 子窗口。|
|[CMDIChildwnd：：设置手柄](#sethandles)|设置菜单和快捷键资源的句柄。|

## <a name="remarks"></a>备注

MDI 子窗口与典型的框架窗口非常类似，只不过 MDI 子窗口显示在 MDI 框架窗口内，而不是桌面上。 MDI 子窗口没有自己的菜单栏，而是共享 MDI 框架窗口的菜单。 框架会自动更改 MDI 框架菜单以表示当前处于活动状态的 MDI 子窗口。

要为应用程序创建有用的 MDI 子窗口，请从`CMDIChildWnd`派生类。 将成员变量添加到派生类以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

有三种方法可以构造 MDI 子窗口：

- 使用`Create`直接构造它。

- 使用`LoadFrame`直接构造它。

- 通过文档模板间接构造它。

在调用`Create`或`LoadFrame`之前，必须**使用新运算符**C++在堆上构造帧窗口对象。 在调用`Create`之前，您还可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数注册窗口类，以设置框架的图标和类样式。

使用`Create`成员函数将帧的创建参数作为即时参数传递。

`LoadFrame`需要的参数少于`Create`，而是从资源检索其大部分默认值，包括框架的标题、图标、快捷键表和菜单。 要被`LoadFrame`访问，所有这些资源必须具有相同的资源 ID（例如，IDR_MAINFRAME）。

当对象`CMDIChildWnd`包含视图和文档时，它们由框架间接创建，而不是由程序员直接创建。 该`CDocTemplate`对象协调框架的创建、包含视图的创建以及视图与相应文档的连接。 构造函数的`CDocTemplate`参数指定所涉及的三`CRuntimeClass`个类（文档、框架和视图）的参数。 框架`CRuntimeClass`使用对象在用户指定时动态创建新框架（例如，通过使用"文件新建"命令或 MDI Window New 命令）。

必须用DECLARE_DYNCREATE声明派生的`CMDIChildWnd`帧窗口类，以便上述RUNTIME_CLASS机制正常工作。

类`CMDIChildWnd`从`CFrameWnd`继承其大部分默认实现。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 该`CMDIChildWnd`类具有以下附加功能：

- 与类结合，`CMultiDocTemplate`同一文档`CMDIChildWnd`模板中的多个对象共享同一个菜单，从而节省了 Windows 系统资源。

- 当前活动的 MDI 子窗口菜单完全替换 MDI 框架窗口的菜单，当前活动 MDI 子窗口的标题将添加到 MDI 框架窗口的标题中。 有关与 MDI 框架窗口结合实现的 MDI 子窗口函数的进一步示例，请参阅`CMDIFrameWnd`类说明。

请勿使用C++**删除**运算符来破坏框架窗口。 请改用 `CWnd::DestroyWindow`。 当`CFrameWnd`窗口被`PostNcDestroy`破坏时，将删除C++对象。 当用户关闭帧窗口时，默认`OnClose`处理程序将调用`DestroyWindow`。

有关 的详细信息`CMDIChildWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildwnd：CMDIChildwnd

调用以构造对象`CMDIChildWnd`。

```
CMDIChildWnd();
```

### <a name="remarks"></a>备注

调用`Create`以创建可见窗口。

### <a name="example"></a>示例

  请参阅[CMDIChildWnd 的示例：：创建](#create)。

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildwnd：创建

调用此成员函数以创建 Windows MDI 子窗口并将其附加到`CMDIChildWnd`对象。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
指向命名 Windows 类[（WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构）的 null 端接字符串。 类名称可以是注册为[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数的任何名称。 标准 应为`CMDIChildWnd`NULL。

*lpsz窗口名称*<br/>
指向表示窗口名称的 null 端接字符串。 用作标题栏的文本。

*dwStyle*<br/>
指定窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。 WS_CHILD样式是必需的。

*矩形*<br/>
包含窗口的大小和位置。 该`rectDefault`值允许 Windows 指定新`CMDIChildWnd`的大小和位置。

*pparentwnd*<br/>
指定窗口的父级。 如果为 NULL，则使用主应用程序窗口。

*pContext*<br/>
指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以是 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

当前处于活动状态的 MDI 子框架窗口可以确定父框架窗口的标题。 此功能通过关闭子框架窗口的FWS_ADDTOTITLE样式位而禁用。

框架调用此成员函数以响应用户命令以创建子窗口，并且框架使用*pContext*参数将子窗口正确连接到应用程序。 调用 时`Create` *，pContext*可以为 NULL。

### <a name="example"></a>示例

示例 1：

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>示例

示例 2：

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildwnd：：GetMDIFrame

调用此函数以返回 MDI 父帧。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>返回值

指向 MDI 父框架窗口的指针。

### <a name="remarks"></a>备注

返回的帧是从 中删除的两个`CMDIChildWnd`父级，是管理对象的 MDICLIENT 类型窗口的`CMDIChildWnd`父级。 调用[GetParent](../../mfc/reference/cwnd-class.md#getparent)成员函数以`CMDIChildWnd`返回对象的直接 MDICLIENT 父级作为临时`CWnd`指针。

### <a name="example"></a>示例

  请参阅[CMDIFrameWnd 的示例：：MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildwnd：MDIActivate

调用此成员函数以独立于 MDI 框架窗口激活 MDI 子窗口。

```
void MDIActivate();
```

### <a name="remarks"></a>备注

当帧变为活动状态时，上次激活的子窗口也将激活。

### <a name="example"></a>示例

  请参阅[CMDIFrameWnd 的示例：获取窗口菜单弹出](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildwnd：MDI销毁

调用此成员函数以销毁 MDI 子窗口。

```
void MDIDestroy();
```

### <a name="remarks"></a>备注

成员函数从框架窗口中删除子窗口的标题，并停用子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildwnd：：MDI最大化

调用此成员函数以最大化 MDI 子窗口。

```
void MDIMaximize();
```

### <a name="remarks"></a>备注

最大化子窗口时，Windows 会调整其大小，使其工作区填充框架窗口的工作区。 Windows 将子窗口的"控件"菜单放在框架的菜单栏中，以便用户可以还原或关闭子窗口，并将子窗口的标题添加到框架窗口标题中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildwnd：：MDI恢复

调用此成员函数以从最大大小或最小化大小还原 MDI 子窗口。

```
void MDIRestore();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildwnd：：设置手柄

设置菜单和快捷键资源的句柄。

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
菜单资源的句柄。

*哈克尔*<br/>
加速器资源的句柄。

### <a name="remarks"></a>备注

调用此函数以设置 MDI 子窗口对象使用的菜单和快捷键资源。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)
