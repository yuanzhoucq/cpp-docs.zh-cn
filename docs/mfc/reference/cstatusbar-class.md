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
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502338"
---
# <a name="cstatusbar-class"></a>CStatusBar 类

含有文本输出窗格或“指示符”的控件条。

## <a name="syntax"></a>语法

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|构造 `CStatusBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|获取给定指示器 ID 的索引。|
|[CStatusBar::Create](#create)|创建状态栏, 将其附加到`CStatusBar`对象, 并设置初始字体和栏高度。|
|[CStatusBar::CreateEx](#createex)|使用嵌入`CStatusBarCtrl`对象的其他样式创建对象。`CStatusBar`|
|[CStatusBar::DrawItem](#drawitem)|当所有者描述的状态栏控件的可视方位更改时调用。|
|[CStatusBar::GetItemID](#getitemid)|获取给定索引的指示器 ID。|
|[CStatusBar::GetItemRect](#getitemrect)|获取给定索引的显示矩形。|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|获取给定索引的指示器 ID、样式和宽度。|
|[CStatusBar::GetPaneStyle](#getpanestyle)|获取给定索引的指示器样式。|
|[CStatusBar::GetPaneText](#getpanetext)|获取给定索引的指示器文本。|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允许直接访问基础公共控件。|
|[CStatusBar::SetIndicators](#setindicators)|设置指示器 Id。|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|设置给定索引的指示器 ID、样式和宽度。|
|[CStatusBar::SetPaneStyle](#setpanestyle)|设置给定索引的指示器样式。|
|[CStatusBar::SetPaneText](#setpanetext)|设置给定索引的指示器文本。|

## <a name="remarks"></a>备注

输出窗格通常用作消息行和状态指示器。 示例包括菜单帮助-消息行, 其中简要说明了所选菜单命令以及显示滚动锁定状态、NUM LOCK 和其他键的指示器。

使用[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)(MFC 4.0 的一种新成员函数), 可以利用 Windows 公共控件对状态栏自定义和其他功能的支持。 `CStatusBar`成员函数为你带来了 Windows 公共控件的大多数功能;但是, 当你调用`GetStatusBarCtrl`时, 你可以为你的状态栏指定 Windows 95/98 状态栏的更多特性。 调用`GetStatusBarCtrl`时, 它将返回`CStatusBarCtrl`对对象的引用。 有关使用 Windows 公共控件设计工具栏的详细信息, 请参阅[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 。 有关公共控件的更多常规信息, 请参阅 Windows SDK 中的[公共控件](/windows/win32/Controls/common-controls-intro)。

框架将指示器信息存储在一个数组中, 其最左侧的指示器位于位置0。 当您创建状态栏时, 将使用一个字符串 Id 数组, 该数组与相应的指示器关联。 然后, 可以使用字符串 ID 或索引访问指示器。

默认情况下, 第一个指示器是 "弹性": 它占用其他指示器窗格未使用的状态栏长度, 使其他窗格右对齐。

若要创建状态栏, 请执行以下步骤:

1. 构造 `CStatusBar` 对象。

1. 调用[create](#create) (或[CreateEx](#createex)) 函数以创建状态栏窗口, 并将`CStatusBar`其附加到对象。

1. 调用[SetIndicators](#setindicators)可将字符串 ID 与每个指示器关联。

有三种方法可更新状态栏窗格中的文本:

1. 调用[CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)仅更新窗格0中的文本。

1. 在状态栏的 ON_UPDATE_COMMAND_UI 处理程序中调用[CCmdUI:: SetText](../../mfc/reference/ccmdui-class.md#settext) 。

1. 调用[SetPaneText](#setpanetext)可更新任何窗格的文本。

调用[SetPaneStyle](#setpanestyle) , 以更新状态栏窗格的样式。

有关使用`CStatusBar`的详细信息, 请参阅[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[技术说明 31:控件条](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>要求

**标头:** afxext。h

##  <a name="commandtoindex"></a>CStatusBar:: CommandToIndex

获取给定 ID 的指示器索引。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

*nIDFind*<br/>
要检索其索引的指示器的字符串 ID。

### <a name="return-value"></a>返回值

如果成功, 则为指示器的索引;如果不成功, 则为-1。

### <a name="remarks"></a>备注

第一个指示器的索引为0。

##  <a name="create"></a>CStatusBar:: Create

创建状态栏 (子窗口) 并将其与`CStatusBar`对象关联。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针, 该对象的 Windows 窗口是状态栏的父对象。

*dwStyle*<br/>
状态栏样式。 除了标准 Windows[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)以外, 还支持这些样式。

- CBRS_TOP 控件条位于框架窗口的顶部。

- CBRS_BOTTOM 控件条位于框架窗口的底部。

- 调整父级大小时, 不会重新定位 CBRS_NOALIGN 控件条。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

还设置初始字体并将状态栏的高度设置为默认值。

##  <a name="createex"></a>CStatusBar:: CreateEx

调用此函数可创建状态栏 (子窗口), 并将其与`CStatusBar`对象关联。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针, 该对象的 Windows 窗口是状态栏的父对象。

*dwCtrlStyle*<br/>
用于创建嵌入[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象的其他样式。 默认情况下, 在没有大小调整手柄或 tooltip 支持的情况下指定状态栏。 支持的状态栏样式为:

- SBARS_SIZEGRIP 状态栏控件在状态栏的右端包含一个大小调整手柄。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。

- SBT_TOOLTIPS 状态栏支持工具提示。

有关这些样式的详细信息, 请参阅[CStatusBarCtrl 的设置](../../mfc/settings-for-the-cstatusbarctrl.md)。

*dwStyle*<br/>
状态栏样式。 默认值指定在框架窗口底部创建可见状态栏。 应用[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create)中列出的状态栏控件样式的任意组合。 但是, 此参数应始终包含 WS_CHILD 和 WS_VISIBLE 样式。

*nID*<br/>
状态栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数还设置初始字体, 并将状态栏的高度设置为默认值。

如果`CreateEx`在创建嵌入的状态栏控件期间需要提供某些样式, 请使用, 而不是[创建](#create)。 例如, 将*dwCtrlStyle*设置为 SBT_TOOLTIPS, 以在状态栏对象中显示工具提示。

##  <a name="cstatusbar"></a>CStatusBar:: CStatusBar

构造一个`CStatusBar`对象, 根据需要创建默认的状态栏字体, 并将字体特征设置为默认值。

```
CStatusBar();
```

##  <a name="drawitem"></a>CStatusBar::D rawItem

当所有者描述的状态栏的视觉方面发生变化时, 框架会调用此成员函数。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针, 该结构包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构的成员定义要执行的绘图操作。 `itemAction` 重写此成员函数以实现所有者描述`CStatusBar`对象的绘制。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 (GDI) 对象。

##  <a name="getitemid"></a>CStatusBar:: GetItemID

返回由*nIndex*指定的指示器的 ID。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其 ID 的指示器的索引。

### <a name="return-value"></a>返回值

*NIndex*指定的指示器 ID。

##  <a name="getitemrect"></a>CStatusBar:: GetItemRect

将*nIndex*指定的指示器的坐标复制到*lpRect*指向的结构。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其矩形坐标的指示器的索引。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象, 该对象将接收由*nIndex*指定的指示器的坐标。

### <a name="remarks"></a>备注

坐标以像素为单位, 相对于状态栏的左上角。

##  <a name="getpaneinfo"></a>CStatusBar:: GetPaneInfo

将*nID*、 *nStyle*和*cxWidth*设置为*nIndex*指定的位置处的指示器窗格的 ID、样式和宽度。

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
对设置为窗格宽度的整数的引用。

##  <a name="getpanestyle"></a>CStatusBar:: GetPaneStyle

调用此成员函数以检索状态栏的窗格样式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其样式的窗格的索引。

### <a name="return-value"></a>返回值

*NIndex*指定的状态栏窗格的样式。

### <a name="remarks"></a>备注

窗格的样式决定了窗格的显示方式。

有关可用于状态栏的样式的列表, 请参阅[创建](#create)。

##  <a name="getpanetext"></a>CStatusBar:: GetPaneText

调用此成员函数以检索显示在状态栏窗格中的文本。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其文本的窗格的索引。

*rString*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用, 该对象包含要检索的文本。

### <a name="return-value"></a>返回值

包含窗格文本的对象。`CString`

### <a name="remarks"></a>备注

此成员函数的第二种形式使用`CString`字符串文本填充对象。

##  <a name="getstatusbarctrl"></a>CStatusBar:: GetStatusBarCtrl

此成员函数允许直接访问基础公共控件。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>返回值

包含对[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

使用`GetStatusBarCtrl`可以利用 Windows 状态栏公共控件的功能, 并利用支持[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供的功能来进行状态栏自定义。 例如, 通过使用公共控件, 可以指定在状态栏上包含大小调整手柄的样式, 也可以指定样式, 使状态栏出现在父窗口的工作区顶部。

有关公共控件的更多常规信息, 请参阅 Windows SDK 中的[公共控件](/windows/win32/Controls/common-controls-intro)。

##  <a name="setindicators"></a>CStatusBar:: SetIndicators

将每个指示器的 ID 设置为数组*lpIDArray*的相应元素所指定的值, 加载每个 ID 指定的字符串资源, 并将指示器的文本设置为字符串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

*lpIDArray*<br/>
指向 Id 的数组的指针。

*nIDCount*<br/>
*LpIDArray*指向的数组中的元素数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="setpaneinfo"></a>CStatusBar:: SetPaneInfo

将指定的指示器窗格设置为新的 ID、样式和宽度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其样式的指示器窗格的索引。

*nID*<br/>
指示器窗格的新 ID。

*nStyle*<br/>
指示器窗格的新样式。

*cxWidth*<br/>
指示器窗格的新宽度。

### <a name="remarks"></a>备注

支持以下指示器样式:

- SBPS_NOBORDERS 在窗格周围没有三维边框。

- SBPS_POPOUT, 使文本 "弹出"。

- SBPS_DISABLED 不绘制文本。

- 用于填充未使用空间的 SBPS_STRETCH 拉伸窗格。 每个状态栏只有一个窗格可以具有此样式。

- SBPS_NORMAL 无 stretch、边框或弹出窗口。

##  <a name="setpanestyle"></a>CStatusBar:: SetPaneStyle

调用此成员函数设置状态栏的窗格样式。

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

窗格的样式决定了窗格的显示方式。

有关可用于状态栏的样式的列表, 请参阅[SetPaneInfo](#setpaneinfo)。

##  <a name="setpanetext"></a>CStatusBar:: SetPaneText

调用此成员函数可将窗格文本设置为*lpszNewText*指向的字符串。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其文本的窗格的索引。

*lpszNewText*<br/>
指向新窗格文本的指针。

*bUpdate*<br/>
如果为 TRUE, 则在设置文本后, 窗格会失效。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

调用`SetPaneText`后, 您必须添加一个 UI 更新处理程序, 以便在状态栏中显示新文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 类](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
