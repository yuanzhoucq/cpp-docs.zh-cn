---
title: CContainedWindowT 类
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747747"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 类

此类实现包含在另一个对象中的窗口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>参数

*TBase*<br/>
新类的基类。 默认基类为`CWindow`。

*特温·特威茨*<br/>
定义窗口样式的特征类。 默认为 `CControlWinTraits`。

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是 中的`CContainedWindowT`一个专门化。 如果要更改基类或特征，请使用`CContainedWindowT`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C包含窗口：：C包含窗口T](#ccontainedwindowt)|构造函数。 初始化数据成员以指定将处理包含的窗口的消息的消息。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C包含窗口T：创建](#create)|创建一个窗口。|
|[C包含窗口T：:DefWindowProc](#defwindowproc)|提供默认消息处理。|
|[C包含窗口T：获取当前消息](#getcurrentmessage)|返回当前消息。|
|[CContained窗口：：注册Wnd超级类](#registerwndsuperclass)|注册包含窗口的窗口类。|
|[C包含窗口T：：子类窗口](#subclasswindow)|对窗口子类化。|
|[C包含窗口T：：切换消息映射](#switchmessagemap)|更改用于处理包含的窗口的消息的消息映射。|
|[包含窗口：：取消子类窗口](#unsubclasswindow)|还原先前子类化的窗口。|
|[C包含窗口T：：窗口Proc](#windowproc)|（静态）处理发送到包含的窗口的消息。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C包含窗口：：m_dwMsgMapID](#m_dwmsgmapid)|标识将处理包含的窗口的消息的消息。|
|[C包含窗口：：m_lpszClassName](#m_lpszclassname)|指定新窗口类将基于的现有窗口类的名称。|
|[C包含窗口T：m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|
|[C包含窗口T：m_pObject](#m_pobject)|指向包含的对象。|

## <a name="remarks"></a>备注

`CContainedWindowT`实现包含在另一个对象中的窗口。 `CContainedWindowT`的窗口过程使用包含对象中的消息映射将消息定向到相应的处理程序。 构造对象时`CContainedWindowT`，应指定应使用的消息映射。

`CContainedWindowT`允许您通过对现有窗口类进行超类化来创建新窗口。 该方法`Create`首先注册一个基于现有类但使用`CContainedWindowT::WindowProc`的窗口类。 `Create`然后基于此新窗口类创建一个窗口。 的每个`CContainedWindowT`实例都可以对不同的窗口类进行类超类。

`CContainedWindowT` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CContainedWindowT` 对象并将窗口过程更改为 `CContainedWindowT::WindowProc`。 `CContainedWindowT` 的每个实例可以子类化其他窗口。

> [!NOTE]
> 对于任何给定`CContainedWindowT`对象，调用 任`Create`一`SubclassWindow`对象或 。 不应在同一对象上调用这两种方法。

当您使用基于 ATL 项目向导中选项**的添加控件**时，向导将自动向实现该控件`CContainedWindowT`的类添加数据成员。 下面的示例演示如何声明包含的窗口：

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|使用 ATL 中的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) SDK 中的 Windows 及其后续主题|

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>C包含窗口：：C包含窗口T

构造函数初始化数据成员。

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
[在]包含的窗口将基于的现有窗口类的名称。

*pObject*<br/>
[在]指向声明消息映射的包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]标识将处理包含的窗口的消息的消息映射。 默认值 0 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射。 要使用使用[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射`msgMapID`，请通过 。

### <a name="remarks"></a>备注

如果要通过[Create](#create)创建新窗口，则必须传递*lpszClassName*参数的现有窗口类的名称。 例如，请参阅[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概述。

有三个构造函数：

- 具有三个参数的构造函数是通常调用的构造函数。

- 具有两个参数的构造函数使用 中的`TBase::GetWndClassName`类名称。

- 如果以后要提供参数，将使用没有参数的构造函数。 以后调用`Create`时，必须提供窗口类名称、消息映射对象和消息映射 ID。

如果通过[子类窗口](#subclasswindow)对现有窗口进行子类类，则不会使用 lpszClassName 值;如果通过子类窗口对现有窗口进行子类分类，则不使用*lpszClassName*值。因此，您可以为此参数传递 NULL。

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>C包含窗口T：创建

调用[RegisterWndSuper 类](#registerwndsuperclass)注册基于现有类但使用[CContainedWindowT：：windowProc](#windowproc)的窗口类。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
[在]包含的窗口将基于的现有窗口类的名称。

*pObject*<br/>
[在]指向声明消息映射的包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]标识将处理包含的窗口的消息的消息映射。 默认值 0 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射。 要使用使用[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射`msgMapID`，请通过 。

*hWnd 父母*<br/>
[在]父窗口或所有者窗口的句柄。

*矩形*<br/>
[在]指定窗口位置的[RECT](/windows/win32/api/windef/ns-windef-rect)结构。 `RECT`可以通过指针或引用传递 。

*szWindow名称*<br/>
[在]指定窗口的名称。 默认值为 NULL。

*dwStyle*<br/>
[在]窗口的样式。 默认值为&#124;WS_VISIBLEWS_CHILD。 有关可能值的列表，请参阅在 Windows SDK 中[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*dwExStyle*<br/>
[在]扩展窗口样式。 默认值为 0，表示没有扩展样式。 有关可能值的列表，请参阅在 Windows SDK 中[创建 WindowsEx。](/windows/win32/api/winuser/nf-winuser-createwindowexw)

*菜单OrID*<br/>
[在]对于子窗口，窗口标识符。 对于顶级窗口，窗口的菜单句柄。 默认值为**0U**。

*lpCreateParam*<br/>
[在]指向窗口创建数据的指针。 有关完整说明，请参阅[创建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最终参数的说明。

### <a name="return-value"></a>返回值

如果成功，则对新创建的窗口的句柄;否则，NULL。

### <a name="remarks"></a>备注

现有窗口类名称保存在[m_lpszClassName](#m_lpszclassname)中。 `Create`然后基于此新类创建一个窗口。 新创建的窗口将自动附加到`CContainedWindowT`对象。

> [!NOTE]
> 如果您已经调用`Create`[了子类窗口](#subclasswindow)，请不要调用 。

> [!NOTE]
> 如果 0 用作*MenuOrID*参数的值，则必须将其指定为 0U（默认值），以避免编译器错误。

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>C包含窗口T：:DefWindowProc

由[WindowProc](#windowproc)调用以处理消息映射未处理的邮件。

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*乌姆斯格*<br/>
[在]发送到窗口的消息。

*wParam*<br/>
[在]其他特定于消息的信息。

*lParam*<br/>
[在]其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

默认情况下，`DefWindowProc`调用[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函数将消息信息发送到[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的窗口过程。

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>C包含窗口T：获取当前消息

返回当前消息 （`m_pCurrentMsg`。

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>返回值

当前消息，打包在结构中`MSG`。

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>C包含窗口：：m_dwMsgMapID

保存当前用于包含窗口的消息映射的标识符。

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>备注

必须在包含对象中声明此消息映射。

默认消息映射（使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明）始终以零标识。 使用[ALT_MSG_MAP （msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的替代消息映射由 标识`msgMapID`。

`m_dwMsgMapID`首先由构造函数初始化，可以通过调用[SwitchMessageMap](#switchmessagemap)进行更改。 例如，请参阅[CContainedWindowT 概述](../../atl/reference/ccontainedwindowt-class.md)。

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>C包含窗口：：m_lpszClassName

指定现有窗口类的名称。

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>备注

创建窗口时[，Create](#create)会注册基于此现有类但使用[CContainedWindowT：：windowProc](#windowproc)的新窗口类。

`m_lpszClassName`由构造函数初始化。 例如，请参阅[C包含窗口T](../../atl/reference/ccontainedwindowt-class.md)概述。

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>C包含窗口T：m_pfnSuperWindowProc

如果包含的窗口被子分类，`m_pfnSuperWindowProc`则指向窗口类的原始窗口过程。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>备注

如果包含的窗口是超类的，这意味着它基于修改现有类的窗口类，则`m_pfnSuperWindowProc`指向现有窗口类的窗口过程。

[DefWindowProc](#defwindowproc)方法将消息信息发送到保存在 中`m_pfnSuperWindowProc`的窗口过程。

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>C包含窗口T：m_pObject

指向包含`CContainedWindowT`对象的对象。

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>备注

此容器的类必须派生自[CMessageMap，](../../atl/reference/cmessagemap-class.md)声明包含的窗口使用的消息映射。

`m_pObject`由构造函数初始化。 例如，请参阅[C包含窗口T](../../atl/reference/ccontainedwindowt-class.md)概述。

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContained窗口：：注册Wnd超级类

通过["创建"](#create)调用以注册包含窗口的窗口类。

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>返回值

如果成功，则唯一标识要注册的窗口类的原子;否则，零。

### <a name="remarks"></a>备注

此窗口类基于现有类，但使用[CContainedWindowT：：windowProc](#windowproc)。 现有窗口类的名称和窗口过程分别保存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc。](#m_pfnsuperwindowproc)

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>C包含窗口T：：子类窗口

对*hWnd*标识的窗口进行子类，并将其附加到`CContainedWindowT`对象。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]正在子类窗口的句柄。

### <a name="return-value"></a>返回值

如果窗口已成功下类，则为 TRUE;如果窗口已成功下分类。否则，FALSE。

### <a name="remarks"></a>备注

子类窗口现在使用[CContainedWindowT：：windowProc](#windowproc)。 原始窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
> 如果已调用`SubclassWindow` [Create，](#create)请不要调用 。

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>C包含窗口T：：切换消息映射

更改将用于处理包含的窗口的消息的消息。

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>参数

*dwMsgMapID*<br/>
[在]消息映射标识符。 要使用用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射，则传递零。 要使用使用[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射`msgMapID`，请通过 。

### <a name="remarks"></a>备注

必须在包含对象中定义消息映射。

最初在构造函数中指定消息映射标识符。

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>包含窗口：：取消子类窗口

从`CContainedWindowT`对象分离子分类窗口，并还原保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)的原始窗口过程。

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>参数

*bForce*<br/>
[在]设置为 TRUE 以强制还原原始窗口过程，即使此`CContainedWindowT`对象的窗口过程当前未处于活动状态也是如此。 如果*bForce*设置为 FALSE，并且此`CContainedWindowT`对象的窗口过程当前未处于活动状态，则原始窗口过程将不会还原。

### <a name="return-value"></a>返回值

以前子类窗口的句柄。 如果*bForce*设置为 FALSE 并且此`CContainedWindowT`对象的窗口过程当前未处于活动状态，则返回 NULL。

### <a name="remarks"></a>备注

仅当要在销毁窗口之前还原原始窗口过程时，才使用此方法。 否则[，WindowProc](#windowproc)将在窗口被销毁时自动执行此操作。

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>C包含窗口T：：窗口Proc

此静态方法实现窗口过程。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]窗口的句柄。

*乌姆斯格*<br/>
[在]发送到窗口的消息。

*wParam*<br/>
[在]其他特定于消息的信息。

*lParam*<br/>
[在]其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

`WindowProc`将消息定向到[m_dwMsgMapID](#m_dwmsgmapid)标识的消息映射。 如有必要，`WindowProc`请调用[DefWindowProc](#defwindowproc)进行其他消息处理。

## <a name="see-also"></a>请参阅

[CWindow 类](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 类](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
