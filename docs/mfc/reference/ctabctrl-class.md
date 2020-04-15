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
ms.openlocfilehash: 7d4a478b560be686e4da6f6dea623d6058626562
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365955"
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
|[CtCtrl：：CTabCtrl](#ctabctrl)|构造 `CTabCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CtCtrl：：调整](#adjustrect)|计算给定窗口矩形的制表符控件的显示区域，或计算对应于给定显示区域的窗口矩形。|
|[CTabCtrl：：创建](#create)|创建选项卡控件并将其附加到`CTabCtrl`对象的实例。|
|[CTabCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建选项卡控件，并将其附加到`CTabCtrl`对象的实例。|
|[CTabCtrl：:DeleteAll项目](#deleteallitems)|从选项卡控件中删除所有项。|
|[CTabCtrl：:Delete项目](#deleteitem)|从选项卡控件中删除项。|
|[CTabCtrl：:Deselect全部](#deselectall)|重置选项卡控件中的项，清除任何按下的项目。|
|[CtCtrl：:D原始项目](#drawitem)|绘制选项卡控件的指定项。|
|[CtCtrl：获取CurFocus](#getcurfocus)|检索具有选项卡控件当前焦点的选项卡。|
|[CtCtrl：：获取CurSel](#getcursel)|确定选项卡控件中当前选定的选项卡。|
|[CtCtrl：：获取扩展样式](#getextendedstyle)|检索当前用于选项卡控件的扩展样式。|
|[CTabCtrl：获取图像列表](#getimagelist)|检索与选项卡控件关联的图像列表。|
|[CTabCtrl：获取项目](#getitem)|检索有关选项卡控件中选项卡的信息。|
|[CTabCtrl：：获取项目计数](#getitemcount)|检索选项卡控件中的选项卡数。|
|[CTabCtrl：：获取项目重新完成](#getitemrect)|检索选项卡控件中选项卡的边界矩形。|
|[CTabCtrl：：获取项目状态](#getitemstate)|检索指示的选项卡控制项的状态。|
|[CtCtrl：：获取罗计数](#getrowcount)|检索选项卡控件中当前数量的选项卡数。|
|[CTabCtrl：获取工具提示](#gettooltips)|检索与选项卡控件关联的工具尖端控件的句柄。|
|[CTabCtrl：：亮点项目](#highlightitem)|设置选项卡项的突出显示状态。|
|[CtCtrl：hitTest](#hittest)|确定哪个选项卡（如果有）位于指定的屏幕位置。|
|[CTabCtrl：：插入项目](#insertitem)|在选项卡控件中插入新选项卡。|
|[CTabCtrl：：删除图像](#removeimage)|从选项卡控件的图像列表中删除图像。|
|[CtCtrl：：设置CurFocus](#setcurfocus)|将焦点设置到选项卡控件中的指定选项卡。|
|[CtCtrl：：SetCurSel](#setcursel)|在选项卡控件中选择选项卡。|
|[CtCtrl：：设置扩展样式](#setextendedstyle)|设置选项卡控件的扩展样式。|
|[CTabCtrl：：设置图像列表](#setimagelist)|将图像列表分配给选项卡控件。|
|[CTabCtrl：：设置项目](#setitem)|设置选项卡的部分或全部属性。|
|[CTabCtrl：：设置项目额外](#setitemextra)|设置选项卡控件中为应用程序定义的数据保留的每个选项卡的字节数。|
|[CTabCtrl：：设置项目大小](#setitemsize)|设置项目的宽度和高度。|
|[CTabCtrl：：设置项目状态](#setitemstate)|设置指示的选项卡控制项的状态。|
|[CTabCtrl：：设置明点宽度](#setmintabwidth)|设置选项卡控件中项目的最小宽度。|
|[CTabCtrl：：设置](#setpadding)|设置选项卡控件中每个选项卡图标和标签周围的空间量（填充）。|
|[CTabCtrl：：设置工具提示](#settooltips)|将工具提示控件分配给选项卡控件。|

## <a name="remarks"></a>备注

"选项卡控件"类似于笔记本中的分隔符或文件柜中的标签。 通过使用选项卡控件，应用程序可以为窗口或对话框的相同区域定义多个页。 每个页面由一组信息或一组控件组成，当用户选择相应的选项卡时，应用程序会显示这些信息或控件组。特殊类型的选项卡控件显示看起来像按钮的选项卡。 单击按钮应立即执行命令，而不是显示页面。

此控件（因此该`CTabCtrl`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关 使用`CTabCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CTabCtrl](../../mfc/using-ctabctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CtCtrl：：调整

计算给定窗口矩形的制表符控件的显示区域，或计算对应于给定显示区域的窗口矩形。

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>参数

*b 更大*<br/>
指示要执行的操作。 如果此参数为*TRUE，lpRect*指定显示矩形并接收相应的窗口矩形。 如果此参数为*FALSE，lpRect*指定一个窗口矩形并接收相应的显示矩形。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构指定给定的矩形并接收计算的矩形。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl：：创建

创建选项卡控件并将其附加到`CTabCtrl`对象的实例。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定选项卡控件的样式。 应用 Windows SDK 中描述的[选项卡控件样式](/windows/win32/Controls/tab-control-styles)的任意组合。 有关也可以应用于控件的窗口样式的列表，请参阅**备注**。

*矩形*<br/>
指定选项卡控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pparentwnd*<br/>
指定选项卡控件的父窗口，通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定选项卡控件的 ID。

### <a name="return-value"></a>返回值

如果对象的初始化成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

分两步`CTabCtrl`构造对象。 首先调用构造函数，然后调用`Create`，这将创建选项卡控件并将其附加到`CTabCtrl`对象。

除了选项卡控件样式之外，还可以将以下窗口样式应用于选项卡控件：

- WS_CHILD 创建表示选项卡控件的子窗口。 不能与WS_POPUP样式一起使用。

- WS_VISIBLE 创建最初可见的选项卡控件。

- WS_DISABLED 创建最初禁用的窗口。

- WS_GROUP 指定一组控件的第一个控件，用户可以在其中使用箭头键从一个控件移动到下一个控件。 在第一个控件之后使用WS_GROUP样式定义的所有控件都属于同一组。 具有WS_GROUP样式的下一个控件结束样式组并启动下一个组（即，一个组结束下一个组开始的位置）。

- WS_TABSTOP 指定用户可以使用 TAB 键移动的任意数量的控件之一。 TAB 键将用户移动到WS_TABSTOP样式指定的下一个控件。

要创建具有扩展窗口样式的选项卡控件，请调用[CTabCtrl：：createEx](#createex)而不是`Create`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl：：创建Ex

创建控件（子窗口），并将其与`CTabCtrl`对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定选项卡控件的样式。 应用 Windows SDK 中描述的[选项卡控件样式](/windows/win32/Controls/tab-control-styles)的任意组合。 请参阅["创建"](#create)中**注释**中查看也可以应用于控件的窗口样式列表。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则为非零，否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

`CreateEx`使用*dwExStyle*指定的扩展 Windows 样式创建控件。 使用[Set 扩展样式](#setextendedstyle)设置特定于控件的扩展样式。 例如，用于`CreateEx`将此类样式设置为WS_EX_CONTEXTHELP，但用于`SetExtendedStyle`将此类样式设置为TCS_EX_FLATSEPARATORS。 有关详细信息，请参阅 Windows SDK 中的[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)中描述的样式。

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CtCtrl：：CTabCtrl

构造 `CTabCtrl` 对象。

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl：:DeleteAll项目

从选项卡控件中删除所有项。

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl：:Delete项目

从选项卡控件中删除指定的项。

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
要删除的项的零基值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl：:Deselect全部

重置选项卡控件中的项，清除任何按下的项目。

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>参数

*f排除焦点*<br/>
指定项目取消选择范围的标志。 如果此参数设置为 FALSE，则将重置所有选项卡按钮。 如果将其设置为 TRUE，则除当前选择的项目外的所有选项卡项都将重置。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall)的行为，如 Windows SDK 中所述。

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CtCtrl：:D原始项目

当所有者绘制选项卡控件的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向描述要绘制的项的[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者绘制对象的绘图`CTabCtrl`。

应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CtCtrl：获取CurFocus

检索具有当前焦点的选项卡的索引。

```
int GetCurFocus() const;
```

### <a name="return-value"></a>返回值

具有当前焦点的选项卡的零基索引。

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CtCtrl：：获取CurSel

检索选项卡控件中当前选定的选项卡。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

如果成功，则所选选项卡的零索引;如果未选择选项卡，则为 - 1。

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CtCtrl：：获取扩展样式

检索当前用于选项卡控件的扩展样式。

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>返回值

表示当前用于选项卡控件的扩展样式。 此值是[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)的组合，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)的行为，如 Windows SDK 中所述。

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl：获取图像列表

检索与选项卡控件关联的图像列表。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

如果成功，则为指向选项卡控件的图像列表的指针；否则为 NULL。

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl：获取项目

检索有关选项卡控件中选项卡的信息。

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>参数

*nItem*<br/>
选项卡的零索引。

*pTabCtrl项目*<br/>
指向[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针，用于指定要检索的信息。 还用于接收有关选项卡的信息。此结构与`InsertItem`、`GetItem`和`SetItem`成员函数一起使用。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;否则。

### <a name="remarks"></a>备注

发送消息时，`mask`成员指定要返回的属性。 如果`mask`成员指定TCIF_TEXT值，`pszText`则成员必须包含接收项文本的缓冲区的地址，`cchTextMax`并且成员必须指定缓冲区的大小。

- `mask`

   指定要检索`TCITEM`或设置的结构成员的值。 此成员可以是零或以下值的组合：

  - TCIF_TEXT`pszText`该成员有效。

  - TCIF_IMAGE该`iImage`成员有效。

  - TCIF_PARAM`lParam`该成员有效。

  - TCIF_RTLREADING 在希`pszText`伯来语或阿拉伯语系统上使用从右到左的阅读顺序显示 的文本。

  - TCIF_STATE`dwState`该成员有效。

- `pszText`

   如果结构包含有关选项卡的信息，则指向包含选项卡文本的 null 端接字符串的指针。如果结构正在接收信息，则此成员指定接收选项卡文本的缓冲区的地址。

- `cchTextMax`

   指向`pszText`的缓冲区的大小。 如果结构未接收信息，则忽略此成员。

- `iImage`索引到选项卡控件的图像列表中，如果选项卡没有图像，则为 - 1。

- `lParam`

   与选项卡关联的应用程序定义数据。如果每个选项卡的应用程序定义数据超过四个字节，则应用程序必须定义结构并使用它而不是`TCITEM`结构。 应用程序定义结构的第一个成员必须是[TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)结构。 结构`TCITEMHEADER`与结构相同，`TCITEM`但没有成员。 `lParam` 结构大小和`TCITEMHEADER`结构大小之间的差异应等于每个选项卡的额外字节数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl：：获取项目计数

检索选项卡控件中的选项卡数。

```
int GetItemCount() const;
```

### <a name="return-value"></a>返回值

选项卡控件中的项数。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl：：获取项目重新完成

检索选项卡控件中指定选项卡的边界矩形。

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nItem*<br/>
选项卡项的零索引。

*lpRect*<br/>
指向接收选项卡边界矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。这些坐标使用视口的当前映射模式。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl：：获取项目状态

检索*nItem*标识的选项卡控制项的状态。

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>参数

*nItem*<br/>
要检索状态信息的项的零基索引号。

*dwMask*<br/>
蒙版指定要返回哪个项的状态标志。 有关值列表，请参阅[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的掩码成员，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

对接收状态信息的 DWORD 值的引用。 可以是以下值之一：

|“值”|说明|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|选择了选项卡控制项。|
|TCIS_HIGHLIGHTED|选项卡控件项将突出显示，并使用当前高光颜色绘制选项卡和文本。 使用高光颜色时，这将是真正的插值，而不是抖除的颜色。|

### <a name="remarks"></a>备注

项的状态由`dwState``TCITEM`结构的成员指定。

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CtCtrl：：获取罗计数

检索选项卡控件中的当前行数。

```
int GetRowCount() const;
```

### <a name="return-value"></a>返回值

选项卡控件中的选项卡行数。

### <a name="remarks"></a>备注

只有具有TCS_MULTILINE样式的选项卡控件才能具有多行选项卡。

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl：获取工具提示

检索与选项卡控件关联的工具尖端控件的句柄。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

如果成功，则处理工具尖端控制;否则 NULL。

### <a name="remarks"></a>备注

如果选项卡控件具有TCS_TOOLTIPS样式，则创建工具提示控件。 您还可以使用`SetToolTips`成员函数将工具提示控件分配给选项卡控件。

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl：：亮点项目

设置选项卡项的突出显示状态。

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>参数

*idItem*<br/>
选项卡控件项的零基索引。

*f 突出显示*<br/>
指定要设置的高光状态的值。 如果此值为 TRUE，则选项卡将突出显示;如果此值为 TRUE，则选项卡将突出显示。如果 FALSE，则选项卡设置为其默认状态。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)，如 Windows SDK 中所述。

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CtCtrl：hitTest

确定哪个选项卡（如果有）位于指定的屏幕位置。

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>参数

*pHitTestInfo*<br/>
指向[TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo)结构的指针，如 Windows SDK 中所述，该结构指定要测试的屏幕位置。

### <a name="return-value"></a>返回值

如果指定位置没有选项卡，则返回选项卡的零索引或 - 1。

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl：：插入项目

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

### <a name="parameters"></a>参数

*nItem*<br/>
新选项卡的零索引。

*pTabCtrl项目*<br/>
指向指定选项卡属性的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针。

*lpszItem*<br/>
包含选项卡文本的 null 终止字符串的地址。

*n图像*<br/>
要从图像列表中插入的图像的零基索引。

*nMask*<br/>
指定要`TCITEM`设置的结构属性。 可以是零或以下值的组合：

- TCIF_TEXT`pszText`该成员有效。

- TCIF_IMAGE该`iImage`成员有效。

- TCIF_PARAM *lParam*成员有效。

- TCIF_RTLREADING 在希`pszText`伯来语或阿拉伯语系统上使用从右到左的阅读顺序显示 的文本。

- TCIF_STATE *dwState*成员有效。

*lParam*<br/>
与选项卡关联的应用程序定义数据。

*德沃州*<br/>
指定项状态的值。 有关详细信息，请参阅 Windows SDK 中的[TCITEM。](/windows/win32/api/commctrl/ns-commctrl-tcitemw)

*dwStateMask*<br/>
指定要设置哪些状态。 有关详细信息，请参阅 Windows SDK 中的[TCITEM。](/windows/win32/api/commctrl/ns-commctrl-tcitemw)

### <a name="return-value"></a>返回值

如果成功，则新选项卡的零基索引;否则 - 1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl：：删除图像

从选项卡控件的图像列表中删除指定的图像。

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>参数

*n图像*<br/>
要删除的图像的零索引。

### <a name="remarks"></a>备注

选项卡控件更新每个选项卡的图像索引，以便每个选项卡与同一图像保持关联。

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CtCtrl：：设置CurFocus

将焦点设置到选项卡控件中的指定选项卡。

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
指定获取焦点的选项卡的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为TCM_SETCURFOCUS，](/windows/win32/Controls/tcm-setcurfocus)如 Windows SDK 中所述。

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CtCtrl：：SetCurSel

在选项卡控件中选择选项卡。

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
要选择的项的零基索引。

### <a name="return-value"></a>返回值

以前选择的选项卡的零索引（如果成功，否则为 - 1）。

### <a name="remarks"></a>备注

使用此功能选择选项卡时，选项卡控件不会发送TCN_SELCHANGING或TCN_SELCHANGE通知消息。 当用户单击或使用键盘更改选项卡时，将使用WM_NOTIFY发送这些通知。

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CtCtrl：：设置扩展样式

设置选项卡控件的扩展样式。

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>参数

*dwNewStyle*<br/>
指定选项卡控件扩展样式组合的值。

*dwExMask*<br/>
DWORD 值，指示*dwNewStyle*中的哪些样式将受到影响。 只有*dwExMask*中的扩展样式才会更改。 所有其他样式将保持不变。 如果此参数为零，则*dwNewStyle*中的所有样式都将受到影响。

### <a name="return-value"></a>返回值

包含上一个[选项卡控件扩展样式](/windows/win32/Controls/tab-control-extended-styles)的 DWORD 值，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

此成员函数实现 win32 消息[的行为TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)，如 Windows SDK 中所述。

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl：：设置图像列表

将图像列表分配给选项卡控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向要分配给选项卡控件的图像列表的指针。

### <a name="return-value"></a>返回值

如果没有以前的图像列表，则返回指向上一个图像列表或 NULL 的指针。

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl：：设置项目

设置选项卡的部分或全部属性。

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
项的零索引。

*pTabCtrl项目*<br/>
指向包含新项属性的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的指针。 成员`mask`指定要设置的属性。 如果`mask`成员指定TCIF_TEXT值，则`pszText`该成员是 null 终止字符串的地址，`cchTextMax`并且该成员将被忽略。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[GetItem](#getitem)的示例。

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl：：设置项目额外

设置选项卡控件中为应用程序定义的数据保留的每个选项卡的字节数。

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要设置的额外字节数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)的行为，如 Windows SDK 中所述。

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl：：设置项目大小

设置选项卡控件项的宽度和高度。

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>参数

*大小*<br/>
选项卡控件项的新宽度和高度（以像素为单位）。

### <a name="return-value"></a>返回值

返回选项卡控件项的旧宽度和高度。

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl：：设置项目状态

设置*nItem*标识的选项卡控件项的状态。

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>参数

*nItem*<br/>
要为其设置状态信息的项的零基索引编号。

*dwMask*<br/>
蒙版指定要设置哪个项的状态标志。 有关值列表，请参阅[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构的掩码成员，如 Windows SDK 中所述。

*德沃州*<br/>
对包含状态信息的 DWORD 值的引用。 可以是以下值之一：

|“值”|说明|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|选择了选项卡控制项。|
|TCIS_HIGHLIGHTED|选项卡控件项将突出显示，并使用当前高光颜色绘制选项卡和文本。 使用高光颜色时，这将是真正的插值，而不是抖除的颜色。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl：：设置明点宽度

设置选项卡控件中项目的最小宽度。

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>参数

*残雪*<br/>
要为选项卡控件项设置的最小宽度。 如果此参数设置为 -1，则控件将使用默认选项卡宽度。

### <a name="return-value"></a>返回值

上一个最小选项卡宽度。

### <a name="return-value"></a>返回值

此成员函数实现 Win32 消息[TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)的行为，如 Windows SDK 中所述。

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl：：设置

设置选项卡控件中每个选项卡图标和标签周围的空间量（填充）。

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>参数

*大小*<br/>
设置选项卡控件中每个选项卡图标和标签周围的空间量（填充）。

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl：：设置工具提示

将工具提示控件分配给选项卡控件。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>参数

*pwndTip*<br/>
工具尖端控件的手柄。

### <a name="remarks"></a>备注

您可以通过调用 来获取与制表符控件关联的工具提示控件`GetToolTips`。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl 类](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)
