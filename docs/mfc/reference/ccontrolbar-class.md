---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: deb95d76e6d68ba5b9fad82bca1d88fd71c5a547
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369398"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控件栏类 CStatusBar、CToolBar、CDialogBar、CRebar 和[CReBar](../../mfc/reference/crebar-class.md) [COleResizebar](../../mfc/reference/coleresizebar-class.md)的基类。 [CStatusBar](../../mfc/reference/cstatusbar-class.md) [CToolBar](../../mfc/reference/ctoolbar-class.md) [CDialogBar](../../mfc/reference/cdialogbar-class.md)

## <a name="syntax"></a>语法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[C控制栏：C控制栏](#ccontrolbar)|构造 `CControlBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C控制栏：：CalcDynamic布局](#calcdynamiclayout)|将动态控制栏的大小作为[CSize](../../atl-mfc-shared/reference/csize-class.md)对象返回。|
|[C控制栏：：卡尔卡固定布局](#calcfixedlayout)|将控制栏的大小作为[CSize](../../atl-mfc-shared/reference/csize-class.md)对象返回。|
|[C控制栏：：卡尔卡内雷茨](#calcinsiderect)|返回控制条区域的当前尺寸;包括边界。|
|[C控制栏：:DoPaint](#dopaint)|渲染控制栏的边框和夹持器。|
|[C控制栏：:D原始边界](#drawborders)|渲染控制栏的边框。|
|[C控制栏：:D原始夹钳](#drawgripper)|渲染控制条的夹持器。|
|[C控制栏：：启用停靠](#enabledocking)|允许停靠或浮动控制栏。|
|[C控制栏：获取栏样式](#getbarstyle)|检索控制栏样式设置。|
|[C控制栏：获取边框](#getborders)|检索控制栏的边框值。|
|[C控制栏：获取计数](#getcount)|返回控制栏中非 HWND 元素的数量。|
|[C控制栏：获取扩展帧](#getdockingframe)|返回指向控件栏停靠到的帧的指针。|
|[C控制栏：是浮动的](#isfloating)|如果有问题的控制栏是浮动控制栏，则返回非零值。|
|[C控制栏：：更新CmdUI](#onupdatecmdui)|调用命令 UI 处理程序。|
|[C控制栏：：设置栏样式](#setbarstyle)|修改控件栏样式设置。|
|[C控制栏：：设置边框](#setborders)|设置控制栏的边框值。|
|[C控制栏：：设置位置所有者](#setinplaceowner)|更改控件栏的就地所有者。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C控制栏：m_bAutoDelete](#m_bautodelete)|如果为非零，`CControlBar`则在销毁 Windows 控制栏时将删除该对象。|
|[C控制栏：m_pInPlaceOwner](#m_pinplaceowner)|控制栏的就地所有者。|

## <a name="remarks"></a>备注

控制栏是通常与框架窗口的左侧或右侧对齐的窗口。 它可能包含基于 HWND 的控件的子项，这些控件是生成和响应 Windows 消息的窗口，或者非基于 HWND 的项目，它们不是窗口，由应用程序代码或框架代码管理。 列表框和编辑控件是基于 HWND 的控件的示例;状态栏窗格和位图按钮是基于 HWND 的控件的示例。

控制栏窗口通常是父框架窗口的子窗口，通常是框架窗口的客户端视图或 MDI 客户端的同级窗口。 对象`CControlBar`使用有关父窗口的客户端矩形的信息来定位自身。 然后，它会通知父窗口在父窗口的工作区中有多少空间未分配。

有关 的详细信息`CControlBar`，请参阅：

- [控件条](../../mfc/control-bars.md)

- [技术说明31：控制栏](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>C控制栏：：CalcDynamic布局

框架调用此成员函数以计算动态工具栏的尺寸。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>参数

*n 长度*<br/>
控制栏的所需尺寸，水平或垂直，具体取决于*dwMode*。

*nMode*<br/>
以下预定义标志用于确定动态控制栏的高度和宽度。 使用位 OR （&#124;） 运算符组合标志。

|布局模式标志|含义|
|-----------------------|-------------------|
|LM_STRETCH|指示控制栏是否应拉伸到框架的大小。 如果条形不是停靠栏（不适用于停靠），则设置。 未设置柱线停靠或浮动时（可用于停靠）。 如果设置，LM_STRETCH忽略*nLength 并根据*LM_HORZ状态返回维度。 LM_STRETCH工作原理与[CalcFixedLayout](#calcfixedlayout)中使用的*b 拉伸*参数类似;有关拉伸和方向之间关系的更多信息，请参阅该成员函数。|
|LM_HORZ|指示条形是水平或垂直方向的。 设置如果条形是水平方向的，并且如果它是垂直方向的，则不设置它。 LM_HORZ工作原理与[CalcFixedLayout](#calcfixedlayout)中使用的*bHorz*参数类似;有关拉伸和方向之间关系的更多信息，请参阅该成员函数。|
|LM_MRUWIDTH|最近使用的动态宽度。 忽略*nLength 参数*并使用记住最近使用的宽度。|
|LM_HORZDOCK|水平停靠尺寸。 忽略*nLength 参数*并返回宽度最大的动态大小。|
|LM_VERTDOCK|垂直停靠尺寸。 忽略*nLength 参数*并返回具有最大高度的动态大小。|
|LM_LENGTHY|设置*nLength*是否指示高度（Y 方向）而不是宽度。|
|LM_COMMIT|将LM_MRUWIDTH重置为浮动控制栏的当前宽度。|

### <a name="return-value"></a>返回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)对象的控制栏大小（以像素为单位）。

### <a name="remarks"></a>备注

重写此成员函数，在派生自 的`CControlBar`类中提供您自己的动态布局。 派生自`CControlBar`（CToolbar）[CToolbar](../../mfc/reference/ctoolbar-class.md)的 MFC 类将重写此成员函数并提供其自己的实现。

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>C控制栏：：卡尔卡固定布局

调用此成员函数以计算控制条的水平大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*b 拉伸*<br/>
指示是否应将条形拉伸到框架的大小。 当条形不是停靠柱（不适用于停靠条）时 *，bStretch*参数为非零，在停靠或浮动时为 0（可用于停靠）。

*布霍兹*<br/>
指示条形是水平或垂直方向的。 如果条形是水平方向，*则 bHorz*参数为非零;如果条形是垂直方向，则为 0。

### <a name="return-value"></a>返回值

`CSize`对象的控件栏大小（以像素为单位）。

### <a name="remarks"></a>备注

工具栏等控制栏可以水平或垂直拉伸，以适应控制栏中包含的按钮。

如果*bStretch*为 TRUE，则沿*bHorz*提供的方向拉伸尺寸。 换句话说，如果*bHorz*是 FALSE，则控制条是垂直拉伸的。 如果*b 拉伸*为 FALSE，则不拉伸。 下表显示了*bStretch*和*bHorz*的可能排列和生成的控制栏样式。

|b 拉伸|布霍兹|伸展|方向|停靠/未停靠|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|水平拉伸|横向|不停靠|
|TRUE|FALSE|垂直拉伸|垂直方向|不停靠|
|FALSE|TRUE|无拉伸可用|横向|停靠|
|FALSE|FALSE|无拉伸可用|垂直方向|停靠|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>C控制栏：：卡尔卡内雷茨

框架调用此函数以计算控制栏的工作区。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>参数

*矩形*<br/>
包含控制栏的当前尺寸;包括边界。

*布霍兹*<br/>
指示条形是水平或垂直方向的。 如果条形是水平方向，*则 bHorz*参数为非零;如果条形是垂直方向，则为 0。

### <a name="remarks"></a>备注

在绘制控制条之前调用此功能。

重写此函数以自定义控制栏边框和夹持栏的渲染。

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>C控制栏：C控制栏

构造 `CControlBar` 对象。

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>C控制栏：:DoPaint

由框架调用，以呈现控制栏的边框和夹持杆。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于渲染控制栏边框和夹持器的设备上下文。

### <a name="remarks"></a>备注

重写此函数以自定义控制栏的绘图行为。

另一种自定义方法是重写`DrawBorders`和`DrawGripper`函数，并为边框和夹持器添加自定义绘图代码。 由于这些方法由默认`DoPaint`方法调用，因此不需要重写。 `DoPaint`

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>C控制栏：:D原始边界

由框架调用以呈现控制栏的边框。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现控制栏边框的设备上下文。

*矩形*<br/>
包含`CRect`控制栏尺寸的对象。

### <a name="remarks"></a>备注

重写此函数以自定义控制栏边框的外观。

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>C控制栏：:D原始夹钳

由框架调用以呈现控制条的夹持器。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于渲染控制栏夹持器的设备上下文。

*矩形*<br/>
包含`CRect`控制条夹持器尺寸的对象。

### <a name="remarks"></a>备注

重写此函数以自定义控制栏夹持器的外观。

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>C控制栏：：启用停靠

调用此函数以启用停靠控制栏。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDock风格*<br/>
指定控制栏是否支持停靠，以及控制栏可以停靠到的父窗口的两侧（如果受支持）。 可以是以下一种或多项：

- CBRS_ALIGN_TOP 允许在工作区的顶部停靠。

- CBRS_ALIGN_BOTTOM允许在工作区的底部停靠。

- CBRS_ALIGN_LEFT 允许在工作区左侧停靠。

- CBRS_ALIGN_RIGHT允许在工作区的右侧停靠。

- CBRS_ALIGN_ANY 允许在工作区的任何一侧停靠。

- CBRS_FLOAT_MULTI 允许在单个微型框架窗口中浮动多个控制栏。

如果 0（即表示没有标志），则控制栏将不会停靠。

### <a name="remarks"></a>备注

指定的边必须与启用在目标帧窗口中停靠的一个边匹配，或者控制栏无法停靠到该帧窗口。

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>C控制栏：获取栏样式

调用此函数以确定当前为控制栏设置了哪些**CBRS_（** 控制栏样式）设置。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>返回值

控制栏的当前**CBRS_（** 控制栏样式）设置。 有关可用样式的完整列表，请参阅[CControlBar：设置栏样式](#setbarstyle)。

### <a name="remarks"></a>备注

不处理**WS_（** 窗口样式）样式。

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>C控制栏：获取边框

返回控制栏的当前边框值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>返回值

包含`CRect`控制栏对象每侧的当前宽度（以像素为单位）的对象。 例如[，CRect](../../atl-mfc-shared/reference/crect-class.md)对象的*左侧*成员的值是左侧边框的宽度。

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>C控制栏：获取计数

返回`CControlBar`对象上的非 HWND 项数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

`CControlBar`对象上的非 HWND 项数。 对于[CDialogBar](../../mfc/reference/cdialogbar-class.md)对象，此功能返回 0。

### <a name="remarks"></a>备注

项的类型取决于派生对象[：CStatusBar](../../mfc/reference/cstatusbar-class.md)对象的窗格，[以及 CToolBar](../../mfc/reference/ctoolbar-class.md)对象的按钮和分隔符。

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>C控制栏：获取扩展帧

调用此成员函数以获取指向控件栏停靠的当前帧窗口的指针。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>返回值

指向帧窗口的指针（如果成功）;如果成功，则指向框架窗口的指针。否则 NULL。

如果控制栏未停靠到框架窗口（即，如果控制栏是浮动的），则此函数将返回指向其父[CMiniFrameWnd 的](../../mfc/reference/cminiframewnd-class.md)指针。

### <a name="remarks"></a>备注

有关可停靠控制栏的详细信息，请参阅[CControlBar：启用停靠](#enabledocking)和[CFramewnd：:DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>C控制栏：是浮动的

调用此成员函数以确定控制栏是浮动还是停靠。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>返回值

如果控制条是浮动的，则非零;否则 0。

### <a name="remarks"></a>备注

要将控制栏的状态从停靠更改为浮动，请致电[CFrameWnd：：floatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>C控制栏：m_bAutoDelete

如果为非零，`CControlBar`则在销毁 Windows 控制栏时将删除该对象。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>备注

*m_bAutoDelete*是 BOOL 类型的公共变量。

控件栏对象通常嵌入到框架窗口对象中。 在这种情况下 *，m_bAutoDelete*为 0，因为在破坏帧窗口时，嵌入的控制栏对象将被摧毁。

如果在堆上分配`CControlBar`对象，并且不打算调用**delete**， 则此变量将设置为非零值。

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>C控制栏：m_pInPlaceOwner

控制栏的就地所有者。

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>C控制栏：：更新CmdUI

框架调用此成员函数以更新工具栏或状态栏的状态。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>参数

*p目标*<br/>
指向应用程序的主框架窗口。 此指针用于路由更新消息。

*b 禁用IfNoHndler*<br/>
指示是否应自动显示为禁用的控件的标志。

### <a name="remarks"></a>备注

要更新单个按钮或窗格，请使用消息映射中的ON_UPDATE_COMMAND_UI宏来适当地设置更新处理程序。 有关使用此宏的详细信息，请参阅[ON_UPDATE_COMMAND_UI。](message-map-macros-mfc.md#on_update_command_ui)

`OnUpdateCmdUI`当应用程序处于空闲状态时，框架调用。 要更新的帧窗口必须是可见框架窗口的子窗口，至少间接是。 `OnUpdateCmdUI`是一个先进的超易。

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>C控制栏：：设置栏样式

调用此函数以设置控件栏所需的**CBRS_** 样式。

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
控制栏所需的样式。 可以是以下一种或多项：

- CBRS_ALIGN_TOP 允许将控制栏停靠到框架窗口的工作区顶部。

- CBRS_ALIGN_BOTTOM 允许控制栏停靠到框架窗口的工作区的底部。

- CBRS_ALIGN_LEFT允许控制栏停靠到框架窗口的工作区的左侧。

- CBRS_ALIGN_RIGHT 允许控制栏停靠到框架窗口的工作区的右侧。

- CBRS_ALIGN_ANY 允许控制栏停靠到框架窗口的工作区的任何一侧。

- CBRS_BORDER_TOP 使边框在控制栏的顶部边缘上绘制时可见。

- CBRS_BORDER_BOTTOM 使边框在控制栏的底部边缘上绘制时可见。

- CBRS_BORDER_LEFT 使边框在控制栏的左边缘上绘制时可见。

- CBRS_BORDER_RIGHT 使边框在控制栏的右边缘上绘制时可见。

- CBRS_FLOAT_MULTI 允许在单个微型框架窗口中浮动多个控制栏。

- CBRS_TOOLTIPS 使工具提示显示在控制栏上。

- CBRS_FLYBY 使邮件文本与工具提示同时更新。

- CBRS_GRIPPER 使抓手（类似于`CReBar`对象中波段中使用的抓手）绘制为任何`CControlBar`派生类。

### <a name="remarks"></a>备注

不影响**WS_（** 窗口样式）设置。

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>C控制栏：：设置边框

调用此函数以设置控制栏边框的大小。

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*cx 左*<br/>
控件栏左边框的宽度（以像素为单位）。

*cyTop*<br/>
控制栏顶部边框的高度（以像素为单位）。

*cxRight*<br/>
控件栏右边框的宽度（以像素为单位）。

*cyBottom*<br/>
控制栏底部边框的高度（以像素为单位）。

*lpRect*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针，其中包含控件栏对象每个边框的当前宽度（以像素为单位）。

### <a name="example"></a>示例

以下代码示例将控制栏的顶部和底部边框设置为 5 像素，左侧和右侧边框为 2 像素：

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>C控制栏：：设置位置所有者

更改控件栏的就地所有者。

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
一个指向 `CWnd` 对象的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 类](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 类](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 类](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 类](../../mfc/reference/crebar-class.md)
