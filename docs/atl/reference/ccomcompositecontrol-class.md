---
title: CComCompositeControl 类
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320807"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 类

此类提供实现复合控件所需的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及您要支持复合控件的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom复合控制：CCom复合控制](#ccomcompositecontrol)|构造函数。|
|[CCom复合控制：*CCom复合控制](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom复合控制：：建议SinkMap](#advisesinkmap)|调用此方法可建议或取消建议由复合控件承载的所有控件。|
|[CCom复合控制：：钙度](#calcextent)|调用此方法以 HIMETRIC 单位的形式计算用于承载复合控件的对话框资源的大小。|
|[CCom复合控制：创建](#create)|调用此方法是为了创建复合控件的控制窗口。|
|[CCom 复合控制：：创建控制窗口](#createcontrolwindow)|调用此方法以创建控件窗口并通知任何托管控件。|
|[CCom复合控制：：从环境设置背景颜色](#setbackgroundcolorfromambient)|调用此方法以使用容器的背景颜色设置复合控件的背景颜色。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCom复合控制：：m_hbrBackground](#m_hbrbackground)|背景画笔。|
|[CCom复合控制：：m_hWndFocus](#m_hwndfocus)|当前具有焦点的窗口的句柄。|

## <a name="remarks"></a>备注

从类`CComCompositeControl`派生的类继承 ActiveX 复合控件的功能。 派生自的`CComCompositeControl`ActiveX 控件由标准对话框承载。 这些类型的控件称为复合控件，因为它们能够承载其他控件（本机 Windows 控件和 ActiveX 控件）。

`CComCompositeControl`通过在子类中查找枚举的数据成员，标识用于创建复合控件的对话框资源。 此子类的成员 IDD 设置为将用作控件窗口的对话框资源的资源 ID。 下面是派生的`CComCompositeControl`类应包含的数据成员的示例，用于标识要用于控件窗口的对话框资源：

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> 复合控件始终是窗口控件，尽管它们可以包含无窗口控件。

派生`CComCompositeControl`类实现的控件内置了默认制表符行为。 当控件通过在包含应用程序中的选项卡式接收焦点时，连续按下 TAB 键将导致焦点循环通过所有复合控件的包含控件，然后从复合控件中循环到容器的选项卡顺序下一个项。 托管控件的选项卡顺序由对话框资源确定，并确定选项卡的进行顺序。

> [!NOTE]
> 为了使加速器在`CComCompositeControl`创建控件时加载加速器表，将句柄和加速器数传回[IOleControlImpl：getControlInfo，](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)最后在释放控件时销毁该表。

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CCom复合控制：：建议SinkMap

调用此方法可建议或取消建议由复合控件承载的所有控件。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>参数

*b 建议*<br/>
如果建议所有控件，则为 True;否则是虚假的。

### <a name="return-value"></a>返回值

|||
|-|-|
|S_OK  |事件接收器映射中的所有控件已成功连接或断开其事件源。|
|E_FAIL  |并非所有事件接收器映射中的控件都可以成功连接或断开其事件源。|
|E_POINTER  |此错误通常表示控件的事件接收器映射中的条目有问题，`IDispEventImpl`或者在 或`IDispEventSimpleImpl`基类中使用的模板参数有问题。|
|CONNECT_E_ADVISELIMIT  |该连接点已经达到其连接极限，无法再进行接受了。|
|CONNECT_E_CANNOTCONNECT  |接收器不支持此连接点所需的接口。|
|CONNECT_E_NOCONNECTION  |Cookie 值不表示有效的连接。 此错误通常表示控件的事件接收器映射中的条目有问题，`IDispEventImpl`或者在 或`IDispEventSimpleImpl`基类中使用的模板参数有问题。|

### <a name="remarks"></a>备注

此方法的基本实现搜索事件接收器映射中的条目。 然后，它建议或取消建议与事件接收器映射的接收器条目描述的 COM 对象的连接点。 此成员方法还依赖于派生类从要建议或不通知的接收器映射中每个控件`IDispEventImpl`的一个实例继承这一事实。

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CCom复合控制：：钙度

调用此方法以 HIMETRIC 单位的形式计算用于承载复合控件的对话框资源的大小。

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>参数

*大小*<br/>
对要由此方法`SIZE`填充的结构的引用。

### <a name="return-value"></a>返回值

如果控件由对话框承载，则为 TRUE;如果控件由对话框承载，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

大小在*大小*参数中返回。

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CCom复合控制：创建

调用此方法是为了创建复合控件的控制窗口。

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
控件的父窗口的句柄。

*rcPos*<br/>
保留。

*德维尼帕拉姆*<br/>
在创建控件期间要传递给控件的数据。 作为*dwInitParam*传递的数据将显示为[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息的 LPARAM 参数，该参数将在创建时发送到复合控件。

### <a name="return-value"></a>返回值

新创建的复合控件对话框的句柄。

### <a name="remarks"></a>备注

此方法通常在控件的就地激活期间调用。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CCom复合控制：CCom复合控制

构造函数。

```
CComCompositeControl();
```

### <a name="remarks"></a>备注

初始化[CCom 复合控制：：m_hbrBackground](#m_hbrbackground)和[CCom 复合控制：：m_hWndFocus](#m_hwndfocus)数据成员到 NULL。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CCom复合控制：*CCom复合控制

析构函数。

```
~CComCompositeControl();
```

### <a name="remarks"></a>备注

删除背景对象（如果存在）。

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CCom 复合控制：：创建控制窗口

调用此方法以创建控件窗口并通知任何托管控件。

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
控件的父窗口的句柄。

*rcPos*<br/>
相对于*hWndParent*的复合控件的位置矩形。

### <a name="return-value"></a>返回值

将句柄返回到新创建的复合控件对话框。

### <a name="remarks"></a>备注

此方法调用[CCom 复合控制：：创建](#create)和[CCom 复合控制：：建议 SinkMap](#advisesinkmap)。

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CCom复合控制：：m_hbrBackground

背景画笔。

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CCom复合控制：：m_hWndFocus

当前具有焦点的窗口的句柄。

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CCom复合控制：：从环境设置背景颜色

调用此方法以使用容器的背景颜色设置复合控件的背景颜色。

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)<br/>
[类概述](../../atl/atl-class-overview.md)
