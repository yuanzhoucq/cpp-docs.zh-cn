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
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320768"
---
# <a name="ccomcontrol-class"></a>CComControl 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>参数

*T*<br/>
实现控件的类。

*温基*<br/>
实现窗口函数的基类。 默认值为[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom控制：CCom控制](#ccomcontrol)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom控制：：控制查询接口](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CCom 控制：：创建控制窗口](#createcontrolwindow)|为控件创建一个窗口。|
|[CComControl：火通](#fireonchanged)|通知容器的接收器控件属性已更改。|
|[CComControl：：火对请求编辑](#fireonrequestedit)|通知容器的接收器控件属性即将更改，并且对象正在询问接收器如何继续。|
|[CComControl：消息框](#messagebox)|调用此方法以创建、显示和操作消息框。|

## <a name="remarks"></a>备注

`CComControl`是一组有用的控制帮助器功能和 ATL 控件的基本数据成员。 使用 ATL 控件向导创建标准控件或 DHTML 控件时，向导将自动从`CComControl`派生类。 `CComControl`它的大部分方法来自[CComControlBase。](../../atl/reference/ccomcontrolbase-class.md)

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息，请参阅创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)的文章。

有关方法和数据成员`CComControl`的演示，请参阅[中国保监会](../../overview/visual-cpp-samples.md)示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CCom控制：CCom控制

构造函数。

```
CComControl();
```

### <a name="remarks"></a>备注

调用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)构造函数，传递`m_hWnd`通过[CWindowImpl](../../atl/reference/cwindowimpl-class.md)继承的数据成员。

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CCom控制：：控制查询接口

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]请求的接口的 GUID。

*Ppv*<br/>
[出]指向*iid*标识的接口指针，如果找不到接口，则指向 NULL 的指针。

### <a name="remarks"></a>备注

仅处理 COM 地图表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CCom 控制：：创建控制窗口

默认情况下，通过调用`CWindowImpl::Create`为 控件创建一个窗口。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
[在]处理父窗口或所有者窗口。 必须提供有效的窗口句柄。 控制窗口限制在其父窗口的区域。

*rcPos*<br/>
[在]要创建的窗口的初始大小和位置。

### <a name="remarks"></a>备注

如果要执行创建单个窗口以外的操作，例如创建两个窗口，其中一个窗口将成为控件的工具栏，请重写此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl：火通

通知容器的接收器控件属性已更改。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>参数

*脱从ID*<br/>
[在]已更改的属性的标识符。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

如果控件类派生自[IPropertyNotifySink，](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)则此方法调用[CFirePropNotifyEvent：：FireOnS，](cfirepropnotifyevent-class.md#fireonchanged)用于通知所有`IPropertyNotifySink`连接的接口指定的控件属性已更改。 如果控件类不派生自`IPropertyNotifySink`，则此方法返回S_OK。

即使您的控件不支持连接点，也安全地调用此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl：：火对请求编辑

通知容器的接收器控件属性即将更改，并且对象正在询问接收器如何继续。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>参数

*脱从ID*<br/>
[在]要更改的属性的标识符。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

如果控件类派生自[IPropertyNotifySink，](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)则此方法调用[CFirePropNotifyEvent：：FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)以通知所有`IPropertyNotifySink`连接的接口指定的控件属性即将更改。 如果控件类不派生自`IPropertyNotifySink`，则此方法返回S_OK。

即使您的控件不支持连接点，也安全地调用此方法。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl：消息框

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
对话框标题。 如果为 NULL（默认值），则使用标题"错误"。

nType**<br/>
指定对话框的内容和行为。 有关可用的不同消息框的列表，请参阅 Windows SDK 文档中的[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)条目。 默认值提供了一个简单的 **"确定"** 按钮。

### <a name="return-value"></a>返回值

返回一个整数值，指定 Windows SDK 文档中[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)下列出的菜单项值之一。

### <a name="remarks"></a>备注

`MessageBox`在开发过程中非常有用，并且作为向用户显示错误或警告消息的简便方法。

## <a name="see-also"></a>另请参阅

[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComControlBase 类](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl 类](../../atl/reference/ccomcompositecontrol-class.md)
