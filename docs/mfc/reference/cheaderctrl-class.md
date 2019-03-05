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
ms.openlocfilehash: a683c877b67f4eae1a7411f5916987c9789b6817
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261344"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 类

提供 Windows 公共标头控件的功能。

## <a name="syntax"></a>语法

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|构造 `CHeaderCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除所有筛选器的标头控件。|
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除标头控件的筛选器。|
|[CHeaderCtrl::Create](#create)|创建标头控件，并将其附加到`CHeaderCtrl`对象。|
|[Cheaderctrl:: Createdragimage](#createdragimage)|创建标头控件中的项的图像的透明版本。|
|[CHeaderCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的标头控件并将其附加到`CListCtrl`对象。|
|[CHeaderCtrl::DeleteItem](#deleteitem)|从标头控件中删除项。|
|[CHeaderCtrl::DrawItem](#drawitem)|绘制指定的标头控件的项。|
|[CHeaderCtrl::EditFilter](#editfilter)|开始编辑指定的筛选器的标头控件。|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|检索标头控件中的位图的边距的宽度。|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|获取当前具有焦点的标题控件中的项标识符。|
|[CHeaderCtrl::GetImageList](#getimagelist)|检索用于绘制控件中的标头项的图像列表的句柄。|
|[Cheaderctrl:: Getitem](#getitem)|检索标头控件中的项有关的信息。|
|[CHeaderCtrl::GetItemCount](#getitemcount)|检索标头控件中的项的计数。|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|标头控件中获取指定的下拉按钮的边界矩形信息。|
|[CHeaderCtrl::GetItemRect](#getitemrect)|检索标头控件中的给定项的边框。|
|[Cheaderctrl:: Getorderarray](#getorderarray)|检索标头控件中的项的从左到右顺序。|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|获取当前标头控件的溢出按钮的边框。|
|[CHeaderCtrl::HitTest](#hittest)|确定哪些标头项 （如果有的话，是位于指定点。|
|[Cheaderctrl:: Insertitem](#insertitem)|将新项插入到标头控件。|
|[CHeaderCtrl::Layout](#layout)|检索的大小和位置标头控件给定矩形内。|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|检索基于标头控件中的顺序的项的索引值。|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|设置标头控件中的位图的边距的宽度。|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|设置之间的时间更改发生在筛选器特性和的文章的超时间隔`HDN_FILTERCHANGE`通知。|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|将焦点设置为当前的标头控件中的指定的标头项。|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|更改标头项以指示手动之间的分隔线拖放的标头项。|
|[CHeaderCtrl::SetImageList](#setimagelist)|将图像列表分配给标头控件。|
|[Cheaderctrl:: Setitem](#setitem)|设置标头控件中的指定项的属性。|
|[Cheaderctrl:: Setorderarray](#setorderarray)|设置标头控件中项的从左到右顺序。|

## <a name="remarks"></a>备注

标头控件是一个窗口通常位于上面的一组列的文本或数字。 它包含每个列的标题和分为部分。 用户可以将分隔的各个部分，设置每列的宽度的分隔条。 标头控件的说明，请参阅[标头控件](/windows/desktop/Controls/header-controls)。

此控件 (并因此`CHeaderCtrl`类) 仅适用于 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

添加对 Windows 95/Internet Explorer 4.0 公共控件的功能包括：

- 标头项自定义排序。

- 标头项拖放，为标头项重新排序。 在创建时使用 HDS_DRAGDROP 样式`CHeaderCtrl`对象。

- 可在重设列大小不断地查看标头列文本。 在创建时使用 HDS_FULLDRAG 样式`CHeaderCtrl`对象。

- 标头的热跟踪，其中突出显示的标题项，当指针悬停于其上。 在创建时使用 HDS_HOTTRACK 样式`CHeaderCtrl`对象。

- 图像列表支持。 标头项可以包含存储在映像`CImageList`对象或文本。

有关使用详细信息`CHeaderCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl

构造 `CHeaderCtrl` 对象。

