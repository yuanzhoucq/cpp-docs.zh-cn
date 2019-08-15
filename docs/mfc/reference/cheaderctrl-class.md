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
ms.openlocfilehash: 407ba2747ed4d6e56e56fe4ccb2ccb828240a732
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506711"
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
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除标头控件的所有筛选器。|
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除标头控件的筛选器。|
|[CHeaderCtrl::Create](#create)|创建标头控件, 并将其附加`CHeaderCtrl`到对象。|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|在标头控件内创建项图像的透明版本。|
|[CHeaderCtrl::CreateEx](#createex)|创建具有指定 Windows 扩展样式的标头控件, 并将其附加`CListCtrl`到对象。|
|[CHeaderCtrl::DeleteItem](#deleteitem)|删除标头控件中的项。|
|[CHeaderCtrl::DrawItem](#drawitem)|绘制标头控件的指定项。|
|[CHeaderCtrl::EditFilter](#editfilter)|开始编辑指定的标头控件筛选器。|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|检索标头控件中位图的边距宽度。|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|获取当前标头控件中具有焦点的项的标识符。|
|[CHeaderCtrl::GetImageList](#getimagelist)|检索用于在标题控件中绘制标题项的图像列表的句柄。|
|[CHeaderCtrl::GetItem](#getitem)|检索有关标头控件中的项的信息。|
|[CHeaderCtrl::GetItemCount](#getitemcount)|检索标头控件中项的计数。|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|获取标头控件中指定下拉按钮的边框信息。|
|[CHeaderCtrl::GetItemRect](#getitemrect)|检索标头控件中给定项的边框。|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|检索标头控件中项的从左到右顺序。|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|获取当前标头控件的溢出按钮的边框。|
|[CHeaderCtrl::HitTest](#hittest)|确定位于指定点处的标头项 (如果有)。|
|[CHeaderCtrl::InsertItem](#insertitem)|在标头控件中插入新项。|
|[CHeaderCtrl::Layout](#layout)|检索给定矩形内的标头控件的大小和位置。|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|基于项在标头控件中的顺序检索项的索引值。|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|设置标题控件中位图的边距宽度。|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|设置筛选器属性中发生更改和发布`HDN_FILTERCHANGE`通知之间的超时时间间隔。|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|将焦点设置到当前标头控件中的指定标头项。|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|更改标头项之间的分隔符, 以指示手动拖放标头项。|
|[CHeaderCtrl::SetImageList](#setimagelist)|将图像列表分配给标头控件。|
|[CHeaderCtrl::SetItem](#setitem)|设置标头控件中指定项的属性。|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|设置标头控件中项的从左到右的顺序。|

## <a name="remarks"></a>备注

标头控件是一个窗口, 该窗口通常位于一组文本或数字的列的上方。 它包含每一列的标题, 并可划分为多个部分。 用户可以拖动分隔部分的分隔线, 设置每列的宽度。 有关标头控件的图例, 请参阅[标题控件](/windows/win32/Controls/header-controls)。

此控件 (因而`CHeaderCtrl`类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

为 Windows 95/Internet Explorer 4.0 公共控件添加的功能包括:

- 标头项自定义排序。

- 用于标题项的重新排序的标头项拖放。 创建`CHeaderCtrl`对象时使用 HDS_DRAGDROP 样式。

- 在列大小调整期间, 标题列文本可持续查看。 创建`CHeaderCtrl`对象时使用 HDS_FULLDRAG 样式。

- 标头热跟踪, 当指针悬停在标题项上方时, 将突出显示该标头项。 创建`CHeaderCtrl`对象时使用 HDS_HOTTRACK 样式。

- 图像列表支持。 标头项可以包含`CImageList`对象或文本中存储的图像。

有关使用`CHeaderCtrl`的详细信息, 请参阅[控件](../../mfc/controls-mfc.md)和[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cheaderctrl"></a>CHeaderCtrl:: CHeaderCtrl

构造 `CHeaderCtrl` 对象。

```
CHeaderCtrl();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>CHeaderCtrl:: ClearAllFilters

清除标头控件的所有筛选器。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行为, 其列值为-1, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

清除标头控件的筛选器。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
指示要清除的筛选器的列值。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>CHeaderCtrl:: Create

创建标头控件, 并将其附加`CHeaderCtrl`到对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定标头控件的样式。 有关标头控件样式的说明, 请参阅 Windows SDK 中的[标题控件样式](/windows/win32/Controls/header-control-styles)。

*rect*<br/>
指定标头控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pParentWnd*<br/>
指定标头控件的父窗口 (通常为`CDialog`)。 它不能为 NULL。

*nID*<br/>
指定标头控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为零。

### <a name="remarks"></a>备注

可以通过`CHeaderCtrl`两个步骤构造对象。 首先, 调用构造函数, 然后调用`Create`, 它会创建标头控件并将其附加`CHeaderCtrl`到对象。

除了标头控件样式以外, 还可以使用以下公共控件样式来确定标头控件的位置和大小 (有关详细信息, 请参阅[公共控件样式](/windows/win32/Controls/common-control-styles)):

- CCS_BOTTOM 使控件将自身定位在父窗口的工作区的底部, 并将宽度设置为与父窗口的宽度相同。

- CCS_NODIVIDER 防止在控件的顶部绘制两像素的突出显示。

- CCS_NOMOVEY 导致控件调整大小并水平移动, 但不会在响应 WM_SIZE 消息时垂直移动。 如果使用了 CCS_NORESIZE 样式, 则不应用此样式。 默认情况下, 标头控件具有此样式。

- CCS_NOPARENTALIGN 可防止控件自动移动到父窗口的顶部或底部。 相反, 无论父窗口的大小发生更改, 控件都将保留其在父窗口中的位置。 如果还使用 CCS_TOP 或 CCS_BOTTOM 样式, 则高度将调整为默认值, 但位置和宽度保持不变。

- CCS_NORESIZE 在设置初始大小或新大小时, 防止控件使用默认的宽度和高度。 相反, 控件使用请求中指定的宽度和高度来创建或调整大小。

- CCS_TOP 使控件将自身定位在父窗口的工作区顶部, 并将宽度设置为与父窗口的宽度相同。

还可以将以下窗口样式应用于标题控件 (有关详细信息, 请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)):

- WS_CHILD 创建子窗口。 不能与 WS_POPUP 样式一起使用。

- WS_VISIBLE 创建一个最初可见的窗口。

- WS_DISABLED 创建一个最初处于禁用状态的窗口。

- WS_GROUP 指定一组控件的第一个控件, 用户可以使用箭头键从一个控件移动到下一个控件。 在第一个控件属于同一组后, 所有用 WS_GROUP 样式定义的控件。 具有 WS_GROUP 样式的下一个控件将结束样式组, 并启动下一组 (即, 一个组在下一次开始时结束)。

- WS_TABSTOP 指定任意数量的控件, 用户可以使用 TAB 键移动这些控件。 TAB 键将用户移动到 WS_TABSTOP 样式指定的下一个控件。

如果要在控件中使用扩展的 windows 样式, 请调用[CreateEx](#createex)而不`Create`是。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl:: CreateEx

创建一个控件 (子窗口) 并将其与`CHeaderCtrl`对象关联。

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
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表, 请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
标头控件的样式。 有关标头控件样式的说明, 请参阅 Windows SDK 中的[标题控件样式](/windows/win32/Controls/header-control-styles)。 有关其他样式的列表, 请参阅[创建](#create)。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构描述要创建的窗口的大小和位置 (以*pParentWnd*的工作区坐标表示)。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是来应用扩展的windows样式,由windows扩展样式指定的WS_EX_。`Create`

##  <a name="createdragimage"></a>CHeaderCtrl:: CreateDragImage

在标头控件内创建项图像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
标头控件中项的从零开始的索引。 为此项分配的图像是透明图像的基础。

### <a name="return-value"></a>返回值

如果成功, 则为指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针;否则为 NULL。 返回的列表仅包含一个图像。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)的行为, 如 Windows SDK 中所述。 提供它是为了支持标头项拖放。

返回的指针指向的对象是临时对象,并在下一次空闲时处理时删除。`CImageList`

##  <a name="deleteitem"></a>CHeaderCtrl::D eleteItem

删除标头控件中的项。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要删除的项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>CHeaderCtrl::D rawItem

当所有者描述的标题控件的可视方位发生更改时由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针, 该结构描述要绘制的项。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构的成员定义要执行的绘图操作。 `itemAction`

默认情况下, 此成员函数不执行任何操作。 重写此成员函数以实现所有者描述`CHeaderCtrl`对象的绘制。

此成员函数终止之前, 应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 (GDI) 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>CHeaderCtrl:: EditFilter

开始编辑指定的标头控件的筛选器。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>参数

*nColumn*<br/>
要编辑的列。

*bDiscardChanges*<br/>
一个值, 指定当发送[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)消息时用户正在编辑筛选器的过程中, 如何处理用户的编辑更改。

指定 TRUE 以放弃用户所做的更改, 或指定 FALSE 以接受用户所做的更改。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>CHeaderCtrl:: GetBitmapMargin

检索标头控件中位图的边距宽度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>返回值

位图边距的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>CHeaderCtrl:: GetFocusedItem

获取在当前标头控件中具有焦点的项的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>返回值

具有焦点的标头项的从零开始的索引。

### <a name="remarks"></a>备注

此方法发送[HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_headerCtrl`标头控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示了`SetFocusedItem`和`GetFocusedItem`方法。 在代码的前面部分中, 我们创建了一个包含五个列的标题控件。 但是, 您可以拖动列分隔符, 使列不可见。 下面的示例设置并确认最后一个列标题为焦点项。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>CHeaderCtrl:: GetImageList

检索用于在标题控件中绘制标题项的图像列表的句柄。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)的行为, 如 Windows SDK 中所述。 返回的指针指向的对象是临时对象,并在下一次空闲时处理时删除。`CImageList`

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>CHeaderCtrl:: GetItem

检索有关标头控件项的信息。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定要检索的项的从零开始的索引。

*pHeaderItem*<br/>
指向接收新项的[HDITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw)结构的指针。 此结构与`InsertItem`和`SetItem`成员函数结合使用。 `mask`元素中设置的任何标志都确保返回时正确填充相应元素中的值。 `mask`如果元素设置为零, 则其他结构元素中的值毫无意义。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>CHeaderCtrl:: GetItemCount

检索标头控件中项的计数。

```
int GetItemCount() const;
```

### <a name="return-value"></a>返回值

如果成功, 则为标头控件项的数目;否则为-1。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl::D eleteitem](#deleteitem)的示例。

##  <a name="getitemdropdownrect"></a>CHeaderCtrl:: GetItemDropDownRect

获取当前标头控件中的标题项的下拉按钮的边框。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iItem*|中其样式为 HDF_SPLITBUTTON 的标头项的从零开始的索引。 有关详细信息, 请参阅`fmt` [HDITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw)结构的成员。|
|*lpRect*|弄一个指针, 指向用于接收边框信息的[RECT](/previous-versions/dd162897\(v=vs.85\))结构。|

### <a name="return-value"></a>返回值

如果此函数成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_headerCtrl`标头控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示`GetItemDropDownRect`方法。 在代码的前面部分中, 我们创建了一个包含五个列的标题控件。 下面的代码示例在为标头下拉按钮保留的第一列上的位置周围绘制一个三维矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>CHeaderCtrl:: GetItemRect

检索标头控件中给定项的边框。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
标头控件项的从零开始的索引。

*lpRect*<br/>
一个指针, 指向用于接收边框信息的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的地址。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法实现 Win32 消息[HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)的行为, 如 Windows SDK 中所述。

##  <a name="getorderarray"></a>CHeaderCtrl:: GetOrderArray

检索标头控件中项的从左到右顺序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>参数

*piArray*<br/>
指向缓冲区的地址的指针, 该缓冲区接收标头控件中项的索引值 (按照它们从左到右的显示顺序)。

*iCount*<br/>
标头控件项的数目。 必须为非负数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)的行为, 如 Windows SDK 中所述。 提供它是为了支持标头项排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>CHeaderCtrl:: GetOverflowRect

获取当前标头控件的溢出按钮的边框。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpRect*|弄一个指针, 指向用于接收边框信息的[RECT](/previous-versions/dd162897\(v=vs.85\))结构。|

### <a name="return-value"></a>返回值

如果此函数成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果标题控件包含的项数超过了可以同时显示的项数, 则控件可以显示一个滚动到不可见项的溢出按钮。 标头控件必须具有 HDS_OVERFLOW 和 HDF_SPLITBUTTON 样式, 才能显示溢出按钮。 边框包含溢出按钮, 仅当显示溢出按钮时才存在。 有关详细信息, 请参阅[标题控件样式](/windows/win32/Controls/header-control-styles)。

此方法发送[HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_headerCtrl`标头控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示`GetOverflowRect`方法。 在代码的前面部分中, 我们创建了一个包含五个列的标题控件。 但是, 您可以拖动列分隔符, 使列不可见。 如果某些列不可见, 则标头控件将绘制溢出按钮。 下面的代码示例在溢出按钮的位置周围绘制一个三维矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>CHeaderCtrl:: System.windows.media.visualtreehelper.hittest

确定位于指定点处的标头项 (如果有)。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*phdhti*|[in, out]指向[HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-_hd_hittestinfo)结构的指针, 该结构指定测试和接收测试结果的点。|

### <a name="return-value"></a>返回值

位于指定位置的标头项的从零开始的索引 (如果有);否则为-1。

### <a name="remarks"></a>备注

此方法发送[HDM_HITTEST](/windows/win32/Controls/hdm-hittest)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_headerCtrl`标头控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示`HitTest`方法。 在此代码示例的前面部分中, 我们创建了一个包含五个列的标题控件。 但是, 您可以拖动列分隔符, 使列不可见。 如果该列可见, 此示例将报告该列的索引; 如果列不可见, 则为-1。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>CHeaderCtrl:: InsertItem

在标头控件中的指定索引处插入一个新项。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要插入的项的索引（索引从零开始）。 如果值为零, 则在标头控件的开头插入该项。 如果该值大于最大值, 则会在标头控件的末尾插入该项。

*phdi*<br/>
指向[HDITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw)结构的指针, 该结构包含要插入的项的相关信息。

### <a name="return-value"></a>返回值

如果成功, 则为新项的索引;否则为-1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>CHeaderCtrl:: Layout

检索给定矩形内的标头控件的大小和位置。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>参数

*pHeaderLayout*<br/>
指向[HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-_hd_layout)结构的指针, 该结构包含用于设置标头控件的大小和位置的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数用于为要占用给定矩形的新标头控件确定适当的维度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

基于项在标头控件中的顺序检索项的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>参数

*nOrder*<br/>
项在标题控件中显示的从零开始的顺序, 从左到右。

### <a name="return-value"></a>返回值

项的索引, 它基于其在标头控件中的顺序。 索引从左到右, 从0开始计数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏[HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)的行为, 如 Windows SDK 中所述。 提供它是为了支持标头项排序。

##  <a name="setbitmapmargin"></a>CHeaderCtrl:: SetBitmapMargin

设置标题控件中位图的边距宽度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
现有标题控件内的位图周围的边距的宽度 (以像素为单位指定)。

### <a name="return-value"></a>返回值

位图边距的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>CHeaderCtrl:: SetFilterChangeTimeout

设置筛选器属性中发生更改和发布[HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange)通知之间的超时时间间隔。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>参数

*dwTimeOut*<br/>
超时值 (以毫秒为单位)。

### <a name="return-value"></a>返回值

正在修改的筛选器控件的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>CHeaderCtrl:: SetFocusedItem

将焦点设置到当前标头控件中的指定标头项。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iItem*|中标头项的从零开始的索引。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_headerCtrl`标头控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>示例

下面的代码示例演示了`SetFocusedItem`和`GetFocusedItem`方法。 在代码的前面部分中, 我们创建了一个包含五个列的标题控件。 但是, 您可以拖动列分隔符, 使列不可见。 下面的示例设置并确认最后一个列标题为焦点项。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>CHeaderCtrl:: SetHotDivider

更改标头项之间的分隔符, 以指示手动拖放标头项。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>参数

*pt*<br/>
指针的位置。 标头控件基于指针的位置突出显示相应的分隔线。

*nIndex*<br/>
突出显示的分隔线的索引。

### <a name="return-value"></a>返回值

突出显示的分隔线的索引。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)的行为, 如 Windows SDK 中所述。 提供它是为了支持标头项拖放。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>CHeaderCtrl:: SetImageList

将图像列表分配给标头控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向`CImageList`对象的指针, 该对象包含要分配给标头控件的图像列表。

### <a name="return-value"></a>返回值

指向之前分配给标头控件的[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)的行为, 如 Windows SDK 中所述。 返回的指针指向的对象是临时对象,并在下一次空闲时处理时删除。`CImageList`

### <a name="example"></a>示例

  请参阅[CHeaderCtrl:: GetImageList](#getimagelist)的示例。

##  <a name="setitem"></a>CHeaderCtrl:: SetItem

设置标头控件中指定项的属性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>参数

*nPos*<br/>
要操作的项的从零开始的索引。

*pHeaderItem*<br/>
指向[HDITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw)结构的指针, 该结构包含有关新项的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl:: GetItem](#getitem)的示例。

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

设置标头控件中项的从左到右的顺序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>参数

*iCount*<br/>
标头控件项的数目。

*piArray*<br/>
指向缓冲区的地址的指针, 该缓冲区接收标头控件中项的索引值 (按照它们从左到右的显示顺序)。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 宏[HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)的行为, 如 Windows SDK 中所述。 提供它是为了支持标头项排序。

### <a name="example"></a>示例

  请参阅[CHeaderCtrl:: GetOrderArray](#getorderarray)的示例。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 类](../../mfc/reference/cimagelist-class.md)
