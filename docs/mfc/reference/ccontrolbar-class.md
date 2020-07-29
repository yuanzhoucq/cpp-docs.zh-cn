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
ms.openlocfilehash: 7a08efb7cbe848ec6d8ccba57671f3ef0dc8e74c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212561"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控件栏类[CStatusBar](../../mfc/reference/cstatusbar-class.md)、 [CToolBar](../../mfc/reference/ctoolbar-class.md)、 [CDialogBar](../../mfc/reference/cdialogbar-class.md)、 [CReBar](../../mfc/reference/crebar-class.md)和[COleResizeBar](../../mfc/reference/coleresizebar-class.md)的基类。

## <a name="syntax"></a>语法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CControlBar：： CControlBar](#ccontrolbar)|构造 `CControlBar` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CControlBar：： CalcDynamicLayout](#calcdynamiclayout)|以[CSize](../../atl-mfc-shared/reference/csize-class.md)对象的形式返回动态控件栏的大小。|
|[CControlBar：： CalcFixedLayout](#calcfixedlayout)|以[CSize](../../atl-mfc-shared/reference/csize-class.md)对象的形式返回控件栏的大小。|
|[CControlBar：： CalcInsideRect](#calcinsiderect)|返回控件条区域的当前尺寸;包括边框。|
|[CControlBar：:D oPaint](#dopaint)|呈现控件栏的边框和控制手柄。|
|[CControlBar：:D rawBorders](#drawborders)|呈现控件栏的边框。|
|[CControlBar：:D rawGripper](#drawgripper)|呈现控件栏的手柄。|
|[CControlBar：： EnableDocking](#enabledocking)|允许停靠或浮动控件条。|
|[CControlBar：： GetBarStyle](#getbarstyle)|检索控件条样式设置。|
|[CControlBar：： GetBorders](#getborders)|检索控件栏的边框值。|
|[CControlBar：： GetCount](#getcount)|返回控件栏中的非 HWND 元素的数目。|
|[CControlBar：： GetDockingFrame](#getdockingframe)|返回一个指针，该指针指向控件栏停靠到的框架。|
|[CControlBar：： IsFloating](#isfloating)|如果相关的控件栏是一个浮动控件栏，则返回一个非零值。|
|[CControlBar：： OnUpdateCmdUI](#onupdatecmdui)|调用命令 UI 处理程序。|
|[CControlBar：： SetBarStyle](#setbarstyle)|修改控件条样式设置。|
|[CControlBar：： SetBorders](#setborders)|设置控件栏的边框值。|
|[CControlBar：： SetInPlaceOwner](#setinplaceowner)|更改控件条的就地所有者。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CControlBar：： m_bAutoDelete](#m_bautodelete)|如果为非零，则在 `CControlBar` 销毁 Windows 控件栏时将删除该对象。|
|[CControlBar：： m_pInPlaceOwner](#m_pinplaceowner)|控件条的就地所有者。|

## <a name="remarks"></a>备注

控件条是一个窗口，通常与框架窗口的左侧或右侧对齐。 它可能包含基于 HWND 的控件（即生成和响应 Windows 消息的窗口）或不基于 HWND 的项（不是 windows，由应用程序代码或框架代码管理）的子项。 列表框和编辑控件是基于 HWND 的控件的示例;状态栏窗格和位图按钮都是基于 HWND 的控件的示例。

控件栏窗口通常是父框架窗口的子窗口，通常是框架窗口的客户端视图或 MDI 客户端的同级。 `CControlBar`对象使用有关父窗口的客户端矩形的信息来定位自身。 然后，它会向父窗口通知父窗口的工作区中未分配的空间量。

有关的详细信息 `CControlBar` ，请参阅：

- [控制条](../../mfc/control-bars.md)

- [技术说明31：控件条](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>要求

**标头：** afxext。h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar：： CalcDynamicLayout

框架调用此成员函数来计算动态工具栏的尺寸。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>参数

*nLength*<br/>
控件条的请求维度（水平或垂直），取决于*dwMode*。

*nMode*<br/>
以下预定义的标记用于确定动态控件栏的高度和宽度。 使用按位 "或" （&#124;）运算符组合标志。

|布局模式标志|含义|
|-----------------------|-------------------|
|LM_STRETCH|指示是否应将控件条拉伸到帧的大小。 如果栏不是停靠栏（不可停靠），则设置。 当条停靠或浮动（可用于停靠）时未设置。 如果设置，LM_STRETCH 将忽略*nLength* ，并基于 LM_HORZ 状态返回维度。 LM_STRETCH 的工作方式类似于[CalcFixedLayout](#calcfixedlayout)中使用的*bStretch*参数;有关拉伸和方向之间的关系的详细信息，请参阅该成员函数。|
|LM_HORZ|指示条形是水平方向还是垂直方向。 如果条形图是水平方向的，则设置，如果垂直方向，则不设置。 LM_HORZ 的工作方式类似于[CalcFixedLayout](#calcfixedlayout)中使用的*bHorz*参数;有关拉伸和方向之间的关系的详细信息，请参阅该成员函数。|
|LM_MRUWIDTH|最近使用的动态宽度。 忽略*nLength*参数，并使用记住的最近使用的宽度。|
|LM_HORZDOCK|水平停靠尺寸。 忽略*nLength*参数并返回最大宽度的动态大小。|
|LM_VERTDOCK|垂直停靠尺寸。 忽略*nLength*参数，并返回最大高度的动态大小。|
|LM_LENGTHY|如果*nLength*指示高度（Y 方向）而不是宽度，则设置。|
|LM_COMMIT|将 LM_MRUWIDTH 重置为浮动控件栏的当前宽度。|

### <a name="return-value"></a>返回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)对象的控件条大小（以像素为单位）。

### <a name="remarks"></a>备注

重写此成员函数以在派生自的类中提供自己的动态布局 `CControlBar` 。 从派生的 MFC 类（ `CControlBar` 如[CToolbar](../../mfc/reference/ctoolbar-class.md)）将重写此成员函数并提供其自己的实现。

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar：： CalcFixedLayout

调用此成员函数可计算控件条的水平大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*bStretch*<br/>
指示是否应将栏拉伸到帧的大小。 如果栏不是停靠栏（不能用于停靠）， *bStretch*参数为非零值，当停靠或浮动（可用于停靠）时，此参数为0。

*bHorz*<br/>
指示条形是水平方向还是垂直方向。 如果条形水平方向，则*bHorz*参数为非零值，如果垂直方向，则为0。

### <a name="return-value"></a>返回值

对象的控件条大小（以像素为单位） `CSize` 。

### <a name="remarks"></a>备注

控件条（如工具栏）可以水平或垂直拉伸，以容纳控制栏中包含的按钮。

如果*bStretch*为 TRUE，则沿*bHorz*提供的方向拉伸维度。 换言之，如果*bHorz*为 FALSE，则控件条将垂直拉伸。 如果*bStretch*为 FALSE，则不进行延伸。 下表显示了*bStretch*和*bHorz*的可能排列和生成的控件条形样式。

|bStretch|bHorz|拉伸|方向|停靠/未插接|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|水平拉伸|水平方向|未停靠|
|TRUE|FALSE|垂直拉伸|垂直方向|未停靠|
|FALSE|TRUE|无拉伸可用|水平方向|停靠|
|FALSE|FALSE|无拉伸可用|垂直方向|停靠|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar：： CalcInsideRect

框架调用此函数来计算控件栏的工作区。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>参数

*rect*<br/>
包含控件栏的当前尺寸;包括边框。

*bHorz*<br/>
指示条形是水平方向还是垂直方向。 如果条形水平方向，则*bHorz*参数为非零值，如果垂直方向，则为0。

### <a name="remarks"></a>备注

此函数在绘制控件栏之前被调用。

重写此函数可自定义控件栏的边框和抓取栏的呈现。

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar：： CControlBar

构造 `CControlBar` 对象。

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar：:D oPaint

由框架调用以呈现控件栏的边框和抓取器栏。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现控件栏的边框和控制手柄的设备上下文。

### <a name="remarks"></a>备注

重写此函数可自定义控件栏的绘制行为。

另一种自定义方法是重写 `DrawBorders` 和 `DrawGripper` 函数，并为边框和手柄添加自定义绘制代码。 由于这些方法是由默认方法调用的 `DoPaint` ，因此 `DoPaint` 不需要重写。

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar：:D rawBorders

由框架调用以呈现控件栏的边框。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现控件栏边框的设备上下文。

*rect*<br/>
`CRect`包含控件条尺寸的对象。

### <a name="remarks"></a>备注

重写此函数可自定义控件条边框的外观。

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar：:D rawGripper

由框架调用以呈现控件栏的手柄。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现控制条控制手柄的设备上下文。

*rect*<br/>
一个 `CRect` 对象，它包含控制条控制手柄的尺寸。

### <a name="remarks"></a>备注

重写此函数以自定义控制条控制手柄的外观。

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar：： EnableDocking

调用此函数可启用停靠控件条。

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDockStyle*<br/>
指定控件栏是否支持停靠以及控件栏可以停靠到的父窗口的侧（如果支持）。 可以是下列一项或多项：

- CBRS_ALIGN_TOP 允许在工作区顶部停靠。

- CBRS_ALIGN_BOTTOM 允许在工作区的底部停靠。

- CBRS_ALIGN_LEFT 允许在工作区的左侧停靠。

- CBRS_ALIGN_RIGHT 允许在客户端区域的右侧停靠。

- CBRS_ALIGN_ANY 允许在客户端区域的任何一侧停靠。

- CBRS_FLOAT_MULTI 允许在单个袖珍框架窗口中浮动多个控制条。

如果为0（即，指示没有标志），则不会停靠控件条。

### <a name="remarks"></a>备注

指定的边必须与 "目标帧" 窗口中启用了停靠的一条边匹配，否则控件条无法停靠到该框架窗口中。

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar：： GetBarStyle

调用此函数可确定当前为控件栏设置了哪些**CBRS_** （控件条形样式）设置。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>返回值

控件栏的当前**CBRS_** （控件条形样式）设置。 有关可用样式的完整列表，请参阅[CControlBar：： SetBarStyle](#setbarstyle) 。

### <a name="remarks"></a>备注

不处理**WS_** （窗口样式）样式。

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar：： GetBorders

返回控件栏的当前边框值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>返回值

一个 `CRect` 对象，该对象包含控件条对象两侧的当前宽度（以像素为单位）。 例如， [CRect](../../atl-mfc-shared/reference/crect-class.md)对象的*左侧*成员的值为左边框的宽度。

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar：： GetCount

返回对象上非 HWND 项的数目 `CControlBar` 。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

对象上的非 HWND 项的数目 `CControlBar` 。 对于[CDialogBar](../../mfc/reference/cdialogbar-class.md)对象，此函数返回0。

### <a name="remarks"></a>备注

项的类型取决于派生对象： [CStatusBar](../../mfc/reference/cstatusbar-class.md)对象的窗格，以及[CToolBar](../../mfc/reference/ctoolbar-class.md)对象的按钮和分隔符。

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar：： GetDockingFrame

调用此成员函数以获取指向控件栏停靠到的当前框架窗口的指针。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>返回值

如果成功，则为指向帧窗口的指针;否则为 NULL。

如果控件条未停靠到框架窗口（即，如果控件栏是浮动控件），则此函数将返回指向其父[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)的指针。

### <a name="remarks"></a>备注

有关可停靠控件条的详细信息，请参阅[CControlBar：： EnableDocking](#enabledocking)和[CFrameWnd：:D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar：： IsFloating

调用此成员函数以确定控件条是浮动的还是停靠的。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>返回值

如果控件栏是浮动的，则为非零值;否则为0。

### <a name="remarks"></a>备注

若要将控件栏的状态从停靠更改为浮动，请调用[CFrameWnd：： FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar：： m_bAutoDelete

如果为非零，则在 `CControlBar` 销毁 Windows 控件栏时将删除该对象。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>备注

*m_bAutoDelete*是 BOOL 类型的公共变量。

控件栏对象通常嵌入在框架窗口对象中。 在这种情况下， *m_bAutoDelete*为0，因为在销毁框架窗口时会销毁嵌入的控件栏对象。

如果在 `CControlBar` 堆上分配对象，但不打算调用，请将此变量设置为非零值 **`delete`** 。

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar：： m_pInPlaceOwner

控件条的就地所有者。

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar：： OnUpdateCmdUI

框架调用此成员函数以更新工具栏或状态栏的状态。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>参数

*pTarget*<br/>
指向应用程序的主框架窗口。 此指针用于路由更新消息。

*bDisableIfNoHndler*<br/>
一个标志，该标志指示是否应自动将没有更新处理程序的控件显示为禁用。

### <a name="remarks"></a>备注

若要更新单个按钮或窗格，请使用消息映射中的 ON_UPDATE_COMMAND_UI 宏来适当地设置更新处理程序。 有关使用此宏的详细信息，请参阅[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 。

`OnUpdateCmdUI`当应用程序处于空闲状态时，由框架调用。 要更新的框架窗口必须是可见框架窗口的子窗口，至少是间接的。 `OnUpdateCmdUI`是一个高级可重写。

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar：： SetBarStyle

调用此函数可设置所需的控件栏**CBRS_** 样式。

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
控件条的所需样式。 可以是下列一项或多项：

- CBRS_ALIGN_TOP 允许控件栏停靠在框架窗口的工作区的顶部。

- CBRS_ALIGN_BOTTOM 允许控件栏停靠在框架窗口的工作区的底部。

- CBRS_ALIGN_LEFT 允许控件栏停靠在框架窗口的工作区的左侧。

- CBRS_ALIGN_RIGHT 允许控件栏停靠在框架窗口的工作区的右侧。

- CBRS_ALIGN_ANY 允许控件栏停靠到框架窗口的工作区的任何一侧。

- CBRS_BORDER_TOP，将在控件条的上边缘绘制一个边框。

- CBRS_BORDER_BOTTOM 会导致在控件栏的下边缘上绘制边框。

- CBRS_BORDER_LEFT 会导致在控件栏的左边缘上绘制边框。

- CBRS_BORDER_RIGHT 会导致在控件栏的右边缘上绘制边框。

- CBRS_FLOAT_MULTI 允许在单个袖珍框架窗口中浮动多个控制条。

- CBRS_TOOLTIPS 将为控件条显示工具提示。

- CBRS_FLYBY 使消息文本同时作为工具提示进行更新。

- CBRS_GRIPPER 将导致为 `CReBar` 任何派生类绘制类似于在对象中使用的手柄 `CControlBar` 。

### <a name="remarks"></a>备注

不会影响**WS_** （窗口样式）设置。

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar：： SetBorders

调用此函数可设置控件栏边框的大小。

```cpp
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*cxLeft*<br/>
控件栏左边框的宽度（以像素为单位）。

*cyTop*<br/>
控件条上边框的高度（以像素为单位）。

*cxRight*<br/>
控件条右边框的宽度（以像素为单位）。

*cyBottom*<br/>
控件条下边框的高度（以像素为单位）。

*lpRect*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针，该对象包含控件条对象的每个边框的当前宽度（以像素为单位）。

### <a name="example"></a>示例

下面的代码示例将控件栏的上边框和下边框设置为5个像素，将左边框和右边框设置为2个像素：

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar：： SetInPlaceOwner

更改控件条的就地所有者。

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
一个指向 `CWnd` 对象的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 类](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 类](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 类](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 类](../../mfc/reference/crebar-class.md)
