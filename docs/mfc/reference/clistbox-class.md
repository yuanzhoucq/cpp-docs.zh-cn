---
title: CListBox 类
description: MFC CListBox 类及其成员函数的说明。
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518421"
---
# <a name="clistbox-class"></a>CListBox 类

提供 Windows 列表框功能。

## <a name="syntax"></a>语法

```
class CListBox : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|构造 `CListBox` 对象。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[CListBox::AddString](#addstring)|将字符串添加到列表框。|
|[CListBox::CharToItem](#chartoitem)|重写以为不包含字符串的所有者描述列表框提供自定义 WM_CHAR 处理。|
|[CListBox::CompareItem](#compareitem)|由框架调用，以确定新项在排序的所有者描述列表框中的位置。|
|[CListBox::Create](#create)|创建 Windows 列表框并将其附加到 `CListBox` 对象上。|
|[CListBox::DeleteItem](#deleteitem)|当用户从所有者描述的列表框中删除项时，由框架调用。|
|[CListBox::DeleteString](#deletestring)|从列表框中删除字符串。|
|[CListBox::Dir](#dir)|将当前目录中的文件名、驱动器或同时添加到列表框。|
|[CListBox::DrawItem](#drawitem)|当所有者描述列表框的视觉方面发生变化时，由框架调用。|
|[CListBox::FindString](#findstring)|搜索列表框中的字符串。|
|[CListBox::FindStringExact](#findstringexact)|查找与指定字符串匹配的第一个列表框字符串。|
|[CListBox::GetAnchorIndex](#getanchorindex)|检索列表框中当前定位项的从零开始的索引。|
|[CListBox::GetCaretIndex](#getcaretindex)|确定在多选列表框中具有聚焦框的项的索引。|
|[CListBox::GetCount](#getcount)|返回列表框中的字符串数。|
|[CListBox::GetCurSel](#getcursel)|返回列表框中当前选定字符串的从零开始的索引。|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|返回列表框可水平滚动的宽度（以像素为单位）。|
|[CListBox::GetItemData](#getitemdata)|返回与列表框项关联的值。|
|[CListBox::GetItemDataPtr](#getitemdataptr)|返回指向列表框项的指针。|
|[CListBox::GetItemHeight](#getitemheight)|确定列表框中项的高度。|
|[CListBox::GetItemRect](#getitemrect)|返回当前显示的列表框项的边框。|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|检索每个列的项数。|
|[CListBox::GetLocale](#getlocale)|检索列表框的区域设置标识符。|
|[CListBox::GetSel](#getsel)|返回列表框项的选择状态。|
|[CListBox::GetSelCount](#getselcount)|返回在多选列表框中当前选定的字符串的数目。|
|[CListBox::GetSelItems](#getselitems)|返回列表框中当前选定的字符串的索引。|
|[CListBox::GetText](#gettext)|将列表框项复制到缓冲区中。|
|[CListBox::GetTextLen](#gettextlen)|返回列表框项的长度（以字节为单位）。|
|[CListBox::GetTopIndex](#gettopindex)|返回列表框中第一个可见字符串的索引。|
|[CListBox::InitStorage](#initstorage)|列表框项和字符串的预分配内存块。|
|[CListBox::InsertString](#insertstring)|在列表框中的特定位置插入字符串。|
|[CListBox::ItemFromPoint](#itemfrompoint)|返回最接近某个点的列表框项的索引。|
|[CListBox::MeasureItem](#measureitem)|当创建所有者描述列表框以确定列表框尺寸时，由框架调用。|
|[CListBox::ResetContent](#resetcontent)|清除列表框中的所有条目。|
|[CListBox::SelectString](#selectstring)|在单项选择列表框中搜索并选择一个字符串。|
|[CListBox::SelItemRange](#selitemrange)|选择或取消选择多选列表框中的一系列字符串。|
|[CListBox::SetAnchorIndex](#setanchorindex)|设置多选列表框中的定位点以开始扩展选定内容。|
|[CListBox::SetCaretIndex](#setcaretindex)|将焦点矩形设置为多选列表框中指定索引处的项。|
|[CListBox::SetColumnWidth](#setcolumnwidth)|设置多列列表框的列宽。|
|[CListBox::SetCurSel](#setcursel)|选择列表框字符串。|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|设置列表框可水平滚动的宽度（以像素为单位）。|
|[CListBox::SetItemData](#setitemdata)|设置与列表框项关联的值。|
|[CListBox::SetItemDataPtr](#setitemdataptr)|设置指向列表框项的指针。|
|[CListBox::SetItemHeight](#setitemheight)|设置列表框中项的高度。|
|[CListBox::SetLocale](#setlocale)|设置列表框的区域设置标识符。|
|[CListBox::SetSel](#setsel)|选择或取消选择多选列表框中的列表框项。|
|[CListBox::SetTabStops](#settabstops)|在列表框中设置制表位位置。|
|[CListBox::SetTopIndex](#settopindex)|设置列表框中第一个可见字符串的从零开始的索引。|
|[CListBox::VKeyToItem](#vkeytoitem)|重写以为具有 LBS_WANTKEYBOARDINPUT 样式集的列表框提供自定义 WM_KEYDOWN 处理。|

## <a name="remarks"></a>备注

列表框显示用户可以查看和选择的项列表，如文件名。

在单项选择列表框中，用户只能选择一项。 在多选列表框中，可以选择一系列项。 当用户选择某个项时，该项将突出显示，并且列表框将向父窗口发送通知消息。

可以通过对话框模板或直接在代码中创建列表框。 若要直接创建它，请构造 `CListBox` 对象，然后调用[create](#create)成员函数以创建 Windows 列表框控件，并将其附加到 `CListBox` 对象。 若要在对话框模板中使用列表框，请在对话框类中声明列表框变量，然后在对话框类的 `DoDataExchange` 函数中使用 `DDX_Control` 将成员变量连接到控件。 （当您向对话框类添加控件变量时，会自动完成此操作。）

构造可以是派生自 `CListBox`的类中的一个单步过程。 写入派生类的构造函数，并从构造函数内调用 `Create`。

如果要将列表框发送的 Windows 通知消息处理到其父级（通常是派生自[CDialog](../../mfc/reference/cdialog-class.md)的类），请将消息映射项和消息处理程序成员函数添加到每条消息的父类。

每个消息映射项都采用以下形式：

`ON_Notification( id, memberFxn )`

其中 `id` 指定发送通知的列表框控件的子窗口 ID，`memberFxn` 是已编写用来处理通知的父成员函数的名称。

父的函数原型如下所示：

`afx_msg void memberFxn( );`

下面是可能的消息映射项的列表，以及要将它们发送到父级的情况的说明：

- ON_LBN_DBLCLK 用户双击列表框中的字符串。 只有具有[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表框才会发送此通知消息。

- ON_LBN_ERRSPACE 列表框无法分配足够的内存来满足该请求。

- ON_LBN_KILLFOCUS 列表框丢失了输入焦点。

- ON_LBN_SELCANCEL 取消当前列表框选择。 此消息仅在列表框具有 LBS_NOTIFY 样式时发送。

- ON_LBN_SELCHANGE 列表框中的选定内容已更改。 如果[CListBox：： SetCurSel](#setcursel)成员函数更改了所选内容，则不会发送此通知。 此通知仅适用于具有 LBS_NOTIFY 样式的列表框。 无论用户按箭头键，都将为多选列表框发送 LBN_SELCHANGE 通知消息，即使所选内容未更改也是如此。

- ON_LBN_SETFOCUS 列表框正在接收输入焦点。

- ON_WM_CHARTOITEM 所有者描述的列表框中没有字符串接收 WM_CHAR 消息。

- ON_WM_VKEYTOITEM 具有 LBS_WANTKEYBOARDINPUT 样式的列表框将收到 WM_KEYDOWN 消息。

如果在对话框中创建一个 `CListBox` 对象（通过对话框资源），则当用户关闭该对话框时，`CListBox` 对象将自动销毁。

如果在窗口中创建 `CListBox` 对象，可能需要销毁 `CListBox` 对象。 如果在堆栈上创建 `CListBox` 对象，则该对象会自动销毁。 如果使用**new**函数在堆上创建 `CListBox` 对象，则必须对该对象调用**delete** ，以便在用户关闭父窗口时销毁该对象。

如果在 `CListBox` 对象中分配任何内存，请重写 `CListBox` 析构函数以释放分配。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>需求

**标头:** afxwin.h

##  <a name="addstring"></a>CListBox：： AddString

将字符串添加到列表框。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
指向要添加的以 null 值结束的字符串。

### <a name="return-value"></a>返回值

列表框中的字符串的从零开始的索引。 如果发生错误，将 LB_ERR 返回值;如果没有足够的可用空间来存储新的字符串，则返回值为 LB_ERRSPACE。

### <a name="remarks"></a>备注

如果列表框不是用[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建的，则会将该字符串添加到列表的末尾。 否则，会将字符串插入列表，并对列表进行排序。 如果列表框是使用 LBS_SORT 样式而不是[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建的，则框架将通过一个或多个对 `CompareItem` 成员函数的调用来对列表进行排序。

使用[InsertString](#insertstring)将字符串插入到列表框中的特定位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>CListBox：： CharToItem

当列表框的父窗口从列表框接收到 WM_CHARTOITEM 消息时由框架调用。

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>参数

*nKey*<br/>
用户键入的字符的 ANSI 代码。

*nIndex*<br/>
列表框插入符号的当前位置。

### <a name="return-value"></a>返回值

返回-1 或-2 （表示无进一步操作）或非负数，以指定列表框项的索引，此列表框项将对其执行击键的默认操作。 默认实现返回-1。

### <a name="remarks"></a>备注

WM_CHARTOITEM 消息在收到 WM_CHAR 消息时由列表框发送，但仅当列表框满足以下所有条件时：

- 是所有者描述的列表框。

- 没有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)的样式集。

- 至少有一项。

切勿自行调用此函数。 重写此函数以提供您自己对键盘消息的自定义处理。

在重写中，必须返回一个值，告诉框架你执行的操作。 如果返回值为-1 或-2，则表示您已处理了选择项并且列表框不需要进一步操作的所有方面。 在返回-1 或-2 之前，你可以设置选择或移动插入符号，也可以同时移动。 若要设置选择，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，请使用[SetCaretIndex](#setcaretindex)。

如果返回值为0或更大，则指定列表框中项的索引，并指示列表框应为指定项上的键击执行默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox：： CListBox

构造 `CListBox` 对象。

```
CListBox();
```

### <a name="remarks"></a>备注

可以通过两个步骤构造一个 `CListBox` 对象。 首先，`ClistBox` 调用构造函数，然后调用 `Create`（初始化 Windows 列表框并将其附加到 `CListBox`）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>CListBox：： CompareItem

由框架调用，以确定新项在排序的所有者描述列表框中的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lpCompareItemStruct*<br/>
指向 `COMPAREITEMSTRUCT` 结构的长指针。

### <a name="return-value"></a>返回值

指示[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)结构中描述的两个项的相对位置。 它可以是下列值之一：

|{2&gt;值&lt;2}|含义|
|-----------|-------------|
|-1|项目1排在第2项之前。|
|0|项1和项2排序相同。|
|1|项1在项2之后排序。|

有关 `COMPAREITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) 。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 如果创建具有 LBS_SORT 样式的所有者描述的列表框，则必须重写此成员函数，以帮助框架对添加到列表框的新项进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>CListBox：： Create

