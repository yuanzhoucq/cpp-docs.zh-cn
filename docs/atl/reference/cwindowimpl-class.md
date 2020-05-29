---
title: CWindowImpl 类
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: ea150195f06d12cd6549b9026714d9e1bbf392df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745997"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 类

提供创建或子类化窗口的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的新类，派生自 `CWindowImpl`。

*TBase*<br/>
您的类的基类。 默认情况下，基类是[CWindow](../../atl/reference/cwindow-class.md)。

*特温·特威茨*<br/>
定义窗口样式的[特征类](../../atl/understanding-window-traits.md)。 默认为 `CControlWinTraits`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWindowImpl：：创建](#create)|创建一个窗口。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法

|||
|-|-|
|[DefWindowProc](#defwindowproc)|提供默认消息处理。|
|[GetCurrentMessage](#getcurrentmessage)|返回当前消息。|
|[GetWindowProc](#getwindowproc)|返回当前窗口过程。|
|[OnFinalMessage](#onfinalmessage)|收到最后一条消息后调用（通常WM_NCDESTROY）。|
|[SubclassWindow](#subclasswindow)|对窗口子类化。|
|[UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|

### <a name="static-methods"></a>静态方法

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|返回[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的静态实例，该实例管理窗口类信息。|
|[WindowProc](#windowproc)|处理发送到窗口的消息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|

## <a name="remarks"></a>备注

可以使用`CWindowImpl`创建现有窗口的窗口或子类。 `CWindowImpl`窗口过程使用消息映射将消息定向到相应的处理程序。

`CWindowImpl::Create`基于[由 CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)管理的窗口类信息创建一个窗口。 `CWindowImpl`包含[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏，这意味着`CWndClassInfo`注册一个新的窗口类。 如果要超类现有窗口类，请从`CWindowImpl`DECLARE_WND_SUPERCLASS宏派生类并包含该[宏](window-class-macros.md#declare_wnd_superclass)。 在这种情况下，`CWndClassInfo` 将注册基于现有类的窗口类，但使用 `CWindowImpl::WindowProc`。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> 由于 `CWndClassInfo` 只管理一个窗口类的信息，所以通过 `CWindowImpl` 实例创建的每个窗口都基于同一个窗口类。

`CWindowImpl` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CWindowImpl` 对象并将窗口过程更改为 `CWindowImpl::WindowProc`。 `CWindowImpl` 的每个实例可以子类化其他窗口。

> [!NOTE]
> 对于任何给定`CWindowImpl`对象，调用 任`Create`一`SubclassWindow`对象或 。 不要对同一对象调用两种方法。

除 之外`CWindowImpl`，ATL 还提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)来创建包含在另一个对象中的窗口。

基类析构函数 （* `CWindowImplRoot`） 可确保窗口在对象销毁之前消失。

`CWindowImpl`派生自`CWindowImplBaseT`派生自`CWindowImplRoot``TBase`[和](../../atl/reference/cmessagemap-class.md)的 。

|详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|使用 ATL 中的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl：：创建

基于新窗口类创建窗口。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
[在]父窗口或所有者窗口的句柄。

*矩形*<br/>
[在]指定窗口位置的[RECT](/windows/win32/api/windef/ns-windef-rect)结构。 `RECT`可以通过指针或引用传递 。

*szWindow名称*<br/>
[在]指定窗口的名称。 默认值为 NULL。

*dwStyle*<br/>
[在]窗口的样式。 此值与窗口的特征类提供的样式结合使用。 默认值使特征类对样式完全控制。 有关可能值的列表，请参阅在 Windows SDK 中[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*dwExStyle*<br/>
[在]扩展窗口样式。 此值与窗口的特征类提供的样式结合使用。 默认值使特征类对样式完全控制。 有关可能值的列表，请参阅在 Windows SDK 中[创建 WindowsEx。](/windows/win32/api/winuser/nf-winuser-createwindowexw)

*菜单OrID*<br/>
[在]对于子窗口，窗口标识符。 对于顶级窗口，窗口的菜单句柄。 默认值为**0U**。

*lpCreateParam*<br/>
[在]指向窗口创建数据的指针。 有关完整说明，请参阅[创建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最终参数的说明。

### <a name="return-value"></a>返回值

如果成功，则对新创建的窗口的句柄。 否则，NULL。

### <a name="remarks"></a>备注

`Create`如果窗口类尚未注册，则首先注册该窗口类。 新创建的窗口将自动附加到`CWindowImpl`对象。

> [!NOTE]
> 如果您已经调用`Create`[了子类窗口](#subclasswindow)，请不要调用 。

要使用基于现有窗口类的窗口类，请从`CWindowImpl`DECLARE_WND_SUPERCLASS宏派生类并包含该[宏](window-class-macros.md#declare_wnd_superclass)。 现有窗口类的窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

> [!NOTE]
> 如果 0 用作*MenuOrID*参数的值，则必须将其指定为 0U（默认值），以避免编译器错误。

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl：:DefWindowProc

由[WindowProc](#windowproc)调用以处理消息映射未处理的邮件。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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

没有参数的函数会自动从当前消息中检索所需的参数。

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowimpl：：获取当前消息

返回当前消息，该消息打包在`MSG`结构中。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>返回值

当前消息。

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl：：获取窗口Proc

返回`WindowProc`，当前窗口过程。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>返回值

当前窗口过程。

### <a name="remarks"></a>备注

重写此方法以将窗口过程替换为您自己的窗口过程。

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl：：获取WndClassinfo

由[Create](#create)调用以访问窗口类信息。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>返回值

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的静态实例。

### <a name="remarks"></a>备注

默认情况下，`CWindowImpl`通过[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏获取此方法，该宏指定了一个新的窗口类。

要超类现有窗口类，请从`CWindowImpl`派生类，并包括[要](window-class-macros.md#declare_wnd_superclass)重写`GetWndClassInfo`的DECLARE_WND_SUPERCLASS宏。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

除了使用DECLARE_WND_CLASS和DECLARE_WND_SUPERCLASS宏外，您还可以使用自己的实现进行`GetWndClassInfo`重写。

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl：：m_pfnSuperWindowProc

根据窗口的不同，指向以下窗口过程之一。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>备注

|窗口类型|窗口过程|
|--------------------|----------------------|
|基于新窗口类的窗口，通过[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏指定。|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 功能。|
|基于修改现有类的窗口类的窗口，该窗口通过[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏指定。|现有窗口类的窗口过程。|
|子类窗口。|子类窗口的原始窗口过程。|

[CWindowImpl：:DefWindowProc](#defwindowproc)将消息信息发送到保存在 中`m_pfnSuperWindowProc`的窗口过程。

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowimpl：：打开最终消息

收到最后一条消息后调用（通常WM_NCDESTROY）。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]正在销毁的窗口的句柄。

### <a name="remarks"></a>备注

的`OnFinalMessage`默认实现不执行任何操作，但您可以重写此函数，以在销毁窗口之前处理清理。 如果要在窗口破坏时自动删除对象，可以调用 **"删除此";** 在此函数中。

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl：：子类窗口

对*hWnd*标识的窗口进行子类，并将其附加到`CWindowImpl`对象。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]正在子类窗口的句柄。

### <a name="return-value"></a>返回值

如果窗口已成功下类，则为 TRUE;如果窗口已成功下分类。否则，FALSE。

### <a name="remarks"></a>备注

子类窗口现在使用[CWindowImpl：：windowProc](#windowproc)。 原始窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
> 如果已调用`SubclassWindow` [Create，](#create)请不要调用 。

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl：：取消子类窗口

从`CWindowImpl`对象分离子分类窗口，并还原保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)的原始窗口过程。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>返回值

以前子类窗口的句柄。

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>窗口Impl：：窗口Proc

此静态函数实现窗口过程。

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

`WindowProc`使用默认消息映射（使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)） 将消息定向到相应的处理程序。 如有必要，`WindowProc`请调用[DefWindowProc](#defwindowproc)进行其他消息处理。 如果未处理最后一条消息，`WindowProc`则执行以下操作：

- 如果窗口未下类，则执行取消子类。

- 清除 `m_hWnd`。

- 在窗口销毁之前调用["最终消息](#onfinalmessage)"。

您可以重写`WindowProc`以提供用于处理消息的不同机制。

## <a name="see-also"></a>请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
