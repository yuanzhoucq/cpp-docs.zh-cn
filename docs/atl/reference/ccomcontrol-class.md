---
title: CComControl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs:
- C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb2d345e0bb8be8f5150d48237df9845acf451dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036160"
---
# <a name="ccomcontrol-class"></a>CComControl 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
实现开窗函数的基本类。 默认情况下[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CComControl::CreateControlWindow](#createcontrolwindow)|创建控件的窗口。|
|[CComControl::FireOnChanged](#fireonchanged)|通知控件属性已更改的容器的接收器。|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|控件属性即将更改并继续操作，该对象要求接收器通知容器的接收器。|
|[CComControl::MessageBox](#messagebox)|调用此方法来创建、 显示和操作的消息框。|

## <a name="remarks"></a>备注

`CComControl` 是一组非常有用的控件帮助器函数和 ATL 控件的基本数据成员。 标准控件或 DHTML 控件使用 ATL 控件向导创建时，向导将自动派生您的类从`CComControl`。 `CComControl` 派生从其方法中的大多数[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)。

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。

有关的演示`CComControl`方法和数据成员，请参阅[CIRC](../../visual-cpp-samples.md)示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

构造函数。

```
CComControl();
```

### <a name="remarks"></a>备注

调用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)构造函数，并传递`m_hWnd`数据成员通过继承[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的 GUID。

*ppv*<br/>
[out]通过标识的接口指针的指针*iid*，或如果找不到该接口，则为 NULL。

### <a name="remarks"></a>备注

仅处理 COM 映射表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

默认情况下，通过调用创建一个窗口，以控制`CWindowImpl::Create`。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
[in]父级或所有者窗口句柄。 必须提供有效的窗口句柄。 控制窗口范围限制为其父窗口的区域。

*rcPos*<br/>
[in]初始大小和要创建窗口的位置。

### <a name="remarks"></a>备注

如果你想要执行一些操作，重写此方法不是创建一个窗口，例如，若要创建两个窗口，其中一个将成为您的控件的工具栏。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

通知控件属性已更改的容器的接收器。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>参数

*dispID*<br/>
[in]已更改的属性的标识符。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果你的控件类派生自[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)，此方法调用[CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)通知所有连接`IPropertyNotifySink`接口指定的控件属性已更改。 如果你的控件类不是派生自`IPropertyNotifySink`，此方法返回 S_OK。

此方法可以安全地调用即使控件不支持连接点。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

控件属性即将更改并继续操作，该对象要求接收器通知容器的接收器。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>参数

*dispID*<br/>
[in]要更改的属性的标识符。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果你的控件类派生自[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)，此方法调用[CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)通知所有连接`IPropertyNotifySink`接口指定控件属性是将要更改。 如果你的控件类不是派生自`IPropertyNotifySink`，此方法返回 S_OK。

此方法可以安全地调用即使控件不支持连接点。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

调用此方法来创建、 显示和操作的消息框。

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
对话框的标题。 如果为 NULL （默认值），使用"错误"的标题。

*n 类型*<br/>
指定的内容和对话框中的行为。 请参阅[MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox)可用的不同的消息框的列表的 Windows SDK 文档中的条目。 默认值提供了一个简单**确定**按钮。

### <a name="return-value"></a>返回值

返回一个整数值，指定下列出的菜单项值之一[MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) Windows SDK 文档中。

### <a name="remarks"></a>备注

`MessageBox` 在开发期间以及作为方便地向用户显示的错误或警告消息，则很有用。

## <a name="see-also"></a>请参阅

[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComControlBase 类](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl 类](../../atl/reference/ccomcompositecontrol-class.md)
