---
title: CListBox 类
ms.date: 11/04/2016
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
ms.openlocfilehash: b448f725bac68c2b67dc44d660c664c075aa86da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225264"
---
# <a name="clistbox-class"></a>CListBox 类

提供 Windows 列表框功能。

## <a name="syntax"></a>语法

```
class CListBox : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|构造 `CListBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CListBox::AddString](#addstring)|将字符串添加到列表框。|
|[CListBox::CharToItem](#chartoitem)|重写以提供自定义 WM_CHAR 处理所有者描述列表框没有字符串。|
|[CListBox::CompareItem](#compareitem)|由框架调用以确定新项的已排序的所有者描述列表框中的位置。|
|[CListBox::Create](#create)|创建 Windows 列表框，并将其附加到`CListBox`对象。|
|[CListBox::DeleteItem](#deleteitem)|当用户从所有者描述列表框中删除项时由框架调用。|
|[CListBox::DeleteString](#deletestring)|从列表框中删除一个字符串。|
|[CListBox::Dir](#dir)|将文件名、 驱动器或同时从当前目录添加到列表框中。|
|[CListBox::DrawItem](#drawitem)|由框架在所有者描述列表框中更改的可视方面时调用。|
|[CListBox::FindString](#findstring)|在列表框中的字符串搜索。|
|[CListBox::FindStringExact](#findstringexact)|查找与指定的字符串匹配的第一个列表框中字符串。|
|[CListBox::GetAnchorIndex](#getanchorindex)|检索列表框中当前的定位点项的从零开始的索引。|
|[CListBox::GetCaretIndex](#getcaretindex)|确定具有多选列表框中的聚焦框的项的索引。|
|[CListBox::GetCount](#getcount)|在列表框中返回的字符串的数目。|
|[CListBox::GetCurSel](#getcursel)|返回列表框中当前所选字符串的从零开始的索引。|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可以水平滚动列表框的宽度。|
|[CListBox::GetItemData](#getitemdata)|返回与列表框项关联的 32 位值。|
|[CListBox::GetItemDataPtr](#getitemdataptr)|返回到列表框项的指针。|
|[CListBox::GetItemHeight](#getitemheight)|确定列表框中项的高度。|
|[CListBox::GetItemRect](#getitemrect)|返回当前显示的列表框项的边框。|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|检索每个列的项的数目。|
|[CListBox::GetLocale](#getlocale)|检索列表框的区域设置标识符。|
|[CListBox::GetSel](#getsel)|返回一个列表框项的选择状态。|
|[CListBox::GetSelCount](#getselcount)|返回多选列表框中当前选定的字符串数。|
|[CListBox::GetSelItems](#getselitems)|返回当前所选列表框中的字符串的索引。|
|[CListBox::GetText](#gettext)|将列表框项复制到缓冲区。|
|[CListBox::GetTextLen](#gettextlen)|返回以字节为单位的列表框项的长度。|
|[CListBox::GetTopIndex](#gettopindex)|返回列表框中的第一个可见字符串的索引。|
|[CListBox::InitStorage](#initstorage)|预先分配列表框项和字符串的内存的块。|
|[CListBox::InsertString](#insertstring)|列表框中的特定位置处插入的字符串。|
|[CListBox::ItemFromPoint](#itemfrompoint)|返回最接近的点的列表框项的索引。|
|[CListBox::MeasureItem](#measureitem)|创建所有者描述列表框来确定列表框维度时由框架调用。|
|[CListBox::ResetContent](#resetcontent)|清除列表框中的所有条目。|
|[CListBox::SelectString](#selectstring)|搜索并选择单选列表框中的字符串。|
|[CListBox::SelItemRange](#selitemrange)|选择或取消选择一系列多选列表框中的字符串。|
|[CListBox::SetAnchorIndex](#setanchorindex)|若要开始针对扩展的所选的多选列表框中设置定位点。|
|[CListBox::SetCaretIndex](#setcaretindex)|多选列表框中将聚焦框设置为指定索引处的项。|
|[CListBox::SetColumnWidth](#setcolumnwidth)|设置多列列表框中的列宽度。|
|[CListBox::SetCurSel](#setcursel)|选择一个列表框的字符串。|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|设置以像素为单位可以水平滚动列表框的宽度。|
|[CListBox::SetItemData](#setitemdata)|设置与列表框项关联的 32 位值。|
|[CListBox::SetItemDataPtr](#setitemdataptr)|将指针设置为列表框项。|
|[CListBox::SetItemHeight](#setitemheight)|在列表框中设置项的高度。|
|[CListBox::SetLocale](#setlocale)|设置的列表框的区域设置标识符。|
|[CListBox::SetSel](#setsel)|选择或取消选择多选列表框中的列表框项。|
|[CListBox::SetTabStops](#settabstops)|设置在列表框中的制表位位置。|
|[CListBox::SetTopIndex](#settopindex)|在列表框中设置第一个可见字符串的从零开始的索引。|
|[CListBox::VKeyToItem](#vkeytoitem)|重写以提供自定义 WM_KEYDOWN 处理 LBS_WANTKEYBOARDINPUT 样式设置的列表框。|

## <a name="remarks"></a>备注

列表框中显示项，例如，用户可以查看和选择的文件名的列表。

在单选择列表框中，用户可以选择只有一项。 在多选列表框中，可以选择的项的范围。 当用户选择某个项时，它被突出显示和列表框向父窗口发送一条通知消息。

从对话框模板或直接在代码中，可以创建一个列表框。 若要直接创建，请构造`CListBox`对象，然后调用[创建](#create)成员函数来创建 Windows 列表框控件并将其附加到`CListBox`对象。 若要使用对话框模板中的列表框，列表框中声明变量对话框类，然后使用`DDX_Control`在自己对话框类的`DoDataExchange`函数连接到该控件的成员变量。 （这是为你自动完成时将控件变量添加到对话框类。）

构造可以是在派生类中的一步过程`CListBox`。 编写构造函数作为派生的类，并调用`Create`从构造函数内。

如果你想要处理 Windows 通知消息的列表框发送给其父级 (从派生的类通常[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。

每个消息映射条目采用以下形式：

`ON_Notification( id, memberFxn )`

其中`id`指定将通知发送到该列表框控件的子窗口 ID 和`memberFxn`是您编写以处理通知的父成员函数的名称。

父项的函数原型如下所示：

`afx_msg void memberFxn( );`

下面是可能的消息映射条目和的情况下，将向父级发送说明的列表：

- ON_LBN_DBLCLK 用户双击列表框中的字符串。 有一个列表框[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式将发送此通知消息。

- ON_LBN_ERRSPACE 列表框无法分配足够的内存来满足请求。

- ON_LBN_KILLFOCUS 列表框正在失去输入的焦点。

- ON_LBN_SELCANCEL 当前列表框选定内容将被取消。 列表框含有 LBS_NOTIFY 样式时，才发送此消息。

- ON_LBN_SELCHANGE 列表框中的选项已更改。 如果通过更改所选内容不会发送此通知[CListBox::SetCurSel](#setcursel)成员函数。 此通知仅适用于具有 LBS_NOTIFY 样式的列表框。 LBN_SELCHANGE 发送通知消息是多选列表框中的每次用户按箭头键，即使所选内容不会更改。

- ON_LBN_SETFOCUS 列表框将接收输入的焦点。

- ON_WM_CHARTOITEM 一个所有者描述列表框，其中具有无附加条件接收 WM_CHAR 消息。

- LBS_WANTKEYBOARDINPUT 样式 ON_WM_VKEYTOITEM 一个列表框中接收 WM_KEYDOWN 消息。

如果您创建`CListBox`（通过对话框资源） 对话框中的对象`CListBox`在用户关闭对话框时自动销毁对象。

如果您创建`CListBox`对象内一个窗口，您可能需要销毁`CListBox`对象。 如果您创建`CListBox`对象在堆栈上被自动销毁。 如果您创建`CListBox`通过使用堆上的对象**新**函数，必须调用**删除**上要在用户关闭父窗口时对其进行销毁的对象。

如果分配任何内存`CListBox`对象，请重写`CListBox`析构函数释放分配。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

将字符串添加到列表框。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
指向要添加的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

到列表框中的字符串的从零开始索引。 返回值是 LB_ERR，如果发生错误;如果没有足够空间可用于存储新字符串，返回值将为 LB_ERRSPACE。

### <a name="remarks"></a>备注

如果不通过创建列表框[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并且对列表进行排序。 如果使用 LBS_SORT 样式创建列表框，但不是[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，该框架对列表进行排序的一个或多个调用`CompareItem`成员函数。

使用[InsertString](#insertstring)要插入到列表框中的特定位置的字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

从列表框中，列表框中的父窗口收到 WM_CHARTOITEM 消息时由框架调用。

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

返回-1 或 2 的任何进一步的操作或一个非负数字来指定要对其执行键击的默认操作的列表框项的索引。 默认实现返回-1。

### <a name="remarks"></a>备注

当它收到 WM_CHAR 消息，但仅当列表框满足以下所有条件的列表框发送 WM_CHARTOITEM 消息：

- 是一个所有者描述列表框。

- 不具有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式集。

- 具有至少一个项。

您永远不应自行调用此函数。 重写此函数可提供您自己的键盘消息的自定义处理。

在替代中，您必须返回一个值，以通知框架执行哪些操作。 返回值为-1 或 2 指示处理选择相应的项的所有方面，不需要进一步的操作的列表框。 返回的前 1 或-2，您可以设置所选内容或移动和 / 或将插入符号。 若要设置所选内容，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要将插入符号，请使用[SetCaretIndex](#setcaretindex)。

返回值为 0 或更高版本的列表框中指定的项的索引，并指示列表框中应为击键上给定的项执行默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>  CListBox::CListBox

构造 `CListBox` 对象。

```
CListBox();
```

### <a name="remarks"></a>备注

构造`CListBox`两个步骤中的对象。 首先，调用构造函数`ClistBox`，然后调用`Create`，其中初始化 Windows 列表框并将其附加到`CListBox`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

由框架调用以确定新项的已排序的所有者描述列表框中的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lpCompareItemStruct*<br/>
指向的长指针`COMPAREITEMSTRUCT`结构。

### <a name="return-value"></a>返回值

指示中所述的两个项目的相对位置[COMPAREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct)结构。 它可能是以下值之一：

|“值”|含义|
|-----------|-------------|
|-1|第 1 项进行排序项 2 之前。|
|0|第 1 项和项 2 排序相同。|
|1|在项 2 之后，第 1 项进行排序。|

请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`结构。

### <a name="remarks"></a>备注

默认情况下，此成员函数没有任何影响。 如果使用 LBS_SORT 样式创建所有者描述列表框中，必须重写此成员函数以帮助对新项添加到列表框排序的框架。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

创建 Windows 列表框，并将其附加到`CListBox`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定列表框的样式。 应用的任意组合[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)给数字显示框。

*rect*<br/>
指定列表框大小和位置。 可以是`CRect`对象或`RECT`结构。

*pParentWnd*<br/>
指定列表框中的父窗口 (通常`CDialog`对象)。 它不能为 NULL。

*nID*<br/>
指定列表框控件 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

构造`CListBox`两个步骤中的对象。 首先，调用构造函数，然后调用`Create`，其中初始化 Windows 列表框并将其附加到`CListBox`对象。

当`Create`执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，并且[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)向列表框控件的消息。

默认情况下处理这些消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，以及[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，从派生类`CListBox`、 将消息映射添加到新类和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要执行的一个新类所需的初始化。

将以下内容应用[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到列表框控件。

- WS_CHILD 始终

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 到添加的垂直滚动条

- WS_HSCROLL 到添加的水平滚动条

- WS_GROUP 与组控件

- WS_TABSTOP 到允许 tab 键移到此控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

当用户从所有者描述删除项时由框架调用`CListBox`对象或销毁列表框。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lpDeleteItemStruct*<br/>
指向 Windows 的长指针[DELETEITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct)结构，其中包含有关已删除的项的信息。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以重绘根据需要一个所有者描述列表框。

请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关的说明`DELETEITEMSTRUCT`结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

删除位置中的项*nIndex*从列表框。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要删除的字符串的从零开始的索引。

### <a name="return-value"></a>返回值

在列表中剩余的字符串的计数。 如果，则返回值为 LB_ERR *nIndex*指定列表中的索引大于项的数目。

### <a name="remarks"></a>备注

后面的所有项*nIndex*现在将下移一个位置。 例如，如果列表框包含两个项，则删除的第一项将导致剩余的项现在位于第一个位置。 *nIndex*= 0 中的第一个位置的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>  CListBox::Dir

添加的文件名、 驱动器和 / 或列表框的列表。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是任何组合**enum**值中所述`CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus)，或以下值的任意组合：

|“值”|含义|
|-----------|-------------|
|0x0000|可以读取或写入到文件。|
|0x0001|可以从读取但不是会写入到文件。|
|0x0002|文件处于隐藏状态，并且未出现在目录列表。|
|0x0004|文件是系统文件。|
|0x0010|指定的名称*lpszWildCard*指定的目录。|
|0x0020|已存档文件。|
|0x4000|包含与指定的名称相匹配的所有驱动器*lpszWildCard*。|
|0x8000|独占标志。 如果设置了排他的标志，列出了仅指定类型的文件。 否则，除了"normal"的文件都列出了指定类型的文件。|

*lpszWildCard*<br/>
指向文件规范的字符串。 该字符串可包含通配符 (例如，*。\*)。

### <a name="return-value"></a>返回值

最后一个文件名添加到列表中的从零开始的索引。 返回值是 LB_ERR，如果发生错误;如果没有足够空间可用于存储新字符串，返回值将为 LB_ERRSPACE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>  CListBox::DrawItem

由框架在所有者描述列表框中更改的可视方面时调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向的长指针[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)结构，其中包含有关绘图所需的类型的信息。

### <a name="remarks"></a>备注

`itemAction`并`itemState`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。

默认情况下，此成员函数没有任何影响。 重写此成员函数以实现绘制所有者描述的`CListBox`对象。 应用程序应还原所有图形设备接口 (GDI) 对象的显示上下文中提供选定*lpDrawItemStruct*之前此成员函数将终止。

请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关的说明`DRAWITEMSTRUCT`结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

查找包含指定的前缀，而无需更改的列表框中选择的列表框中的第一个字符串。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nStartAfter*。 如果*nStartAfter*为-1，从开始处搜索整个列表框。

*lpszItem*<br/>
指向包含要搜索的前缀的以 null 结尾的字符串。 搜索是独立的因此，此字符串可能包含的任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

LB_ERR 如果搜索未成功的匹配项的从零开始的索引。

### <a name="remarks"></a>备注

使用[SelectString](#selectstring)成员函数，以同时查找并选择一个字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

查找中指定的字符串匹配的第一个列表框中字符串*lpszFind*。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndexStart*<br/>
指定要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nIndexStart*。 如果*nIndexStart*为-1，从开始处搜索整个列表框。

*lpszFind*<br/>
指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名，将该扩展。 搜索不区分大小写，因此该字符串可包含的任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

LB_ERR 如果搜索未成功的匹配项的索引。

### <a name="remarks"></a>备注

如果使用列表框创建所有者绘制样式了但没有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式`FindStringExact`成员函数将尝试匹配的值的双字值*lpszFind*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

检索列表框中当前的定位点项的从零开始的索引。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，则当前定位点项的索引否则为 LB_ERR。

### <a name="remarks"></a>备注

在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::SetAnchorIndex](#setanchorindex)。

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

确定具有多选列表框中的聚焦框的项的索引。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>返回值

在列表框具有焦点矩形的项的从零开始的索引。 列表框是否单选列表框中，则如果任何返回值将为已选中的项的索引。

### <a name="remarks"></a>备注

项可能会或可能不会选择。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::SetCaretIndex](#setcaretindex)。

##  <a name="getcount"></a>  CListBox::GetCount

检索列表框中项的数目。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

在列表框中或如果发生错误的 LB_ERR 中项的数目。

### <a name="remarks"></a>备注

返回的计数是一个大于 （索引为从零开始） 的最后一项的索引值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

如果有单选列表框中，检索当前选定项的从零开始的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

如果它是单选列表框的当前选定项的从零开始的索引。 如果当前未不选择任何项，则 LB_ERR。

在多选列表框中，具有焦点的项的索引。

### <a name="remarks"></a>备注

不要调用`GetCurSel`多选列表框。 使用[CListBox::GetSelItems](#getselitems)相反。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent

从列表框检索以像素为单位，它可以进行水平滚动的宽度。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

可滚动列表框中，以像素为单位的宽度。

### <a name="remarks"></a>备注

这是仅适用于该列表框具有水平滚动条。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

检索与指定的列表框项关联的应用程序提供双字值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的从零开始的索引。

### <a name="return-value"></a>返回值

如果发生错误的项或 LB_ERR 与关联的 32 位值。

### <a name="remarks"></a>备注

双字值已*dwItemData*的参数[SetItemData](#setitemdata)调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

检索与指定的列表框项作为指针关联的应用程序提供 32 位值 (**void** <strong>\*</strong>)。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的从零开始的索引。

### <a name="return-value"></a>返回值

检索一个指针，则为-1，如果发生错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

确定列表框中项的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的从零开始的索引。 仅当列表框含有 LBS_OWNERDRAWVARIABLE 样式; 使用此参数否则，它应设置为 0。

### <a name="return-value"></a>返回值

以像素为单位，列表框中的项的高度。 如果列表框含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，返回值是由指定的项的高度*nIndex*。 如果发生错误，则返回值是 LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

检索当前显示在列表框窗口矩形的尺寸的边界列表框项。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*lpRect*<br/>
指定指向的长指针[RECT 结构](/windows/desktop/api/windef/ns-windef-tagrect)接收项的列表框中客户端坐标。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

检索每个列的项的数目。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>返回值

每个列的项目数`CListBox`对象。

### <a name="remarks"></a>备注

此成员函数模拟的功能[LB_GETLISTBOXINFO](/windows/desktop/Controls/lb-getlistboxinfo)消息，如 Windows SDK 中所述。

##  <a name="getlocale"></a>  CListBox::GetLocale

检索列表框中使用的区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

在列表框中字符串的区域设置标识符 (LCID) 值。

### <a name="remarks"></a>备注

使用区域设置是，例如，若要确定已排序的列表框中字符串的排序顺序。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::SetLocale](#setlocale)。

##  <a name="getsel"></a>  CListBox::GetSel

检索项的选择状态。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

### <a name="return-value"></a>返回值

如果指定的项处于选中状态，，正数否则，则为 0。 如果发生错误，则返回值是 LB_ERR。

### <a name="remarks"></a>备注

此成员函数适用于这两个单个和多选列表框。

若要检索当前所选列表框项的索引，请使用[CListBox::GetCurSel](#getcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

检索多选列表框中选定项的总数。

```
int GetSelCount() const;
```

### <a name="return-value"></a>返回值

列表框中选定项的计数。 如果列表框中，单选择列表框中的返回值是 LB_ERR。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::GetSelItems](#getselitems)。

##  <a name="getselitems"></a>  CListBox::GetSelItems

使用多选列表框中指定的所选的项的项号的整数数组填充缓冲区。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>参数

*nMaxItems*<br/>
指定其项号的放置在缓冲区中的选定项的最大数目。

*rgIndex*<br/>
指定一个指向缓冲区足够大的由指定的整数个数*nMaxItems*。

### <a name="return-value"></a>返回值

在缓冲区中放置的项的实际数目。 如果列表框中，单选择列表框中的返回值是`LB_ERR`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

从列表框中获取的字符串。

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
指向接收字符串的缓冲区。 缓冲区必须有足够的空间的字符串和终止 null 字符。 通过调用，可以提前确定字符串的大小`GetTextLen`成员函数。

*rString*<br/>
对 `CString` 对象的引用。

### <a name="return-value"></a>返回值

不包括终止 null 字符的字符串长度 （以字节为单位）。 如果*nIndex*未指定有效的索引，则返回值是 LB_ERR。

### <a name="remarks"></a>备注

此成员的第二种形式函数填充`CString`具有字符串文本对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

在列表框项中获取字符串的长度。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定字符串的从零开始的索引。

### <a name="return-value"></a>返回值

以字符为单位，不包括终止 null 字符的字符串的长度。 如果*nIndex*未指定有效的索引，则返回值是 LB_ERR。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::GetText](#gettext)。

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

检索列表框中的第一个可见项的从零开始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，一个列表框中的第一个可见项的从零开始的索引; 否则为 LB_ERR。

### <a name="remarks"></a>备注

最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能会在顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

为存储列表框项分配内存。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>参数

*nItems*<br/>
指定要添加的项的数目。

*nBytes*<br/>
以字节为单位，若要为项字符串分配指定内存的量。

### <a name="return-value"></a>返回值

如果成功，最大的列表框可以存储在内存重新分配之前的项很有需要否则为 LB_ERRSPACE，这不意味着足够的内存。

### <a name="remarks"></a>备注

添加大量的项之前调用此函数`CListBox`。

此函数可帮助加快有大量的项 (超过 100) 的列表框中的初始化。 预先分配指定的数量的内存以便将后续[AddString](#addstring)， [InsertString](#insertstring)，并[Dir](#dir)函数采用最短的时间。 您可以对参数使用估计值。 如果您要估计得高一些，一些额外的内存分配;如果你低估，进行一般分配用于超过预先分配的量的项。

Windows 95/98 仅：*NItems*参数最多为 16 位值。 这意味着列表框不能包含超过 32,767 个项。 项的数目受到限制，尽管列表框中的项的总大小仅受可用内存。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

将一个字符串插入到列表框。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要将该字符串的位置的从零开始索引。 如果此参数为-1，则字符串被添加到列表的末尾。

*lpszItem*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 返回值是 LB_ERR，如果发生错误;如果没有足够空间可用于存储新字符串，返回值将为 LB_ERRSPACE。

### <a name="remarks"></a>备注

与不同[AddString](#addstring)成员函数`InsertString`不会导致与列表[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

确定最近的中指定的点的列表框项*pt*。

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
要为其查找最近的项，指定相对于列表框的工作区的左上角的点。

*bOutside*<br/>
将设置为 TRUE 的布尔值变量的引用*pt*最近的列表框项的工作区以外是 FALSE; *pt*内最接近的列表框项的工作区。

### <a name="return-value"></a>返回值

中指定的点到最近的项的索引*pt*。

### <a name="remarks"></a>备注

此函数可用于确定鼠标光标移到上的列表框项。

### <a name="example"></a>示例

  有关示例，请参阅[CListBox::SetAnchorIndex](#setanchorindex)。

##  <a name="measureitem"></a>  CListBox::MeasureItem

创建具有所有者绘制样式的列表框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lpMeasureItemStruct*<br/>
指向的长指针[MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct)结构。

### <a name="remarks"></a>备注

默认情况下，此成员函数没有任何影响。 重写此成员函数，并填充`MEASUREITEMSTRUCT`结构以通知 Windows 列表框维度。 如果使用创建列表框[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，框架将调用此成员函数为每个项的列表框中。 否则，只有一次调用此成员。

有关使用详细信息[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)中创建具有一个所有者描述列表框样式`SubclassDlgItem`成员函数`CWnd`，请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md).

请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

从列表框中移除所有项。

```
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

搜索列表框项的匹配指定的字符串，并且如果找到匹配项，则将选择此项。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nStartAfter*。 如果*nStartAfter*为-1，从开始处搜索整个列表框。

*lpszItem*<br/>
指向包含要搜索的前缀的以 null 结尾的字符串。 搜索是独立的因此，此字符串可能包含的任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

如果搜索成功，则选定的项的索引。 如果搜索不成功，则返回值是 LB_ERR 和当前所选内容不会更改。

### <a name="remarks"></a>备注

如有必要，以使所选的项在视图滚动列表框。

此成员函数不能用于具有一个列表框[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式。

仅当其初始字符 （从起始点） 与指定的字符串中的字符匹配选定的项*lpszItem*。

使用`FindString`成员函数查找字符串，而不选择相应的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

多选列表框中选择多个连续的项。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>参数

*bSelect*<br/>
指定如何设置所选内容。 如果*bSelect*为 TRUE 时，选中并突出显示的字符串; 如果为 FALSE，删除突出显示，并且字符串不再处于选中状态。

*nFirstItem*<br/>
指定要设置的第一个项的从零开始索引。

*nLastItem*<br/>
指定要设置的最后一个项的从零开始索引。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

此成员函数仅使用多选列表框。 如果需要进行多选列表框中选择一个项 — 即，如果*nFirstItem*等于*nLastItem* — 调用[SetSel](#setsel)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

若要开始针对扩展的所选的多选列表框中设置定位点。

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定将为定位点的列表框项的从零开始索引。

### <a name="remarks"></a>备注

在多选列表框中，定位点项是连续的选定项的块中的第一个或最后一个项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

多选列表框中将聚焦框设置为指定索引处的项。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要接收聚焦框在列表框中的项的从零开始索引。

*bScroll*<br/>
如果此值为 0，则会将项滚动直到完全可见。 如果此值不为 0，项滚动直到至少部分可见。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

如果项不是可见的它被滚动到视图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

多列列表框中设置以像素为单位的所有列的宽度 (使用创建[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式)。

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>参数

*cxWidth*<br/>
指定以像素为单位的所有列的宽度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

选择一个字符串，并将其滚动到视图中，如有必要。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*nSelect*<br/>
指定要选择的字符串的从零开始的索引。 如果*请选择*为-1，列表框设置为不具有任何选择。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

选择新的字符串时，列表框从以前所选字符串删除突出显示。

此成员函数只能用于单选列表框。

若要设置或删除所选的多选列表框中，使用[CListBox::SetSel](#setsel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent

在列表框可以进行水平滚动的像素为单位设置宽度。

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>参数

*cxExtent*<br/>
指定列表框可以进行水平滚动的像素数。

### <a name="remarks"></a>备注

如果列表框的大小小于此值，水平滚动条将水平滚动列表框中的项。 如果列表框一样大，或者大于此值，则隐藏水平滚动条。

若要对调用做出响应`SetHorizontalExtent`，列表框中必须使用定义[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)样式。

此成员函数不是适用于多列列表框。 对于多列列表框中，调用`SetColumnWidth`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

设置与列表框中指定的项关联的 32 位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*dwItemData*<br/>
指定要与项相关联的值。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

设置为指定的指针的列表框中的指定项关联的 32 位值 ( **void** <strong>\*</strong>)。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定项的从零开始的索引。

*pData*<br/>
指定要与项相关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

此指针保持有效的列表框中，生命周期，即使列表框中项的相对位置添加或删除项时可能会更改。 因此，可以更改框中的项的索引，但指针保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

在列表框中设置项的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在列表框中指定项的从零开始的索引。 仅当列表框含有 LBS_OWNERDRAWVARIABLE 样式; 使用此参数否则，它应设置为 0。

*cyItemHeight*<br/>
指定以像素为单位的项的高度。

### <a name="return-value"></a>返回值

如果索引或高度无效，LB_ERR。

### <a name="remarks"></a>备注

如果列表框含有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，此函数将由指定的项的高度*nIndex*。 否则，此函数的列表框中设置的所有项的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

设置此列表框的区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*nNewLocale*<br/>
新区域设置标识符 (LCID) 要设置的值的列表框。

### <a name="return-value"></a>返回值

此列表框的上一个区域设置标识符 (LCID) 值。

### <a name="remarks"></a>备注

如果`SetLocale`未调用，默认值从系统获取区域设置。 此系统默认区域设置可以修改通过使用控制面板中的区域 （或国际） 应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>  CListBox::SetSel

多选列表框中选择一个字符串。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的字符串的从零开始的索引。 如果为-1，所选内容添加到或从所有字符串，具体取决于值中删除*bSelect*。

*bSelect*<br/>
指定如何设置所选内容。 如果*bSelect*为 TRUE 时，选中并突出显示的字符串; 如果为 FALSE，删除突出显示，并且字符串不再处于选中状态。 指定的字符串是选中并突出显示默认情况下。

### <a name="return-value"></a>返回值

如果发生错误，LB_ERR。

### <a name="remarks"></a>备注

此成员函数仅使用多选列表框。

若要从单选列表框中选择某个项目，请使用[CListBox::SetCurSel](#setcursel)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>  CListBox::SetTabStops

设置在列表框中的制表位位置。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>参数

*cxEachStop*<br/>
制表位设置为每个*cxEachStop*对话框单元为单位。 请参阅*rgTabStops*对话框单位的说明。

*nTabStops*<br/>
指定在列表框中的所有制表位的数量。

*rgTabStops*<br/>
指向包含对话框单元为单位中的制表位位置的整数的数组的第一个成员。 对话框单位是水平或垂直距离。 一个水平对话框单位等于 1 / 4 的当前对话框基本宽度单位，并且一个垂直对话框单位等于当前对话框基本高度单位的 1 / 8。 对话框基本单位根据当前系统字体的高度和宽度计算。 `GetDialogBaseUnits` Windows 函数以像素为单位返回当前对话框基本单位。 必须以递增顺序; 排序的制表位不允许向后制表位。

### <a name="return-value"></a>返回值

如果已设置所有选项卡; 非零值否则为 0。

### <a name="remarks"></a>备注

若要设置为默认大小为 2 个对话框单位的所有制表位，调用此成员函数的无参数版本。 若要设置为 2 以外的大小的所有制表位，调用的版本与*cxEachStop*参数。

若要设置制表位大小的数组，使用与版本*rgTabStops*并*nTabStops*参数。 将每个值中设置制表位*rgTabStops*，指定的数目可高达*nTabStops*。

若要对调用做出响应`SetTabStops`成员函数的列表框中必须已使用创建了[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

确保特定的列表框项可见。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则为零或 LB_ERR 如果发生错误。

### <a name="remarks"></a>备注

系统之前指定的任意一项滚动列表框*nIndex*显示顶部的列表框或最大滚动范围达到了。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

从列表框中，列表框中的父窗口收到 WM_VKEYTOITEM 消息时由框架调用。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>参数

*nKey*<br/>
该密钥的虚拟键代码用户按下。 标准虚拟键代码的列表，请参见 Winuser.h

*nIndex*<br/>
列表框插入符号的当前位置。

### <a name="return-value"></a>返回值

返回-2 表示不执行进一步的操作、-1 为默认操作或一个非负数字来指定要对其执行键击的默认操作的列表框项的索引。

### <a name="remarks"></a>备注

当它收到 WM_KEYDOWN 消息，但仅当列表框满足以下两个列表框发送 WM_VKEYTOITEM 消息：

- 具有[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式集。

- 具有至少一个项。

您永远不应自行调用此函数。 重写此函数可提供您自己的键盘消息的自定义处理。

您必须返回一个值，以告知框架重写执行什么操作。 返回值为-2 指示应用程序处理的选择项的所有方面并不需要进一步的操作的列表框。 之前返回-2，无法设置所选内容或移动和 / 或将插入符号。 若要设置所选内容，请使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要将插入符号，请使用[SetCaretIndex](#setcaretindex)。

返回值为-1 表示列表框中应执行击键的响应的默认操作。默认实现返回-1。

返回值为 0 或更高版本的列表框中指定的项的索引，并指示列表框中应为击键上给定的项执行默认操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)
