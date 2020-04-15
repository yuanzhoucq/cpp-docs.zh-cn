---
title: CReBar 类
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363930"
---
# <a name="crebar-class"></a>CReBar 类

提供 Rebar 控件的布局、持久性和状态信息的控件条。

## <a name="syntax"></a>语法

```
class CReBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CReBar：添加条](#addbar)|将带添加到钢筋。|
|[CReBar：创建](#create)|创建钢筋控件并将其附加到`CReBar`对象。|
|[CReBar：：获取 RebarCtrl](#getrebarctrl)|允许直接访问基础公共控件。|

## <a name="remarks"></a>备注

Rebar 对象可以包含各种子窗口，通常为其他控件，包括编辑框、工具栏和列表框。 Rebar 对象可以在指定位图上显示其子窗口。 应用程序可以自动调整钢筋的大小，或者用户可以通过单击或拖动其夹持栏手动调整钢筋的大小。

![RebarMenu 示例](../../mfc/reference/media/vc4sc61.gif "RebarMenu 示例")

## <a name="rebar-control"></a>钢筋控制

钢筋对象的行为与工具栏对象类似。 钢筋使用单击和拖动机制调整其波段的大小。 Rebar 控件可以包含一个或多个带区，每个带区都有手柄栏、位图、文本标签和子窗口的任意组合。 但是，带区不可包含多个子窗口。

`CReBar`使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)类来提供其实现。 您可以通过[GetReBarCtrl](#getrebarctrl)访问钢筋控件，以利用控件的自定义选项。 有关钢筋控件的详细信息，请参阅`CReBarCtrl`。 有关使用钢筋控件的详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

> [!CAUTION]
> 钢筋和钢筋控制对象不支持 MFC 控制条停靠。 如果`CRebar::EnableDocking`调用，您的应用程序将断言。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制栏](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar：添加条

调用此成员函数以向钢筋添加带。

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
指向要插入钢筋`CWnd`的子窗口的对象的指针。 引用的对象必须具有WS_CHILD。

*lpszText*<br/>
指向要显示在钢筋上的文本的字符串的指针。 默认情况下为 NULL。 *lpszText*中包含的文本不是子窗口的一部分;因此，该文本中的文本不是子窗口的一部分。它在钢筋本身。

*pbmp*<br/>
指向要显示在钢筋`CBitmap`背景上的对象的指针。 默认情况下为 NULL。

*dwStyle*<br/>
包含要应用于钢筋的样式的 DWORD。 有关波段`fStyle`样式的完整列表，请参阅 Win32 结构[REBARBANDINFO 中的](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)函数说明。

*clrFore*<br/>
表示钢筋前景颜色的 COLORREF 值。

*clrBack*<br/>
表示钢筋背景颜色的 COLORREF 值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar：创建

调用此成员函数以创建钢筋。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向其`CWnd`Windows 窗口是状态栏的父级的对象的指针。 通常，您的框架窗口。

*dwCtrl风格*<br/>
钢筋控制样式。 默认情况下，RBS_BANDBORDERS，它显示窄线以分隔钢筋控件中的相邻波段。 有关样式列表，请参阅 Windows SDK 中的[钢筋控制样式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
钢筋窗口样式。

*nID*<br/>
钢筋的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CReBar：：addBar](#addbar)的示例。

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CReBar：：获取 RebarCtrl

此成员函数允许直接访问基础公共控件。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>返回值

对[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

调用此成员函数以利用 Windows 钢筋通用控件在自定义钢筋时的功能。 调用`GetReBarCtrl`时，它将引用对象返回到该对象`CReBarCtrl`，以便可以使用任一组成员函数。

有关使用自定义`CReBarCtrl`钢筋的详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
