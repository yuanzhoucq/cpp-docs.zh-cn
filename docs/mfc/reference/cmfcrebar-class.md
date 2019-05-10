---
title: CMFCReBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: 7776bf504d502feee8ef51949b8adc8e44f94c8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410130"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 类

一个`CMFCReBar`对象是提供了布局、 持久性和 rebar 控件的状态信息的控件条。
有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。
## <a name="syntax"></a>语法

```
class CMFCReBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|向 rebar 带区。|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(重写[cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CMFCReBar::CanFloat](#canfloat)|(重写[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|
|[CMFCReBar::Create](#create)|创建 rebar 控件，并将其附加到`CMFCReBar`对象。|
|[CMFCReBar::EnableDocking](#enabledocking)|(重写[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|提供直接访问权限的基础[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)公共控件。|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(重写[cpane:: Onshowcontrolbarmenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(重写[CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)。)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(重写[CBasePane::OnUpdateCmdUI](cbasepane-class.md)。)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(重写[CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)。)|

## <a name="remarks"></a>备注

一个`CMFCReBar`对象可包含各种子窗口。 这包括编辑框、 工具栏和列表框。 以编程方式调整大小 rebar 或用户可以通过拖动其手柄栏手动调整 rebar。 此外可以向所选的位图设置 rebar 对象的背景。

Rebar 对象的行为类似于工具栏对象。 Rebar 控件可以包含一个或多个带区，并且每个带区可以包含一个手柄栏、 位图、 文本标签和子窗口。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCReBar` 类中的各种方法。 该示例演示如何创建 rebar 控件并向其添加带区。 带区充当内部工具栏。 此代码片段属于[Rebar 测试示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>要求

**标头：** afxRebar.h

##  <a name="addbar"></a>  CMFCReBar::AddBar

向 rebar 带区。

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>参数

*pBar*<br/>
[in、 out]指向要插入到 rebar 的子窗口的指针。 引用的对象必须具有**WS_CHILD**窗口样式。

*pszText*<br/>
[in]指定在 rebar 中显示的文本。 文本不是子窗口的一部分。 相反，它被显示在 rebar 本身。

*pbmp*<br/>
[in、 out]指定要在 rebar 背景上显示的位图。

*dwStyle*<br/>
[in]包含要应用于带区的样式。 带样式的完整列表，请参阅的说明`fStyle`中[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) Windows SDK 文档中的结构。

*clrFore*<br/>
[in]表示 rebar 的前景色。

*clrBack*<br/>
[in]表示 rebar 的背景色。

### <a name="return-value"></a>返回值

如果带区已成功添加到 rebar; 则为 TRUE否则为 FALSE。

##  <a name="create"></a>  CMFCReBar::Create

创建 rebar 控件，并将其附加到[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)对象。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in、 out]指向此 rebar 控件的父窗口的指针。

*dwCtrlStyle*<br/>
[in]指定对 rebar 控件的样式。 默认样式值是**RBS_BANDBORDERS**，它显示缩小范围行来分隔相邻带，可在 rebar 控件。 有关有效的样式的列表，请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK 文档中。

*dwStyle*<br/>
[in]Rebar 控件的窗口样式。 有关有效的样式的列表，请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
[in]Rebar 的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则创建 rebar，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl

提供直接访问权限`CReBarCtrl`为基础的常见控件`CMFCReBar`对象。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>返回值

对基础引用`CReBarCtrl`对象。

### <a name="remarks"></a>备注

调用此方法以自定义你 rebar 时充分利用 Windows rebar 常用控制功能。

##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canfloat"></a>  CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

[in] *dwDockStyle*<br/>

### <a name="remarks"></a>备注

##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>参数

[in]*CPoint*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>参数

[in] *point*<br/>
[in] *pTI*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

[in] *pTarget*<br/>
[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>备注

##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>参数

[in] *dwAlignment*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl 类](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane 类](../../mfc/reference/cpane-class.md)
