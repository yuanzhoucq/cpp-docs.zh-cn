---
title: CTabCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426341"
---
# <a name="ctabctrl-class"></a>CTabCtrl 类

提供 Windows 公共选项卡控件的功能。

## <a name="syntax"></a>语法

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CTabCtrl：： CTabCtrl](#ctabctrl)|构造 `CTabCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTabCtrl：： AdjustRect](#adjustrect)|计算给定窗口矩形的选项卡控件的显示区域，或计算与给定显示区域相对应的窗口矩形。|
|[CTabCtrl：： Create](#create)|创建选项卡控件，并将其附加到 `CTabCtrl` 对象的实例。|
|[CTabCtrl：： CreateEx](#createex)|创建具有指定 Windows 扩展样式的选项卡控件，并将其附加到 `CTabCtrl` 对象的实例。|
|[CTabCtrl：:D eleteAllItems](#deleteallitems)|从选项卡控件中移除所有项。|
|[CTabCtrl：:D eleteItem](#deleteitem)|从选项卡控件中移除项。|
|[CTabCtrl：:D eselectAll](#deselectall)|重置选项卡控件中的项，清除已按下的任何项。|
|[CTabCtrl：:D rawItem](#drawitem)|绘制选项卡控件的指定项。|
|[CTabCtrl：： GetCurFocus](#getcurfocus)|检索具有选项卡控件的当前焦点的选项卡。|
|[CTabCtrl：： GetCurSel](#getcursel)|确定选项卡控件中当前选定的选项卡。|
|[CTabCtrl：： GetExtendedStyle](#getextendedstyle)|检索当前用于选项卡控件的扩展样式。|
|[CTabCtrl：： GetImageList](#getimagelist)|检索与选项卡控件关联的图像列表。|
|[CTabCtrl：： GetItem](#getitem)|检索有关选项卡控件中的选项卡的信息。|
|[CTabCtrl：： GetItemCount](#getitemcount)|检索选项卡控件中选项卡的数目。|
|[CTabCtrl：： GetItemRect](#getitemrect)|检索选项卡控件中选项卡的边框。|
|[CTabCtrl：： GetItemState](#getitemstate)|检索所指示的选项卡控件项的状态。|
|[CTabCtrl：： GetRowCount](#getrowcount)|检索选项卡控件中选项卡的当前行数。|
|[CTabCtrl：： GetToolTips](#gettooltips)|检索与选项卡控件关联的工具提示控件的句柄。|
|[CTabCtrl：： HighlightItem](#highlightitem)|设置选项卡项的突出显示状态。|
|[CTabCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|确定哪个选项卡（如果有）位于指定的屏幕位置。|
|[CTabCtrl：： InsertItem](#insertitem)|在选项卡控件中插入新选项卡。|
|[CTabCtrl：： RemoveImage](#removeimage)|从选项卡控件的图像列表中移除图像。|
|[CTabCtrl：： SetCurFocus](#setcurfocus)|将焦点设置到选项卡控件中的指定选项卡。|
|[CTabCtrl：： SetCurSel](#setcursel)|选择选项卡控件中的选项卡。|
|[CTabCtrl：： SetExtendedStyle](#setextendedstyle)|设置选项卡控件的扩展样式。|
|[CTabCtrl：： SetImageList](#setimagelist)|将图像列表分配给选项卡控件。|
|[CTabCtrl：： SetItem](#setitem)|设置选项卡的部分或全部属性。|
|[CTabCtrl：： SetItemExtra](#setitemextra)|设置选项卡控件中为应用程序定义的数据保留的每个选项卡的字节数。|
|[CTabCtrl：： SetItemSize](#setitemsize)|设置项的宽度和高度。|
|[CTabCtrl：： SetItemState](#setitemstate)|设置所指示的选项卡控件项的状态。|
|[CTabCtrl：： SetMinTabWidth](#setmintabwidth)|设置选项卡控件中项的最小宽度。|
|[CTabCtrl：： SetPadding](#setpadding)|设置选项卡控件中每个选项卡的图标和标签周围的空间量（填充）。|
|[CTabCtrl：： SetToolTips](#settooltips)|将工具提示控件分配给选项卡控件。|

## <a name="remarks"></a>备注

"选项卡控件" 类似于笔记本中的分隔条或文件柜中的标签。 通过使用选项卡控件，应用程序可以为窗口或对话框的相同区域定义多个页。 每个页面都包含一组信息或一组控件，当用户选择相应的选项卡时，应用程序会显示该选项卡。特殊类型的选项卡控件显示类似按钮的选项卡。 单击某个按钮应立即执行命令，而不是显示页面。

此控件（因此 `CTabCtrl` 类）仅适用于在 Windows 95/98 和 Windows NT 版本3.51 及更高版本下运行的程序。

有关使用 `CTabCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CTabCtrl](../../mfc/using-ctabctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="adjustrect"></a>CTabCtrl：： AdjustRect

计算给定窗口矩形的选项卡控件的显示区域，或计算与给定显示区域相对应的窗口矩形。

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>parameters

*bLarger*<br/>
指示要执行的操作。 如果此参数为 TRUE，则*lpRect*将指定一个显示矩形并接收相应的窗口矩形。 如果此参数为 FALSE，则*lpRect*指定一个窗口矩形并接收相应的显示矩形。

*lpRect*<br/>
指向[矩形结构的指针，该结构](/previous-versions/dd162897\(v=vs.85\))指定给定矩形并接收计算矩形。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl：： Create

创建选项卡控件，并将其附加到 `CTabCtrl` 对象的实例。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwStyle*<br/>
指定选项卡控件的样式。 应用 Windows SDK 中所述的任何[选项卡控件样式](/windows/win32/Controls/tab-control-styles)组合。 有关还可以应用于控件的窗口样式列表，请参阅 "**备注**"。

*rect*<br/>
指定选项卡控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pParentWnd*<br/>
指定选项卡控件的父窗口，通常为 `CDialog`。 值不得为 NULL。

*nID*<br/>
指定选项卡控件的 ID。

### <a name="return-value"></a>返回值

如果对象初始化成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

可以通过两个步骤构造一个 `CTabCtrl` 对象。 首先，调用构造函数，然后调用 `Create`，这将创建选项卡控件，并将其附加到 `CTabCtrl` 对象。

除了选项卡控件样式以外，还可以将以下窗口样式应用于选项卡控件：

- WS_CHILD 创建一个表示选项卡控件的子窗口。 不能与 WS_POPUP 样式一起使用。

- WS_VISIBLE 创建一个最初可见的选项卡控件。

- WS_DISABLED 创建一个最初处于禁用状态的窗口。

- WS_GROUP 指定一组控件中的第一个控件，用户可以使用箭头键从一个控件移动到下一个控件。 在第一个控件属于同一组之后，用 WS_GROUP 样式定义的所有控件。 具有 WS_GROUP 样式的下一个控件将结束样式组，并启动下一组（即，一个组在下一开始的位置结束）。

- WS_TABSTOP 指定多个控件中的一个，用户可以使用 TAB 键移动这些控件。 TAB 键将用户移动到 WS_TABSTOP 样式指定的下一个控件。

若要创建具有扩展窗口样式的选项卡控件，请调用[CTabCtrl：： CreateEx](#createex)而不是 `Create`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl：： CreateEx

创建一个控件（子窗口）并将其与 `CTabCtrl` 对象相关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwExStyle*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定选项卡控件的样式。 应用 Windows SDK 中所述的任何[选项卡控件样式](/windows/win32/Controls/tab-control-styles)组合。 有关还可以应用于控件的窗口样式列表，请参阅[创建](#create)中的**备注**。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构描述要创建的窗口的大小和位置（以*pParentWnd*的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则为非零; 否则为0。

### <a name="remarks"></a>备注

使用 `CreateEx` 而不是[Create](#create)来应用扩展的 windows 样式，该样式由 Windows 扩展样式指定的前言**WS_EX_** 开头。

`CreateEx` 使用*dwExStyle*指定的扩展 Windows 样式创建控件。 使用[SetExtendedStyle](#setextendedstyle)设置特定于控件的扩展样式。 例如，使用 `CreateEx` 将此类样式设置 WS_EX_CONTEXTHELP，但使用 `SetExtendedStyle` 将此类样式设置为 "TCS_EX_FLATSEPARATORS"。 有关详细信息，请参阅在 Windows SDK 中的[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)中所述的样式。

##  <a name="ctabctrl"></a>CTabCtrl：： CTabCtrl

构造 `CTabCtrl` 对象。

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl：:D eleteAllItems

从选项卡控件中移除所有项。

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="deleteitem"></a>CTabCtrl：:D eleteItem

从选项卡控件中移除指定项。

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
要删除的项的从零开始的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl：:D eselectAll

重置选项卡控件中的项，清除已按下的任何项。

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>parameters

*fExcludeFocus*<br/>
指定项 deselection 的作用域的标志。 如果此参数设置为 "FALSE"，则将重置所有选项卡按钮。 如果设置为 TRUE，则将重置当前所选的所有选项卡项。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息的行为， [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall)，如 Windows SDK 中所述。

##  <a name="drawitem"></a>CTabCtrl：:D rawItem

当所有者描述的选项卡控件的可视方位更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>parameters

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，该结构描述要绘制的项。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT` 结构的 `itemAction` 成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现 `CTabCtrl` 对象的所有者描述的绘图。

此成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

##  <a name="getcurfocus"></a>CTabCtrl：： GetCurFocus

检索具有当前焦点的选项卡的索引。

```
int GetCurFocus() const;
```

### <a name="return-value"></a>返回值

具有当前焦点的选项卡的从零开始的索引。

##  <a name="getcursel"></a>CTabCtrl：： GetCurSel

检索选项卡控件中当前选定的选项卡。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

如果成功，则为所选选项卡的从零开始的索引; 如果未选择任何选项卡，则为-1。

##  <a name="getextendedstyle"></a>CTabCtrl：： GetExtendedStyle

检索当前用于选项卡控件的扩展样式。

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>返回值

表示选项卡控件当前使用的扩展样式。 此值是[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)的组合，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)的行为，如 Windows SDK 中所述。

##  <a name="getimagelist"></a>CTabCtrl：： GetImageList

检索与选项卡控件关联的图像列表。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

如果成功，则为指向选项卡控件的图像列表的指针；否则为 NULL。

##  <a name="getitem"></a>CTabCtrl：： GetItem

检索有关选项卡控件中的选项卡的信息。

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>parameters

*nItem*<br/>
选项卡的从零开始的索引。

*pTabCtrlItem*<br/>
指向[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针，该结构用于指定要检索的信息。 还用于接收有关选项卡的信息。此结构与 `InsertItem`、`GetItem`和 `SetItem` 成员函数结合使用。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

发送消息时，`mask` 成员指定要返回的属性。 如果 `mask` 成员指定 TCIF_TEXT 值，则 `pszText` 成员必须包含接收项文本的缓冲区的地址，并且 `cchTextMax` 成员必须指定缓冲区的大小。

- `mask`

   指定要检索或设置的 `TCITEM` 结构成员的值。 此成员可以为零或以下值的组合：

   - TCIF_TEXT `pszText` 成员有效。

   - TCIF_IMAGE `iImage` 成员有效。

   - TCIF_PARAM `lParam` 成员有效。

   - TCIF_RTLREADING 在希伯来语或阿拉伯语系统上使用从右到左的阅读顺序显示 `pszText` 的文本。

   - TCIF_STATE `dwState` 成员有效。

- `pszText`

   指向以 null 结尾的字符串的指针，如果该结构包含有关选项卡的信息，则该字符串包含选项卡文本。如果结构正在接收信息，则此成员指定接收选项卡文本的缓冲区的地址。

- `cchTextMax`

   `pszText`所指向的缓冲区大小。 如果结构未接收信息，则忽略此成员。

- 将索引 `iImage` 到选项卡控件的图像列表中，如果该选项卡没有图像，则为-1。

- `lParam`

   与选项卡关联的应用程序定义数据。如果每个选项卡的应用程序定义的数据超过四个字节，应用程序必须定义一个结构，并使用它而不是 `TCITEM` 结构。 应用程序定义的结构的第一个成员必须是[TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)结构。 `TCITEMHEADER` 结构与 `TCITEM` 结构相同，但没有 `lParam` 成员。 结构大小与 `TCITEMHEADER` 结构的大小之间的差异应该等于每个选项卡的额外字节数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl：： GetItemCount

检索选项卡控件中选项卡的数目。

```
int GetItemCount() const;
```

### <a name="return-value"></a>返回值

选项卡控件中的项数。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="getitemrect"></a>CTabCtrl：： GetItemRect

检索选项卡控件中的指定选项卡的边框。

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>parameters

*nItem*<br/>
选项卡项的从零开始的索引。

*lpRect*<br/>
一个指针，指向用于接收该选项卡的边框的[RECT](/previous-versions/dd162897\(v=vs.85\))结构。这些坐标使用视区的当前映射模式。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="getitemstate"></a>CTabCtrl：： GetItemState

检索由*nItem*标识的选项卡控件项的状态。

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>parameters

*nItem*<br/>
要为其检索状态信息的项的从零开始的索引号。

*dwMask*<br/>
指定要返回的项的状态标志的掩码。 有关值的列表，请参阅[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的 mask 成员，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

对接收状态信息的 DWORD 值的引用。 可以是以下值之一：

|值|说明|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|选择 "选项卡控件" 项。|
|TCIS_HIGHLIGHTED|选项卡控件项将突出显示，并使用当前突出显示颜色绘制选项卡和文本。 使用突出显示颜色时，这将是真正的插值，而不是抖动颜色。|

### <a name="remarks"></a>备注

项的状态由 `TCITEM` 结构的 `dwState` 成员指定。

##  <a name="getrowcount"></a>CTabCtrl：： GetRowCount

检索选项卡控件中的当前行数。

```
int GetRowCount() const;
```

### <a name="return-value"></a>返回值

选项卡控件中选项卡的行数。

### <a name="remarks"></a>备注

只有具有 TCS_MULTILINE 样式的选项卡控件才能有多行选项卡。

##  <a name="gettooltips"></a>CTabCtrl：： GetToolTips

检索与选项卡控件关联的工具提示控件的句柄。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

如果成功，则为工具提示控件的句柄;否则为 NULL。

### <a name="remarks"></a>备注

选项卡控件创建具有 TCS_TOOLTIPS 样式的工具提示控件。 还可以通过使用 `SetToolTips` 成员函数向选项卡控件分配工具提示控件。

##  <a name="highlightitem"></a>CTabCtrl：： HighlightItem

设置选项卡项的突出显示状态。

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>parameters

*idItem*<br/>
选项卡控件项的从零开始的索引。

*fHighlight*<br/>
指定要设置的突出显示状态的值。 如果此值为 TRUE，则突出显示该选项卡;如果为 FALSE，则选项卡将设置为其默认状态。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)，如 Windows SDK 中所述。

##  <a name="hittest"></a>CTabCtrl：： System.windows.media.visualtreehelper.hittest

确定哪个选项卡（如果有）位于指定的屏幕位置。

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>parameters

*pHitTestInfo*<br/>
指向[TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo)结构的指针，如 Windows SDK 中所述，它指定要测试的屏幕位置。

### <a name="return-value"></a>返回值

返回选项卡的从零开始的索引; 如果在指定位置没有选项卡，则返回-1。

##  <a name="insertitem"></a>CTabCtrl：： InsertItem

在现有选项卡控件中插入新选项卡。

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
新选项卡的从零开始的索引。

*pTabCtrlItem*<br/>
指向[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针，该结构指定选项卡的属性。

*lpszItem*<br/>
以 null 结尾的包含选项卡文本的字符串的地址。

*n*<br/>
要从图像列表插入的图像的从零开始的索引。

*nMask*<br/>
指定要设置的 `TCITEM` 结构特性。 可以为零或以下值的组合：

- TCIF_TEXT `pszText` 成员有效。

- TCIF_IMAGE `iImage` 成员有效。

- TCIF_PARAM *lParam*成员有效。

- TCIF_RTLREADING 在希伯来语或阿拉伯语系统上使用从右到左的阅读顺序显示 `pszText` 的文本。

- TCIF_STATE *dwState*成员有效。

*lParam*<br/>
与选项卡关联的应用程序定义数据。

*dwState*<br/>
指定项的状态值。 有关详细信息，请参阅 Windows SDK 中的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 。

*dwStateMask*<br/>
指定要设置的状态。 有关详细信息，请参阅 Windows SDK 中的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 。

### <a name="return-value"></a>返回值

如果成功，则为新选项卡的从零开始的索引;否则为-1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl：： RemoveImage

从选项卡控件的图像列表中移除指定的图像。

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>parameters

*n*<br/>
要移除的图像的从零开始的索引。

### <a name="remarks"></a>备注

选项卡控件将更新每个选项卡的图像索引，以便每个选项卡与同一个图像保持关联。

##  <a name="setcurfocus"></a>CTabCtrl：： SetCurFocus

将焦点设置到选项卡控件中的指定选项卡。

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
指定获取焦点的选项卡的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)的行为，如 Windows SDK 中所述。

##  <a name="setcursel"></a>CTabCtrl：： SetCurSel

选择选项卡控件中的选项卡。

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
要选择的项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则为之前选择的选项卡的从零开始的索引; 否则为-1。

### <a name="remarks"></a>备注

使用此函数选择选项卡时，选项卡控件不发送 TCN_SELCHANGING 或 TCN_SELCHANGE 通知消息。 当用户单击或使用键盘更改选项卡时，将使用 WM_NOTIFY 发送这些通知。

##  <a name="setextendedstyle"></a>CTabCtrl：： SetExtendedStyle

设置选项卡控件的扩展样式。

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>parameters

*dwNewStyle*<br/>
指定选项卡控件扩展样式组合的值。

*dwExMask*<br/>
一个 DWORD 值，指示要对*dwNewStyle*中的哪些样式产生影响。 仅更改*dwExMask*中的扩展样式。 所有其他样式将按原样维护。 如果此参数为零，则将影响*dwNewStyle*中的所有样式。

### <a name="return-value"></a>返回值

一个 DWORD 值，其中包含上一个[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

此成员函数实现 Win32 消息[TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)的行为，如 Windows SDK 中所述。

##  <a name="setimagelist"></a>CTabCtrl：： SetImageList

将图像列表分配给选项卡控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>parameters

*pImageList*<br/>
指向要分配给选项卡控件的图像列表的指针。

### <a name="return-value"></a>返回值

返回指向上一个图像列表的指针; 如果没有上一个图像列表，则返回 NULL。

##  <a name="setitem"></a>CTabCtrl：： SetItem

设置选项卡的部分或全部属性。

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
项的从零开始的索引。

*pTabCtrlItem*<br/>
指向[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针，该结构包含新的项特性。 `mask` 成员指定要设置的特性。 如果 `mask` 成员指定 TCIF_TEXT 值，则 `pszText` 成员是以 null 结尾的字符串的地址，并且忽略 `cchTextMax` 成员。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[GetItem](#getitem)的示例。

##  <a name="setitemextra"></a>CTabCtrl：： SetItemExtra

设置选项卡控件中为应用程序定义的数据保留的每个选项卡的字节数。

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>parameters

*nBytes*<br/>
要设置的额外字节数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)的行为，如 Windows SDK 中所述。

##  <a name="setitemsize"></a>CTabCtrl：： SetItemSize

设置选项卡控件项的宽度和高度。

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>parameters

size<br/>
选项卡控件项的新宽度和高度（以像素为单位）。

### <a name="return-value"></a>返回值

返回选项卡控件项的旧宽度和高度。

##  <a name="setitemstate"></a>CTabCtrl：： SetItemState

设置由*nItem*标识的选项卡控件项的状态。

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>parameters

*nItem*<br/>
要为其设置状态信息的项的从零开始的索引号。

*dwMask*<br/>
指定要设置的项的状态标志的掩码。 有关值的列表，请参阅[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的 mask 成员，如 Windows SDK 中所述。

*dwState*<br/>
对包含状态信息的 DWORD 值的引用。 可以是以下值之一：

|值|说明|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|选择 "选项卡控件" 项。|
|TCIS_HIGHLIGHTED|选项卡控件项将突出显示，并使用当前突出显示颜色绘制选项卡和文本。 使用突出显示颜色时，这将是真正的插值，而不是抖动颜色。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="setmintabwidth"></a>CTabCtrl：： SetMinTabWidth

设置选项卡控件中项的最小宽度。

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>parameters

*cx*<br/>
为选项卡控件项设置的最小宽度。 如果将此参数设置为-1，则控件将使用默认选项卡宽度。

### <a name="return-value"></a>返回值

上一个最小制表符宽度。

### <a name="return-value"></a>返回值

此成员函数实现 Win32 消息[TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)的行为，如 Windows SDK 中所述。

##  <a name="setpadding"></a>CTabCtrl：： SetPadding

设置选项卡控件中每个选项卡的图标和标签周围的空间量（填充）。

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>parameters

size<br/>
设置选项卡控件中每个选项卡的图标和标签周围的空间量（填充）。

##  <a name="settooltips"></a>CTabCtrl：： SetToolTips

将工具提示控件分配给选项卡控件。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>parameters

*pWndTip*<br/>
工具提示控件的句柄。

### <a name="remarks"></a>备注

可以通过调用 `GetToolTips`来获取与选项卡控件关联的工具提示控件。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl 类](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)
