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
ms.openlocfilehash: 2eae6e149cf6f7422d0653c1c15f46985d8d55c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496846"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 类

此类实现包含在另一个对象中的窗口。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>参数

*TBase*<br/>
新类的基类。 默认基类为`CWindow`。

*TWinTraits*<br/>
定义窗口样式的特征类。 默认值为 `CControlWinTraits`。

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是的`CContainedWindowT`专用化。 如果要更改基类或特征, 请直接使用`CContainedWindowT` 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|构造函数。 初始化数据成员, 以指定将处理所包含窗口消息的消息映射。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|创建一个窗口。|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供默认消息处理。|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|返回当前消息。|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|注册所包含窗口的窗口类。|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|对窗口子类化。|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|更改用于处理所包含窗口消息的消息映射。|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|还原先前子类化的窗口。|
|[CContainedWindowT::WindowProc](#windowproc)|静止处理发送到所包含窗口的消息。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|标识哪些消息映射将处理所包含窗口的消息。|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新窗口类将基于的现有窗口类的名称。|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向窗口类的原始窗口过程。|
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含对象。|

## <a name="remarks"></a>备注

`CContainedWindowT`实现一个包含在另一个对象中的窗口。 `CContainedWindowT`的窗口过程在包含对象中使用消息映射将消息定向到适当的处理程序。 构造`CContainedWindowT`对象时, 可以指定应使用的消息映射。

`CContainedWindowT`允许通过 superclassing 现有窗口类来创建新窗口。 方法首先注册一个基于现有类但使用`CContainedWindowT::WindowProc`的窗口类。 `Create` `Create`然后, 基于此新窗口类创建窗口。 的`CContainedWindowT`每个实例都可以是不同的窗口类的超类。

`CContainedWindowT` 还支持窗口子类化。 `SubclassWindow` 方法将现有的窗口附加到 `CContainedWindowT` 对象并将窗口过程更改为 `CContainedWindowT::WindowProc`。 `CContainedWindowT` 的每个实例可以子类化其他窗口。

> [!NOTE]
>  对于任何给定`CContainedWindowT`的对象, 请`Create`调用`SubclassWindow`或。 不应对同一对象调用这两种方法。

当使用 ATL 项目向导中的 "**基于此添加控件**" 选项时, 向导会自动将`CContainedWindowT`数据成员添加到实现控件的类。 下面的示例演示如何声明包含的窗口:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|有关以下内容的详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|使用 ATL 中的窗口|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|
|Windows|Windows SDK 中的[Windows](/windows/win32/winmsg/windows)和后续主题|

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>要求

**标头:** atlwin。h

##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

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

*lpszClassName*<br/>
中包含的窗口将基于的现有窗口类的名称。

*pObject*<br/>
中指向声明消息映射的包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
中标识将处理所包含窗口的消息的消息映射。 默认值为 0, 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射。 若要使用通过[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射, `msgMapID`请传递。

### <a name="remarks"></a>备注

如果希望通过 "[创建](#create)" 来创建新窗口, 则必须为*lpszClassName*参数传递现有窗口类的名称。 有关示例, 请参阅[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概述。

有三个构造函数:

- 带有三个参数的构造函数是通常调用的构造函数。

- 具有两个参数的构造函数使用中`TBase::GetWndClassName`的类名称。

- 如果要在以后提供参数, 则使用不带参数的构造函数。 以后调用`Create`时, 必须提供窗口类名称、消息映射对象和消息映射 ID。

如果通过[SubclassWindow](#subclasswindow)为现有窗口划分子类, 则不会使用*lpszClassName*值;因此, 可以为此参数传递 NULL。

##  <a name="create"></a>CContainedWindowT:: Create

调用[RegisterWndSuperclass](#registerwndsuperclass)来注册基于现有类但使用[CContainedWindowT:: WindowProc](#windowproc)的窗口类。

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

*lpszClassName*<br/>
中包含的窗口将基于的现有窗口类的名称。

*pObject*<br/>
中指向声明消息映射的包含对象的指针。 此对象的类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
中标识将处理所包含窗口的消息的消息映射。 默认值为 0, 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射。 若要使用通过[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射, `msgMapID`请传递。

*hWndParent*<br/>
中父窗口或所有者窗口的句柄。

*rect*<br/>
中指定窗口位置的[矩形](/previous-versions/dd162897\(v=vs.85\))结构。 `RECT`可以通过指针或引用传递。

*szWindowName*<br/>
中指定窗口的名称。 默认值为 NULL。

*dwStyle*<br/>
中窗口的样式。 默认值为 WS_CHILD &#124; WS_VISIBLE。 有关可能值的列表, 请参阅 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*dwExStyle*<br/>
中扩展的窗口样式。 默认值为 0, 表示没有扩展样式。 有关可能值的列表, 请参阅 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 。

*MenuOrID*<br/>
中对于子窗口, 则为窗口标识符。 对于顶级窗口, 为窗口的菜单控点。 默认值为**0u**。

*lpCreateParam*<br/>
中指向窗口创建数据的指针。 有关完整说明, 请参阅[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最终参数说明。

### <a name="return-value"></a>返回值

如果成功, 则为新创建的窗口的句柄;否则为 NULL。

### <a name="remarks"></a>备注

现有的窗口类名称保存在[m_lpszClassName](#m_lpszclassname)中。 `Create`然后, 基于此新类创建窗口。 新创建的窗口将自动附加到`CContainedWindowT`对象。

> [!NOTE]
>  如果已调用`Create` [SubclassWindow](#subclasswindow), 请不要调用。

> [!NOTE]
>  如果将0用作*MenuOrID*参数的值, 则必须将其指定为 0u (默认值), 以避免出现编译器错误。

##  <a name="defwindowproc"></a>CContainedWindowT::D efWindowProc

由[WindowProc](#windowproc)调用, 用于处理不是由消息映射处理的消息。

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

返回当前消息 (`m_pCurrentMsg`)。

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>返回值

在`MSG`结构中打包的当前消息。

##  <a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

保存当前用于所包含窗口的消息映射的标识符。

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>备注

此消息映射必须在包含对象中声明。

使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射始终由零标识。 用[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射由`msgMapID`标识。

`m_dwMsgMapID`首先由构造函数初始化, 可以通过调用[SwitchMessageMap](#switchmessagemap)来更改。 有关示例, 请参阅[CContainedWindowT 概述](../../atl/reference/ccontainedwindowt-class.md)。

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

指定现有窗口类的名称。

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>备注

创建窗口时, [create](#create)将注册基于此现有类的新窗口类, 但使用[CContainedWindowT:: WindowProc](#windowproc)。

`m_lpszClassName`是由构造函数初始化的。 有关示例, 请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

如果包含的窗口为子类, `m_pfnSuperWindowProc`则指向窗口类的原始窗口过程。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>备注

如果包含的窗口是超类的, 这意味着它基于修改现有类的窗口类, `m_pfnSuperWindowProc`指向现有窗口类的窗口过程。

[DefWindowProc](#defwindowproc)方法将消息信息发送到保存在中`m_pfnSuperWindowProc`的窗口过程。

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

指向包含`CContainedWindowT`对象的对象。

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>备注

此容器 (其类必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)) 声明包含的窗口使用的消息映射。

`m_pObject`是由构造函数初始化的。 有关示例, 请参阅[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概述。

##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

由[Create](#create)调用, 用于注册所包含窗口的窗口类。

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>返回值

如果成功, 则为唯一标识要注册的窗口类的 atom;否则为零。

### <a name="remarks"></a>备注

此窗口类基于现有类, 但使用[CContainedWindowT:: WindowProc](#windowproc)。 现有窗口类的名称和窗口过程分别保存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

##  <a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

子类由*hWnd*标识并将其附加到`CContainedWindowT`对象。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中要进行子类处理的窗口的句柄。

### <a name="return-value"></a>返回值

如果窗口成功进行了子类化, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

子类窗口现在使用[CContainedWindowT:: WindowProc](#windowproc)。 原始窗口过程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
>  如果已调用`SubclassWindow` [Create](#create), 请不要调用。

##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

更改将用于处理所包含窗口消息的消息映射。

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>参数

*dwMsgMapID*<br/>
中消息映射标识符。 若要使用通过[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射, 请传递零。 若要使用通过[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射, `msgMapID`请传递。

### <a name="remarks"></a>备注

消息映射必须在包含对象中进行定义。

最初在构造函数中指定消息映射标识符。

##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

从`CContainedWindowT`对象分离子类窗口, 并还原原始窗口过程, 保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>参数

*bForce*<br/>
中如果设置为 TRUE, 则强制还原原始窗口过程, 即使此`CContainedWindowT`对象的窗口过程当前不处于活动状态也是如此。 如果*bForce*设置为 FALSE, 并且此`CContainedWindowT`对象的窗口过程当前不处于活动状态, 则不会还原原始窗口过程。

### <a name="return-value"></a>返回值

之前子类的窗口的句柄。 如果*bForce*设置为 FALSE, 并且此`CContainedWindowT`对象的窗口过程当前不处于活动状态, 则返回 NULL。

### <a name="remarks"></a>备注

仅当要在销毁窗口之前还原原始窗口过程时, 才使用此方法。 否则, 当窗口被销毁时, [WindowProc](#windowproc)将自动执行此操作。

##  <a name="windowproc"></a>CContainedWindowT:: WindowProc

此静态方法实现窗口过程。

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

`WindowProc`将消息定向到由[m_dwMsgMapID](#m_dwmsgmapid)标识的消息映射。 如有必要`WindowProc` , 调用[DefWindowProc](#defwindowproc)进行其他消息处理。

## <a name="see-also"></a>请参阅

[CWindow 类](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 类](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
