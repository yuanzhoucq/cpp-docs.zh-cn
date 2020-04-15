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
ms.openlocfilehash: 5bc66ab2775ebb9023c65c9decae205604c978c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372229"
---
# <a name="clistbox-class"></a>CListBox 类

提供 Windows 列表框功能。

## <a name="syntax"></a>语法

```
class CListBox : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CListBox：CListBox](#clistbox)|构造 `CListBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CListBox::AddString](#addstring)|将字符串添加到列表框。|
|[CListBox：：查理斯](#chartoitem)|覆盖以为没有字符串的所有者绘制列表框提供自定义WM_CHAR处理。|
|[CListBox：比较项目](#compareitem)|由框架调用以确定新项目在排序的所有者绘制列表框中的位置。|
|[CListBox：创建](#create)|创建 Windows 列表框并将其附加到`CListBox`对象。|
|[CListBox：:Delete项目](#deleteitem)|当用户从所有者绘制列表框中删除项目时，由框架调用。|
|[CListBox：:DeleteString](#deletestring)|从列表框中删除字符串。|
|[CListBox：:Dir](#dir)|将文件名、驱动器或两者从当前目录添加到列表框。|
|[CListBox：:D原始项目](#drawitem)|当所有者绘制列表框的可视方面发生更改时，由框架调用。|
|[CListBox：：查找字符串](#findstring)|在列表框中搜索字符串。|
|[CListBox：：查找字符串精确](#findstringexact)|查找与指定字符串匹配的第一个列表框字符串。|
|[CListBox：获取锚定索引](#getanchorindex)|在列表框中检索当前锚点项的零基索引。|
|[CListBox：获取关怀索引](#getcaretindex)|确定在多选择列表框中具有焦点矩形的项的索引。|
|[CListBox：获取计数](#getcount)|返回列表框中的字符串数。|
|[CListBox：获取CurSel](#getcursel)|在列表框中返回当前所选字符串的零基索引。|
|[CListBox：获取水平范围](#gethorizontalextent)|返回列表框可以水平滚动的宽度。|
|[CListBox：获取项目数据](#getitemdata)|返回与列表框项关联的值。|
|[CListBox：获取项目数据Ptr](#getitemdataptr)|返回指向列表框项的指针。|
|[CListBox：获取项目高度](#getitemheight)|确定列表框中项目的高度。|
|[CListBox：获取项目已重新完成](#getitemrect)|返回列表框项当前显示的边界矩形。|
|[CListBox：获取列表框信息](#getlistboxinfo)|检索每列的项目数。|
|[CListBox：获取本地化](#getlocale)|检索列表框的区域设置标识符。|
|[CListBox：GetSel](#getsel)|返回列表框项的选择状态。|
|[CListBox：获取塞尔计数](#getselcount)|返回在多选列表框中当前选择的字符串数。|
|[CListBox：获取塞尔项目](#getselitems)|返回当前在列表框中选择的字符串的索引。|
|[CListBox：获取文本](#gettext)|将列表框项复制到缓冲区中。|
|[CListBox：获取文本](#gettextlen)|返回列表框项的长度（以字节为单位）。|
|[CListBox：获取热门索引](#gettopindex)|返回列表框中第一个可见字符串的索引。|
|[CListBox：：在内存储](#initstorage)|预分配列表框项和字符串的内存块。|
|[CListBox::InsertString](#insertstring)|在列表框中在特定位置插入字符串。|
|[CListBox：项目从点](#itemfrompoint)|返回离点最近的列表框项的索引。|
|[CListBox：测量项目](#measureitem)|创建所有者绘制列表框以确定列表框维度时，由框架调用。|
|[CListBox：重置内容](#resetcontent)|清除列表框中的所有条目。|
|[CListBox：选择字符串](#selectstring)|在单选列表框中搜索并选择字符串。|
|[CListBox：：塞尔项目范围](#selitemrange)|在多选列表框中选择或取消选择一系列字符串。|
|[CListBox：：设置锚定索引](#setanchorindex)|在多选列表框中设置锚点以开始扩展选择。|
|[CListBox：：设置关怀索引](#setcaretindex)|在多选列表框中将焦点矩形设置到指定索引处的项。|
|[列表框：：设置列宽](#setcolumnwidth)|设置多列列表框的列宽度。|
|[CListBox：：设置CurSel](#setcursel)|选择列表框字符串。|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|设置列表框可以水平滚动的像素宽度。|
|[CListBox：设置项目数据](#setitemdata)|设置与列表框项关联的值。|
|[CListBox：：设置项目数据Ptr](#setitemdataptr)|设置指向列表框项的指针。|
|[CListBox：设置项目高度](#setitemheight)|在列表框中设置项目的高度。|
|[CListBox：：设置本地化](#setlocale)|设置列表框的区域设置标识符。|
|[CListBox：：设置塞尔](#setsel)|在多选列表框中选择或取消选择列表框项。|
|[CListBox：：设置标签](#settabstops)|在列表框中设置制表位。|
|[CListBox：：设置顶索引](#settopindex)|设置列表框中第一个可见字符串的零基索引。|
|[CListBox：：Vkeyto项目](#vkeytoitem)|覆盖以提供具有LBS_WANTKEYBOARDINPUT样式集的列表框的自定义WM_KEYDOWN处理。|

## <a name="remarks"></a>备注

列表框显示用户可以查看和选择的项目列表（如文件名）。

在单选列表框中，用户只能选择一个项目。 在多选列表框中，可以选择一系列项目。 当用户选择项目时，它将突出显示，列表框向父窗口发送通知消息。

可以从对话框模板或直接在代码中创建列表框。 要直接创建它，请构造`CListBox`对象，然后调用[Create](#create)成员函数以创建 Windows 列表框控件并将其附加到`CListBox`对象。 要在对话框模板中使用列表框，请声明对话框类中的列表框变量，然后在对话框类的`DDX_Control``DoDataExchange`函数中使用将成员变量连接到控件。 （当您向对话框类添加控件变量时，会自动为您完成此操作。

构造可以是派生自`CListBox`的类中的一个步骤。 为派生类编写一个构造函数，并从`Create`构造函数内部调用。

如果要处理列表框发送到其父项的 Windows 通知消息（通常是从[CDialog](../../mfc/reference/cdialog-class.md)派生的类），则为每个消息向父类添加消息映射条目和消息处理程序成员函数。

每个消息映射条目采用以下形式：

`ON_Notification( id, memberFxn )`

其中`id`指定发送通知的列表框控件的子窗口 ID，以及`memberFxn`您为处理通知而编写的父成员函数的名称。

父函数原型如下所示：

`afx_msg void memberFxn( );`

以下是潜在消息映射条目的列表，以及将它们发送到父项的情况说明：

- ON_LBN_DBLCLK 用户双击列表框中的字符串。 只有具有[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表框才会发送此通知消息。

- ON_LBN_ERRSPACE 列表框无法分配足够的内存以满足请求。

- ON_LBN_KILLFOCUS 列表框正在失去输入焦点。

- ON_LBN_SELCANCEL取消当前列表框选择。 仅当列表框具有LBS_NOTIFY样式时，才会发送此消息。

- ON_LBN_SELCHANGE 列表框中的选择已更改。 如果[CListBox：setCurSel](#setcursel)成员函数更改了所选内容，则不会发送此通知。 此通知仅适用于具有LBS_NOTIFY样式的列表框。 当用户按箭头键时，都会为多选择列表框发送LBN_SELCHANGE通知消息，即使所选内容没有变化也是如此。

- ON_LBN_SETFOCUS 列表框正在接收输入焦点。

- ON_WM_CHARTOITEM没有字符串的所有者绘制列表框会收到WM_CHAR消息。

- ON_WM_VKEYTOITEM具有LBS_WANTKEYBOARDINPUT样式的列表框接收WM_KEYDOWN消息。

如果在对话框中创建`CListBox`对象（通过对话框资源），则当用户关闭对话框时，`CListBox`该对象将自动销毁。

如果在窗口中创建`CListBox`对象，则可能需要销毁该`CListBox`对象。 如果在堆栈上`CListBox`创建对象，则会自动销毁该对象。 如果使用新函数在`CListBox`堆上创建对象，则必须调用**new**对象**上的 delete**以在用户关闭父窗口时销毁该对象。

如果在`CListBox`对象中分配任何内存，请重写`CListBox`析构函数以释放分配。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox：：添加字符串

将字符串添加到列表框。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
指向要添加的 null 终止字符串。

### <a name="return-value"></a>返回值

列表框中字符串的零基索引。 如果发生错误，返回值将LB_ERR;如果没有足够的空间来存储新字符串，则返回值LB_ERRSPACE。

### <a name="remarks"></a>备注

如果未使用[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建列表框，则字符串将添加到列表的末尾。 否则，字符串将插入到列表中，并排序列表。 如果列表框使用LBS_SORT样式创建，但未创建[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则框架将按对成员函数的`CompareItem`一个或多个调用对列表进行排序。

使用[InsertString](#insertstring)将字符串插入到列表框中的特定位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox：：查理斯

当列表框的父窗口从列表框中接收WM_CHARTOITEM消息时，由框架调用。

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>参数

*n键*<br/>
用户键入的字符的 ANSI 代码。

*nIndex*<br/>
列表框的当前位置。

### <a name="return-value"></a>返回值

返回 - 1 或 - 2，无需进一步操作或非负数来指定列表框项的索引，以执行击键的默认操作。 默认实现返回 - 1。

### <a name="remarks"></a>备注

WM_CHARTOITEM消息在收到WM_CHAR消息时由列表框发送，但仅当列表框满足以下所有条件时：：

- 是所有者绘制列表框。

- 没有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式集。

- 至少有一个项目。

您绝不应自行调用此功能。 重写此函数以提供您自己的键盘消息的自定义处理。

在重写中，必须返回一个值，告诉框架您执行了哪些操作。 返回值 - 1 或 - 2 表示您处理了选择项的所有方面，并且不需要列表框执行进一步操作。 在返回 - 1 或 - 2 之前，您可以设置选择或移动 caret 或两者。 要设置选择，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 要移动 caret，请使用[SetCaretIndex](#setcaretindex)。

返回值 0 或更高指定列表框中项的索引，并指示列表框应对给定项执行击键的默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox：CListBox

构造 `CListBox` 对象。

```
CListBox();
```

### <a name="remarks"></a>备注

分两步`CListBox`构造对象。 首先调用构造函数`ClistBox`，然后调用`Create`，该调用将初始化 Windows 列表框并将其附加到 。 `CListBox`

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox：比较项目

由框架调用以确定新项目在排序的所有者绘制列表框中的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lp比较项目结构*<br/>
指向结构的长`COMPAREITEMSTRUCT`指针。

### <a name="return-value"></a>返回值

指示[比较项目结构](/windows/win32/api/winuser/ns-winuser-compareitemstruct)中描述的两个项目的相对位置。 它可能是以下任何值：

|“值”|含义|
|-----------|-------------|
|-1|项目 1 在项目 2 之前排序。|
|0|项目 1 和项目 2 排序相同。|
|1|项目 1 在项目 2 之后排序。|

有关`COMPAREITEMSTRUCT`结构的说明，请参阅[CWnd：On比较项目](../../mfc/reference/cwnd-class.md#oncompareitem)。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 如果使用LBS_SORT样式创建所有者绘制列表框，则必须重写此成员函数，以帮助框架对添加到列表框的新项进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox：创建

创建 Windows 列表框并将其附加到`CListBox`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定列表框的样式。 将[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)的任意组合应用于该框。

*矩形*<br/>
指定列表框大小和位置。 可以是`CRect`对象或`RECT`结构。

*pparentwnd*<br/>
指定列表框的父窗口（通常是`CDialog`对象）。 值不得为 NULL。

*nID*<br/>
指定列表框的控制 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两步`CListBox`构造对象。 首先调用构造函数，然后调用`Create`，该调用将初始化 Windows 列表框并将其附加到`CListBox`对象。

执行`Create`时，Windows 会将[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息发送到列表框控件。 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)

默认情况下，这些消息`CWnd`由基类中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数处理。 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate) [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) 要扩展默认消息处理，从`CListBox`派生类，向新类添加消息映射，并重写前面的消息处理程序成员函数。 例如`OnCreate`，重写以执行新类所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于列表框控件。

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL 添加垂直滚动条

- WS_HSCROLL 添加水平滚动条

- WS_GROUP组控件

- WS_TABSTOP 允许选项卡到此控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox：:Delete项目

当用户从所有者绘制`CListBox`对象中删除项目或销毁列表框时，由框架调用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lp 删除项目已删除*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)结构的长指针，其中包含有关已删除项的信息。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 根据需要重写此函数以重绘所有者绘制列表框。

有关`DELETEITEMSTRUCT`结构的说明，请参阅[CWnd：OnDeleteItem。](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox：:DeleteString

从列表框中删除位置*nIndex*中的项。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要删除的字符串的零基索引。

### <a name="return-value"></a>返回值

列表中剩余字符串的计数。 如果*nIndex*指定的索引大于列表中的项数，则返回值LB_ERR。

### <a name="remarks"></a>备注

*nIndex*之后的所有项目现在向下移动一个位置。 例如，如果列表框包含两个项目，删除第一个项将导致其余项现在位于第一个位置。 *nIndex*#0 表示第一个位置中的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox：:Dir

将文件名、驱动器或两者的列表添加到列表框。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是`CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)中描述的**枚举**值的任意组合，也可以是以下值的任意组合：

|“值”|含义|
|-----------|-------------|
|0x0000|文件可以从读取或写入。|
|0x0001|文件可以从读取，但不能写入。|
|0x0002|文件是隐藏的，不会显示在目录列表中。|
|0x0004|文件是系统文件。|
|0x0010|*lpszWildCard*指定的名称指定一个目录。|
|0x0020|文件已存档。|
|0x4000|包括与*lpszWildCard*指定的名称匹配的所有驱动器。|
|0x8000|独占标志。 如果设置了独占标志，则仅列出指定类型的文件。 否则，除了"正常"文件外，还列出指定类型的文件。|

*lpsz通配符*<br/>
指向文件规范字符串。 字符串可以包含通配符（例如 ，*.\*

### <a name="return-value"></a>返回值

添加到列表中的姓氏的零基索引。 如果发生错误，返回值将LB_ERR;如果没有足够的空间来存储新字符串，则返回值LB_ERRSPACE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox：:D原始项目

当所有者绘制列表框的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

结构`itemAction``itemState`和`DRAWITEMSTRUCT`成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者绘制对象的绘图`CListBox`。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

有关`DRAWITEMSTRUCT`结构的说明，请参阅[CWnd：OnDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox：：查找字符串

在包含指定前缀的列表框中查找第一个字符串，而不更改列表框选择。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>参数

*n 开始后*<br/>
包含要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nStartAfter*指定的项。 如果*nStartAfter*为 -1，则从一开始就搜索整个列表框。

*lpszItem*<br/>
指向包含要搜索的前缀的 null 终止字符串。 搜索是独立于大小写，因此此字符串可能包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

匹配项的零基索引，或LB_ERR搜索不成功时。

### <a name="remarks"></a>备注

使用[SelectString](#selectstring)成员函数查找和选择字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox：：查找字符串精确

查找与*lpszFind*中指定的字符串匹配的第一个列表框字符串。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndex 开始*<br/>
指定要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nIndexStart*指定的项。 如果*nIndexStart*为 -1，则从一开始就搜索整个列表框。

*lpszFind*<br/>
指向要搜索的 null 终止字符串。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此字符串可以包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

匹配项的索引，或LB_ERR搜索不成功。

### <a name="remarks"></a>备注

如果列表框创建时具有所有者绘制样式，但没有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则`FindStringExact`成员函数将尝试将双字值与*lpszFind*的值匹配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox：获取锚定索引

在列表框中检索当前锚点项的零基索引。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>返回值

当前锚点项的索引（如果成功）;否则LB_ERR。

### <a name="remarks"></a>备注

在多选列表框中，锚点项是连续选定项目块中的第一个或最后一个项。

### <a name="example"></a>示例

  请参阅[CListBox：：setAnchorIndex 的示例](#setanchorindex)。

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox：获取关怀索引

确定在多选择列表框中具有焦点矩形的项的索引。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>返回值

列表框中具有焦点矩形的项的零基索引。 如果列表框是单选列表框，则返回值是所选项的索引（如果有）。

### <a name="remarks"></a>备注

该项目可能被选中，也可能未被选中。

### <a name="example"></a>示例

  请参阅[CListBox：：setCaretIndex 的示例](#setcaretindex)。

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox：获取计数

检索列表框中的项目数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

列表框中的项目数，如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

返回的计数大于最后一个项的索引值（索引为零）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox：获取CurSel

在单选列表框中检索当前选定项（如果有）的零基索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

当前选定项的零索引（如果是单选列表框）。 如果未当前选择任何项目，则LB_ERR。

在多选列表框中，具有焦点的项的索引。

### <a name="remarks"></a>备注

不要调用`GetCurSel`多选列表框。 使用[CListBox：而是获取塞尔项目](#getselitems)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox：获取水平范围

从列表框检索可水平滚动的宽度（以像素为单位）。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

列表框的可滚动宽度（以像素为单位）。

### <a name="remarks"></a>备注

仅当列表框具有水平滚动条时，才适用此选项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox：获取项目数据

检索与指定列表框项关联的应用程序提供的双字值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的零基索引。

### <a name="return-value"></a>返回值

与项关联的值，或LB_ERR发生错误时的值。

### <a name="remarks"></a>备注

双字值是[SetItemData](#setitemdata)调用的*dwItemData*参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox：获取项目数据Ptr

检索与指定列表框项关联的应用程序提供的 32 位值作为指针 **（void）。** <strong>\*</strong>

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的零基索引。

### <a name="return-value"></a>返回值

如果发生错误，则检索指针，或 -1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox：获取项目高度

确定列表框中项目的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的零基索引。 仅当列表框具有LBS_OWNERDRAWVARIABLE样式时，才使用此参数;否则，应将其设置为 0。

### <a name="return-value"></a>返回值

列表框中项目的高度（以像素为单位）。 如果列表框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则返回值是*nIndex*指定的项的高度。 如果发生错误，则返回值LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox：获取项目已重新完成

检索当前显示在列表框窗口中的列表框项的矩形的尺寸。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的零基索引。

*lpRect*<br/>
指定指向接收项的列表框客户端坐标的[RECT 结构](/windows/win32/api/windef/ns-windef-rect)的长指针。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox：获取列表框信息

检索每列的项目数。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>返回值

`CListBox`对象每列的项数。

### <a name="remarks"></a>备注

此成员函数模拟[LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo)消息的功能，如 Windows SDK 中所述。

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox：获取本地化

检索列表框使用区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

列表框中字符串区域设置标识符 （LCID） 值。

### <a name="remarks"></a>备注

例如，区域设置用于确定排序列表框中字符串的排序顺序。

### <a name="example"></a>示例

  请参阅[CListBox：：设置区域设置的示例](#setlocale)。

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox：GetSel

检索项的选择状态。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的零基索引。

### <a name="return-value"></a>返回值

如果选择了指定的项，则为正数;如果选择了指定项，则为正数。否则，它是 0。 如果发生错误，返回值LB_ERR。

### <a name="remarks"></a>备注

此成员函数适用于单选和多选列表框。

要检索当前选择的列表框项的索引，请使用[CListBox：：getCurSel](#getcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox：获取塞尔计数

检索多选列表框中所选项的总数。

```
int GetSelCount() const;
```

### <a name="return-value"></a>返回值

列表框中所选项目的计数。 如果列表框是单选列表框，则返回值LB_ERR。

### <a name="example"></a>示例

  请参阅[CListBox 的示例：获取塞尔项目](#getselitems)。

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox：获取塞尔项目

使用整数数组填充缓冲区，该数组在多选列表框中指定选定项的项编号。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>参数

*nMax项目*<br/>
指定要放置在缓冲区中的项目编号的选定项目的最大数量。

*rgIndex*<br/>
指定指向缓冲区的指针，该指针足够大，以容纳*nMaxItems*指定的整数数。

### <a name="return-value"></a>返回值

放置在缓冲区中的实际项数。 如果列表框是单选列表框，则返回值为`LB_ERR`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox：获取文本

从列表框中获取字符串。

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
指定要检索的字符串的零基索引。

*lpszBuffer*<br/>
指向接收字符串的缓冲区。 缓冲区必须有足够的空间用于字符串和终止空字符。 可以通过调用`GetTextLen`成员函数提前确定字符串的大小。

*rString*<br/>
对 `CString` 对象的引用。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止空字符。 如果*nIndex*未指定有效的索引，则返回值LB_ERR。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用字符串文本填充`CString`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox：获取文本

获取列表框项目中字符串的长度。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定字符串的零基索引。

### <a name="return-value"></a>返回值

字符串的长度（以字符表示），不包括终止空字符。 如果*nIndex*未指定有效的索引，则返回值LB_ERR。

### <a name="example"></a>示例

  请参阅[CListBox 的示例：：获取文本](#gettext)。

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox：获取热门索引

检索列表框中第一个可见项的零基索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，列表框中第一个可见项的零基索引（如果成功）LB_ERR。

### <a name="remarks"></a>备注

最初，项目 0 位于列表框的顶部，但如果滚动列表框，则另一项可能位于顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox：：在内存储

分配内存以存储列表框项。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>参数

*n项目*<br/>
指定要添加的项数。

*n 字节*<br/>
指定要为项字符串分配的内存量（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则列表框在需要重新分配内存之前可以存储的最大项数，否则LB_ERRSPACE，这意味着内存不足。

### <a name="remarks"></a>备注

在将大量项添加到`CListBox`之前调用此函数。

此功能有助于加快初始化具有大量项（超过 100 个）的列表框。 它预分配指定的内存量，以便后续[的 AddString、InsertString](#addstring)和[Dir](#dir)函数花费尽可能短的时间。 [InsertString](#insertstring) 您可以使用参数的估计值。 如果高估，将分配一些额外的内存;如果估计过高，则分配一些额外的内存。如果低估，则正常分配用于超过预分配金额的物料。

仅限 Windows 95/98：nItems 参数限制为 16 位值。 *nItems* 这意味着列表框不能包含超过 32，767 个项目。 尽管项目数受到限制，但列表框中项目的总大小仅受可用内存的限制。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox：：插入字符串

将字符串插入到列表框中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要插入字符串的位置的零基索引。 如果此参数为 -1，则字符串将添加到列表的末尾。

*lpszItem*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 如果发生错误，返回值将LB_ERR;如果没有足够的空间来存储新字符串，则返回值LB_ERRSPACE。

### <a name="remarks"></a>备注

与[AddString](#addstring)成员函数`InsertString`不同，不会导致对具有[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox：项目从点

确定与*pt*中指定的点之近的列表框项。

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
要查找最近的项的点，相对于列表框的工作区的左上角指定。

*b 外部*<br/>
如果*pt*位于列表框的工作区之外，则对 BOOL 变量的引用将设置为 TRUE;如果*pt*位于列表框的工作区内，则为 FALSE。

### <a name="return-value"></a>返回值

最接近的项的索引到*pt*中指定的点。

### <a name="remarks"></a>备注

您可以使用此函数确定鼠标光标移动的列表框项。

### <a name="example"></a>示例

  请参阅[CListBox：：setAnchorIndex 的示例](#setanchorindex)。

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox：测量项目

创建具有所有者绘制样式的列表框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lp 测量项目结构*<br/>
指向[测量结构](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的长指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 重写此成员函数并填充`MEASUREITEMSTRUCT`结构以通知 Windows 列表框维度。 如果列表框是使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建的，则框架将针对列表框中的每个项目调用此成员函数。 否则，仅调用此成员一次。

有关使用`SubclassDlgItem`成员函数创建的所有者绘制列表框中使用`CWnd`[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的详细信息，请参阅[技术说明 14](../../mfc/tn014-custom-controls.md)中的讨论。

有关`MEASUREITEMSTRUCT`结构的说明，请参阅[CWnd：onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox：重置内容

从列表框中删除所有项目。

```
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox：选择字符串

搜索与指定字符串匹配的列表框项，如果找到匹配项，则选择该项。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*n 开始后*<br/>
包含要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nStartAfter*指定的项。 如果*nStartAfter*为 -1，则从一开始就搜索整个列表框。

*lpszItem*<br/>
指向包含要搜索的前缀的 null 终止字符串。 搜索是独立于大小写，因此此字符串可能包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

如果搜索成功，则所选项的索引。 如果搜索不成功，则返回值LB_ERR，并且当前选择不会更改。

### <a name="remarks"></a>备注

如有必要，将滚动列表框，以使所选项目进入视图。

此成员函数不能与具有[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的列表框一起使用。

仅当项的初始字符（从起始点）与*lpszItem*指定的字符串中的字符匹配时，才选择项。

使用`FindString`成员函数查找字符串而不选择项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox：：塞尔项目范围

在多选列表框中选择多个连续项目。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>参数

*b选择*<br/>
指定如何设置所选内容。 如果 bSelect 为 TRUE，则选择字符串并突出显示;如果*bSelect*为 TRUE，则选择字符串并突出显示该字符串。如果 FALSE，则删除高光，并且不再选择字符串。

*n 第一项目*<br/>
指定要设置的第一个项的零基索引。

*n 最后项目*<br/>
指定要设置的最后一个项目的零基索引。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

仅对多个选择列表框使用此成员函数。 如果需要在多选列表框中仅选择一个项目（即，如果*nFirstItem*等于*nLastItem），* 请改为调用[SetSel](#setsel)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox：：设置锚定索引

在多选列表框中设置锚点以开始扩展选择。

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定将作为锚点的列表框项的零基索引。

### <a name="remarks"></a>备注

在多选列表框中，锚点项是连续选定项目块中的第一个或最后一个项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox：：设置关怀索引

在多选列表框中将焦点矩形设置到指定索引处的项。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要在列表框中接收焦点矩形的项的零基索引。

*bScroll*<br/>
如果此值为 0，则滚动该项目，直到完全可见。 如果此值不是 0，则滚动该项目，直到它至少部分可见。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

如果项目不可见，则将其滚动到视图中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>列表框：：设置列宽

在多列列表框中设置所有列的宽度（使用[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建）。

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>参数

*cxWidth*<br/>
指定所有列的宽度（以像素为单位）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox：：设置CurSel

如有必要，选择字符串并将其滚动到视图中。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*n选择*<br/>
指定要选择的字符串的零基索引。 如果*nSelect*为 -1，则列表框设置为没有选择。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

选择新字符串后，列表框将从以前选定的字符串中删除高光。

仅对单选列表框使用此成员函数。

要在多选选择列表框中设置或删除选择，请使用[CListBox：：SetSel](#setsel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox：：设置水平范围

设置宽度（以像素为单位），通过该宽度可以水平滚动列表框。

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>参数

*cx范围*<br/>
指定可以水平滚动列表框的像素数。

### <a name="remarks"></a>备注

如果列表框的大小小于此值，则水平滚动条将水平滚动列表框中的项目。 如果列表框大于或大于此值，则水平滚动条将隐藏。

要响应 对`SetHorizontalExtent`的调用，列表框必须已使用[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)样式定义。

此成员函数对多列列表框没有用处。 对于多列列表框，调用`SetColumnWidth`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox：设置项目数据

在列表框中设置与指定项关联的值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的零基索引。

*dwItemData*<br/>
指定要与项关联的值。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox：：设置项目数据Ptr

将列表框中与指定项关联的 32 位值设置为指定的指针 **（void）。** <strong>\*</strong>

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的零基索引。

*pData*<br/>
指定要与项关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

此指针在列表框的生命周期内仍然有效，即使项目在列表框中的相对位置可能会随着项目添加或删除而更改。 因此，框中的项索引可以更改，但指针保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox：设置项目高度

在列表框中设置项目的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的零基索引。 仅当列表框具有LBS_OWNERDRAWVARIABLE样式时，才使用此参数;否则，应将其设置为 0。

*cyItemHeight*<br/>
指定项目的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果索引或高度无效，LB_ERR。

### <a name="remarks"></a>备注

如果列表框具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则此函数将设置*nIndex*指定的项的高度。 否则，此函数将设置列表框中所有项目的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox：：设置本地化

设置此列表框的区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*n 新地*<br/>
要为列表框设置的新区域设置标识符 （LCID） 值。

### <a name="return-value"></a>返回值

此列表框的上一个区域设置标识符 （LCID） 值。

### <a name="remarks"></a>备注

如果未`SetLocale`调用，则从系统获取默认区域设置。 此系统默认区域设置可以使用控制面板的区域（或国际）应用程序进行修改。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox：：设置塞尔

在多选列表框中选择字符串。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的字符串的零基索引。 如果 -1，则根据*bSelect*的值，将所选内容添加到所有字符串或从所有字符串中删除。

*b选择*<br/>
指定如何设置所选内容。 如果 bSelect 为 TRUE，则选择字符串并突出显示;如果*bSelect*为 TRUE，则选择字符串并突出显示该字符串。如果 FALSE，则删除高光，并且不再选择字符串。 默认情况下，选择并突出显示指定的字符串。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

仅对多个选择列表框使用此成员函数。

要从单选列表框中选择项目，请使用[CListBox：：SetCurSel](#setcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox：：设置标签

在列表框中设置制表位。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>参数

*cxEachStop*<br/>
在每个*cxEachStop*对话框单元设置制表位。 有关对话框单元的说明，请参阅*rgTabStops。*

*nTabStops*<br/>
指定列表框中要具有的制表符停止数。

*rgTabStops*<br/>
指向包含对话框单元中的制表位位的整数数组的第一个成员。 对话框单位是水平或垂直距离。 一个水平对话框单位等于当前对话框基本宽度单位的四分之一，一个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 Windows`GetDialogBaseUnits`函数返回当前以像素为单位的当前对话框基本单位。 必须按增加的顺序对制表位进行排序;不允许返回选项卡。

### <a name="return-value"></a>返回值

如果设置了所有选项卡，则非零;否则 0。

### <a name="remarks"></a>备注

要将制表符停止设置为 2 个对话框单位的默认大小，请调用此成员函数的无参数版本。 要将制表符停止设置为大小 2 以外的大小，请使用*cxEachStop*参数调用版本。

要将制表符停止设置为大小数组，请使用具有*rgTabStops*和*nTabStops*参数的版本。 将在*rgTabStops*中为每个值设置一个制表停止点，最多为*nTabStops*指定的数字。

要响应对成员函数的`SetTabStops`调用，列表框必须使用[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox：：设置顶索引

确保特定列表框项可见。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的零基索引。

### <a name="return-value"></a>返回值

如果成功，则为零，如果发生错误，则LB_ERR。

### <a name="remarks"></a>备注

系统滚动列表框，直到*nIndex*指定的项显示在列表框的顶部或已达到最大滚动范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox：：Vkeyto项目

当列表框的父窗口从列表框中接收WM_VKEYTOITEM消息时，由框架调用。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>参数

*n键*<br/>
用户按下的密钥的虚拟密钥代码。 有关标准虚拟密钥代码的列表，请参阅 Winuser.h

*nIndex*<br/>
列表框的当前位置。

### <a name="return-value"></a>返回值

返回 - 2 表示没有进一步操作，1 表示默认操作，或非负数，用于指定列表框项的索引，用于执行击键的默认操作。

### <a name="remarks"></a>备注

WM_VKEYTOITEM消息在收到WM_KEYDOWN消息时由列表框发送，但仅当列表框满足以下两个消息时才发送：

- 设置了[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式。

- 至少有一个项目。

您绝不应自行调用此功能。 重写此函数以提供您自己的键盘消息的自定义处理。

您必须返回一个值，告诉框架执行了哪些操作。 返回值 - 2 表示应用程序处理了选择项的所有方面，并且不需要列表框执行进一步操作。 在返回 - 2 之前，您可以设置选择或移动支持者或两者。 要设置选择，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 要移动 caret，请使用[SetCaretIndex](#setcaretindex)。

返回值 - 1 表示列表框应执行默认操作以响应击键。默认实现返回 - 1。

返回值 0 或更高指定列表框中项的索引，并指示列表框应对给定项执行击键的默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)
