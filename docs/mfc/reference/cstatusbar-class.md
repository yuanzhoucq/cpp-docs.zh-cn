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
ms.openlocfilehash: e7aa577d237c1800ca9df3f0af4c44acdaae9ae2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279492"
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
|[CStatusBar::CommandToIndex](#commandtoindex)|获取索引的给定的指标 id。|
|[CStatusBar::Create](#create)|创建状态栏，并将其附加到`CStatusBar`对象，并设置初始的字体和栏高度。|
|[CStatusBar::CreateEx](#createex)|创建`CStatusBar`具有其他样式的嵌入对象`CStatusBarCtrl`对象。|
|[CStatusBar::DrawItem](#drawitem)|当所有者描述状态栏控件发生更改的可视方面时调用。|
|[CStatusBar::GetItemID](#getitemid)|获取给定索引指示符 ID。|
|[CStatusBar::GetItemRect](#getitemrect)|获取显示给定索引的矩形。|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|获取给定索引的指示符 ID、 样式和宽度。|
|[CStatusBar::GetPaneStyle](#getpanestyle)|获取给定索引的指示器样式。|
|[CStatusBar::GetPaneText](#getpanetext)|获取给定索引指示器文本。|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允许直接访问基础公共控件。|
|[CStatusBar::SetIndicators](#setindicators)|设置指示符 Id。|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|设置指标 ID、 样式和宽度为给定的索引。|
|[CStatusBar::SetPaneStyle](#setpanestyle)|设置给定索引的指示器样式。|
|[CStatusBar::SetPaneText](#setpanetext)|设置给定索引的指示符文本。|

## <a name="remarks"></a>备注

输出窗格通常用作消息行状态指示器，以及使用。 示例包括简要介绍所选的菜单命令的菜单帮助消息行和指示器显示 SCROLL LOCK、 NUM LOCK 和其他键的状态。

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成员函数新增到 MFC 4.0，让您充分利用状态栏自定义项和其他功能的 Windows 公共控件的支持。 `CStatusBar` 成员函数为您提供的大多数 Windows 公共控件; 功能但是，在调用`GetStatusBarCtrl`，您可以为您状态栏甚至多个 Windows 95/98 状态栏的特征。 当您调用`GetStatusBarCtrl`，它将返回到引用`CStatusBarCtrl`对象。 请参阅[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 有关公共控件的更多常规信息，请参阅[公共控件](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

该框架将指标信息存储在数组位置 0 处最左侧的指示符。 当您创建一个状态栏时，使用字符串框架相关联的相应指标的 Id 的数组。 然后可以使用字符串 ID 或索引访问指示器。

默认情况下，第一个标记是"弹性": 其占用未由其他指示器窗格、 状态栏长度，以使其他窗格右对齐。

若要创建一个状态栏，执行以下步骤：

1. 构造 `CStatusBar` 对象。

1. 调用[创建](#create)(或[CreateEx](#createex)) 函数来创建状态栏窗口，并将其附加到`CStatusBar`对象。

1. 调用[SetIndicators](#setindicators)若要将字符串 ID 与每个指标相关联。

有三种方法来更新状态栏窗格中的文本：

1. 调用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新仅窗格 0 中的文本。

1. 调用[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext)状态栏的 ON_UPDATE_COMMAND_UI 处理程序中。

1. 调用[SetPaneText](#setpanetext)更新任何窗格的文本。

调用[SetPaneStyle](#setpanestyle)更新状态栏窗格的样式。

有关使用的详细信息`CStatusBar`，请参阅文章[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[技术说明 31:控件条](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

获取指示器索引的给定的 id。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

*nIDFind*<br/>
指示器的索引是要检索的字符串 ID。

### <a name="return-value"></a>返回值

如果成功，则该标记的索引如果不成功，为-1。

### <a name="remarks"></a>备注

第一个指示器的索引为 0。

##  <a name="create"></a>  CStatusBar::Create

创建状态栏 （子窗口），并将其与`CStatusBar`对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 窗口是状态栏的父对象。

*dwStyle*<br/>
状态栏样式中。 除了标准的 Windows[样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)，支持这些样式。

- CBRS_TOP 控件条是在框架窗口的顶部。

- CBRS_BOTTOM 控件条是在框架窗口的底部。

- 父级重设大小时，CBRS_NOALIGN 控件栏不会重新定位。

*nID*<br/>
工具栏的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此外设置初始字体并将状态设置为默认值的条形图的高度。

##  <a name="createex"></a>  CStatusBar::CreateEx

调用此函数可创建状态栏 （子窗口），并将其与`CStatusBar`对象。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 窗口是状态栏的父对象。

*dwCtrlStyle*<br/>
创建嵌入其他样式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象。 默认值指定一个状态栏，而无需大小调整手柄或工具提示支持。 状态条样式支持是：

- SBARS_SIZEGRIP 状态栏控件包括右端状态栏的大小调整手柄。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。

- SBT_TOOLTIPS 状态栏支持工具提示。

有关这些样式的详细信息，请参阅[CStatusBarCtrl 的设置](../../mfc/settings-for-the-cstatusbarctrl.md)。

*dwStyle*<br/>
状态栏样式。 默认值指定在框架窗口的底部创建可见的状态栏。 应用状态栏控件样式中列出的任意组合[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)并[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 但是，此参数应始终包含 WS_CHILD 和 WS_VISIBLE 样式。

*nID*<br/>
状态栏的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数还设置初始字体并将状态设置为默认值的条形图的高度。

使用`CreateEx`，而不是[创建](#create)，当需要嵌入式的状态栏控件在创建期间提供特定的样式。 例如，设置*dwCtrlStyle*到 SBT_TOOLTIPS 中状态条对象显示工具提示。

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

构造`CStatusBar`对象创建如有必要的默认状态栏的字体和字体特征设置为默认值。

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

所有者描述的状态栏会发生变化的可视方面时由框架调用此成员函数。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
一个指向[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)结构，其中包含有关绘图所需的类型的信息。

### <a name="remarks"></a>备注

`itemAction`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 重写此成员函数以实现绘制所有者描述的`CStatusBar`对象。 应用程序应还原所有图形设备接口 (GDI) 对象的显示上下文中提供选定*lpDrawItemStruct*之前终止此成员函数。

##  <a name="getitemid"></a>  CStatusBar::GetItemID

返回由指定的指示器的 ID *nIndex*。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
其 ID 是要检索的指示器的索引。

### <a name="return-value"></a>返回值

通过指定指标的 ID *nIndex*。

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

复制指定的指标的坐标*nIndex*到指向的结构*lpRect*。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要从中检索其矩形坐标的指示器的索引。

*lpRect*<br/>
指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它将接收指定指示器的坐标*nIndex*。

### <a name="remarks"></a>备注

坐标是状态栏的相对于左上角以像素为单位。

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

集*nID*， *nStyle*，并*cxWidth*对 ID、 样式和在指定的位置指示器窗格的宽度*nIndex*。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其信息窗格的索引。

*nID*<br/>
设置窗格的 ID 为 uint 的引用。

*nStyle*<br/>
对设置为窗格中的样式 UINT 引用。

*cxWidth*<br/>
为设置窗格的宽度为整数的引用。

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

调用此成员函数以检索一个状态栏窗格的样式。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
是要检索其样式窗格中的索引。

### <a name="return-value"></a>返回值

指定状态栏窗格的样式*nIndex*。

### <a name="remarks"></a>备注

一个窗格样式确定在窗格的显示方式。

适用于状态栏的样式的列表，请参阅[创建](#create)。

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

调用此成员函数以检索在状态栏窗格中显示的文本。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其文本窗格的索引。

*rString*<br/>
对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要检索的文本。

### <a name="return-value"></a>返回值

一个`CString`对象，其中包含窗格的文本。

### <a name="remarks"></a>备注

此成员的第二种形式函数填充`CString`具有字符串文本对象。

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

此成员函数允许直接访问基础公共控件。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>返回值

包含对引用[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象。

### <a name="remarks"></a>备注

使用`GetStatusBarCtrl`充分利用 Windows 状态栏公共控件的功能并利用支持[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供自定义状态栏。 例如，通过使用一个常用的控件，可以指定包含在状态栏中，大小调整手柄的样式或可以指定要具有显示在父窗口工作区顶部的状态栏的样式。

有关公共控件的更多常规信息，请参阅[公共控件](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

每个指标的 ID 设置为指定数组的相应元素的值*lpIDArray*、 加载每个 ID，指定的字符串资源和指示符的文本设置为字符串。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

*lpIDArray*<br/>
指向一个 Id 数组的指针。

*nIDCount*<br/>
指向数组中的元素数目*lpIDArray*。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

将指定的指标窗格设置为新的 ID、 样式和宽度。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指示器窗格中将设置其样式的索引。

*nID*<br/>
指示器窗格中的新 ID。

*nStyle*<br/>
指示器窗格中的新样式。

*cxWidth*<br/>
指示器窗格中的新宽度。

### <a name="remarks"></a>备注

支持以下指示器样式：

- SBPS_NOBORDERS No 窗格中的三维边框。

- SBPS_POPOUT 反向边界，以便文本"弹出。"

- SBPS_DISABLED 执行不绘制文本。

- SBPS_STRETCH Stretch 窗格以填充未使用的空间。 只有一个窗格中的每个状态栏可以有此样式。

- SBPS_NORMAL 否 stretch、 边框或弹出。

##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle

调用此成员函数可将一个状态栏窗格的样式设置。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
将设置其样式窗格中的索引。

*nStyle*<br/>
将设置其样式窗格中的样式。

### <a name="remarks"></a>备注

一个窗格样式确定在窗格的显示方式。

适用于状态栏的样式的列表，请参阅[SetPaneInfo](#setpaneinfo)。

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

调用此成员函数可将窗格文本设置为指向的字符串*lpszNewText*。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
其中的文本是设置窗格中的索引。

*lpszNewText*<br/>
指向新窗格文本指针。

*bUpdate*<br/>
如果为 TRUE，窗格会失效后的文本设置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

调用后`SetPaneText`，必须添加用户界面更新处理程序，在状态栏中显示新文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[MFC 示例 DLGCBR32](../../visual-cpp-samples.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 类](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