创建 Windows 列表框并将其附加到 `CListBox` 对象上。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定列表框的样式。 应用[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)与框的任意组合。

*rect*<br/>
指定列表框的大小和位置。 可以是 `CRect` 对象或 `RECT` 结构。

*pParentWnd*<br/>
指定列表框的父窗口（通常为 `CDialog` 对象）。 值不得为 NULL。

*nID*<br/>
指定列表框的控件 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过两个步骤构造一个 `CListBox` 对象。 首先，调用构造函数，然后调用 `Create`，后者初始化 Windows 列表框并将其附加到 `CListBox` 对象。

当 `Create` 执行时，Windows 将向列表框控件发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息。

默认情况下，这些消息由 `CWnd` 基类中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数处理。 若要扩展默认消息处理，请从 `CListBox`中派生一个类，将消息映射添加到新类，然后重写前面的消息处理程序成员函数。 重写 `OnCreate`，例如，为新类执行所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于列表框控件。

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

- 添加垂直滚动条的 WS_VSCROLL

- WS_HSCROLL 以添加水平滚动条

- WS_GROUP 分组控件

- 允许 tab 键切换到此控件的 WS_TABSTOP

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>CListBox：:D eleteItem

当用户从所有者描述 `CListBox` 对象删除项或销毁列表框时，由框架调用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lpDeleteItemStruct*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)结构的长指针，其中包含有关已删除项的信息。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以根据需要重绘所有者描述的列表框。

