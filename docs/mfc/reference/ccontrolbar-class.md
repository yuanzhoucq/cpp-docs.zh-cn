---
title: CControlBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd69813251a96051f844051f27155e1d4ed404d6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393409"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

控件条类的基类[CStatusBar](../../mfc/reference/cstatusbar-class.md)， [CToolBar](../../mfc/reference/ctoolbar-class.md)， [CDialogBar](../../mfc/reference/cdialogbar-class.md)， [CReBar](../../mfc/reference/crebar-class.md)，和[COleResizeBar](../../mfc/reference/coleresizebar-class.md)。

## <a name="syntax"></a>语法

```
class CControlBar : public CWnd
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|构造 `CControlBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|返回作为动态控件条的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|返回作为控件条的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。|
|[CControlBar::CalcInsideRect](#calcinsiderect)|返回控件栏区域; 的当前维度这包括边框。|
|[CControlBar::DoPaint](#dopaint)|呈现的边框和控件条的控制手柄。|
|[CControlBar::DrawBorders](#drawborders)|呈现控件条的边框。|
|[CControlBar::DrawGripper](#drawgripper)|呈现控件条的控制手柄。|
|[CControlBar::EnableDocking](#enabledocking)|允许为停靠或浮动的控件条。|
|[CControlBar::GetBarStyle](#getbarstyle)|检索控件栏样式设置。|
|[CControlBar::GetBorders](#getborders)|检索控件条的边框值。|
|[CControlBar::GetCount](#getcount)|在将控件条中返回非 HWND 元素的数。|
|[CControlBar::GetDockingFrame](#getdockingframe)|返回一个指向到的停靠控件条的帧。|
|[CControlBar::IsFloating](#isfloating)|如果有问题的控件栏是浮动的控件条，则返回非零值。|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|调用命令 UI 处理程序。|
|[CControlBar::SetBarStyle](#setbarstyle)|修改控件栏样式设置。|
|[CControlBar::SetBorders](#setborders)|设置控件条的边框值。|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|更改控件条的就地的所有者。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|如果非零，`CControlBar`销毁 Windows 控件条时删除对象。|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|控件条的就地所有者。|

## <a name="remarks"></a>备注

控件条是通常对齐的左侧或右侧的框架窗口的窗口。 它可能包含基于 HWND 的控件，这是生成和响应 Windows 消息的窗口，或非基于 HWND 的项，而不是 windows 管理的应用程序代码或框架代码的子项目。 列表框和编辑控件是基于 HWND 的控件; 的示例状态栏窗格和位图按钮是非基于 HWND 的控件的示例。

控件条 windows 通常是父框架窗口的子窗口，并通常是与客户端视图或 MDI 客户端框架窗口的同级。 一个`CControlBar`对象使用父窗口的客户端矩形有关的信息来为自身定位。 然后，它通知父窗口并在父窗口工作区中剩余未分配多少空间。

有关详细信息`CControlBar`，请参阅：

- [控件条](../../mfc/control-bars.md)

- [技术说明 31： 控件条](../../mfc/tn031-control-bars.md)。

- 知识库文章 Q242577: PRB： 更新命令 UI 处理程序执行不工作的菜单附加到对话框

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

框架调用此成员函数以计算动态工具栏的维度。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>参数

*nLength*<br/>
控件条，水平或垂直的具体取决于请求的维度*dwMode*。

*nMode*<br/>
以下预定义的标志用于确定的高度和宽度的动态控件条。 使用按位或 (&#124;) 运算符合并后标志。

|布局模式标志|这意味着|
|-----------------------|-------------------|
|LM_STRETCH|指示是否将控件条被拉伸到帧的大小。 如果在栏不是停靠栏 （不可用于停靠），设置。 如果不设置栏停靠或浮动 （适用于停靠）。 如果设置，LM_STRETCH 将忽略*nLength* ，并返回维度根据 LM_HORZ 状态。 LM_STRETCH 工作原理类似于*bStretch*中使用参数[CalcFixedLayout](#calcfixedlayout); 请参阅有关拉伸和方向之间的关系的详细信息的成员函数。|
|LM_HORZ|指示该线条是水平或垂直。 在该线条是水平方向，但如果它是垂直方向，未设置时设置。 LM_HORZ 工作原理类似于*bHorz*中使用参数[CalcFixedLayout](#calcfixedlayout); 请参阅有关拉伸和方向之间的关系的详细信息的成员函数。|
|LM_MRUWIDTH|最近使用的动态宽度。 将忽略*nLength*参数，并使用已记住最近使用的宽度。|
|LM_HORZDOCK|水平停靠维度。 将忽略*nLength*参数并返回动态大小最大宽度。|
|LM_VERTDOCK|垂直停靠维度。 将忽略*nLength*参数并返回动态大小的最大高度。|
|LM_LENGTHY|如果设置*nLength*指示而不是 width 的高度 （Y 轴方向）。|
|LM_COMMIT|将 LM_MRUWIDTH 重置为浮动的控件条的当前宽度。|

### <a name="return-value"></a>返回值

控件条的大小，以像素为单位的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

### <a name="remarks"></a>备注

重写此成员函数以提供您自己在从派生的类中的动态布局`CControlBar`。 MFC 类派生自`CControlBar`，如[CToolbar](../../mfc/reference/ctoolbar-class.md)、 重写此成员函数并提供其自己的实现。

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

调用此成员函数来计算的控件条的水平大小。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*bStretch*<br/>
指示是否应被栏拉伸到帧的大小。 *BStretch*栏不是停靠栏 （不可用于停靠） 和为 0 时停靠或浮动 （适用于停靠） 时，参数为非零值。

*bHorz*<br/>
指示该线条是水平或垂直。 *BHorz*参数为非零值，如果在栏是水平方向和垂直方向是否为 0。

### <a name="return-value"></a>返回值

控件条的大小，以像素为单位的`CSize`对象。

### <a name="remarks"></a>备注

如工具栏的控件条可以拉伸水平或垂直以容纳这些按钮包含在控件条。

如果*bStretch*为 TRUE，拉伸方向提供沿维度*bHorz*。 换而言之，如果*bHorz*为 FALSE 时，将控件条的垂直方向拉伸。 如果*bStretch*为 FALSE 时，没有延伸时发生。 下表显示了可能的排列，并生成的控制条样式的*bStretch*并*bHorz*。

|bStretch|bHorz|拉伸|方向|停靠/未停靠|
|--------------|-----------|----------------|-----------------|--------------------------|
|true|true|水平拉伸|水平方向|不停靠|
|true|false|垂直拉伸|垂直方向|不停靠|
|false|true|没有拉伸可用|水平方向|停靠|
|false|false|没有拉伸可用|垂直方向|停靠|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

框架调用此函数可计算控件条的客户端区域。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>参数

*rect*<br/>
包含控件条中; 当前维度这包括边框。

*bHorz*<br/>
指示该线条是水平或垂直。 *BHorz*参数为非零值，如果在栏是水平方向和垂直方向是否为 0。

### <a name="remarks"></a>备注

绘制控件条之前调用此函数。

重写此函数可自定义的边框和控件条的手柄栏的呈现。

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

构造 `CControlBar` 对象。

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

由框架调用以呈现边框和控件条的手柄栏。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要用于呈现边框和控件条的控制手柄的设备上下文。

### <a name="remarks"></a>备注

重写此函数可自定义控件条的绘制行为。

另一种自定义方法是重写`DrawBorders`和`DrawGripper`函数并添加边框和控制手柄的自定义绘制代码。 因为默认情况下调用这些方法`DoPaint`方法中，重写`DoPaint`不需要。

##  <a name="drawborders"></a>  CControlBar::DrawBorders

由框架调用以呈现控件条的边框。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向设备上下文以用于呈现控件条的边框。

*rect*<br/>
一个`CRect`对象，其中包含的控件条的维度。

### <a name="remarks"></a>备注

重写此函数可自定义控件栏边框的外观。

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

由框架调用以呈现控件条的控制手柄。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要用于呈现控件栏控制手柄的设备上下文。

*rect*<br/>
一个`CRect`对象，其中包含的控件条控制手柄尺寸。

### <a name="remarks"></a>备注

重写此函数可自定义控件栏控制手柄的外观。

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

调用此函数可启用可停靠控件条。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

*dwDockStyle*<br/>
如果支持，指定是否将控件条支持停靠和到可停靠控件条，其父窗口的边。 可以是一个或多项操作：

- CBRS_ALIGN_TOP 允许停靠在工作区的顶部。

- CBRS_ALIGN_BOTTOM 允许客户端区域底部的停靠。

- CBRS_ALIGN_LEFT 允许客户端区域的左侧停靠。

- CBRS_ALIGN_RIGHT 允许客户端区域右侧停靠。

- CBRS_ALIGN_ANY 允许任意一侧的客户端区域停靠。

- CBRS_FLOAT_MULTI 允许多个控件条，以在单个微型框架窗口中浮动。

如果为 0 （即，指示任何标志），将不停靠控件条。

### <a name="remarks"></a>备注

指定边必须匹配一方为停靠在目标框架窗口中，启用或不到该框架窗口停靠控件条。

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

调用此函数可确定哪个**CBRS_** 控件栏的当前设置 （控制条样式） 设置。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>返回值

当前**CBRS_** 的控件条 （控件栏样式） 设置。 请参阅[CControlBar::SetBarStyle](#setbarstyle)可用样式的完整列表。

### <a name="remarks"></a>备注

不处理**WS_** （窗口样式） 样式。

##  <a name="getborders"></a>  CControlBar::GetBorders

返回控件条的当前边框值。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>返回值

一个`CRect`对象，其中包含每个边的控件条对象的当前宽度 （以像素为单位）。 例如，值*左*成员的[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，则左侧显示边框的宽度。

##  <a name="getcount"></a>  CControlBar::GetCount

返回有关非 HWND 项数`CControlBar`对象。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

非 HWND 项目的数目`CControlBar`对象。 此函数将返回 0 [CDialogBar](../../mfc/reference/cdialogbar-class.md)对象。

### <a name="remarks"></a>备注

项的类型取决于派生的对象： 窗格[CStatusBar](../../mfc/reference/cstatusbar-class.md)对象和按钮和用于分隔符[CToolBar](../../mfc/reference/ctoolbar-class.md)对象。

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

调用此成员函数可获取当前的框架窗口到停靠控件条的指针。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>返回值

框架窗口，如果成功，则指向的指针否则为，为 NULL。

如果 （即，如果浮动的控件条） 框架窗口不停靠控件条，此函数将返回一个指向其父[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)。

### <a name="remarks"></a>备注

有关可停靠控件条的详细信息，请参阅[CControlBar::EnableDocking](#enabledocking)并[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。

##  <a name="isfloating"></a>  CControlBar::IsFloating

调用此成员函数以确定是否浮动或停靠控件条。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>返回值

如果浮动的控件条; 非零值否则为 0。

### <a name="remarks"></a>备注

若要更改的状态中的控件栏的停靠浮动，调用[CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

如果非零，`CControlBar`销毁 Windows 控件条时删除对象。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>备注

*m_bAutoDelete* BOOL 类型的公共变量。

控件条对象通常嵌入在框架窗口对象中。 在这种情况下， *m_bAutoDelete*为 0，因为嵌入的控件条对象被销毁时销毁框架窗口。

将此变量设置为非零值，如果分配`CControlBar`对象上，在堆，并且不打算调用**删除**。

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

控件条的就地所有者。

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

此成员函数调用由框架以更新工具栏或状态栏的状态。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>参数

*pTarget*<br/>
指向应用程序的主框架窗口。 此指针用来发送更新消息。

*bDisableIfNoHndler*<br/>
该标志指示是否没有任何更新处理程序的控件应自动显示为已禁用。

### <a name="remarks"></a>备注

若要更新的单个按钮或窗格中，使用消息映射中 ON_UPDATE_COMMAND_UI 宏来适当地设置一个更新处理程序。 请参阅[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)有关使用此宏的详细信息。

`OnUpdateCmdUI` 当应用程序处于空闲状态时，是由框架调用。 要更新的框架窗口必须是子窗口中，至少间接可见框架窗口。 `OnUpdateCmdUI` 是一种高级可重写。

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

调用此函数可设置所需**CBRS_** 样式的控件条。

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
控件条所需的样式。 可以是一个或多项操作：

- CBRS_ALIGN_TOP 允许控件栏可停靠到框架窗口的工作区的顶部。

- CBRS_ALIGN_BOTTOM 允许控件栏可停靠到框架窗口的工作区的底部。

- CBRS_ALIGN_LEFT 允许到左侧和右侧的框架窗口的客户端区域停靠控件条。

- CBRS_ALIGN_RIGHT 允许框架窗口的客户端区域的右侧停靠控件条。

- CBRS_ALIGN_ANY 允许控件栏可停靠到框架窗口的工作区的任何一侧。

- CBRS_BORDER_TOP 会导致要利用的控制条时它都是可见的上边缘的边框。

- CBRS_BORDER_BOTTOM 会导致要绘制的栏时它都是可见的控件下边缘的边框。

- CBRS_BORDER_LEFT 会导致要在上栏时它都是可见的控件的左边缘绘制的边框。

- CBRS_BORDER_RIGHT 会导致要利用的栏时它都是可见的控件的右边缘的边框。

- CBRS_FLOAT_MULTI 允许多个控件条，以在单个微型框架窗口中浮动。

- CBRS_TOOLTIPS 会导致工具提示显示的控件条。

- CBRS_FLYBY 会导致消息正文作为工具提示一次更新。

- CBRS_GRIPPER 导致手柄，类似于上带区中使用`CReBar`对象，若要绘制的任何`CControlBar`-派生的类。

### <a name="remarks"></a>备注

不会影响**WS_** （窗口样式） 设置。

##  <a name="setborders"></a>  CControlBar::SetBorders

调用此函数可设置的控件条的边框大小。

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*cxLeft*<br/>
控件条的左边框宽度 （以像素为单位）。

*cyTop*<br/>
控件条上边框的高度 （以像素为单位）。

*cxRight*<br/>
控件条的右边框宽度 （以像素为单位）。

*cyBottom*<br/>
控件条的下边框的高度 （以像素为单位）。

*lpRect*<br/>
一个指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含每个边框的控件条对象的当前宽度 （以像素为单位）。

### <a name="example"></a>示例

下面的代码示例将 5 个像素，将控件条的顶部和底部边框和左和右边框设置为 2 个像素：

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

更改控件条的就地的所有者。

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
一个指向`CWnd`对象。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 类](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 类](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 类](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 类](../../mfc/reference/crebar-class.md)
