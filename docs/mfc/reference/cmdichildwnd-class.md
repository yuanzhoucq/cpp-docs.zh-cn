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
ms.openlocfilehash: ffe7b975443b8bdc050bcb19af4f990b2e5ffafa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576626"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 类

提供 Windows 多文档界面 (MDI) 子窗口功能，并提供管理窗口的成员。

## <a name="syntax"></a>语法

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|构造 `CMDIChildWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|创建与关联的 Windows MDI 子窗口`CMDIChildWnd`对象。|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|返回父级的 MDI 客户端窗口的 MDI 框架。|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|激活此 MDI 子窗口。|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|销毁此 MDI 子窗口。|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|最大化此 MDI 子窗口。|
|[CMDIChildWnd::MDIRestore](#mdirestore)|从最大化或最小化大小还原此 MDI 子窗口。|
|[CMDIChildWnd::SetHandles](#sethandles)|设置菜单和快捷键资源的句柄。|

## <a name="remarks"></a>备注

MDI 子窗口看上去像一个典型的框架窗口，只不过 MDI 子窗口将显示在 MDI 框架窗口内，而不是桌面。 MDI 子窗口不具有其自己的菜单栏，但改为共享 MDI 框架窗口的菜单。 该框架将自动更改来表示当前处于活动状态的 MDI 子窗口的 MDI 框架菜单。

若要创建你的应用程序的有用 MDI 子窗口，从派生类`CMDIChildWnd`。 将成员变量添加到派生类，以存储特定于你的应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

有三种方法来构造的 MDI 子窗口：

- 直接构造使用`Create`。

- 直接构造使用`LoadFrame`。

- 间接构造通过文档模板。

在调用之前`Create`或`LoadFrame`，必须构造上使用 c + + 堆的框架窗口对象**新**运算符。 然后再调用`Create`您还可以注册窗口类[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数设置的帧的图标和类样式。

使用`Create`成员函数将为快速参数传递的帧创建参数。

`LoadFrame` 需要较少的参数，而不是`Create`，并改为从资源，包括帧的标题、 图标、 快捷键对应表和菜单检索大部分其默认值。 可由`LoadFrame`，所有这些资源必须具有相同的资源 ID (例如，IDR_MAINFRAME)。

当`CMDIChildWnd`对象包含的视图和文档、 通过的框架，而不是直接由程序员创建间接。 `CDocTemplate`对象协调帧的创建、 包含视图的创建和连接到相应的文档的视图。 参数`CDocTemplate`构造函数指定`CRuntimeClass`的三个类涉及到 （文档、 框架和视图）。 一个`CRuntimeClass`框架使用对象来动态创建新帧时由用户指定 （例如，通过使用新建文件命令或 MDI 窗口新命令）。

框架窗口类派生自`CMDIChildWnd`必须使用 DECLARE_DYNCREATE 声明使上述的 RUNTIME_CLASS 机制，才能正常工作。

`CMDIChildWnd`类继承了其默认实现从大量`CFrameWnd`。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 `CMDIChildWnd`类具有下列附加功能：

- 结合`CMultiDocTemplate`类，多个`CMDIChildWnd`从同一个文档模板对象共享相同的菜单上，保存 Windows 系统资源。

- 当前处于活动状态的 MDI 子窗口菜单完全替换 MDI 框架窗口的菜单中，并且当前处于活动状态的 MDI 子窗口的标题添加到 MDI 框架窗口的标题。 实现结合 MDI 框架窗口的 MDI 子窗口函数的更多示例，请参阅`CMDIFrameWnd`类说明。

不使用 c + +**删除**运算符来销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd`的实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。

有关详细信息`CMDIChildWnd`，请参阅[帧 Windows](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

调用以构造`CMDIChildWnd`对象。

```
CMDIChildWnd();
```

### <a name="remarks"></a>备注

调用`Create`创建可见的窗口。

### <a name="example"></a>示例

  有关示例，请参阅[CMDIChildWnd::Create](#create)。

##  <a name="create"></a>  CMDIChildWnd::Create

调用此成员函数可创建的 Windows MDI 子窗口，并将其附加到`CMDIChildWnd`对象。

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

*lpszClassName*<br/>
指向以 null 结尾的字符串命名的 Windows 类 ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)结构)。 类名可以是任何名称与注册[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数。 应为 NULL 的一种标准`CMDIChildWnd`。

*lpszWindowName*<br/>
指向以 null 结尾的字符串的字符串表示窗口名称。 用作标题栏文本。

*dwStyle*<br/>
指定的窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。 WS_CHILD 样式是必需的。

*rect*<br/>
包含的大小和窗口的位置。 `rectDefault`值，则允许指定的大小和位置的新的 Windows `CMDIChildWnd`。

*pParentWnd*<br/>
指定窗口的父级。 如果为 NULL，则使用主应用程序窗口。

*pContext*<br/>
指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

当前处于活动状态的 MDI 子框架窗口可以确定父框架窗口的标题。 通过关闭 FWS_ADDTOTITLE 样式位子框架窗口的情况下禁用此功能。

框架调用此成员函数以响应用户命令以创建子窗口，并使用框架*pContext*参数正确连接到该应用程序的子窗口。 当您调用`Create`， *pContext*可以为 NULL。

### <a name="example"></a>示例

示例 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>示例

示例 2：

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

调用此函数可返回 MDI 父框架。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>返回值

指向 MDI 父框架窗口的指针。

### <a name="remarks"></a>备注

返回该框架是从删除的两个父代`CMDIChildWnd`，是指类型管理的 MDICLIENT 窗口的父`CMDIChildWnd`对象。 调用[GetParent](../../mfc/reference/cwnd-class.md#getparent)成员函数返回`CMDIChildWnd`作为临时对象的直接 MDICLIENT 父`CWnd`指针。

### <a name="example"></a>示例

  有关示例，请参阅[CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

调用此成员函数以激活独立于 MDI 框架窗口的 MDI 子窗口。

```
void MDIActivate();
```

### <a name="remarks"></a>备注

当帧变为活动状态时，上次激活的子窗口也将被激活。

### <a name="example"></a>示例

  有关示例，请参阅[CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

调用此成员函数要销毁的 MDI 子窗口。

```
void MDIDestroy();
```

### <a name="remarks"></a>备注

成员函数从框架窗口中删除子窗口的标题和停用的子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

调用此成员函数以最大化的 MDI 子窗口。

```
void MDIMaximize();
```

### <a name="remarks"></a>备注

当子窗口已最大化时，Windows 调整大小以使其填充框架窗口的客户端区域的工作区。 Windows 将放置子窗口的控件菜单在框架的菜单栏中，以便用户可以还原或关闭子窗口，并将子窗口的标题添加到框架窗口标题。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

调用此成员函数以最大化或最小化大小从还原的 MDI 子窗口。

```
void MDIRestore();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

设置菜单和快捷键资源的句柄。

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
菜单资源的句柄。

*hAccel*<br/>
快捷键资源的句柄。

### <a name="remarks"></a>备注

调用此函数可设置使用 MDI 子窗口对象的菜单和快捷键资源。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../visual-cpp-samples.md)<br/>
[MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)