有关 `DELETEITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>CListBox：:D eleteString

从列表框中删除位置*nIndex*中的项。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要删除的字符串的从零开始的索引。

### <a name="return-value"></a>返回值

列表中剩余的字符串的计数。 如果*nIndex*指定的索引大于列表中的项数，则返回值为 LB_ERR。

### <a name="remarks"></a>备注

*NIndex*后面的所有项现在都向下移动一个位置。 例如，如果列表框包含两个项，则删除第一项将导致剩余项现在位于第一个位置。 对于第一个位置中的项， *nIndex*= 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox：:D ir

将文件名、驱动器或二者的列表添加到列表框。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是 `CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)中描述的**枚举**值的任意组合，或者以下值的任意组合：

|{2&gt;值&lt;2}|含义|
|-----------|-------------|
|0x0000|可以读取或写入文件。|
|0x0001|文件可以从读取，但不能写入。|
|0x0002|文件处于隐藏状态，并且不会显示在目录列表中。|
|0x0004|文件是系统文件。|
|0x0010|*LpszWildCard*指定的名称指定目录。|
|0x0020|文件已存档。|
|0x4000|包含与*lpszWildCard*指定的名称相匹配的所有驱动器。|
|0x8000|排他标志。 如果设置了独占标志，则仅列出指定类型的文件。 否则，除了 "正常" 文件，还会列出指定类型的文件。|

