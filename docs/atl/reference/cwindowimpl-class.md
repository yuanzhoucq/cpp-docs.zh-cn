---
title: CWindowImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39a0938f6faadc05b2fdb3d716417a56512768b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084546"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 类

提供创建或子类化窗口的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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

*TWinTraits*<br/>
一个[特征类](../../atl/understanding-window-traits.md)，它定义为您的窗口样式。 默认值为 `CControlWinTraits`。

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
|[OnFinalMessage](#onfinalmessage)|接收到最后一条消息后调用 (通常 WM_NCDESTROY)。|
|[SubclassWindow](#subclasswindow)|对窗口子类化。|
|[UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|

### <a name="static-methods"></a>静态方法

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|返回的静态实例[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)，用于管理窗口类信息。|
|[WindowProc](#windowproc)|处理发送到窗口的消息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|

## <a name="remarks"></a>备注

可以使用`CWindowImpl`创建窗口或子类现有窗口。 `CWindowImpl`窗口过程使用消息映射来将消息定向到相应的处理程序。

`CWindowImpl::Create` 创建基于由管理的窗口类信息的窗口[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。 `CWindowImpl` 包含[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)宏，这意味着`CWndClassInfo`注册新的窗口类。 如果你想超类现有的窗口类，派生类从`CWindowImpl`，包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 在这种情况下，`CWndClassInfo` 将注册基于现有类的窗口类，但使用 `CWindowImpl::WindowProc`。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  由于 `CWndClassInfo` 只管理一个窗口类的信息，所以通过 `CWindowImpl` 实例创建的每个窗口都基于同一个窗口类。

`CWindowImpl` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CWindowImpl` 对象并将窗口过程更改为 `CWindowImpl::WindowProc`。 `CWindowImpl` 的每个实例可以子类化其他窗口。

> [!NOTE]
>  对于任何给定`CWindowImpl`对象，请调用`Create`或`SubclassWindow`。 不要对同一对象调用两种方法。

除了`CWindowImpl`，ATL 提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)在另一个对象中创建包含一个窗口。

基类析构函数 (~ `CWindowImplRoot`) 可确保窗口消失之前销毁对象。

`CWindowImpl` 派生自`CWindowImplBaseT`，又派生自`CWindowImplRoot`，它派生`TBase`并[CMessageMap](../../atl/reference/cmessagemap-class.md)。

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

**标头：** atlwin.h

##  <a name="create"></a>  CWindowImpl::Create

创建基于新的窗口类的窗口。

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
[in]父级或所有者窗口的句柄。

*rect*<br/>
[in]一个[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定窗口的位置。 `RECT`可以由指针或按引用传递。

*szWindowName*<br/>
[in]指定窗口的名称。 默认值为 NULL。

*dwStyle*<br/>
[in]窗口的样式。 此值被合并在一起对窗口特征类提供的样式。 默认值为特征提供了类样式的完全控制。 有关可能的值的列表，请参阅[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK 中。

*dwExStyle*<br/>
[in]扩展的窗口样式。 此值被合并在一起对窗口特征类提供的样式。 默认值为特征提供了类样式的完全控制。 有关可能的值的列表，请参阅[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*MenuOrID*<br/>
[in]对于子窗口，窗口标识符。 为顶层窗口，窗口的菜单句柄。 默认值是**0U**。

*lpCreateParam*<br/>
[in]指向窗口创建数据的指针。 有关完整说明，请参阅到最后一个参数的说明[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)。

### <a name="return-value"></a>返回值

如果成功，新创建的窗口的句柄。 否则，为 NULL。

### <a name="remarks"></a>备注

`Create` 如果尚未注册，第一次注册窗口类。 新创建的窗口会自动附加到`CWindowImpl`对象。

> [!NOTE]
>  不要调用`Create`如果你已调用[SubclassWindow](#subclasswindow)。

若要使用的窗口类，基于现有的窗口类，派生从类`CWindowImpl`，包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 在保存现有窗口类的窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

> [!NOTE]
>  如果使用 0 的值作为*MenuOrID*参数，则必须指定为 0U （默认值） 以避免编译器错误。

##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc

调用[WindowProc](#windowproc)未处理的消息映射处理消息。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>参数

*uMsg*<br/>
[in]发送到窗口的消息。

*wParam*<br/>
[in]其他特定于消息的信息。

*lParam*<br/>
[in]其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

默认情况下`DefWindowProc`调用[CallWindowProc](https://msdn.microsoft.com/library/windows/desktop/ms633571) Win32 函数来发送消息给中指定的窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

不带任何参数的函数会自动从当前消息中检索所需的参数。

##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage

返回当前消息，打包在`MSG`结构。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>返回值

当前消息。

##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc

返回`WindowProc`，当前窗口过程。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>返回值

当前的窗口过程。

### <a name="remarks"></a>备注

重写此方法以替换为您自己的窗口过程。

##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo

调用[创建](#create)访问窗口类信息。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>返回值

静态实例[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。

### <a name="remarks"></a>备注

默认情况下`CWindowImpl`获取此方法通过[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)宏，它指定新的窗口类。

为超类现有的窗口类，派生从类`CWindowImpl`，包括[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏重写`GetWndClassInfo`。 有关详细信息，请参阅[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

除了使用 {2&gt;declare_wnd_class&lt;2 和 DECLARE_WND_SUPERCLASS 宏，您可以重写`GetWndClassInfo`与您自己的实现。

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

具体取决于窗口中，指向以下窗口过程之一。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>备注

|类型的窗口|窗口过程|
|--------------------|----------------------|
|一个窗口，基于一个新的窗口类，通过指定[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)宏。|[DefWindowProc](/windows/desktop/api/winuser/nf-winuser-defwindowproca) Win32 函数。|
|修改现有类，通过指定的窗口类上基于窗口[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。|现有窗口类的窗口过程。|
|子类化的窗口。|子类化的窗口的原始窗口过程。|

[CWindowImpl::DefWindowProc](#defwindowproc)发送消息到窗口过程中保存信息`m_pfnSuperWindowProc`。

##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage

接收最后一条消息 (通常 WM_NCDESTROY) 之后调用。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]正在销毁窗口的句柄。

### <a name="remarks"></a>备注

默认实现`OnFinalMessage`不执行任何操作，但您可以覆盖此函数可销毁一个窗口之前处理清理。 如果你想要自动删除您在窗口析构时的对象，则可以调用**删除此;** 中此函数。

##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow

窗口由的子类*hWnd*并将其附加到`CWindowImpl`对象。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]正在创建子类的窗口句柄。

### <a name="return-value"></a>返回值

如果对窗口成功子类化; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

子类化的窗口现在使用[CWindowImpl::WindowProc](#windowproc)。 在保存原始窗口过程[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

> [!NOTE]
>  不要调用`SubclassWindow`如果你已调用[创建](#create)。

##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow

从子类化的窗口中分离`CWindowImpl`对象，并还原原始窗口过程，在保存[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>返回值

先前子类化窗口的句柄。

##  <a name="windowproc"></a>  CWindowImpl::WindowProc

此静态函数实现的窗口过程。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]窗口的句柄。

*uMsg*<br/>
[in]发送到窗口的消息。

*wParam*<br/>
[in]其他特定于消息的信息。

*lParam*<br/>
[in]其他特定于消息的信息。

### <a name="return-value"></a>返回值

消息处理的结果。

### <a name="remarks"></a>备注

`WindowProc` 使用默认消息映射 (使用声明[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) 若要将消息定向到相应的处理程序。 如果有必要，请`WindowProc`调用[DefWindowProc](#defwindowproc)进行更多的消息处理。 如果未处理最后一条消息，`WindowProc`执行以下操作：

- 执行 unsubclassing unsubclassed 窗口时。

- 清除`m_hWnd`。

- 调用[OnFinalMessage](#onfinalmessage)窗口被破坏之前。

您可以重写`WindowProc`提供不同的机制，用于处理消息。

## <a name="see-also"></a>请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
