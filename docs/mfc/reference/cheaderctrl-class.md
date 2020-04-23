---
title: CHeaderCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: de1705d47c5692d3563bc7d9cb2646531819197a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750919"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 类

提供 Windows 公共标头控件的功能。

## <a name="syntax"></a>语法

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[斩首：：斩首](#cheaderctrl)|构造 `CHeaderCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[斩首：：清除所有筛选器](#clearallfilters)|清除标头控件的所有筛选器。|
|[斩首：：清除过滤器](#clearfilter)|清除标头控件的筛选器。|
|[斩首：：创建](#create)|创建标头控件并将其附加到`CHeaderCtrl`对象。|
|[斩首：：创建拖动图像](#createdragimage)|在标题控件中创建项图像的透明版本。|
|[斩首：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建标头控件并将其附加到`CListCtrl`对象。|
|[CHeaderctrl：:Delete项目](#deleteitem)|从标头控件中删除项。|
|[斩首：:D原始项目](#drawitem)|绘制标头控件的指定项。|
|[斩首：：编辑过滤器](#editfilter)|开始编辑标头控件的指定筛选器。|
|[斩首：：获取比特图保证金](#getbitmapmargin)|检索标头控件中位图边距的宽度。|
|[斩首：：获取焦点项目](#getfocuseditem)|获取具有焦点的当前标头控件中的项的标识符。|
|[斩首：：获取图像列表](#getimagelist)|检索用于绘制标头控件中标头项的图像列表的句柄。|
|[斩首：：获取项目](#getitem)|检索有关标头控件中项的信息。|
|[斩首：：获取项目计数](#getitemcount)|检索标头控件中的项计数。|
|[斩首：：获取项目下拉](#getitemdropdownrect)|获取标题控件中指定下拉按钮的边界矩形信息。|
|[斩首：：获取项目重新完成](#getitemrect)|检索标头控件中给定项的边界矩形。|
|[斩首：：获取订单数组](#getorderarray)|检索标头控件中项的从左到右的顺序。|
|[斩首：：获取溢出](#getoverflowrect)|获取当前标头控件的溢出按钮的边界矩形。|
|[斩首：：HitTest](#hittest)|确定指定点上的位置（如果有）标头项。|
|[斩首：：插入项目](#insertitem)|将新项目插入到标头控件中。|
|[斩首：：布局](#layout)|检索给定矩形内标头控件的大小和位置。|
|[斩首：：订单索引](#ordertoindex)|根据物料在标头控件中的顺序检索物料的索引值。|
|[斩首：：设置位图页距](#setbitmapmargin)|设置标题控件中位图边距的宽度。|
|[斩首：：设置筛选器更改超时](#setfilterchangetimeout)|设置筛选器属性中发生更改的时间与`HDN_FILTERCHANGE`通知的过帐之间的超时间隔。|
|[斩首：：设置焦点项目](#setfocuseditem)|将焦点设置在当前标头控件中的指定标头项。|
|[斩首：：SetHotDivider](#sethotdivider)|更改标题项之间的分隔符以指示标题项的手动拖放。|
|[斩首：：设置图像列表](#setimagelist)|将图像列表分配给标头控件。|
|[斩首：：设置项目](#setitem)|在标头控件中设置指定项的属性。|
|[斩首：：设置顺序数组](#setorderarray)|设置标头控件中项的从左到右的顺序。|

## <a name="remarks"></a>备注

标题控件是通常位于一组文本或数字列上方的窗口。 它包含每列的标题，可以分为部分。 用户可以拖动分隔零件的分隔符以设置每列的宽度。 有关标头控件的图示，请参阅[标题控件](/windows/win32/Controls/header-controls)。

此控件（因此类`CHeaderCtrl`）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

为 Windows 95/IE4.0 常见控件添加的功能包括：

- 标题项自定义排序。

- 标题项拖放，用于重新排序标头项。 创建`CHeaderCtrl`对象时使用HDS_DRAGDROP样式。

- 标题列文本在列调整大小期间不断查看。 创建`CHeaderCtrl`对象时使用HDS_FULLDRAG样式。

- 头热跟踪，当指针悬停在标题上时，它突出显示标题项。 创建`CHeaderCtrl`对象时使用HDS_HOTTRACK样式。

- 图像列表支持。 标题项可以包含存储在`CImageList`对象或文本中的图像。

有关 使用`CHeaderCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和使用[CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>斩首：：斩首

构造 `CHeaderCtrl` 对象。

```
CHeaderCtrl();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>斩首：：清除所有筛选器

清除标头控件的所有筛选器。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行为，列值为 -1，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>斩首：：清除过滤器

清除标头控件的筛选器。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
列值，指示要清除的筛选器。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>斩首：：创建

创建标头控件并将其附加到`CHeaderCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定标头控件的样式。 有关标头控件样式的说明，请参阅 Windows SDK 中的[标头控件样式](/windows/win32/Controls/header-control-styles)。

*矩形*<br/>
指定标头控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定标头控件的父窗口，通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定标头控件的 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则为零。

### <a name="remarks"></a>备注

分两步`CHeaderCtrl`构造对象。 首先，调用构造函数，然后调用`Create`，这将创建标头控件并将其附加到`CHeaderCtrl`对象。

除了标头控件样式外，还可以使用以下通用控件样式来确定标头控件的位置和调整本身的大小（有关详细信息，请参阅[通用控件样式](/windows/win32/Controls/common-control-styles)）：

- CCS_BOTTOM 使控件将自己定位在父窗口工作区的底部，并将宽度设置为与父窗口的宽度相同。

- CCS_NODIVIDER 防止在控件顶部绘制两像素高光。

- CCS_NOMOVEY 使控件在水平（而不是垂直）上调整控件的大小并移动自身，以响应WM_SIZE消息。 如果使用CCS_NORESIZE样式，则此样式不适用。 默认情况下，标头控件具有此样式。

- CCS_NOPARENTALIGN防止控件自动移动到父窗口的顶部或底部。 相反，控件将其位置保留在父窗口中，尽管父窗口的大小发生了变化。 如果还使用CCS_TOP或CCS_BOTTOM样式，则高度将调整为默认值，但位置和宽度保持不变。

- CCS_NORESIZE 防止控件在设置其初始大小或新大小时使用默认宽度和高度。 相反，控件使用创建或调整大小请求中指定的宽度和高度。

- CCS_TOP 使控件将自己定位在父窗口工作区的顶部，并将宽度设置为与父窗口的宽度相同。

您还可以将以下窗口样式应用于标头控件（有关详细信息，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)）：

- WS_CHILD 创建子窗口。 不能与WS_POPUP样式一起使用。

- WS_VISIBLE 创建最初可见的窗口。

- WS_DISABLED 创建最初禁用的窗口。

- WS_GROUP 指定一组控件的第一个控件，用户可以在其中使用箭头键从一个控件移动到下一个控件。 在第一个控件之后使用WS_GROUP样式定义的所有控件都属于同一组。 具有WS_GROUP样式的下一个控件结束样式组并启动下一个组（即，一个组结束下一个组开始的位置）。

- WS_TABSTOP 指定用户可以使用 TAB 键移动的任意数量的控件之一。 TAB 键将用户移动到WS_TABSTOP样式指定的下一个控件。

如果要将扩展窗口样式与控件一起使用，请调用[CreateEx](#createex) `Create`而不是 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>斩首：：创建Ex

创建控件（子窗口）并将其与`CHeaderCtrl`对象关联。

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
标头控件的样式。 有关标头控件样式的说明，请参阅 Windows SDK 中的[标头控件样式](/windows/win32/Controls/header-control-styles)。 有关其他样式的列表，请参阅[创建](#create)。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是`Create`应用扩展的 Windows 样式，由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>斩首：：创建拖动图像

在标题控件中创建项图像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
标头控件中项的零基索引。 分配给此项的图像是透明图像的基础。

### <a name="return-value"></a>返回值

如果成功，指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针;否则 NULL。 返回的列表仅包含一个图像。

### <a name="remarks"></a>备注

此成员函数实现 win32 消息[HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)的行为，如 Windows SDK 中所述。 它用于支持标题项的拖放。

返回`CImageList`的指针指向的对象是临时对象，并在下次空闲时处理中被删除。

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderctrl：:Delete项目

从标头控件中删除项。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要删除的项的零基索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>斩首：:D原始项目

当所有者绘制标头控件的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向描述要绘制的项的[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者绘制对象的绘图`CHeaderCtrl`。

应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>斩首：：编辑过滤器

开始编辑标头控件的指定筛选器。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
要编辑的列。

*b放弃更改*<br/>
指定在发送[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)消息时用户正在编辑筛选器时如何处理用户的编辑更改的值。

指定 TRUE 以放弃用户所做的更改，或指定 FALSE 以接受用户所做的更改。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法实现 win32 消息[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>斩首：：获取比特图保证金

检索标头控件中位图边距的宽度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>返回值

位图边距的宽度（以像素为单位）。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>斩首：：获取焦点项目

获取当前标头控件中具有焦点的项的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>返回值

具有焦点的标头项的零基索引。

### <a name="remarks"></a>备注

此方法发送[HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前标头控件`m_headerCtrl`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

以下代码示例演示 和`SetFocusedItem``GetFocusedItem`方法。 在代码的早期版本中，我们创建了一个包含五列的标头控件。 但是，您可以拖动列分隔符，以便该列不可见。 以下示例将设置，然后将最后一个列标头确认为焦点项。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>斩首：：获取图像列表

检索用于绘制标头控件中标头项的图像列表的句柄。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)的行为，如 Windows SDK 中所述。 返回`CImageList`的指针指向的对象是临时对象，并在下次空闲时处理中被删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>斩首：：获取项目

检索有关标头控件项的信息。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要检索的项的零基索引。

*pHeader项目*<br/>
指向接收新项目的[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)结构的指针。 此结构与`InsertItem`和`SetItem`成员函数一起使用。 `mask`元素中设置的任何标志都可确保在返回时正确填充相应元素中的值。 如果元素`mask`设置为零，则其他结构元素中的值毫无意义。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>斩首：：获取项目计数

检索标头控件中的项计数。

```
int GetItemCount() const;
```

### <a name="return-value"></a>返回值

标头控制项数（如果成功）;否则 - 1。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl：:DeleteItem](#deleteitem)） 的示例。

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>斩首：：获取项目下拉

获取当前标头控件中头项的下拉按钮的边界矩形。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iItem*|[在]其样式为HDF_SPLITBUTTON的标头项的从零为基础的索引。 有关详细信息，请参阅`fmt`[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)结构的成员。|
|*lpRect*|[出]指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构以接收边界矩形信息的指针。|

### <a name="return-value"></a>返回值

如果此函数成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前标头控件`m_headerCtrl`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

以下代码示例演示了该方法`GetItemDropDownRect`。 在代码的早期版本中，我们创建了一个包含五列的标头控件。 以下代码示例围绕为标题下拉按钮保留的第一列上的位置绘制一个 3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>斩首：：获取项目重新完成

检索标头控件中给定项的边界矩形。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
标头控件项的零基索引。

*lpRect*<br/>
指向接收边界矩形信息的[RECT](/windows/win32/api/windef/ns-windef-rect)结构地址的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)的行为，如 Windows SDK 中所述。

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>斩首：：获取订单数组

检索标头控件中项的从左到右的顺序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>参数

*皮拉里*<br/>
指向缓冲区地址的指针，该缓冲区接收标头控件中项的索引值，其显示顺序从左到右。

*iCount*<br/>
标头控制项数。 必须是非负数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)的行为，如 Windows SDK 中所述。 它用于支持标头项排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>斩首：：获取溢出

获取当前标头控件的溢出按钮的边界矩形。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpRect*|[出]指向接收边界矩形信息的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的指针。|

### <a name="return-value"></a>返回值

如果此函数成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果标题控件包含的项目多于可以同时显示的项，则控件可以显示一个溢出按钮，该按钮滚动到不可见的项目。 标头控件必须具有HDS_OVERFLOW和HDF_SPLITBUTTON样式才能显示溢出按钮。 边界矩形将溢出按钮封闭起来，仅在显示溢出按钮时才存在。 有关详细信息，请参阅[标题控件样式](/windows/win32/Controls/header-control-styles)。

此方法发送[HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前标头控件`m_headerCtrl`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

以下代码示例演示了该方法`GetOverflowRect`。 在代码的早期版本中，我们创建了一个包含五列的标头控件。 但是，您可以拖动列分隔符，以便该列不可见。 如果某些列不可见，则标题控件将绘制溢出按钮。 以下代码示例围绕溢出按钮的位置绘制一个 3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>斩首：：HitTest

确定指定点上的位置（如果有）标头项。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*phdhti*|[进出]指向[HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo)结构的指针，该结构指定要测试的点并接收测试结果。|

### <a name="return-value"></a>返回值

标题项的零索引（如果有）位于指定位置;否则，-1。

### <a name="remarks"></a>备注

此方法发送[HDM_HITTEST](/windows/win32/Controls/hdm-hittest)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前标头控件`m_headerCtrl`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

以下代码示例演示了该方法`HitTest`。 在本代码示例的早期版本中，我们创建了一个包含五列的标头控件。 但是，您可以拖动列分隔符，以便该列不可见。 此示例报告列的索引（如果该列为可见）和 -1（如果列不可见）。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>斩首：：插入项目

将新项目插入指定索引的标头控件。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要插入的项的索引（索引从零开始）。 如果值为零，则项将插入到标头控件的开头。 如果该值大于最大值，则项将插入到标头控件的末尾。

*菲迪*<br/>
指向[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)结构的指针，该结构包含有关要插入的项的信息。

### <a name="return-value"></a>返回值

新项目的索引（如果成功）;否则 - 1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>斩首：：布局

检索给定矩形内标头控件的大小和位置。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>参数

*pHeader布局*<br/>
指向[HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout)结构的指针，其中包含用于设置标头控件的大小和位置的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数用于确定要占用给定矩形的新标头控件的适当维度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>斩首：：订单索引

根据物料在标头控件中的顺序检索物料的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>参数

*n订单*<br/>
项从左到右显示在标头控件中的零基顺序。

### <a name="return-value"></a>返回值

项的索引，基于其在标头控件中的顺序。 索引从左到右计数，从 0 开始。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏[HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)的行为，如 Windows SDK 中所述。 它用于支持标头项排序。

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>斩首：：设置位图页距

设置标题控件中位图边距的宽度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
在现有标头控件中围绕位图的边距的宽度（以像素为单位指定）。

### <a name="return-value"></a>返回值

位图边距的宽度（以像素为单位）。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>斩首：：设置筛选器更改超时

设置筛选器属性中发生更改的时间与[发布HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange)通知之间的超时间隔。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
超时值，以毫秒为单位。

### <a name="return-value"></a>返回值

要修改的筛选器控件的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>斩首：：设置焦点项目

将焦点设置在当前标头控件中的指定标头项。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iItem*|[在]标头项的零索引。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前标头控件`m_headerCtrl`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

以下代码示例演示 和`SetFocusedItem``GetFocusedItem`方法。 在代码的早期版本中，我们创建了一个包含五列的标头控件。 但是，您可以拖动列分隔符，以便该列不可见。 以下示例将设置，然后将最后一个列标头确认为焦点项。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>斩首：：SetHotDivider

更改标题项之间的分隔符以指示标题项的手动拖放。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>参数

*pt*<br/>
指针的位置。 头控件根据指针的位置突出显示相应的分隔线。

*nIndex*<br/>
突出显示的分隔符的索引。

### <a name="return-value"></a>返回值

突出显示的分隔符的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为HDM_SETHOTDIVIDER，](/windows/win32/Controls/hdm-sethotdivider)如 Windows SDK 中所述。 它用于支持标题项的拖放。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>斩首：：设置图像列表

将图像列表分配给标头控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向包含要分配给`CImageList`标头控件的图像列表的对象的指针。

### <a name="return-value"></a>返回值

指向以前分配给标头控件的[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)的行为，如 Windows SDK 中所述。 返回`CImageList`的指针指向的对象是临时对象，并在下次空闲时处理中被删除。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl 的示例：：获取图像列表](#getimagelist)。

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>斩首：：设置项目

在标头控件中设置指定项的属性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要操作的项的零基索引。

*pHeader项目*<br/>
指向包含新项目信息的[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl 的示例：：获取项目](#getitem)。

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>斩首：：设置顺序数组

设置标头控件中项的从左到右的顺序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>参数

*iCount*<br/>
标头控制项数。

*皮拉里*<br/>
指向缓冲区地址的指针，该缓冲区接收标头控件中项的索引值，其显示顺序从左到右。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏[HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)的行为，如 Windows SDK 中所述。 它用于支持标头项排序。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl 的示例：获取Orderarray](#getorderarray)。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 类](../../mfc/reference/cimagelist-class.md)
