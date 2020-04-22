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
ms.openlocfilehash: 409c97aba64c97ecf0443d14a70848cc298a44ba
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749997"
---
# <a name="cmfcrebar-class"></a>CMFCReBar 类

对象`CMFCReBar`是一个控件栏，它为钢筋控件提供布局、持久性和状态信息。
有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCReBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCReBar：addBar](#addbar)|将带添加到钢筋。|
|[CMFCReBar：：钙固定布局](#calcfixedlayout)|（覆盖[CBasePane：：CalcFixed 布局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).）|
|[CMFCReBar：可以浮动](#canfloat)|（覆盖[CBasePane：：可以浮动](../../mfc/reference/cbasepane-class.md#canfloat). ）|
|[CMFCReBar：创建](#create)|创建钢筋控件并将其附加到`CMFCReBar`对象。|
|[CMFCReBar：启用停靠](#enabledocking)|（覆盖[CBasePane：启用停靠](../../mfc/reference/cbasepane-class.md#enabledocking).）|
|[CMFCReBar：获取雷巴班德信息大小](#getrebarbandinfosize)||
|[CMFCReBar：GetReBarCtrl](#getrebarctrl)|提供对基础[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)公共控件的直接访问。|
|[CMFCReBar：在显示控制栏菜单](#onshowcontrolbarmenu)|（覆盖[CPane：在显示控制栏菜单](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).）|
|[CMFCRebar：：在工具命中测试](#ontoolhittest)|（覆盖[Cwnd：onToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)）|
|[CMFCReBar：关于更新CmdUI](#onupdatecmdui)|（覆盖[CBasePane：：更新 CmdUI](cbasepane-class.md).）|
|[CMFCReBar：：设置窗格对齐](#setpanealignment)|（覆盖[CBasePane：设置窗格对齐](../../mfc/reference/cbasepane-class.md#setpanealignment).）|

## <a name="remarks"></a>备注

对象`CMFCReBar`可以包含各种子窗口。 这包括编辑框、工具栏和列表框。 您可以以编程方式调整钢筋的大小，或者用户可以通过拖动钢筋来手动调整钢筋的大小。 您还可以将钢筋对象的背景设置为您选择的位图。

钢筋对象的行为与工具栏对象类似。 钢筋控件可以包含一个或多个波段，每个波段可以包含夹持条、位图、文本标签和子窗口。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCReBar` 类中的各种方法。 该示例演示如何创建钢筋控件并将其添加带。 波段用作内部工具栏。 此代码段是[钢筋测试示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目标](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>要求

**标题：** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar：addBar

将带添加到钢筋。

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
[进出]指向要插入钢筋的子窗口的指针。 引用的对象必须具有**WS_CHILD**窗口样式。

*pszText*<br/>
[在]指定要显示在钢筋上的文本。 文本不是子窗口的一部分。 相反，它显示在钢筋本身。

*pbmp*<br/>
[进出]指定要显示在钢筋背景上的位图。

*dwStyle*<br/>
[在]包含要应用于波段的样式。 有关波段样式的完整列表，请参阅 Windows SDK`fStyle`文档中[的 REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构中的说明。

*clrFore*<br/>
[在]表示钢筋的前景颜色。

*clrBack*<br/>
[在]表示钢筋的背景颜色。

### <a name="return-value"></a>返回值

如果频带已成功添加到钢筋中，则为 TRUE;否则，FALSE。

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar：创建

创建钢筋控件并将其附加到[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)对象。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[进出]指向此钢筋控件的父窗口的指针。

*dwCtrl风格*<br/>
[在]指定钢筋控件的样式。 默认样式值为**RBS_BANDBORDERS**，它显示窄线以分隔钢筋控件上的相邻波段。 有关有效样式的列表，请参阅 Windows SDK 文档中的[钢筋控制样式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
[在]钢筋控件的窗口样式。 有关有效样式的列表，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
[在]钢筋的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功创建钢筋，则为 TRUE;如果钢筋已成功创建，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar：GetReBarCtrl

提供对`CReBarCtrl`对象基础公共控件的直接`CMFCReBar`访问。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>返回值

对基础`CReBarCtrl`对象的引用。

### <a name="remarks"></a>备注

调用此方法以在自定义钢筋时利用 Windows 钢筋通用控制功能。

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar：：钙固定布局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[在]*b 拉伸*<br/>
[在]*布霍兹*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar：可以浮动

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar：启用停靠

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>参数

[在]*dwDock风格*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar：获取雷巴班德信息大小

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar：在显示控制栏菜单

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>参数

[在]*CPoint*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCRebar：：在工具命中测试

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>参数

[在]*点*<br/>
[在]*pTI*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar：关于更新CmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

[在]*p目标*<br/>
[在]*b 禁用IfNoHndler*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar：：设置窗格对齐

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>参数

[在]*dwalignment*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl 类](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
