---
title: CStatusBar 类
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 0549ee10faa15b80b18a0bee2f115425002e1479
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376263"
---
# <a name="cstatusbar-class"></a>CStatusBar 类

含有文本输出窗格或“指示符”的控件条。

## <a name="syntax"></a>语法

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C状态栏：CStatusbar](#cstatusbar)|构造 `CStatusBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStatusbar：：命令索引](#commandtoindex)|获取给定指标 ID 的索引。|
|[C状态栏：创建](#create)|创建状态栏，将其附加到对象，`CStatusBar`并设置初始字体和条形高度。|
|[C状态栏：：创建Ex](#createex)|为`CStatusBar`嵌入`CStatusBarCtrl`对象创建具有其他样式的对象。|
|[CStatusBar：:D原始项目](#drawitem)|当所有者绘制状态栏控件的可视方面发生更改时调用。|
|[CStatusBar：获取项目ID](#getitemid)|获取给定索引的指标 ID。|
|[CStatusBar：获取项目已重新完成](#getitemrect)|获取给定索引的显示矩形。|
|[CStatusBar：获取窗格信息](#getpaneinfo)|获取给定索引的指示器 ID、样式和宽度。|
|[C状态栏：：获取窗格样式](#getpanestyle)|获取给定索引的指示器样式。|
|[C状态栏：：获取窗格文本](#getpanetext)|获取给定索引的指示器文本。|
|[CStatusBar：获取状态栏](#getstatusbarctrl)|允许直接访问基础公共控件。|
|[C状态栏：设置指标](#setindicators)|设置指示器指示符。|
|[C状态栏：：设置窗格信息](#setpaneinfo)|设置给定索引的指示器 ID、样式和宽度。|
|[C状态栏：：设置窗格样式](#setpanestyle)|设置给定索引的指示器样式。|
|[C状态栏：：设置窗格文本](#setpanetext)|设置给定索引的指示器文本。|

## <a name="remarks"></a>备注

输出窗格通常用作消息行和状态指示器。 示例包括简要解释所选菜单命令的菜单帮助消息行以及显示 SCROLL LOCK、NUM LOCK 和其他键状态的指示器。

[CStatusBar：GetStatusBarCtrl](#getstatusbarctrl)是 MFC 4.0 中新成员函数，允许您利用 Windows 通用控件对状态栏自定义和其他功能的支持。 `CStatusBar`成员函数为您提供 Windows 公共控件的大部分功能;但是，当您调用`GetStatusBarCtrl`时，您可以为状态栏提供更多 Windows 95/98 状态栏的特征。 调用`GetStatusBarCtrl`时，它将返回对`CStatusBarCtrl`对象的引用。 有关使用 Windows 常见控件设计工具栏的详细信息，请参阅[CStatusBarCtrl。](../../mfc/reference/cstatusbarctrl-class.md) 有关常见控件的更多一般信息，请参阅 Windows SDK 中[的常见控件](/windows/win32/Controls/common-controls-intro)。

框架将指标信息存储在数组中，其中最左侧的指示器位于位置 0。 创建状态栏时，将使用框架与相应指标关联字符串指示数组。 然后，可以使用字符串 ID 或索引访问指标。

默认情况下，第一个指标是"弹性的"：它占用其他指标窗格不使用的状态栏长度，以便其他窗格右对齐。

要创建状态栏，请按照以下步骤操作：

1. 构造 `CStatusBar` 对象。

1. 调用["创建](#create)"（或[CreateEx](#createex)） 函数以创建状态栏窗口并将其附加到`CStatusBar`对象。

1. 调用[SetIndicators](#setindicators)将字符串 ID 与每个指标相关联。

有三种方法可以更新状态栏窗格中的文本：

1. 调用[CWnd：：设置窗口文本](../../mfc/reference/cwnd-class.md#setwindowtext)以仅更新窗格 0 中的文本。

1. 调用[CCmdUI：在](../../mfc/reference/ccmdui-class.md#settext)状态栏的ON_UPDATE_COMMAND_UI处理程序中设置文本。

1. 调用[SetPaneText](#setpanetext)更新任何窗格的文本。

调用[SetPaneStyle](#setpanestyle)以更新状态栏窗格的样式。

有关使用`CStatusBar`的详细信息，请参阅 MFC[和技术说明 31 中的](../../mfc/tn031-control-bars.md)[状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)文章：控制栏 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制栏](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusbar：：命令索引

获取给定 ID 的指标索引。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

*nIDFind*<br/>
要检索其索引的指标的字符串 ID。

### <a name="return-value"></a>返回值

指标的指数（如果成功）;-1 如果不成功。

### <a name="remarks"></a>备注

第一个指标的索引为 0。

## <a name="cstatusbarcreate"></a><a name="create"></a>C状态栏：创建

创建状态栏（子窗口），并将其与`CStatusBar`对象关联。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向其 Windows 窗口是状态栏的父级的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

*dwStyle*<br/>
状态栏样式。 除了标准 Windows[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)之外，还支持这些样式。

- CBRS_TOP控制栏位于框架窗口的顶部。

- CBRS_BOTTOM控制栏位于框架窗口的底部。

- CBRS_NOALIGN调整父控件栏的大小时，不会重新定位。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此外，还可以设置初始字体并将状态栏的高度设置为默认值。

## <a name="cstatusbarcreateex"></a><a name="createex"></a>C状态栏：：创建Ex

调用此函数以创建状态栏（子窗口），并将其与`CStatusBar`对象关联。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向其 Windows 窗口是状态栏的父级的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

*dwCtrl风格*<br/>
用于创建嵌入式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象的其他样式。 默认值指定没有大小调整手柄或工具提示支持的状态栏。 支持的状态栏样式包括：

- SBARS_SIZEGRIP 状态栏控件包括状态栏右侧的尺寸调整夹。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。

- SBT_TOOLTIPS 状态栏支持工具提示。

有关这些样式的详细信息，请参阅[CStatusBarCtrl 的设置](../../mfc/settings-for-the-cstatusbarctrl.md)。

*dwStyle*<br/>
状态栏样式。 默认值指定在框架窗口底部创建可见状态栏。 应用["窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)"和["CDialog 栏："创建](../../mfc/reference/cdialogbar-class.md#create)"中列出的状态栏控件样式的任意组合。 但是，此参数应始终包括WS_CHILD和WS_VISIBLE样式。

*nID*<br/>
状态栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此功能还设置初始字体，并将状态栏的高度设置为默认值。

在`CreateEx`创建嵌入状态栏控件期间需要存在某些样式时，请使用 而不是[Create。](#create) 例如，将*dwCtrlStyle*设置为SBT_TOOLTIPS以在状态栏对象中显示工具提示。

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>C状态栏：CStatusbar

构造`CStatusBar`对象，如有必要创建默认状态栏字体，并将字体特征设置为默认值。

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar：:D原始项目

当所有者绘制的状态栏的可视方面发生更改时，框架将调用此成员函数。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。 重写此成员函数以实现所有者绘制对象的绘图`CStatusBar`。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar：获取项目ID

返回*nIndex*指定的指标的 ID。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其 ID 的指标的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的指标的 ID。

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar：获取项目已重新完成

将*nIndex*指定的指标的坐标复制到*lpRect*指向的结构中。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其矩形坐标的指标的索引。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，该对象将接收*nIndex*指定的指标的坐标。

### <a name="remarks"></a>备注

坐标相对于状态栏的左上角以像素为单位。

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar：获取窗格信息

将*nID* *、nStyle*和*cxWidth*设置到*nIndex*指定位置的指示器窗格的 ID、样式和宽度。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其信息的窗格的索引。

*nID*<br/>
对设置为窗格 ID 的 UINT 的引用。

*nStyle*<br/>
对设置为窗格样式的 UINT 的引用。

*cxWidth*<br/>
引用设置为窗格宽度的整数。

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>C状态栏：：获取窗格样式

调用此成员函数以检索状态栏窗格的样式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其样式的窗格的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的状态栏窗格的样式。

### <a name="remarks"></a>备注

窗格的样式确定窗格的显示方式。

有关可用于状态栏的样式列表，请参阅[创建](#create)。

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>C状态栏：：获取窗格文本

调用此成员函数以检索显示在状态栏窗格中的文本。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其文本的窗格的索引。

*rString*<br/>
对包含要检索的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

包含`CString`窗格文本的对象。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用字符串文本填充`CString`对象。

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar：获取状态栏

此成员函数允许直接访问基础公共控件。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>返回值

包含对[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

用于`GetStatusBarCtrl`利用 Windows 状态栏通用控件的功能，并利用[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供的状态栏自定义的支持。 例如，通过使用公共控件，可以指定包含状态栏上大小调整的夹点的样式，也可以指定样式，使状态栏显示在父窗口工作区的顶部。

有关常见控件的更多一般信息，请参阅 Windows SDK 中的[常用控件](/windows/win32/Controls/common-controls-intro)。

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>C状态栏：设置指标

将每个指标的 ID 设置到数组*lpIDArray*的相应元素指定的值，加载每个 ID 指定的字符串资源，并将指标的文本设置到字符串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

*lpIDArray*<br/>
指向指示的 I 数组。

*nIDCount*<br/>
*lpIDArray*指向的数组中的元素数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>C状态栏：：设置窗格信息

将指定的指示器窗格设置为新 ID、样式和宽度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其样式的指标窗格的索引。

*nID*<br/>
指示器窗格的新 ID。

*nStyle*<br/>
指示器窗格的新样式。

*cxWidth*<br/>
指示器窗格的新宽度。

### <a name="remarks"></a>备注

支持以下指标样式：

- SBPS_NOBORDERS窗格周围没有三维边框。

- SBPS_POPOUT反向边框，以便文本"弹出"。

- SBPS_DISABLED不要画文本。

- SBPS_STRETCH拉伸窗格以填充未使用的空间。 每个状态栏只能有一个窗格具有此样式。

- SBPS_NORMAL 无拉伸、边框或弹出。

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>C状态栏：：设置窗格样式

调用此成员函数以设置状态栏窗格的样式。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其样式的窗格的索引。

*nStyle*<br/>
要设置其样式的窗格的样式。

### <a name="remarks"></a>备注

窗格的样式确定窗格的显示方式。

有关状态栏可用的样式列表，请参阅[SetPaneInfo](#setpaneinfo)。

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>C状态栏：：设置窗格文本

调用此成员函数将窗格文本设置为*lpszNewText*指向的字符串。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其文本的窗格的索引。

*lpsz 新文本*<br/>
指向新窗格文本的指针。

*b更新*<br/>
如果为 TRUE，则设置文本后窗格将失效。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

调用`SetPaneText`后，必须添加 UI 更新处理程序才能在状态栏中显示新文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 类](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
