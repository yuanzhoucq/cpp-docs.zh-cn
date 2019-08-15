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
ms.openlocfilehash: 434232e8f99bf914b00379db53d4b4a37d24fe36
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502786"
---
# <a name="crebar-class"></a>CReBar 类

提供 Rebar 控件的布局、持久性和状态信息的控件条。

## <a name="syntax"></a>语法

```
class CReBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|向 rebar 添加带区。|
|[CReBar::Create](#create)|创建 rebar 控件并将其附加到`CReBar`对象。|
|[CReBar::GetReBarCtrl](#getrebarctrl)|允许直接访问基础公共控件。|

## <a name="remarks"></a>备注

Rebar 对象可以包含各种子窗口，通常为其他控件，包括编辑框、工具栏和列表框。 Rebar 对象可以在指定位图上显示其子窗口。 您的应用程序可以自动调整 rebar 的大小, 或者用户可以通过单击或拖动其手柄栏来手动调整 rebar 大小。

![RebarMenu 的示例](../../mfc/reference/media/vc4sc61.gif "RebarMenu 的示例")

## <a name="rebar-control"></a>Rebar 控件

Rebar 对象的行为类似于工具栏对象。 Rebar 使用单击并拖动机制调整其带区的大小。 Rebar 控件可以包含一个或多个带区，每个带区都有手柄栏、位图、文本标签和子窗口的任意组合。 但是，带区不可包含多个子窗口。

`CReBar`使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)类提供其实现。 可以通过[GetReBarCtrl](#getrebarctrl)访问 rebar 控件以利用控件的自定义选项。 有关 rebar 控件的详细信息, 请`CReBarCtrl`参阅。 有关使用 rebar 控件的详细信息, 请参阅[Using CReBarCtrl](../../mfc/using-crebarctrl.md)。

> [!CAUTION]
>  Rebar 和 rebar 控件对象不支持 MFC 控件条停靠。 如果`CRebar::EnableDocking`调用, 则应用程序将断言。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>要求

**标头:** afxext。h

##  <a name="addbar"></a>CReBar:: AddBar

调用此成员函数以向 rebar 添加带区。

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
指向`CWnd`对象的指针, 该对象是要插入到 rebar 中的子窗口。 引用的对象必须具有 WS_CHILD。

*lpszText*<br/>
指向字符串的指针, 该字符串包含要在 rebar 上显示的文本。 默认值为 NULL。 *LpszText*中包含的文本不是子窗口的一部分;它在 rebar 本身。

*pbmp*<br/>
一个指针, `CBitmap`指向要在 rebar 背景上显示的对象。 默认值为 NULL。

*dwStyle*<br/>
包含要应用于 rebar 的样式的 DWORD。 有关带`fStyle`区样式的完整列表, 请参阅 Win32 结构[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)中的函数说明。

*clrFore*<br/>
一个 COLORREF 值, 该值表示 rebar 的前景色。

*clrBack*<br/>
一个 COLORREF 值, 该值表示 rebar 的背景色。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>CReBar:: Create

调用此成员函数以创建 rebar。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
一个指针, `CWnd`指向其 Windows 窗口是状态栏的父对象的对象。 通常是框架窗口。

*dwCtrlStyle*<br/>
Rebar 控件样式。 默认情况下, RBS_BANDBORDERS 显示用于分隔 rebar 控件内相邻带区的窄线条。 有关样式列表, 请参阅 Windows SDK 中的[Rebar 控件样式](/windows/win32/Controls/rebar-control-styles)。

*dwStyle*<br/>
Rebar 窗口样式。

*nID*<br/>
Rebar 的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CReBar:: AddBar](#addbar)的示例。

##  <a name="getrebarctrl"></a>CReBar:: GetReBarCtrl

此成员函数允许直接访问基础公共控件。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>返回值

对[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

调用此成员函数以利用自定义 rebar 中 Windows rebar 公共控件的功能。 当你调用`GetReBarCtrl`时, 它将`CReBarCtrl`向对象返回一个引用对象, 以便你可以使用任一组成员函数。

有关使用`CReBarCtrl`自定义 rebar 的详细信息, 请参阅[using CReBarCtrl](../../mfc/using-crebarctrl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
