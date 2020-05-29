---
title: CTabbedPane 类
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365950"
---
# <a name="ctabbedpane-class"></a>CTabbedPane 类

利用可拆分的选项卡实现窗格的功能。

或更多的详细信息，请参阅位于 Visual Studio 安装的**\\VC\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|（覆盖[CBaseTabbedPane：:DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).）|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|启用或禁用自动选项卡着色。|
|[CTabbedPane::FloatTab](#floattab)|浮动窗格，但前提是窗格当前驻留在可拆卸选项卡中。（覆盖[CBaseTabbedPane：：FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).|
|[CTabbed窗格：：获取塔布区域](#gettabarea)|返回选项卡区域在选项卡式窗口中的大小和位置。|
|[CTabbedPane：：GetTabwnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|确定选项卡式窗格是否可以切换为自动隐藏模式。 （覆盖[CBaseTabbed 窗格：：具有 AutoHideMode.）](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|确定选项卡是否位于窗口的底部。|
|[CTabbedPane::ResetTabs](#resettabs)|将所有选项卡式窗格重置为默认状态。|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|设置可以在自动颜色功能启用时可用的自定义颜色列表。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|选项卡在应用程序中的的默认位置。|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|自定义 `CMFCTabCtrl`-派生对象的运行时类信息。|

## <a name="remarks"></a>备注

当用户通过将一个窗格指向第二个窗格的标题的方式来附加到另一个窗格，框架自动创建此类的实例。 由框架创建的所有选项卡式窗格都具有值为 -1 的 ID。

要指定常规选项卡而不是 Outlook 样式选项卡，请将AFX_CBRS_REGULAR_TABS样式传递给[CDockablePane：：CreateEx](../../mfc/reference/cdockablepane-class.md#createex)方法。

如果你使用可拆离的选项卡创建一个选项卡式窗格，该窗格可能会被框架自动销毁，因此，你不应该存储该指针。 若要获取对选项卡式窗格的指针，请调用 `CBasePane::GetParentTabbedPane` 方法。

## <a name="example"></a>示例

我们在此示例中创建了一个 `CTabbedPane` 对象。 接下来，我们使用[CBaseTabbedPane：：AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)附加其他选项卡。

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

## <a name="example"></a>示例

创建选项卡式控制栏对象的另一种方法是使用[可多克窗格：：AttachToTabwnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 该方法`AttachToTabWnd`使用 CDockablePane 设置的运行时类信息动态创建选项卡式窗格对象[：：SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)。

在此示例中，我们动态地创建了一个选项卡式窗格，附加这两个选项卡，并使第二个选项不可拆离。

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[可装窗格](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>要求

**标题：** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane：:D埃塔奇帕内

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

[在]*bHide*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbed 窗格：：启用 TabAutoColor

启用或禁用自动选项卡着色。

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 以启用选项卡的自动着色;否则，FALSE。

### <a name="remarks"></a>备注

使用此静态方法在应用程序中的所有选项卡窗格中启用或禁用选项卡的自动着色。 启用此功能后，每个选项卡都由其自己的颜色填充。 您可以通过调用[CMFCBaseTabCtrl：：getAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)方法找到用于为选项卡着色的颜色列表。

您可以通过调用[CTabbedPane：：setTabAutoColors](#settabautocolors)来指定将用于选项卡的颜色列表。

默认情况下禁用此选项。

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbed窗格：：浮动选项卡

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>
[在]*nTabID*<br/>
[在]*基方法*<br/>
[在]*bHide*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbed窗格：：获取塔布区域

在选项卡式窗口中返回选项卡区域的大小和位置。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>参数

*rectTabAreaTop*<br/>
[出]包含顶部选项卡区域的大小和位置（屏幕坐标）。

*rectTab区域底部*<br/>
[出]包含底部选项卡区域的大小和位置（屏幕坐标）。

### <a name="remarks"></a>备注

框架调用此方法以确定如何停靠用户拖动的窗格。 当用户将窗格拖动到目标窗格的选项卡区域时，框架会尝试将其添加为目标窗格的新选项卡。 否则，它将尝试将窗格停靠到目标窗格的一侧，这涉及使用分隔两个窗格的窗格分隔器创建新窗格容器。

重写`CTabbedPane`派生类中的此方法以更改此行为。

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane：：GetTabwnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbed窗格：：具有自动隐藏模式

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbed 窗格：：位置位置底部

确定选项卡是否位于窗口的底部。

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>返回值

如果选项卡区域位于选项卡式窗口的底部，则为 TRUE;如果选项卡区域位于选项卡式窗口的底部，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbed窗格：：m_bTabsAlwaysTop

选项卡在应用程序中的的默认位置。

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>备注

将此静态成员设置为 TRUE 以强制应用程序中的所有选项卡显示在选项卡式窗格的顶部。

必须在创建选项卡式窗格之前设置此值。

默认值是 FALSE。

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane：：m_pTabWndRTC

自定义 `CMFCTabCtrl`-派生对象的运行时类信息。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>备注

如果要在选项卡式窗格中使用自定义选项卡式窗口，则将此静态成员`CMFCTabCtrl`变量设置为指向派生对象的运行时类信息的指针。

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbed窗格：：重置选项卡

将所有选项卡式窗格重置为默认状态。

```
static void ResetTabs();
```

### <a name="remarks"></a>备注

调用此方法将所有选项卡式窗格还原到其默认状态。 调用时，此方法将重置所有选项卡式窗格的边框大小和自动颜色状态。

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbed 窗格：：设置 TabAuto 颜色

设置启用自动颜色功能时使用的自定义颜色的列表。

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>参数

*阿尔颜色*<br/>
[在]包含要设置的颜色数组。

### <a name="remarks"></a>备注

使用此方法可以自定义启用自动颜色功能时使用的颜色列表。 这是一个静态函数，会影响应用程序中的所有选项卡式窗格。

使用[CTabbed 窗格：启用 TabAutoColor](#enabletabautocolor)以启用或禁用自动颜色功能。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)
