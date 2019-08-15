---
title: CComControl 类
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497522"
---
# <a name="ccomcontrol-class"></a>CComControl 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>参数

*T*<br/>
实现控件的类。

*WinBase*<br/>
实现窗口函数的基类。 默认值为[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CComControl::CreateControlWindow](#createcontrolwindow)|为控件创建窗口。|
|[CComControl::FireOnChanged](#fireonchanged)|通知容器接收器控件属性已更改。|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|通知容器的接收器, 控件属性即将发生更改, 并且对象正在请求接收器如何继续。|
|[CComControl::MessageBox](#messagebox)|调用此方法以创建、显示和操作消息框。|

## <a name="remarks"></a>备注

`CComControl`是适用于 ATL 控件的一组有用的控件 helper 函数和必要的数据成员。 使用 ATL 控件向导创建标准控件或 DHTML 控件时, 向导将自动从`CComControl`派生您的类。 `CComControl`从[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)派生其大部分方法。

有关创建控件的详细信息, 请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息, 请参阅文章[创建 Atl 项目](../../atl/reference/creating-an-atl-project.md)。

有关方法和数据`CComControl`成员的演示, 请参阅[CIRC](../../overview/visual-cpp-samples.md)示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="ccomcontrol"></a>CComControl::CComControl

构造函数。

```
CComControl();
```

### <a name="remarks"></a>备注

调用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)构造函数, 传递通过`m_hWnd` [CWindowImpl](../../atl/reference/cwindowimpl-class.md)继承的数据成员。

##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>参数

*iid*<br/>
中所请求的接口的 GUID。

*ppv*<br/>
弄指向由*iid*标识的接口指针的指针; 如果找不到接口, 则为 NULL。

### <a name="remarks"></a>备注

仅处理 COM 映射表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow

默认情况下, 通过调用`CWindowImpl::Create`为控件创建窗口。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
中父窗口或所有者窗口的句柄。 必须提供有效的窗口句柄。 控制窗口限制为其父窗口的区域。

*rcPos*<br/>
中要创建的窗口的初始大小和位置。

### <a name="remarks"></a>备注

如果你想要执行除创建单个窗口之外的其他操作 (例如, 创建两个窗口, 其中一个窗口将成为控件的工具栏), 请重写此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>CComControl::FireOnChanged

通知容器接收器控件属性已更改。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>参数

*dispID*<br/>
中已更改的属性的标识符。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

如果控件类派生自[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), 则此方法将调用[CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)以通知所有`IPropertyNotifySink`连接的接口指定的控件属性已更改。 如果控件类不是从派生的`IPropertyNotifySink`, 则此方法返回 S_OK。

即使您的控件不支持连接点, 也可以安全地调用此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

通知容器的接收器, 控件属性即将发生更改, 并且对象正在请求接收器如何继续。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>参数

*dispID*<br/>
中要更改的属性的标识符。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

如果控件类派生自[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), 则此方法将调用[CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)以通知所有`IPropertyNotifySink`连接的接口, 指定的控件属性即将发生更改。 如果控件类不是从派生的`IPropertyNotifySink`, 则此方法返回 S_OK。

即使您的控件不支持连接点, 也可以安全地调用此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>CComControl:: MessageBox

调用此方法以创建、显示和操作消息框。

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
要在消息框中显示的文本。

*lpszCaption*<br/>
对话框标题。 如果为 NULL (默认值), 则使用标题 "错误"。

*nType*<br/>
指定对话框的内容和行为。 有关可用的不同消息框的列表, 请参阅 Windows SDK 文档中的[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)条目。 默认值提供简单的 **"确定"** 按钮。

### <a name="return-value"></a>返回值

返回一个整数值, 该值指定 Windows SDK 文档中的 " [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) " 下列出的菜单项值之一。

### <a name="remarks"></a>备注

`MessageBox`在开发过程中十分有用, 并可以轻松地向用户显示错误或警告消息。

## <a name="see-also"></a>请参阅

[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComControlBase 类](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl 类](../../atl/reference/ccomcompositecontrol-class.md)