```
CHeaderCtrl();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters

清除所有筛选器的标头控件。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现的 Win32 消息的行为[HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter)列值为-1，Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

清除标头控件的筛选器。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
列指示若要清除其筛选值。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现的 Win32 消息的行为[HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

创建标头控件，并将其附加到`CHeaderCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定标头控件的样式。 标头控件样式的说明，请参阅[标头控件样式](/windows/desktop/Controls/header-control-styles)Windows SDK 中。

*rect*<br/>
指定标头控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构。

*pParentWnd*<br/>
指定标头控件的父窗口中，通常`CDialog`。 它不能为 NULL。

*nID*<br/>
指定标头控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则非零值否则为零。

### <a name="remarks"></a>备注

构造`CHeaderCtrl`两个步骤中的对象。 首先，调用构造函数，然后调用`Create`，它创建标头控件并将其附加到`CHeaderCtrl`对象。

除了标头控件样式，您可以使用以下常见控件样式以确定标头控件定位和调整自身大小的方式 (请参阅[常见控件样式](/windows/desktop/Controls/common-control-styles)有关详细信息):

- CCS_BOTTOM 导致控件来为自身定位在父窗口工作区的底部，窗口的宽度设置为父项相同的宽度。

- CCS_NODIVIDER 可防止两个像素从突出显示所绘制控件的顶部。

- CCS_NOMOVEY 导致控件来调整和响应 WM_SIZE 消息水平，但不是垂直移动本身。 如果使用 CCS_NORESIZE 样式，则此样式不适用于。 默认情况下，标头控件具有此样式。

- CCS_NOPARENTALIGN 可防止该控件自动将移动到顶部或底部的父窗口。 相反，则控件将保留在父窗口，尽管更改其位置为父窗口的大小。 如果还使用 CCS_TOP 或 CCS_BOTTOM 样式，高度调整为默认值，但位置和宽度保持不变。

- CCS_NORESIZE 可防止该控件使用的默认宽度和高度时设置其初始大小或新的大小。 相反，该控件使用的宽度和高度为创建或调整大小请求中指定。

- CCS_TOP 导致控件来为自身定位在父窗口工作区的顶部，窗口的宽度设置为父项相同的宽度。

此外可以应用以下窗口样式到标题控件 (请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)有关详细信息):

- WS_CHILD 创建子窗口。 不能用于 WS_POPUP 样式。

- WS_VISIBLE 创建初始可见的窗口。

- WS_DISABLED 创建最初处于禁用状态的窗口。

- WS_GROUP 指定一组控件在其中用户可以从一个控件移动到下的箭头键的第一个控件。 定义与 WS_GROUP 样式后的第一个控件属于相同组的所有控件。 WS_GROUP 样式的下一个控件结束样式组，并启动下一个组 （即，一组结束的地方开始下）。

- WS_TABSTOP 指定一个任意数量的通过该用户可以通过使用 TAB 键移动的控件。 TAB 键将用户移动到由 WS_TABSTOP 样式指定的下一个控件。

如果你想要在控件中使用扩展的 windows 样式，则调用[CreateEx](#createex)而不是`Create`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

创建控件 （子窗口），并将其与`CHeaderCtrl`对象。

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
指定要创建的控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
标头控件的样式。 标头控件样式的说明，请参阅[标头控件样式](/windows/desktop/Controls/header-control-styles)Windows SDK 中。 请参阅[创建](#create)有关其他样式的列表。

*rect*<br/>
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是`Create`若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。

##  <a name="createdragimage"></a>  Cheaderctrl:: Createdragimage

创建标头控件中的项的图像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在标题控件中项的从零开始索引。 分配给此项的图像是透明的图像的基础。

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)如果成功，否则该值为 NULL 的对象。 返回的列表包含只能有一个图像。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage)，如 Windows SDK 中所述。 它旨在支持标头项拖放功能。

`CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理中删除。

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

从标头控件中删除项。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要删除的项的从零开始索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

由框架在所有者绘制标头控件更改的可视方面时调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
一个指向[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)结构描述要绘制的项。

### <a name="remarks"></a>备注

`itemAction`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。

默认情况下，此成员函数没有任何影响。 重写此成员函数以实现绘制所有者描述的`CHeaderCtrl`对象。

应用程序应还原所有图形设备接口 (GDI) 对象的显示上下文中提供选定*lpDrawItemStruct*之前此成员函数将终止。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

开始编辑指定的筛选器的标头控件。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
要编辑的列。

*bDiscardChanges*<br/>
一个值，指定如何处理用户的编辑更改，如果用户正在编辑筛选器时[HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter)发送消息。

指定 TRUE，则放弃所做的更改的用户，或 FALSE 以接受用户所做的更改。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现的 Win32 消息的行为[HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

检索标头控件中的位图的边距的宽度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>返回值

以像素为单位的位图边距的宽度。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

获取在当前的标头控件具有焦点的项的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>返回值

具有焦点的标题项的从零开始的索引。

### <a name="remarks"></a>备注

此方法将发送[HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前标头控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示`SetFocusedItem`和`GetFocusedItem`方法。 在前面的代码部分，我们使用五个列创建标头控件。 但是，您可以拖动列分隔符，使该列不可见。 下面的示例设置，然后确认为焦点项的最后一个列标题。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

检索用于绘制控件中的标头项的图像列表的句柄。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist)，如 Windows SDK 中所述。 `CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理中删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>  Cheaderctrl:: Getitem

检索标头控件项目的信息。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要检索的项的从零开始索引。

*pHeaderItem*<br/>
指向[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)接收新项的结构。 此结构用于`InsertItem`和`SetItem`成员函数。 在中设置任何标志`mask`元素确保中的相应元素的值返回时正确填写。 如果`mask`元素设置为零，在其他结构元素中的值为无意义。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

检索标头控件中的项的计数。

```
int GetItemCount() const;
```

### <a name="return-value"></a>返回值

如果成功，则标头控件项目数否则为-1。

