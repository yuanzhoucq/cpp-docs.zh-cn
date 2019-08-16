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
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496189"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 类

提供创建或子类化窗口的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的新类，派生自 `CWindowImpl`。

*TBase*<br/>
您的类的基类。 默认情况下, 基类为[CWindow](../../atl/reference/cwindow-class.md)。

*TWinTraits*<br/>
定义窗口样式的[特征类](../../atl/understanding-window-traits.md)。 默认值为 `CControlWinTraits`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CWindowImpl::Create](#create)|创建一个窗口。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法

|||
|-|-|
|[DefWindowProc](#defwindowproc)|提供默认消息处理。|
|[GetCurrentMessage](#getcurrentmessage)|返回当前消息。|
|[GetWindowProc](#getwindowproc)|返回当前窗口过程。|
|[OnFinalMessage](#onfinalmessage)|在收到最后一条消息后调用 (通常为 WM_NCDESTROY)。|
|[SubclassWindow](#subclasswindow)|对窗口子类化。|
|[UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|

### <a name="static-methods"></a>静态方法

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|返回[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的静态实例, 该实例管理窗口类信息。|
|[WindowProc](#windowproc)|处理发送到窗口的消息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|

## <a name="remarks"></a>备注

您可以使用`CWindowImpl`创建现有窗口的窗口或子类。 `CWindowImpl`窗口过程使用消息映射将消息定向到适当的处理程序。

`CWindowImpl::Create`基于由[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)管理的窗口类信息创建窗口。 `CWindowImpl`包含[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏, 这意味着`CWndClassInfo`将注册新窗口类。 如果要将现有窗口类作为超类, 请从`CWindowImpl`派生类, 并包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 在这种情况下，`CWndClassInfo` 将注册基于现有类的窗口类，但使用 `CWindowImpl::WindowProc`。 例如:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  由于 `CWndClassInfo` 只管理一个窗口类的信息，所以通过 `CWindowImpl` 实例创建的每个窗口都基于同一个窗口类。

`CWindowImpl` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CWindowImpl` 对象并将窗口过程更改为 `CWindowImpl::WindowProc`。 `CWindowImpl` 的每个实例可以子类化其他窗口。

> [!NOTE]
>  对于任何给定`CWindowImpl`的对象, 请`Create`调用`SubclassWindow`或。 不要对同一对象调用两种方法。

除了之外`CWindowImpl`, ATL 还提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)以创建一个包含在另一个对象中的窗口。

基类析构函数 (~ `CWindowImplRoot`) 确保在销毁对象之前窗口已消失。

`CWindowImpl`派生自`CWindowImplRoot`, 它`TBase`派生自和[CMessageMap。](../../atl/reference/cmessagemap-class.md) `CWindowImplBaseT`

|有关以下内容的详细信息|查看|
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

**标头:** atlwin。h

##  <a name="create"></a>CWindowImpl:: Create

基于新的窗口类创建窗口。

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

*hWndParent*<br/>
中父窗口或所有者窗口的句柄。

*rect*<br/>
中指定窗口位置的[矩形](/previous-versions/dd162897\(v=vs.85\))结构。 `RECT`可以通过指针或引用传递。

*szWindowName*<br/>
中指定窗口的名称。 默认值为 NULL。

*dwStyle*<br/>
中窗口的样式。 此值与窗口的特性类提供的样式组合在一起。 默认值为特征类提供完全控制样式。 有关可能值的列表, 请参阅 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*dwExStyle*<br/>
中扩展的窗口样式。 此值与窗口的特性类提供的样式组合在一起。 默认值为特征类提供完全控制样式。 有关可能值的列表, 请参阅 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 。

*MenuOrID*<br/>
中对于子窗口, 则为窗口标识符。 对于顶级窗口, 为窗口的菜单控点。 默认值为**0u**。

*lpCreateParam*<br/>
中指向窗口创建数据的指针。 有关完整说明, 请参阅[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最终参数说明。

### <a name="return-value"></a>返回值

如果成功, 则为新创建的窗口的句柄。 否则为 NULL。

### <a name="remarks"></a>备注

`Create`如果窗口类尚未注册, 则首先注册它。 新创建的窗口将自动附加到`CWindowImpl`对象。

> [!NOTE]
>  如果已调用`Create` [SubclassWindow](#subclasswindow), 请不要调用。

若要使用基于现有窗口类的窗口类, 请从`CWindowImpl`派生类, 并包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 现有窗口类的窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。 有关详细信息, 请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

> [!NOTE]
>  如果将0用作*MenuOrID*参数的值, 则必须将其指定为 0u (默认值), 以避免出现编译器错误。

##  <a name="defwindowproc"></a>CWindowImpl::D efWindowProc

由[WindowProc](#windowproc)调用, 用于处理不是由消息映射处理的消息。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>参数

*uMsg*<br/>
中发送到窗口的消息。

*wParam*<br/>
中其他特定于消息的信息。

*lParam*<br/>
中其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

默认情况下`DefWindowProc` , 调用[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函数将消息信息发送到[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的窗口过程。

不带参数的函数会自动从当前消息中检索所需的参数。

##  <a name="getcurrentmessage"></a>CWindowImpl:: GetCurrentMessage

返回在`MSG`结构中打包的当前消息。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>返回值

当前消息。

##  <a name="getwindowproc"></a>CWindowImpl:: GetWindowProc

返回`WindowProc`当前窗口过程。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>返回值

当前窗口过程。

### <a name="remarks"></a>备注

重写此方法以将窗口过程替换为您自己的。

##  <a name="getwndclassinfo"></a>CWindowImpl:: GetWndClassInfo

由[Create](#create)调用以访问窗口类信息。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>返回值

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的静态实例。

### <a name="remarks"></a>备注

默认情况下`CWindowImpl` , 通过[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏获取此方法, 该宏指定一个新的窗口类。

若要将现有窗口类作为超类, 请从`CWindowImpl`派生类, 并包含要重`GetWndClassInfo`写的[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 有关详细信息, 请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

除了使用 DECLARE_WND_CLASS 和 DECLARE_WND_SUPERCLASS 宏以外, 还可以使用`GetWndClassInfo`自己的实现来替代。

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

根据窗口的不同, 指向以下窗口过程之一。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>备注

|窗口类型|窗口过程|
|--------------------|----------------------|
|基于通过[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏指定的新窗口类的窗口。|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 函数。|
|基于窗口类的窗口, 用于修改通过[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏指定的现有类。|现有窗口类的窗口过程。|
|子类窗口。|子类窗口的原始窗口过程。|

[CWindowImpl::D efwindowproc](#defwindowproc)将消息信息发送到保存在中`m_pfnSuperWindowProc`的窗口过程。

##  <a name="onfinalmessage"></a>CWindowImpl:: OnFinalMessage

在收到最后一条消息后调用 (通常为 WM_NCDESTROY)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中要销毁的窗口的句柄。

### <a name="remarks"></a>备注

的`OnFinalMessage`默认实现不执行任何操作, 但你可以重写此函数以在销毁窗口之前处理清理。 如果要在销毁窗口后自动删除对象, 则可以在此函数中调用**delete this** 。

##  <a name="subclasswindow"></a>CWindowImpl:: SubclassWindow

子类由*hWnd*标识并将其附加到`CWindowImpl`对象。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中要进行子类处理的窗口的句柄。

### <a name="return-value"></a>返回值

如果窗口成功进行了子类化, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

子类窗口现在使用[CWindowImpl:: WindowProc](#windowproc)。 原始窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
>  如果已调用`SubclassWindow` [Create](#create), 请不要调用。

##  <a name="unsubclasswindow"></a>CWindowImpl:: UnsubclassWindow

从`CWindowImpl`对象分离子类窗口, 并还原原始窗口过程, 保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>返回值

之前子类的窗口的句柄。

##  <a name="windowproc"></a>CWindowImpl:: WindowProc

此静态函数实现窗口过程。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中窗口的句柄。

*uMsg*<br/>
中发送到窗口的消息。

*wParam*<br/>
中其他特定于消息的信息。

*lParam*<br/>
中其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

`WindowProc`使用默认消息映射 (用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明) 将消息定向到适当的处理程序。 如有必要`WindowProc` , 调用[DefWindowProc](#defwindowproc)进行其他消息处理。 如果未处理最后一条消息, `WindowProc`将执行以下操作:

- 如果窗口为 unsubclassed, 则执行 unsubclassing。

- 清除`m_hWnd`。

- 在销毁窗口之前调用[OnFinalMessage](#onfinalmessage) 。

可以重写`WindowProc`以提供不同的消息处理机制。

## <a name="see-also"></a>请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
