---
title: CAutoHideDockSite 类
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 1f23729ced02a151c6186bdcc72cb8938416be46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752997"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 类

扩展`CAutoHideDockSite` [CDockSite 类](../../mfc/reference/cdocksite-class.md)以实现自动隐藏停靠窗格。

## <a name="syntax"></a>语法

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CAutoHideDockSite::CAutoHideDockSite`|构造 `CAutoHideDockSite` 对象。|
|`CAutoHideDockSite::~CAutoHideDockSite`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指示 是否`CAutoHideDockSite`显示在窗格菜单上。|
|[CAutoHideDock网站：：接受窗格](#canacceptpane)|确定基本窗格对象是否派生自[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)。|
|[CAutoHideDock网站：:DockPane](#dockpane)|将窗格停靠到此`CAuotHideDockSite`对象。|
|[CAutoHideDock网站：：获得对齐](#getalignrect)|在屏幕坐标中检索停靠站点的大小。|
|[CAutoHideDock网站：重新定位窗格](#repositionpanes)|`CAutoHideDockSite`使用全局边距和按钮间距重绘 上的窗格。|
|[CAutoHideDock网站：：设置偏移左](#setoffsetleft)|设置停靠栏左侧的边距。|
|[CAutoHideDock网站：：设置偏移权](#setoffsetright)|设置停靠栏右侧的边距。|
|[CAutoHideDock网站：：取消设置自动隐藏模式](#unsetautohidemode)|调用[CMFCAutoHideBar：：取消设置 AutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上`CAutoHideDockSite`的对象。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|说明|
|[CAutoHideDock网站：m_nExtraSpace](#m_nextraspace)|定义工具栏和停靠栏边缘之间的空间大小。 此空间从左边缘或上边缘测量，具体取决于停靠空间的对齐方式。|

## <a name="remarks"></a>备注

当您调用[CFrameWndEx：：启用自动隐藏窗格时](../../mfc/reference/cframewndex-class.md#enableautohidepanes)，框架会自动创建一个`CAutoHideDockSite`对象。 在大多数情况下，您不必直接实例化或使用此类。

停靠栏是停靠窗格左侧和[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)左侧之间的间隙。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>示例

下面的示例演示如何从`CAutoHideDockSite``CMFCAutoHideBar`对象检索对象，以及如何设置停靠栏的左右边距。

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDock网站：：接受窗格

确定基本窗格是[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象还是派生自`CMFCAutoHideBar`。

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pBar*|[在]框架测试的基本窗格。|

### <a name="return-value"></a>返回值

如果*pBar*派生自`CMFCAutoHideBar`，则为 TRUE。否则。

### <a name="remarks"></a>备注

如果基础窗格对象派生自`CMFCAutoHideBar`，它可以包含 。 `CAutoHideDockSite`

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDock网站：:DockPane

将窗格停靠到此[CAutoHideDockSite 对象](../../mfc/reference/cautohidedocksite-class.md)。

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pwnd*|[在]框架停靠的窗格。|
|*基方法*|[在]窗格的停靠选项。|
|*lpRect*|[在]指定停靠窗格边界的矩形。|

### <a name="remarks"></a>备注

默认实现不使用参数*dockMethod，* 这是为将来使用而提供的。

如果*lpRect*为 NULL，则框架将窗格置于停靠站点上的默认位置。 如果停靠站点是水平的，则默认位置位于停靠站点的最左侧。 否则，默认位置位于停靠站点的顶部。

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDock网站：：获得对齐

在屏幕坐标中检索停靠站点的大小。

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*矩形*|[在]对矩形的引用。 该方法在此矩形中存储停靠站点的大小。|

### <a name="remarks"></a>备注

矩形会针对偏移边距进行调整，以便不包含它们。

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDock网站：m_nExtraSpace

[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)对象边缘之间的空间大小。

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>备注

`CMFCAutoHideBar`当 停靠在 时`CAutoHideDockSite`，它不应占用整个停靠站点。 此全局变量控制 的`CMFCAutoHideBar`左侧或顶部边框与相应`CAutoHideDockSite`边之间的额外空间。 使用上边缘还是左边缘取决于当前对齐方式。

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDock网站：：设置偏移左

设置停靠栏左侧的边距。

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>参数

*n偏移*<br/>
[在]新的偏移量。

### <a name="remarks"></a>备注

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象以静态方式放置在`CAutoHideDockSite`对象上。 这意味着用户无法手动更改`CMFCAutoHideBar`对象的位置。 该方法`SetOffsetLeft`控制 左侧`CMFCAutoHideBar`和 左侧之间的间距`CAutoHideDockSite`。

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDock网站：：设置偏移权

设置停靠栏右侧的边距。

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>参数

*n偏移*<br/>
[在]新的偏移量。

### <a name="remarks"></a>备注

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象以静态方式放置在`CAutoHideDockSite`对象上。 这意味着用户无法手动更改`CMFCAutoHideBar`对象的位置。 该方法`SetOffsetRight`控制 右侧`CMFCAutoHideBar`和 右侧之间的间距`CAutoHideDockSite`。

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDock网站：重新定位窗格

重绘[CAutoHideDockSite 上的](../../mfc/reference/cautohidedocksite-class.md)窗格。

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*rectNewClient区域*|[在]保留值。|

### <a name="remarks"></a>备注

默认实现不使用*rectNewClientArea*。 它使用全局工具栏边距和按钮间距重绘窗格。

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDock网站：：取消设置自动隐藏模式

调用[CMFCAutoHideBar：：取消设置停靠站点上的对象的自动隐藏模式](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)。

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pAutoHideToolbar*|[在]指向 位于 上的[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象窗格`CAutoHideDockSite`的指针。|

### <a name="remarks"></a>备注

此方法搜索包含*pAutoHideToolbar*的行。 它调用`CMFCAutoHideBar.UnSetAutoHideMode`该行上`CMFCAutoHideBar`的所有对象。 如果未找到*pAutoHideToolbar*或它是 NULL，则此方法将`CMFCAutoHideBar.UnSetAutoHideMode`调用 上`CMFCAutoHideBar``CAutoHideDockSite`的所有对象。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)