### <a name="example"></a>示例

  有关示例，请参阅[CHeaderCtrl::DeleteItem](#deleteitem)。

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

获取当前的标头控件中的标头项的下拉按钮的边框。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iItem*|[in]其样式是 HDF_SPLITBUTTON 标头项的从零开始索引。 有关详细信息，请参阅`fmt`的成员[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)结构。|
|*lpRect*|[out]指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构接收边界矩形信息。|

### <a name="return-value"></a>返回值

如果此函数成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前标头控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示了`GetItemDropDownRect`方法。 在前面的代码部分，我们使用五个列创建标头控件。 下面的代码示例的位置周围绘制三维矩形上保留的标头下拉按钮的第一列。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

检索标头控件中的给定项的边框。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
标头控件项的从零开始索引。

*lpRect*<br/>
指向的地址的指针[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界矩形信息的结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法实现的 Win32 消息的行为[HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect)，如 Windows SDK 中所述。

##  <a name="getorderarray"></a>  Cheaderctrl:: Getorderarray

检索标头控件中的项的从左到右顺序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>参数

*piArray*<br/>
指向在标头控件中，显示从左到右的顺序接收项的索引值的缓冲区的地址的指针。

*iCount*<br/>
标头控件项的数目。 必须为非负数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray)，如 Windows SDK 中所述。 它旨在支持标头项排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

获取当前标头控件的溢出按钮的边框。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpRect*|[out]指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界矩形信息的结构。|

### <a name="return-value"></a>返回值

如果此函数成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果标头控件包含更多的项超过了可同时显示，该控件可以显示溢出按钮滚动到不可见的项。 标头控件必须具有 HDS_OVERFLOW 和 HDF_SPLITBUTTON 样式，以显示溢出按钮。 边界矩形包含溢出按钮，并存在仅当显示溢出按钮。 有关详细信息，请参阅[标头控件样式](/windows/desktop/Controls/header-control-styles)。

此方法将发送[HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前标头控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示了`GetOverflowRect`方法。 在前面的代码部分，我们使用五个列创建标头控件。 但是，您可以拖动列分隔符，使该列不可见。 如果某些列不可见，标头控件绘制溢出按钮。 下面的代码示例的溢出按钮位置周围绘制一个三维矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

确定哪些标头项 （如果有的话，是位于指定点。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*phdhti*|[in、 out]指向[HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo)结构，它指定要测试的点并接收测试的结果。|

### <a name="return-value"></a>返回值

如果任何指定的位置; 处的标头项的从零开始的索引否则为-1。

### <a name="remarks"></a>备注

此方法将发送[HDM_HITTEST](/windows/desktop/Controls/hdm-hittest)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前标头控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示了`HitTest`方法。 在此代码示例的前面部分，我们使用五个列创建标头控件。 但是，您可以拖动列分隔符，使该列不可见。 此示例中报告的列的索引，如果可见和-1 如果列是不可见。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  Cheaderctrl:: Insertitem

将新项插入到指定索引处的标头控件。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要插入的项的索引（索引从零开始）。 如果值为零，标头控件的开始处插入项。 如果值大于最大值，标头控件的末尾插入项。

*phdi*<br/>
指向[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)结构，其中包含要插入的项有关的信息。

### <a name="return-value"></a>返回值

如果成功，则新项的索引否则为-1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

检索的大小和位置标头控件给定矩形内。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>参数

*pHeaderLayout*<br/>
指向[HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout)结构，其中包含用来设置的大小和位置标头控件的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数用于确定是以占据给定的矩形的新标头控件的相应维度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

检索基于标头控件中的顺序的项的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>参数

*nOrder*<br/>
从零开始的项出现在标头控件中，从左到右的顺序。

### <a name="return-value"></a>返回值

基于标头控件中的顺序的项的索引。 索引对从左到右，从 0 开始计数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏的行为[HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355)，如 Windows SDK 中所述。 它旨在支持标头项排序。

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

设置标头控件中的位图的边距的宽度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
指定以像素为单位的边距围绕现有标头控件中的位图的宽度。

### <a name="return-value"></a>返回值

以像素为单位的位图边距的宽度。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

设置之间的时间更改发生在筛选器特性和的文章的超时间隔[HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange)通知。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
超时值，以毫秒为单位。

### <a name="return-value"></a>返回值

正在修改的筛选器控件的索引。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

将焦点设置为当前的标头控件中的指定的标头项。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iItem*|[in]标头项的从零开始的索引。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_headerCtrl`，即用于访问当前标头控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示`SetFocusedItem`和`GetFocusedItem`方法。 在前面的代码部分，我们使用五个列创建标头控件。 但是，您可以拖动列分隔符，使该列不可见。 下面的示例设置，然后确认为焦点项的最后一个列标题。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

更改标头项以指示手动之间的分隔线拖放的标头项。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>参数

*pt*<br/>
指针的位置。 标头控件突出显示相应的分隔符基于指针的位置。

*nIndex*<br/>
突出显示分隔线的索引。

### <a name="return-value"></a>返回值

突出显示分隔线的索引。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider)，如 Windows SDK 中所述。 它旨在支持标头项拖放功能。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

将图像列表分配给标头控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
一个指向`CImageList`对象，其中包含要分配给标头控件的图像列表。

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)以前分配给标头控件的对象。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist)，如 Windows SDK 中所述。 `CImageList`对象向其返回的指针点是临时对象，并在下一步的空闲时间处理中删除。

### <a name="example"></a>示例

  有关示例，请参阅[CHeaderCtrl::GetImageList](#getimagelist)。

##  <a name="setitem"></a>  Cheaderctrl:: Setitem

设置标头控件中的指定项的属性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要操作的项的从零开始的索引。

*pHeaderItem*<br/>
指向[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)结构，其中包含新项目的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  有关示例，请参阅[cheaderctrl:: Getitem](#getitem)。

##  <a name="setorderarray"></a>  Cheaderctrl:: Setorderarray

设置标头控件中项的从左到右顺序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>参数

*iCount*<br/>
标头控件项的数目。

*piArray*<br/>
指向在标头控件中，显示从左到右的顺序接收项的索引值的缓冲区的地址的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏的行为[HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray)，如 Windows SDK 中所述。 它旨在支持标头项排序。

### <a name="example"></a>示例

  有关示例，请参阅[cheaderctrl:: Getorderarray](#getorderarray)。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 类](../../mfc/reference/cimagelist-class.md)
