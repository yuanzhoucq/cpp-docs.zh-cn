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
ms.openlocfilehash: 0acd42db19151001d9e292561ef20e469f9e14ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222961"
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
|[CMDIChildWnd：： CMDIChildWnd](#cmdichildwnd)|构造 `CMDIChildWnd` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMDIChildWnd：： Create](#create)|创建与对象关联的 Windows MDI 子窗口 `CMDIChildWnd` 。|
|[CMDIChildWnd：： GetMDIFrame](#getmdiframe)|返回 MDI 客户端窗口的父 MDI 帧。|
|[CMDIChildWnd：： MDIActivate](#mdiactivate)|激活此 MDI 子窗口。|
|[CMDIChildWnd：： MDIDestroy](#mdidestroy)|销毁此 MDI 子窗口。|
|[CMDIChildWnd：： MDIMaximize](#mdimaximize)|最大化此 MDI 子窗口。|
|[CMDIChildWnd：： MDIRestore](#mdirestore)|从最大化或最小化的大小还原此 MDI 子窗口。|
|[CMDIChildWnd：： SetHandles](#sethandles)|设置菜单和快捷键资源的句柄。|

## <a name="remarks"></a>备注

MDI 子窗口的外观非常类似于典型的框架窗口，只不过 MDI 子窗口出现在 MDI 框架窗口内而不是桌面上。 MDI 子窗口没有自己的菜单栏，而是共享 MDI 框架窗口的菜单。 框架自动更改 MDI 框架菜单，以表示当前处于活动状态的 MDI 子窗口。

若要为应用程序创建有用的 MDI 子窗口，请从派生一个类 `CMDIChildWnd` 。 向派生类添加成员变量，以存储特定于应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。

可以通过三种方式构造 MDI 子窗口：

- 使用直接构造它 `Create` 。

- 使用直接构造它 `LoadFrame` 。

- 通过文档模板间接构造它。

在调用 `Create` 或之前 `LoadFrame` ，必须使用 c + + 运算符在堆上构造框架窗口对象 **`new`** 。 在调用之前 `Create` ，还可以使用[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数注册一个窗口类，以设置该框架的图标和类样式。

使用 `Create` 成员函数将框架的创建参数作为直接参数传递。

`LoadFrame`需要的参数少于 `Create` ，而是从资源中检索其大多数默认值，包括框架的标题、图标、快捷键对应表和菜单。 要使其可供访问 `LoadFrame` ，所有这些资源都必须具有相同的资源 ID （例如 IDR_MAINFRAME）。

当 `CMDIChildWnd` 对象包含视图和文档时，框架会间接创建它们，而不是直接由程序员创建。 `CDocTemplate`对象协调框架创建、创建包含视图的过程，以及将视图连接到相应的文档。 构造函数的参数 `CDocTemplate` 指定 `CRuntimeClass` 所涉及的三个类（文档、框架和视图）的。 `CRuntimeClass`当用户指定时，框架使用对象动态创建新帧（例如，通过使用 "文件" "新建" 或 "MDI 窗口" "新建" 命令）。

从派生的框架窗口类 `CMDIChildWnd` 必须使用 DECLARE_DYNCREATE 进行声明，这样上述 RUNTIME_CLASS 机制才能正常工作。

`CMDIChildWnd`类从继承它的很多默认实现 `CFrameWnd` 。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 `CMDIChildWnd`类具有以下附加功能：

- 与 `CMultiDocTemplate` 类一起， `CMDIChildWnd` 同一文档模板中的多个对象共享相同的菜单，保存 Windows 系统资源。

- 当前处于活动状态的 MDI 子窗口菜单完全取代 MDI 框架窗口菜单，当前活动的 MDI 子窗口的标题将添加到 MDI 框架窗口的标题中。 有关与 MDI 框架窗口一起实现的 MDI 子窗口函数的更多示例，请参阅 `CMDIFrameWnd` 类说明。

不要使用 c + + **`delete`** 运算符销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd` `PostNcDestroy` 当销毁窗口时，的实现将删除 c + + 对象。 当用户关闭框架窗口时，默认 `OnClose` 处理程序将调用 `DestroyWindow` 。

有关的详细信息 `CMDIChildWnd` ，请参阅[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd：： CMDIChildWnd

调用构造 `CMDIChildWnd` 对象。

```
CMDIChildWnd();
```

### <a name="remarks"></a>备注

调用 `Create` 以创建可见窗口。

### <a name="example"></a>示例

  请参阅[CMDIChildWnd：： Create](#create)的示例。

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd：： Create

调用此成员函数以创建 Windows MDI 子窗口，并将其附加到 `CMDIChildWnd` 对象。

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
指向以 null 结尾的字符串，该字符串对 Windows 类（ [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)结构）进行命名。 类名称可以是注册到[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) global 函数的任何名称。 对于标准，应为 NULL `CMDIChildWnd` 。

*lpszWindowName*<br/>
指向以 null 结尾的字符串，该字符串表示窗口名称。 用作标题栏的文本。

*dwStyle*<br/>
指定窗口[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)特性。 WS_CHILD 样式是必需的。

*rect*<br/>
包含窗口的大小和位置。 `rectDefault`该值允许 Windows 指定新的大小和位置 `CMDIChildWnd` 。

*pParentWnd*<br/>
指定窗口的父级。 如果为 NULL，则使用主应用程序窗口。

*pContext*<br/>
指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

当前处于活动状态的 MDI 子框架窗口可以确定父框架窗口的标题。 此功能通过关闭子框架窗口的 FWS_ADDTOTITLE 样式位而禁用。

框架调用此成员函数来响应用户命令以创建子窗口，框架使用*pContext*参数将子窗口正确地连接到应用程序。 调用时 `Create` ， *pContext*可以为 NULL。

### <a name="example"></a>示例

示例 1：

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>示例

示例 2：

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd：： GetMDIFrame

调用此函数可返回 MDI 父框架。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>返回值

指向 MDI 父框架窗口的指针。

### <a name="remarks"></a>备注

返回的帧是从中删除的两个父级 `CMDIChildWnd` ，是管理对象的 MDICLIENT 类型的窗口的父级 `CMDIChildWnd` 。 调用[GetParent](../../mfc/reference/cwnd-class.md#getparent)成员函数，以将 `CMDIChildWnd` 对象的直属 MDICLIENT 父级作为临时指针返回 `CWnd` 。

### <a name="example"></a>示例

  请参阅[CMDIFrameWnd：： MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)的示例。

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd：： MDIActivate

调用此成员函数以独立于 MDI 框架窗口激活 MDI 子窗口。

```cpp
void MDIActivate();
```

### <a name="remarks"></a>备注

当该帧变为活动状态时，最后激活的子窗口也将被激活。

### <a name="example"></a>示例

  请参阅[CMDIFrameWnd：： GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)的示例。

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd：： MDIDestroy

调用此成员函数以销毁 MDI 子窗口。

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>备注

成员函数将从框架窗口中删除子窗口的标题，并停用子窗口。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd：： MDIMaximize

调用此成员函数以最大化 MDI 子窗口。

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>备注

当最大化子窗口时，Windows 会将其调整大小，以使其工作区填充框架窗口的工作区。 Windows 将子窗口的 "控制" 菜单放置在框架的菜单栏中，以便用户可以还原或关闭子窗口，并将子窗口的标题添加到框架窗口标题中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd：： MDIRestore

调用此成员函数以从最大化或最小化的大小还原 MDI 子窗口。

```cpp
void MDIRestore();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd：： SetHandles

设置菜单和快捷键资源的句柄。

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
菜单资源的句柄。

*hAccel*<br/>
加速器资源的句柄。

### <a name="remarks"></a>备注

调用此函数可设置 MDI 子窗口对象所使用的菜单和快捷键资源。

## <a name="see-also"></a>另请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)