*lpszWildCard*<br/>
指向文件规范字符串。 字符串可以包含通配符（例如，*.\*）。

### <a name="return-value"></a>返回值

添加到列表中的最后一个文件名的从零开始的索引。 如果发生错误，将 LB_ERR 返回值;如果没有足够的可用空间来存储新的字符串，则返回值为 LB_ERRSPACE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox：:D rawItem

当所有者描述列表框的视觉方面发生变化时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针，该指针包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT` 结构的 `itemAction` 和 `itemState` 成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现 `CListBox` 对象的所有者描述的绘图。 此成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

有关 `DRAWITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>CListBox：： FindString

查找列表框中包含指定前缀的第一个字符串，而不更改列表框选择。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nStartAfter*指定的项。 如果*nStartAfter*为-1，则从一开始就搜索整个列表框。

*lpszItem*<br/>
指向以 null 结尾的字符串，该字符串包含要搜索的前缀。 搜索不区分大小写，因此此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

匹配项的从零开始的索引; 如果搜索未成功，则 LB_ERR。

### <a name="remarks"></a>备注

使用[SelectString](#selectstring)成员函数查找并选择一个字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>CListBox：： FindStringExact

查找与*lpszFind*中指定的字符串匹配的第一个列表框字符串。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndexStart*<br/>
指定要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nIndexStart*指定的项。 如果*nIndexStart*为-1，则从一开始就搜索整个列表框。

*lpszFind*<br/>
指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名（包括扩展名）。 搜索不区分大小写，因此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

匹配项的索引; 如果搜索未成功，则为 LB_ERR。

### <a name="remarks"></a>备注

如果列表框是使用所有者描述样式创建的，但没有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则 `FindStringExact` 成员函数尝试将双字值与*lpszFind*的值匹配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>CListBox：： GetAnchorIndex

检索列表框中当前定位项的从零开始的索引。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，则为当前定位项的索引;否则 LB_ERR。

### <a name="remarks"></a>备注

在多选列表框中，定位点项是连续选定项的块中的第一项或最后一项。

### <a name="example"></a>示例

  请参阅[CListBox：： SetAnchorIndex](#setanchorindex)的示例。

##  <a name="getcaretindex"></a>CListBox：： GetCaretIndex

确定在多选列表框中具有聚焦框的项的索引。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>返回值

列表框中具有聚焦框的项的从零开始的索引。 如果列表框是单项选择列表框，则返回值是所选项（如果有）的索引。

### <a name="remarks"></a>备注

可以选择也可以不选择项。

### <a name="example"></a>示例

  请参阅[CListBox：： SetCaretIndex](#setcaretindex)的示例。

##  <a name="getcount"></a>CListBox：： GetCount

检索列表框中的项数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

列表框中的项数，如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

返回的计数比最后一项的索引值大1（索引从零开始）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>CListBox：： GetCurSel

检索单个选择列表框中当前选定项的从零开始的索引（如果有）。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

如果当前选定项是单选列表框，则为当前选定项的从零开始的索引。 如果当前未选择任何项，则 LB_ERR。

在多选列表框中，为具有焦点的项的索引。

### <a name="remarks"></a>备注

不要为多选列表框调用 `GetCurSel`。 改[为使用 CListBox：： GetSelItems](#getselitems) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox：： GetHorizontalExtent

从列表框中检索可沿水平方向滚动的宽度（以像素为单位）。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

列表框的可滚动宽度（以像素为单位）。

### <a name="remarks"></a>备注

这仅适用于列表框具有水平滚动条的情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>CListBox：： GetItemData

检索应用程序提供的与指定列表框项关联的双字值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框中项的从零开始的索引。

### <a name="return-value"></a>返回值

与项关联的值; 如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

双字值是[SetItemData](#setitemdata)调用的*dwItemData*参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>CListBox：： GetItemDataPtr

检索应用程序提供的与指定列表框项关联的32位值作为指针（**void** <strong>\*</strong>）。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框中项的从零开始的索引。

### <a name="return-value"></a>返回值

检索指针，如果发生错误，则为-1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>CListBox：： GetItemHeight

确定列表框中项的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框中项的从零开始的索引。 仅当列表框具有 LBS_OWNERDRAWVARIABLE 样式时才使用此参数;否则，它应设置为0。

### <a name="return-value"></a>返回值

列表框中项的高度（以像素为单位）。 如果列表框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则返回值为*nIndex*指定的项的高度。 如果发生错误，则返回值为 LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>CListBox：： GetItemRect

检索将列表框项绑定到列表框窗口中当前显示的框项的矩形的尺寸。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*lpRect*<br/>
指定一个指向[RECT 结构](/windows/win32/api/windef/ns-windef-rect)的长指针，该指针接收项的列表框客户端坐标。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>CListBox：： GetListBoxInfo

检索每个列的项数。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>返回值

`CListBox` 对象每列的项数。

### <a name="remarks"></a>备注

此成员函数模拟[LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo)消息的功能，如 Windows SDK 中所述。

##  <a name="getlocale"></a>CListBox：： GetLocale

检索列表框所使用的区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

列表框中的字符串的区域设置标识符（LCID）值。

### <a name="remarks"></a>备注

例如，使用区域设置来确定排序列表框中的字符串的排序顺序。

### <a name="example"></a>示例

  请参阅[CListBox：： SetLocale](#setlocale)的示例。

##  <a name="getsel"></a>CListBox：： GetSel

检索项的选择状态。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

### <a name="return-value"></a>返回值

如果选定了指定的项，则为正数;否则，为0。 如果发生错误，则返回值为 LB_ERR。

### <a name="remarks"></a>备注

此成员函数可与单选列表框和多选列表框一起使用。

若要检索当前选定的列表框项的索引，请使用[CListBox：： GetCurSel](#getcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>CListBox：： GetSelCount

检索多选列表框中选定项的总数。

```
int GetSelCount() const;
```

### <a name="return-value"></a>返回值

列表框中的选定项的计数。 如果列表框是单项选择列表框，则返回值为 LB_ERR。

### <a name="example"></a>示例

  请参阅[CListBox：： GetSelItems](#getselitems)的示例。

##  <a name="getselitems"></a>CListBox：： GetSelItems

用指定多选列表框中选定项的项编号的整数数组填充缓冲区。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>参数

*nMaxItems*<br/>
指定项号要放入缓冲区的选定项的最大数量。

*rgIndex*<br/>
指定一个指向缓冲区的指针，该指针对于*nMaxItems*指定的整数数量足够大。

### <a name="return-value"></a>返回值

放入缓冲区中的实际项数。 如果列表框是单项选择列表框，则返回值为 `LB_ERR`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>CListBox：： GetText

从列表框中获取一个字符串。

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要检索的字符串的从零开始的索引。

*lpszBuffer*<br/>
指向接收字符串的缓冲区。 缓冲区必须具有足够的空间用于字符串和终止 null 字符。 可以通过调用 `GetTextLen` 成员函数提前确定字符串的大小。

*rString*<br/>
对 `CString` 对象的引用。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止的 null 字符。 如果*nIndex*未指定有效的索引，则返回值为 LB_ERR。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用字符串文本填充 `CString` 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>CListBox：： GetTextLen

获取列表框项中的字符串的长度。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定字符串的从零开始的索引。

### <a name="return-value"></a>返回值

字符串的长度（以字符为限，不包括终止 null 字符）。 如果*nIndex*未指定有效的索引，则返回值为 LB_ERR。

### <a name="example"></a>示例

  请参阅[CListBox：： GetText](#gettext)的示例。

##  <a name="gettopindex"></a>CListBox：： GetTopIndex

检索列表框中第一个可见项的从零开始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，则为列表框中第一个可见项的从零开始的索引，LB_ERR 否则为。

### <a name="remarks"></a>备注

最初，项0位于列表框的顶部，但如果滚动列表框，则其他项可能位于顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>CListBox：： InitStorage

分配用于存储列表框项的内存。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>参数

*nItems*<br/>
指定要添加的项的数目。

*nBytes*<br/>
指定为项字符串分配的内存量（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则在需要重新分配内存之前，列表框可以存储的最大项数，否则 LB_ERRSPACE，这意味着没有足够的内存可用。

### <a name="remarks"></a>备注

在将大量项添加到 `CListBox`之前调用此函数。

此函数有助于加快具有大量项（超过100个）的列表框的初始化速度。 它预分配指定的内存量，以便后续的[AddString](#addstring)、 [InsertString](#insertstring)和[Dir](#dir)函数可以使用最短的时间。 您可以对参数使用估算值。 如果最好，则分配一些额外的内存;如果你低估，则会将常规分配用于超出预分配数量的项。

仅限 Windows 95/98： *nItems*参数限制为16位值。 这意味着列表框包含的项不能超过32767个。 尽管项目数受到限制，列表框中的项的总大小仅受可用内存的限制。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>CListBox：： InsertString

将字符串插入到列表框中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要插入字符串的位置的从零开始的索引。 如果此参数为-1，则字符串将被添加到列表的末尾。

*lpszItem*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 如果发生错误，将 LB_ERR 返回值;如果没有足够的可用空间来存储新的字符串，则返回值为 LB_ERRSPACE。

### <a name="remarks"></a>备注

与[AddString](#addstring)成员函数不同，`InsertString` 不会对具有[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>CListBox：： ItemFromPoint

确定最接近指定时间*点的列表框项。*

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
要查找其最近项的点，该点相对于列表框的工作区的左上角指定。

*bOutside*<br/>
对 BOOL 变量的引用，如果*pt*在列表框的工作区之外，该变量将设置为 TRUE，如果*pt*在列表框的工作区中，则为 FALSE。

### <a name="return-value"></a>返回值

指定为*pt*的点最近的项的索引。

### <a name="remarks"></a>备注

您可以使用此函数来确定鼠标光标移动到的列表框项。

### <a name="example"></a>示例

  请参阅[CListBox：： SetAnchorIndex](#setanchorindex)的示例。

##  <a name="measureitem"></a>CListBox：： MeasureItem

当创建具有所有者描述样式的列表框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lpMeasureItemStruct*<br/>
指向[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)结构的长指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 重写此成员函数并填充 `MEASUREITEMSTRUCT` 结构以通知窗口列表框尺寸。 如果列表框是用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建的，则框架将为列表框中的每个项调用此成员函数。 否则，此成员只调用一次。

有关使用 `CWnd`的 `SubclassDlgItem` 成员函数创建的所有者描述列表框中的[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的详细信息，请参阅[技术说明 14](../../mfc/tn014-custom-controls.md)中的讨论。

有关 `MEASUREITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>CListBox：： ResetContent

从列表框中移除所有项。

```
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>CListBox：： SelectString

搜索与指定字符串匹配的列表框项，如果找到匹配项，则选择该项。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nStartAfter*指定的项。 如果*nStartAfter*为-1，则从一开始就搜索整个列表框。

*lpszItem*<br/>
指向以 null 结尾的字符串，该字符串包含要搜索的前缀。 搜索不区分大小写，因此此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

如果搜索成功，则为选定项的索引。 如果搜索未成功，则返回值为 LB_ERR，当前所选内容不会更改。

### <a name="remarks"></a>备注

如有必要，将滚动列表框以使选定项进入查看状态。

此成员函数不能与具有[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表框一起使用。

仅当项的初始字符（从起始点）与*lpszItem*指定的字符串中的字符匹配时，才会选择该项。

在不选择项的情况下使用 `FindString` 成员函数查找字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>CListBox：： SelItemRange

选择多选列表框中的多个连续项。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>参数

*bSelect*<br/>
指定如何设置选择。 如果*bSelect*为 TRUE，则将选中并突出显示该字符串;如果为 FALSE，则移除突出显示，并且不再选择字符串。

*nFirstItem*<br/>
指定要设置的第一项的从零开始的索引。

*nLastItem*<br/>
指定要设置的最后一项的从零开始的索引。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

仅将此成员函数用于多选列表框。 如果只需要在多选列表框中选择一个项（即，如果*nFirstItem*等于*nLastItem* ），则改为调用[SetSel](#setsel)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>CListBox：： SetAnchorIndex

设置多选列表框中的定位点以开始扩展选定内容。

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定将成为定位点的列表框项的从零开始的索引。

### <a name="remarks"></a>备注

在多选列表框中，定位点项是连续选定项的块中的第一项或最后一项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>CListBox：： SetCaretIndex

将焦点矩形设置为多选列表框中指定索引处的项。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引，该索引用于接收列表框中的聚焦框。

*bScroll*<br/>
如果此值为0，则将滚动项，直到它完全可见。 如果此值不是0，则滚动项，直到至少部分可见。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

如果该项不可见，则滚动到视图中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>CListBox：： SetColumnWidth

设置多列列表框中所有列的宽度（以像素为单位）（使用[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建）。

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>参数

*cxWidth*<br/>
指定所有列的宽度（以像素为单位）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>CListBox：： SetCurSel

如果需要，选择一个字符串并将其滚动到视图中。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*nSelect*<br/>
指定要选择的字符串的从零开始的索引。 如果*选择*为-1，则将列表框设置为 "没有选择"。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

选择新字符串后，列表框将从前面选择的字符串中删除突出显示。

仅将此成员函数与单选列表框一起使用。

若要在多选列表框中设置或删除所选内容，请使用[CListBox：： SetSel](#setsel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox：： SetHorizontalExtent

设置列表框可水平滚动的宽度（以像素为单位）。

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>参数

*cxExtent*<br/>
指定列表框可水平滚动的像素数。

### <a name="remarks"></a>备注

如果列表框的大小小于此值，则水平滚动条将在列表框中水平滚动项。 如果列表框的大小大于或等于此值，则会隐藏水平滚动条。

若要响应对 `SetHorizontalExtent`的调用，必须使用[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)样式定义列表框。

此成员函数对于多列列表框不起作用。 对于多列列表框，请调用 `SetColumnWidth` 成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>CListBox：： SetItemData

设置与列表框中的指定项相关联的值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*dwItemData*<br/>
指定要与项关联的值。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>CListBox：： SetItemDataPtr

将与列表框中的指定项关联的32位值设置为指定的指针（ **void** <strong>\*</strong>）。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*pData*<br/>
指定要与项关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

此指针在列表框的生存期内保持有效，即使在添加或删除项时，列表框中的项的相对位置可能会更改。 因此，框中的项的索引可能会改变，但指针会保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>CListBox：： SetItemHeight

设置列表框中项的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框中项的从零开始的索引。 仅当列表框具有 LBS_OWNERDRAWVARIABLE 样式时才使用此参数;否则，它应设置为0。

*cyItemHeight*<br/>
指定项的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果索引或高度无效，则 LB_ERR。

### <a name="remarks"></a>备注

如果列表框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则此函数将设置*nIndex*指定的项的高度。 否则，此函数将设置列表框中所有项的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>CListBox：： SetLocale

为此列表框设置区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*nNewLocale*<br/>
要为列表框设置的新区域设置标识符（LCID）值。

### <a name="return-value"></a>返回值

此列表框的上一个区域设置标识符（LCID）值。

### <a name="remarks"></a>备注

如果未调用 `SetLocale`，则将从系统中获取默认区域设置。 可以使用 "控制面板" 的 "区域" （或 "国际"）应用程序修改此系统默认区域设置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox：： SetSel

选择多选列表框中的字符串。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的字符串的从零开始的索引。 如果为-1，则将从所有字符串中添加或删除所选内容，具体取决于*bSelect*的值。

*bSelect*<br/>
指定如何设置选择。 如果*bSelect*为 TRUE，则将选中并突出显示该字符串;如果为 FALSE，则移除突出显示，并且不再选择字符串。 默认情况下，选中并突出显示指定的字符串。

### <a name="return-value"></a>返回值

如果发生错误，则 LB_ERR。

### <a name="remarks"></a>备注

仅将此成员函数用于多选列表框。

若要从单项选择列表框中选择项，请使用[CListBox：： SetCurSel](#setcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox：： SetTabStops

在列表框中设置制表位位置。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>参数

*cxEachStop*<br/>
在每个*cxEachStop*对话框单位设置制表位。 有关对话单位的说明，请参阅*rgTabStops* 。

*nTabStops*<br/>
指定列表框中的制表位的数目。

*rgTabStops*<br/>
指向整数数组的第一个成员，其中包含对话框单位中的制表位位置。 对话单位为水平或垂直距离。 一个水平对话框单位等于当前 "对话框基本宽度单位" 的四分之一，一个垂直对话单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 `GetDialogBaseUnits` Windows 函数返回当前的对话框基本单位（以像素为单位）。 制表位必须按递增顺序排序;不允许使用 back 选项卡。

### <a name="return-value"></a>返回值

如果设置了所有选项卡，则为非零值;否则为0。

### <a name="remarks"></a>备注

若要将制表位设置为默认大小2个对话框单位，请调用此成员函数的无参数版本。 若要将制表位设置为除2以外的大小，请使用*cxEachStop*参数调用该版本。

若要将制表位设置为大小数组，请使用带有*rgTabStops*和*nTabStops*参数的版本。 将为*rgTabStops*中的每个值设置一个制表位，直到*nTabStops*指定的数字为止。

若要响应对 `SetTabStops` 成员函数的调用，必须使用[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建列表框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>CListBox：： SetTopIndex

确保特定列表框项可见。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则为零; 如果发生错误，则为 LB_ERR。

### <a name="remarks"></a>备注

系统将滚动列表框，直到*nIndex*指定的项显示在列表框的顶部或已达到最大滚动范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>CListBox：： VKeyToItem

当列表框的父窗口从列表框接收到 WM_VKEYTOITEM 消息时由框架调用。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>参数

*nKey*<br/>
用户按下的键的虚拟键代码。 有关标准虚拟键代码的列表，请参阅 Winuser。h

*nIndex*<br/>
列表框插入符号的当前位置。

### <a name="return-value"></a>返回值

对于 "无进一步" 操作返回-2; 对于默认操作，返回-1; 如果为非零值，则指定要对其执行键击默认操作的列表框项的索引。

### <a name="remarks"></a>备注

WM_VKEYTOITEM 消息在收到 WM_KEYDOWN 消息时由列表框发送，但仅当列表框同时满足以下两个内容时：

- 具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式集。

- 至少有一项。

切勿自行调用此函数。 重写此函数以提供您自己对键盘消息的自定义处理。

必须返回一个值，以告知框架要执行的操作的操作。 如果返回值为-2，则表示应用程序处理了选择该项的所有方面，并且列表框不需要执行任何其他操作。 在返回-2 之前，你可以设置选择或移动插入符号或同时移动。 若要设置选择，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移动插入符号，请使用[SetCaretIndex](#setcaretindex)。

返回值-1 指示列表框应执行默认操作以响应击键。默认实现返回-1。

如果返回值为0或更大，则指定列表框中项的索引，并指示列表框应为指定项上的键击执行默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)
