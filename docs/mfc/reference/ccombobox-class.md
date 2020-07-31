---
title: CComboBox 类
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: 4e7eba94084a96c833136e4c92de481fdc435c7e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183105"
---
# <a name="ccombobox-class"></a>CComboBox 类

提供 Windows 组合框功能。

## <a name="syntax"></a>语法

```
class CComboBox : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComboBox：： CComboBox](#ccombobox)|构造 `CComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|将字符串添加到组合框列表框中列表的末尾，或添加到具有 CBS_SORT 样式的列表框的排序位置。|
|[CComboBox：： Clear](#clear)|删除（清除）编辑控件中的当前选择（如果有）。|
|[CComboBox：： CompareItem](#compareitem)|由框架调用，以确定新列表项在排序的所有者描述的组合框中的相对位置。|
|[CComboBox：： Copy](#copy)|将当前选择（如果有）复制到剪贴板上 CF_TEXT 格式。|
|[CComboBox：： Create](#create)|创建组合框并将其附加到 `CComboBox` 对象。|
|[CComboBox：： Cut](#cut)|删除（剪切）编辑控件中的当前选定内容（如果有），并以 CF_TEXT 格式将删除的文本复制到剪贴板。|
|[CComboBox：:D eleteItem](#deleteitem)|当从所有者描述的组合框中删除列表项时，由框架调用。|
|[CComboBox：:D eleteString](#deletestring)|从组合框的列表框中删除字符串。|
|[CComboBox：:D ir](#dir)|将文件名列表添加到组合框的列表框中。|
|[CComboBox：:D rawItem](#drawitem)|当所有者描述的组合框的视觉方面发生变化时，由框架调用。|
|[CComboBox：： FindString](#findstring)|在组合框的列表框中查找包含指定前缀的第一个字符串。|
|[CComboBox：： FindStringExact](#findstringexact)|查找与指定字符串匹配的第一个列表框字符串（在组合框中）。|
|[CComboBox：： GetComboBoxInfo](#getcomboboxinfo)|检索有关对象的信息 `CComboBox` 。|
|[CComboBox：： GetCount](#getcount)|检索组合框的列表框中的项数。|
|[CComboBox：： GetCueBanner](#getcuebanner)|获取为组合框控件显示的提示文本。|
|[CComboBox：： GetCurSel](#getcursel)|在组合框的列表框中检索当前选定项（如果有）的索引。|
|[CComboBox：： GetDroppedControlRect](#getdroppedcontrolrect)|检索下拉组合框的可见（下拉列表）列表框的屏幕坐标。|
|[CComboBox：： GetDroppedState](#getdroppedstate)|确定下拉组合框的列表框是否可见（删除）。|
|[CComboBox：： GetDroppedWidth](#getdroppedwidth)|检索组合框的下拉列表框部分的最小允许宽度。|
|[CComboBox：： GetEditSel](#geteditsel)|获取组合框编辑控件中当前所选内容的起始和结束字符位置。|
|[CComboBox：： GetExtendedUI](#getextendedui)|确定组合框是否具有默认用户界面或扩展的用户界面。|
|[CComboBox：： GetHorizontalExtent](#gethorizontalextent)|返回组合框的列表框部分可水平滚动的宽度（以像素为单位）。|
|[CComboBox：： GetItemData](#getitemdata)|检索应用程序提供的与指定组合框项关联的32位值。|
|[CComboBox：： GetItemDataPtr](#getitemdataptr)|检索应用程序提供的与指定组合框项关联的32位指针。|
|[CComboBox：： GetItemHeight](#getitemheight)|检索组合框中列表项的高度。|
|[CComboBox：： GetLBText](#getlbtext)|从组合框的列表框中获取一个字符串。|
|[CComboBox：： GetLBTextLen](#getlbtextlen)|获取组合框的列表框中的字符串长度。|
|[CComboBox：： GetLocale](#getlocale)|检索组合框的区域设置标识符。|
|[CComboBox：： GetMinVisible](#getminvisible)|获取当前组合框下拉列表中可见项的最小数目。|
|[CComboBox：： GetTopIndex](#gettopindex)|返回组合框的列表框部分中第一个可见项的索引。|
|[CComboBox：： InitStorage](#initstorage)|组合框的列表框部分中项和字符串的预分配内存块。|
|[CComboBox::InsertString](#insertstring)|将字符串插入组合框的列表框。|
|[CComboBox：： LimitText](#limittext)|限制用户可以在组合框的编辑控件中输入的文本的长度。|
|[CComboBox：： MeasureItem](#measureitem)|当创建所有者描述的组合框时，由框架调用以确定组合框尺寸。|
|[CComboBox：:P aste](#paste)|将剪贴板中的数据插入到当前光标位置的编辑控件中。 仅当剪贴板包含 CF_TEXT 格式的数据时，才插入数据。|
|[CComboBox：： ResetContent](#resetcontent)|从列表框中移除所有项，并在组合框中编辑控件。|
|[CComboBox：： SelectString](#selectstring)|在组合框的列表框中搜索字符串，如果找到该字符串，则选择列表框中的字符串，并将该字符串复制到编辑控件中。|
|[CComboBox：： SetCueBanner](#setcuebanner)|设置为组合框控件显示的提示文本。|
|[CComboBox：： SetCurSel](#setcursel)|在组合框的列表框中选择一个字符串。|
|[CComboBox：： SetDroppedWidth](#setdroppedwidth)|设置组合框的下拉列表框部分的最小允许宽度。|
|[CComboBox：： SetEditSel](#seteditsel)|在组合框的编辑控件中选择字符。|
|[CComboBox：： SetExtendedUI](#setextendedui)|为具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式的组合框选择默认的用户界面或扩展的用户界面。|
|[CComboBox：： SetHorizontalExtent](#sethorizontalextent)|设置组合框的列表框部分可水平滚动的宽度（以像素为单位）。|
|[CComboBox：： SetItemData](#setitemdata)|设置与组合框中的指定项关联的32位值。|
|[CComboBox：： SetItemDataPtr](#setitemdataptr)|设置与组合框中的指定项关联的32位指针。|
|[CComboBox：： SetItemHeight](#setitemheight)|设置组合框中的列表项的高度或组合框的编辑控件（或静态文本）部分的高度。|
|[CComboBox：： SetLocale](#setlocale)|设置组合框的区域设置标识符。|
|[CComboBox：： SetMinVisibleItems](#setminvisibleitems)|设置当前组合框下拉列表中可见项的最小数目。|
|[CComboBox：： SetTopIndex](#settopindex)|指示组合框的列表框部分在顶部显示具有指定索引的项。|
|[CComboBox：： ShowDropDown](#showdropdown)|显示或隐藏具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式的组合框的列表框。|

## <a name="remarks"></a>备注

组合框由与静态控件或编辑控件组合在一起的列表框组成。 控件的列表框部分可能始终显示，或者仅当用户选择控件旁边的下拉箭头时才会出现。

列表框中当前选定的项（如果有）将显示在 "静态" 或 "编辑" 控件中。 此外，如果组合框具有下拉列表样式，则用户可以键入列表中某一项的起始字符，列表框（如果可见）将突出显示带有该初始字符的下一项。

下表比较了这三个组合框[样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|样式|何时显示列表框|静态控件或编辑控件|
|-----------|-------------------------------|-----------------------------|
|简单|始终|编辑|
|Drop-down|放下时|编辑|
|下拉列表|放下时|静态|

可以 `CComboBox` 通过对话框模板或直接在代码中创建对象。 在这两种情况下，首先调用构造函数构造 `CComboBox` `CComboBox` 对象，然后调用[create](#create)成员函数来创建控件并将其附加到 `CComboBox` 对象。

如果要处理由组合框发送到其父级的 Windows 通知消息（通常是从派生的类 `CDialog` ），请将消息映射项和消息处理程序成员函数添加到每条消息的父类。

每个消息映射项都采用以下形式：

`ON_Notification( id, memberFxn )`

其中， `id` 指定发送通知的组合框控件的子窗口 ID， `memberFxn` 是您编写的用于处理通知的父成员函数的名称。

父的函数原型如下所示：

`afx_msg void memberFxn( );`

无法预测某些通知的发送顺序。 具体而言，CBN_SELCHANGE 通知可能发生在 CBN_CLOSEUP 通知之前或之后。

可能的消息映射条目如下：

- ON_CBN_CLOSEUP （Windows 3.1 及更高版本。）组合框的列表框已关闭。 不会为具有[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框发送此通知消息。

- ON_CBN_DBLCLK 用户双击组合框的列表框中的字符串。 仅为具有 CBS_SIMPLE 样式的组合框发送此通知消息。 对于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框，因为单击隐藏列表框，则不会出现双击。

- ON_CBN_DROPDOWN 组合框的列表框将要下拉（使其可见）。 此通知消息仅适用于具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式的组合框。

- ON_CBN_EDITCHANGE 用户执行了一项操作，该操作可能更改了组合框的编辑控件部分中的文本。 与 CBN_EDITUPDATE 消息不同，此消息在 Windows 更新屏幕后发送。 如果组合框具有 CBS_DROPDOWNLIST 样式，则不会发送它。

- ON_CBN_EDITUPDATE 组合框的编辑控件部分将显示已更改的文本。 此通知消息将在控件设置文本格式之后但在显示文本之前发送。 如果组合框具有 CBS_DROPDOWNLIST 样式，则不会发送它。

- ON_CBN_ERRSPACE 组合框无法分配足够的内存来满足特定的请求。

- ON_CBN_SELENDCANCEL （Windows 3.1 及更高版本。）指示应取消用户的选择。 用户单击某个项，然后单击另一个窗口或控件以隐藏组合框的列表框。 此通知消息将在 CBN_CLOSEUP 通知消息之前发送，以指示应忽略用户的选择。 即使未发送 CBN_CLOSEUP 通知消息（例如，在具有 CBS_SIMPLE 样式的组合框的情况下），也会发送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知消息。

- ON_CBN_SELENDOK 用户选择一个项，然后按 ENTER 键或单击向下箭头键以隐藏组合框的列表框。 此通知消息将在 CBN_CLOSEUP 消息之前发送，以指示应将用户的选择视为有效。 即使未发送 CBN_CLOSEUP 通知消息（例如，在具有 CBS_SIMPLE 样式的组合框的情况下），也会发送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知消息。

- ON_CBN_KILLFOCUS 组合框丢失了输入焦点。

- ON_CBN_SELCHANGE 在组合框的列表框中所选内容将因用户单击列表框或使用箭头键更改选择而更改。 当处理此消息时，组合框的编辑控件中的文本只能通过 `GetLBText` 或其他类似函数检索。 `GetWindowText`不能使用。

- ON_CBN_SETFOCUS 组合框接收输入焦点。

如果在 `CComboBox` 对话框中创建对象（通过对话资源），则 `CComboBox` 当用户关闭对话框时，对象会自动销毁。

如果在 `CComboBox` 另一个窗口对象中嵌入对象，则不需要销毁它。 如果在 `CComboBox` 堆栈上创建对象，则该对象会自动销毁。 如果 `CComboBox` 使用函数在堆上创建对象 **`new`** ，则必须对对象调用以在 **`delete`** 销毁 Windows 组合框时销毁该对象。

**注意**如果要处理 WM_KEYDOWN 和 WM_CHAR 消息，则必须为组合框的编辑和列表框控件创建子类，从和派生类， `CEdit` `CListBox` 然后将这些消息的处理程序添加到派生类。 有关详细信息，请参阅[CWnd：： SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox：： AddString

将字符串添加到组合框的列表框中。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向要添加的以 null 值结束的字符串。

### <a name="return-value"></a>返回值

如果返回值大于或等于0，则它是列表框中的字符串的从零开始的索引。 如果发生错误，将 CB_ERR 返回值;如果没有足够的可用空间来存储新的字符串，则返回值为 CB_ERRSPACE。

### <a name="remarks"></a>备注

如果列表框不是用[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建的，则会将该字符串添加到列表的末尾。 否则，会将字符串插入列表，并对列表进行排序。

> [!NOTE]
> Windows 控件不支持此函数 `ComboBoxEx` 。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

若要将字符串插入到列表中的特定位置，请使用[InsertString](#insertstring)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox：： CComboBox

构造 `CComboBox` 对象。

```
CComboBox();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox：： Clear

删除（清除）组合框编辑控件中的当前选择（如果有）。

```cpp
void Clear();
```

### <a name="remarks"></a>备注

若要删除当前所选内容并将删除的内容放到剪贴板上，请使用[Cut](#cut)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox：： CompareItem

由框架调用，用于确定排序的所有者描述组合框的列表框部分中新项的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lpCompareItemStruct*<br/>
指向[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)结构的长指针。

### <a name="return-value"></a>返回值

指示在结构中描述的两个项的相对位置 `COMPAREITEMSTRUCT` 。 可以是以下任一值：

|值|含义|
|-----------|-------------|
|- 1|项目1排在第2项之前。|
|0|项1和项2排序相同。|
|1|项1在项2之后排序。|

有关的说明，请参阅[CWnd：： OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) `COMPAREITEMSTRUCT` 。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 如果创建具有 LBS_SORT 样式的所有者描述组合框，则必须重写此成员函数，以帮助框架对添加到列表框的新项进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox：： Copy

将组合框编辑控件中的当前选定内容（如果有）复制 CF_TEXT 格式的剪贴板上。

```cpp
void Copy();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox：： Create

创建组合框并将其附加到 `CComboBox` 对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定组合框的样式。 将[组合框样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)的任意组合应用于该框。

*rect*<br/>
指向组合框的位置和大小。 可以是[矩形结构](/windows/win32/api/windef/ns-windef-rect)或 `CRect` 对象。

*pParentWnd*<br/>
指定组合框的父窗口（通常为 `CDialog` ）。 值不得为 NULL。

*nID*<br/>
指定组合框的控件 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过 `CComboBox` 两个步骤构造对象。 首先，调用构造函数，然后调用 `Create` ，它创建 Windows 组合框并将其附加到 `CComboBox` 对象。

`Create`执行时，Windows 会将[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息发送到组合框。

默认情况下，将通过基类中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数来处理这些消息 `CWnd` 。 若要扩展默认消息处理，从派生类 `CComboBox` ，将消息映射添加到新类，然后重写前面的消息处理程序成员函数。 `OnCreate`例如，重写，为新类执行所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于组合框控件。 :

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

- WS_VSCROLL 为组合框中的列表框添加垂直滚动

- WS_HSCROLL 为组合框中的列表框添加水平滚动

- WS_GROUP 分组控件

- WS_TABSTOP 以按 tab 键顺序包含组合框

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox：： Cut

删除组合框编辑控件中的当前选定内容（如果有），并以 CF_TEXT 格式将删除的文本复制到剪贴板。

```cpp
void Cut();
```

### <a name="remarks"></a>备注

若要删除当前所选内容而不将删除的文本放到剪贴板上，请调用[Clear](#clear)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox：:D eleteItem

当用户从所有者描述的对象中删除项 `CComboBox` 或销毁组合框时由框架调用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lpDeleteItemStruct*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)结构的长指针，其中包含有关已删除项的信息。 有关此结构的说明，请参阅[CWnd：： OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以根据需要重绘组合框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox：:D eleteString

从组合框中删除位置*nIndex*中的项。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要删除的字符串的索引。

### <a name="return-value"></a>返回值

如果返回值大于或等于0，则为列表中剩余的字符串的计数。 如果*nIndex*指定的索引大于列表中的项数，则返回值为 CB_ERR。

### <a name="remarks"></a>备注

*NIndex*后面的所有项现在都向下移动一个位置。 例如，如果组合框包含两个项，则删除第一项将导致剩余项现在位于第一个位置。 对于第一个位置中的项， *nIndex*= 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox：:D ir

将文件名或驱动器列表添加到组合框的列表框中。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是 **`enum`** [CFile：： GetStatus](../../mfc/reference/cfile-class.md#getstatus)中所述的任何值组合或以下值的任意组合：

- 可以读取或写入 DDL_READWRITE 文件。

- 可以从读取 DDL_READONLY 文件，但不能将其写入。

- DDL_HIDDEN 文件处于隐藏状态，并且不会显示在目录列表中。

- DDL_SYSTEM 文件是系统文件。

- DDL_DIRECTORY *lpszWildCard*指定的名称指定目录。

- DDL_ARCHIVE 文件已存档。

- DDL_DRIVES 包括与*lpszWildCard*指定的名称相匹配的所有驱动器。

- DDL_EXCLUSIVE 排他标志。 如果设置了独占标志，则仅列出指定类型的文件。 否则，除了 "正常" 文件，还会列出指定类型的文件。

*lpszWildCard*<br/>
指向文件规范字符串。 字符串可以包含通配符（例如 *. \* ）。

### <a name="return-value"></a>返回值

如果返回值大于或等于0，则它是添加到列表中的最后一个文件名的从零开始的索引。 如果发生错误，将 CB_ERR 返回值;如果没有足够的可用空间来存储新的字符串，则返回值为 CB_ERRSPACE。

### <a name="remarks"></a>备注

Windows 控件不支持此函数 `ComboBoxEx` 。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox：:D rawItem

当所有者描述的组合框的视觉方面发生变化时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，该结构包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

`itemAction`结构的成员 `DRAWITEMSTRUCT` 定义要执行的绘图操作。 有关此结构的说明，请参阅[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者描述对象的绘制 `CComboBox` 。 此成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox：： FindString

在组合框的列表框中查找（但不选择）包含指定前缀的第一个字符串。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nStartAfter*指定的项。 如果为-1，则从一开始就搜索整个列表框。

*lpszString*<br/>
指向以 null 结尾的字符串，该字符串包含要搜索的前缀。 搜索是独立的，因此，此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

如果返回值大于或等于0，则它是匹配项的从零开始的索引。 如果搜索未成功，则 CB_ERR。

### <a name="remarks"></a>备注

Windows 控件不支持此函数 `ComboBoxEx` 。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox：： FindStringExact

调用 `FindStringExact` 成员函数，查找与*lpszFind*中指定的字符串匹配的第一个列表框字符串（在组合框中）。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndexStart*<br/>
指定要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nIndexStart*指定的项。 如果*nIndexStart*为-1，则从一开始就搜索整个列表框。

*lpszFind*<br/>
指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名（包括扩展名）。 搜索不区分大小写，因此此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

匹配项的从零开始的索引; 如果搜索未成功，则 CB_ERR。

### <a name="remarks"></a>备注

如果使用所有者描述样式创建组合框，但没有[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则 `FindStringExact` 会尝试将双字值与*lpszFind*的值匹配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox：： GetComboBoxInfo

检索对象的信息 `CComboBox` 。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>参数

*pcbi*<br/>
指向[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟[CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo)消息的功能，如 Windows SDK 中所述。

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox：： GetCount

调用此成员函数以检索组合框的列表框部分中的项数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

项数。 返回的计数比最后一项的索引值大1（索引从零开始）。 如果发生错误，则 CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox：： GetCueBanner

获取为组合框控件显示的提示文本。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpszText*|弄指向接收提示横幅文本的缓冲区的指针。|
|*cchText*|中*LpszText*参数指向的缓冲区的大小。|

### <a name="return-value"></a>返回值

在第一个重载中，包含提示横幅文本的[CString](../../atl-mfc-shared/using-cstring.md)对象（如果存在）;否则为 `CString` 长度为零的对象。

-或-

在第二个重载中，如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

提示文本是显示在组合框控件的输入区域中的提示。 显示提示文本直到用户提供输入。

此方法发送 Windows SDK 中描述的[CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner)消息。

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox：： GetCurSel

调用此成员函数以确定组合框中选定的项。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

组合框的列表框中当前选定项的从零开始的索引; 如果未选择任何项，则为 CB_ERR。

### <a name="remarks"></a>备注

`GetCurSel`返回列表中的索引。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox：： GetDroppedControlRect

调用 `GetDroppedControlRect` 成员函数以检索下拉组合框的可见（下拉列表）列表框的屏幕坐标。

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>参数

*lprect*<br/>
指向用于接收坐标的[RECT 结构](/windows/win32/api/windef/ns-windef-rect)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox：： GetDroppedState

调用 `GetDroppedState` 成员函数以确定下拉组合框的列表框是否可见（已删除）。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>返回值

如果列表框可见，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox：： GetDroppedWidth

调用此函数可检索组合框列表框的最小允许宽度（以像素为单位）。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>返回值

如果成功，则为允许的最小宽度（以像素为单位）;否则，CB_ERR。

### <a name="remarks"></a>备注

此函数仅适用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框。

默认情况下，下拉列表框的最小允许宽度为0。 可以通过调用[SetDroppedWidth](#setdroppedwidth)来设置允许的最小宽度。 当显示组合框的列表框部分时，其宽度为允许的最小宽度或组合框宽度中的最大值。

### <a name="example"></a>示例

  请参阅[SetDroppedWidth](#setdroppedwidth)的示例。

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox：： GetEditSel

获取组合框编辑控件中当前所选内容的起始和结束字符位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>返回值

一个32位值，该值包含低序位字中的起始位置和高位字中选定内容末尾后的第一个 nonselected 字符的位置。 如果在没有编辑控件的组合框上使用此函数，将返回 CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox：： GetExtendedUI

调用 `GetExtendedUI` 成员函数以确定组合框是否具有默认用户界面或扩展的用户界面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>返回值

如果组合框具有扩展的用户界面，则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过以下方式识别扩展的用户界面：

- 单击静态控件将仅显示具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框的列表框。

- 按向下键将显示列表框（禁用 F4）。

当项列表不可见（禁用箭头键）时，将禁用静态控件中的滚动。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox：： GetHorizontalExtent

从组合框中检索以像素为单位的宽度（以像素为单位），组合框的列表框部分可水平滚动。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

组合框的列表框部分的可滚动宽度（以像素为单位）。

### <a name="remarks"></a>备注

仅当组合框的列表框部分具有水平滚动条时，此属性才适用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox：： GetItemData

检索应用程序提供的与指定组合框项关联的32位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含组合框的列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

与项关联的32位值，如果发生错误，则 CB_ERR。

### <a name="remarks"></a>备注

可以使用[SetItemData](#setitemdata)成员函数调用的*dwItemData*参数设置32位值。 `GetItemDataPtr`如果要检索的32位值为指针（），请使用成员函数 **`void`** <strong>\*</strong> 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox：： GetItemDataPtr

检索应用程序提供的与指定组合框项关联的32位值作为指针（ **`void`** <strong>\*</strong> ）。

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含组合框的列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

检索指针，如果发生错误，则为-1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox：： GetItemHeight

调用 `GetItemHeight` 成员函数以检索组合框中列表项的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定组合框的组件，要检索其高度。 如果*nIndex*参数为-1，则将检索组合框的编辑控件（或静态文本）部分的高度。 如果组合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则*nIndex*指定要检索其高度的列表项的从零开始的索引。 否则， *nIndex*应设置为0。

### <a name="return-value"></a>返回值

组合框中指定项的高度（以像素为单位）。 返回值是 CB_ERR 如果发生错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox：： GetLBText

从组合框的列表框中获取一个字符串。

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要复制的列表框字符串的从零开始的索引。

*lpszText*<br/>
指向接收字符串的缓冲区。 缓冲区必须具有足够的空间用于字符串和终止 null 字符。

*rString*<br/>
对 `CString` 的引用。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止的 null 字符。 如果*nIndex*未指定有效的索引，则返回值为 CB_ERR。

### <a name="remarks"></a>备注

此成员函数的第二种形式将 `CString` 对象替换为该项的文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox：： GetLBTextLen

获取组合框的列表框中的字符串长度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含列表框字符串的从零开始的索引。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止 null 字符。 如果*nIndex*未指定有效的索引，则返回值为 CB_ERR。

### <a name="example"></a>示例

  请参阅[CComboBox：： GetLBText](#getlbtext)的示例。

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox：： GetLocale

检索组合框所使用的区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

组合框中字符串的区域设置标识符（LCID）值。

### <a name="remarks"></a>备注

例如，使用区域设置来确定已排序组合框中字符串的排序顺序。

### <a name="example"></a>示例

  请参阅[CComboBox：： SetLocale](#setlocale)的示例。

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox：： GetMinVisible

获取当前组合框控件的下拉列表中可见项的最小数目。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>返回值

当前下拉列表中可见项的最小数目。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)消息。

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox：： GetTopIndex

检索组合框的列表框部分中第一个可见项的从零开始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，组合框的列表框部分中第一个可见项的从零开始的索引，CB_ERR 否则为。

### <a name="remarks"></a>备注

最初，项0位于列表框的顶部，但如果滚动列表框，则其他项可能位于顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox：： InitStorage

分配用于在组合框的列表框部分中存储列表框项的内存。

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

如果成功，则在需要重新分配内存之前，组合框的列表框部分可以存储的最大项数，否则 CB_ERRSPACE，这意味着没有足够的内存可用。

### <a name="remarks"></a>备注

在将大量项添加到的列表框部分之前，请调用此函数 `CComboBox` 。

仅限 Windows 95/98： *wParam*参数限制为16位值。 这意味着列表框包含的项不能超过32767个。 尽管项目数受到限制，列表框中的项的总大小仅受可用内存的限制。

此函数有助于加快具有大量项（超过100个）的列表框的初始化速度。 它预分配指定的内存量，以便后续的[AddString](#addstring)、 [InsertString](#insertstring)和[Dir](#dir)函数可以使用最短的时间。 您可以对参数使用估算值。 如果最好，则分配一些额外的内存;如果你低估，则会将常规分配用于超出预分配数量的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox：： InsertString

将字符串插入组合框的列表框。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含一个索引（该索引从零开始），该索引指向列表框中将接收字符串的位置。 如果此参数为-1，则字符串将被添加到列表的末尾。

*lpszString*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 返回值是 CB_ERR 如果发生错误。 如果没有足够空间可用于存储新的字符串，则返回值为 CB_ERRSPACE。

### <a name="remarks"></a>备注

与 [AddString](#addstring) 成员函数不同， `InsertString` 成员函数不会导致对一个列表的 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 样式进行排序。

> [!NOTE]
> Windows 控件不支持此函数 `ComboBoxEx` 。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox：： LimitText

限制用户可以在组合框的编辑控件中输入的文本的长度（以字节为单位）。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>参数

*nMaxChars*<br/>
指定用户可输入的文本的长度（以字节为单位）。 如果此参数为0，则文本长度设置为65535字节。

### <a name="return-value"></a>返回值

如果成功，则为非零值。 如果为样式[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)的组合框或没有编辑控件的组合框调用，则返回值为 CB_ERR。

### <a name="remarks"></a>备注

如果组合框没有样式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，则将文本限制设置为大于编辑控件的大小将不起作用。

`LimitText`仅限制用户可输入的文本。 它不会影响在发送消息时编辑控件中已有的任何文本，也不会影响在选择列表框中的字符串时复制到编辑控件中的文本的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox：： MeasureItem

当创建具有所有者描述样式的组合框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lpMeasureItemStruct*<br/>
指向[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)结构的长指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 重写此成员函数并填充 `MEASUREITEMSTRUCT` 结构，以便在组合框中通知窗口列表框的维度。 如果组合框是用[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建的，则框架将为列表框中的每个项调用此成员函数。 否则，此成员只调用一次。

使用[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成员函数创建的所有者描述组合框中的 CBS_OWNERDRAWFIXED 样式 `CWnd` 涉及到进一步的编程注意事项。 请参阅[技术说明 14](../../mfc/tn014-custom-controls.md)中的讨论。

有关结构的说明，请参阅[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) `MEASUREITEMSTRUCT` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox：:P aste

将剪贴板中的数据插入到当前光标位置的组合框的编辑控件中。

```cpp
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板包含 CF_TEXT 格式的数据时，才插入数据。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox：： ResetContent

从列表框中移除所有项，并在组合框中编辑控件。

```cpp
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox：： SelectString

在组合框的列表框中搜索字符串，如果找到该字符串，则选择列表框中的字符串，并将其复制到编辑控件中。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前项的从零开始的索引。 当搜索到达列表框的底部时，它会从列表框的顶部继续到由*nStartAfter*指定的项。 如果为-1，则从一开始就搜索整个列表框。

*lpszString*<br/>
指向以 null 结尾的字符串，该字符串包含要搜索的前缀。 搜索是独立的，因此，此字符串可以包含任意大小写字母的组合。

### <a name="return-value"></a>返回值

如果找到该字符串，则为选定项的从零开始的索引。 如果搜索未成功，则返回值为 CB_ERR，当前所选内容不会更改。

### <a name="remarks"></a>备注

仅当字符串的初始字符（从起始点开始）与前缀字符串中的字符匹配时，才会选择字符串。

请注意， `SelectString` 和 `FindString` 成员函数都查找字符串，但 `SelectString` 成员函数也会选择字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox：： SetCueBanner

设置为组合框控件显示的提示文本。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpszText*|中指向以 null 结尾的包含提示文本的缓冲区的指针。|

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

提示文本是显示在组合框控件的输入区域中的提示。 显示提示文本直到用户提供输入。

此方法发送 Windows SDK 中描述的[CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问组合框控件的变量*m_combobox*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

下面的代码示例设置组合框控件的提示横幅。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox：： SetCurSel

在组合框的列表框中选择一个字符串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*选择*<br/>
指定要选择的字符串的从零开始的索引。 如果为-1，则删除列表框中的任何当前选择，并清除编辑控件。

### <a name="return-value"></a>返回值

如果消息成功，则为所选项的从零开始的索引。 如果*选择*大于列表中的项数，则返回值为 CB_ERR; 如果*选择*设置为-1，则将清除选择。

### <a name="remarks"></a>备注

如有必要，列表框会将字符串滚动到视图中（如果列表框可见）。 组合框的编辑控件中的文本将更改以反映新的选择。 列表框中以前的任何选择都将被删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox：： SetDroppedWidth

调用此函数可设置组合框列表框的最小允许宽度（以像素为单位）。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
组合框的列表框部分的最小允许宽度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则为列表框的新宽度，否则 CB_ERR。

### <a name="remarks"></a>备注

此函数仅适用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框。

默认情况下，下拉列表框的最小允许宽度为0。 当显示组合框的列表框部分时，其宽度为允许的最小宽度或组合框宽度中的最大值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox：： SetEditSel

在组合框的编辑控件中选择字符。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
指定起始位置。 如果起始位置设置为-1，则将删除任何现有选择。

*nEndChar*<br/>
指定结束位置。 如果结束位置设置为-1，则选择来自编辑控件中的最后一个字符的起始位置的所有文本。

### <a name="return-value"></a>返回值

如果成员函数成功，则为非零值;否则为0。 如果 `CComboBox` 具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式或没有列表框，则 CB_ERR。

### <a name="remarks"></a>备注

位置是从零开始的。 若要选择编辑控件的第一个字符，请指定起始位置0。 结束位置就是最后一个字符之后要选择的字符。 例如，若要选择编辑控件的前四个字符，请使用0的起始位置和结束位置4。

> [!NOTE]
> Windows 控件不支持此函数 `ComboBoxEx` 。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

  请参阅[CComboBox：： GetEditSel](#geteditsel)的示例。

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox：： SetExtendedUI

调用 `SetExtendedUI` 成员函数以为具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框选择默认的用户界面或扩展的用户界面。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>参数

*bExtended*<br/>
指定组合框是否应使用扩展的用户界面或默认用户界面。 如果值为 TRUE，则选择扩展的用户界面;如果值为 FALSE，则选择标准用户界面。

### <a name="return-value"></a>返回值

CB_OKAY 如果操作成功，则为; 如果发生错误，则为 CB_ERR。

### <a name="remarks"></a>备注

可以通过以下方式识别扩展的用户界面：

- 单击静态控件将仅显示具有 CBS_DROPDOWNLIST 样式的组合框的列表框。

- 按向下键将显示列表框（禁用 F4）。

当项列表不可见（禁用箭头键）时，将禁用静态控件中的滚动。

### <a name="example"></a>示例

  请参阅[CComboBox：： GetExtendedUI](#getextendedui)的示例。

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox：： SetHorizontalExtent

设置组合框的列表框部分可水平滚动的宽度（以像素为单位）。

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>参数

*nExtent*<br/>
指定组合框的列表框部分可水平滚动的像素数。

### <a name="remarks"></a>备注

如果列表框的宽度小于此值，则水平滚动条将在列表框中水平滚动项。 如果列表框的宽度等于或大于此值，则水平滚动条是隐藏的，或者，如果组合框具有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则为 "已禁用"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox：： SetItemData

设置与组合框中的指定项关联的32位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的项的从零开始的索引。

*dwItemData*<br/>
包含要与项关联的新值。

### <a name="return-value"></a>返回值

如果发生错误，则 CB_ERR。

### <a name="remarks"></a>备注

`SetItemDataPtr`如果32位项是指针，请使用成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox：： SetItemDataPtr

将与组合框中的指定项关联的32位值设置为指定的指针（ **`void`** <strong>\*</strong> ）。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含项的从零开始的索引。

*pData*<br/>
包含与项关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，则 CB_ERR。

### <a name="remarks"></a>备注

此指针在组合框的生存期内保持有效，即使在添加或删除项时，组合框中的项的相对位置可能会更改。 因此，框中的项的索引可能会改变，但指针会保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox：： SetItemHeight

调用 `SetItemHeight` 成员函数以设置组合框中的列表项的高度或组合框的编辑控件（或静态文本）部分的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定是否设置列表项的高度或组合框的编辑控件（或静态文本）部分的高度。

如果组合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则*nIndex*指定要设置其高度的列表项的从零开始的索引。否则， *nIndex*必须为0，并且将设置所有列表项的高度。

如果*nIndex*为-1，则将设置组合框的编辑控件或静态文本部分的高度。

*cyItemHeight*<br/>
指定由*nIndex*标识的组合框组件的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果索引或高度无效，则 CB_ERR;否则为0。

### <a name="remarks"></a>备注

组合框的编辑控件（或静态文本）部分的高度独立于列表项的高度设置。 应用程序必须确保编辑控件（或静态文本）部分的高度不小于特定列表框项的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox：： SetLocale

为此组合框设置区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*nNewLocale*<br/>
要为组合框设置的新区域设置标识符（LCID）值。

### <a name="return-value"></a>返回值

此组合框的上一个区域设置标识符（LCID）值。

### <a name="remarks"></a>备注

如果 `SetLocale` 未调用，则从系统获取默认区域设置。 可以使用 "控制面板" 的 "区域" （或 "国际"）应用程序修改此系统默认区域设置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox：： SetMinVisibleItems

设置当前组合框控件的下拉列表中可见项的最小数目。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iMinVisible*|中指定可见项的最小数目。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问组合框控件的变量*m_combobox*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

下面的代码示例在组合框控件的下拉列表中插入20个项。 然后，它指定在用户按下下拉箭头时，最少显示10个项。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox：： SetTopIndex

确保在组合框的列表框部分中显示特定项。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则为零; 如果发生错误，则为 CB_ERR。

### <a name="remarks"></a>备注

系统将滚动列表框，直到*nIndex*指定的项显示在列表框的顶部或已达到最大滚动范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox：： ShowDropDown

显示或隐藏具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框的列表框。

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>参数

*bShowIt*<br/>
指定是显示还是隐藏下拉列表框。 如果值为 TRUE，则显示列表框。 如果值为 FALSE，则隐藏列表框。

### <a name="remarks"></a>备注

默认情况下，此样式的组合框将显示列表框。

此成员函数对使用[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建的组合框没有影响。

### <a name="example"></a>示例

  请参阅[CComboBox：： GetDroppedState](#getdroppedstate)的示例。

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
