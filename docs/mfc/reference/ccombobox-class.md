---
title: CComboBox 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d418fc45d3947248c78d70af5d036bd93b204d
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821499"
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
|[CComboBox::CComboBox](#ccombobox)|构造 `CComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Ccombobox:: Addstring](#addstring)|将字符串添加到列表框中的一个组合框，或在列表框使用 CBS_SORT 样式的排序位置列表的末尾。|
|[CComboBox::Clear](#clear)|删除 （清除） 当前选定内容，如果有，编辑控件中。|
|[CComboBox::CompareItem](#compareitem)|由框架调用以确定新列表项的已排序的所有者描述的组合框中的相对位置。|
|[CComboBox::Copy](#copy)|复制当前所选内容，如果有，CF_TEXT 格式在剪贴板上。|
|[CComboBox::Create](#create)|创建组合框，并将其附加到`CComboBox`对象。|
|[CComboBox::Cut](#cut)|（剪切） 中删除当前选定内容，如果任何编辑中控制和 CF_TEXT 格式复制到剪贴板上删除的文本。|
|[CComboBox::DeleteItem](#deleteitem)|从一个所有者描述的组合框删除列表项时由框架调用。|
|[CComboBox::DeleteString](#deletestring)|从组合框的列表框中删除一个字符串。|
|[CComboBox::Dir](#dir)|将文件名称的列表添加到组合框的列表框。|
|[CComboBox::DrawItem](#drawitem)|由框架在所有者描述的组合框中更改的可视方面时调用。|
|[Ccombobox:: Findstring](#findstring)|查找包含指定的前缀组合框的列表框中的第一个字符串。|
|[CComboBox::FindStringExact](#findstringexact)|查找第一个列表框中的字符串 （组合框） 与指定的字符串匹配。|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|检索有关的信息`CComboBox`对象。|
|[CComboBox::GetCount](#getcount)|检索在组合框的列表框中的项的数目。|
|[CComboBox::GetCueBanner](#getcuebanner)|获取组合框控件显示的提示文本。|
|[CComboBox::GetCurSel](#getcursel)|如果有，组合框的列表框中，检索当前选定项的索引。|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|检索一个下拉组合框的可见 （已关闭删除） 列表框的屏幕坐标。|
|[CComboBox::GetDroppedState](#getdroppedstate)|确定一个下拉组合框列表框是否可见的 （下降）。|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|检索的最小允许组合框的下拉列表框部分的宽度。|
|[CComboBox::GetEditSel](#geteditsel)|获取当前选择的组合框编辑控件中的起始和结束字符位置。|
|[CComboBox::GetExtendedUI](#getextendedui)|确定组合框具有默认用户界面或扩展的用户界面。|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|返回以像素为单位可以水平滚动的组合框的列表框部分的宽度。|
|[CComboBox::GetItemData](#getitemdata)|检索与指定的组合框项关联的应用程序提供 32 位值。|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|检索与指定的组合框项相关联的应用程序提供 32 位指针。|
|[CComboBox::GetItemHeight](#getitemheight)|检索在组合框的列表项的高度。|
|[CComboBox::GetLBText](#getlbtext)|从组合框的列表框中获取的字符串。|
|[CComboBox::GetLBTextLen](#getlbtextlen)|在组合框的列表框中获取字符串的长度。|
|[CComboBox::GetLocale](#getlocale)|检索一个组合框的区域设置标识符。|
|[CComboBox::GetMinVisible](#getminvisible)|获取在当前的组合框下拉列表中可见的项的最小数目。|
|[CComboBox::GetTopIndex](#gettopindex)|返回在组合框的列表框部分中的第一个可见项的索引。|
|[CComboBox::InitStorage](#initstorage)|预先分配项目和组合框的列表框部分中的字符串的内存的块。|
|[CComboBox::InsertString](#insertstring)|将字符串插入组合框的列表框。|
|[CComboBox::LimitText](#limittext)|限制用户可以向组合框编辑控件中输入文本的长度。|
|[CComboBox::MeasureItem](#measureitem)|由框架调用以创建一个所有者描述的组合框时确定组合框尺寸。|
|[CComboBox::Paste](#paste)|将数据从剪贴板插入到当前光标位置处的编辑控件。 仅当剪贴板包含 CF_TEXT 格式的数据插入数据。|
|[CComboBox::ResetContent](#resetcontent)|删除所有项从列表框和编辑组合框控件。|
|[CComboBox::SelectString](#selectstring)|搜索字符串的组合框的列表框中，如果找到该字符串，选择列表框中的字符串，并将字符串复制到编辑控件。|
|[CComboBox::SetCueBanner](#setcuebanner)|设置为一个组合框控件显示的提示文本。|
|[CComboBox::SetCurSel](#setcursel)|在组合框的列表框中选择一个字符串。|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|设置最小允许组合框的下拉列表框部分的宽度。|
|[CComboBox::SetEditSel](#seteditsel)|选择组合框编辑控件中的字符。|
|[CComboBox::SetExtendedUI](#setextendedui)|选择默认用户界面或组合框 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式扩展的用户界面。|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|设置以像素为单位可以水平滚动的组合框的列表框部分的宽度。|
|[CComboBox::SetItemData](#setitemdata)|设置与组合框中指定的项关联的 32 位值。|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|设置与组合框中指定的项关联的 32 位指针。|
|[CComboBox::SetItemHeight](#setitemheight)|在组合框或组合框的编辑控件 （或静态文本） 部分的高度设置列表项的高度。|
|[CComboBox::SetLocale](#setlocale)|设置组合框的区域设置标识符。|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|设置当前的组合框的下拉列表中可见的项的最小数目。|
|[CComboBox::SetTopIndex](#settopindex)|指示组合框，以在顶部显示具有指定索引的项的列表框部分。|
|[CComboBox::ShowDropDown](#showdropdown)|显示或隐藏 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式组合框的列表框。|

## <a name="remarks"></a>备注

组合框包含一个列表框，与静态控件或编辑控件结合使用。 控件的列表框部分可能会显示在所有时间或仅可能其在用户选择控件旁边的下拉箭头时下拉列表。

在列表框中的当前选定的项 （如果有） 中静态显示或编辑控件。 此外，如果组合框的下拉列表样式，用户可以在列表中，键入的某个项的初始字符和列表框中，如果可见，请将突出显示与该初始字符的下一项。

下表比较了三个组合框[样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|样式|当列表框是可见的|静态或编辑控件|
|-----------|-------------------------------|-----------------------------|
|简单|Always|Edit|
|Drop-down|向下删除时|Edit|
|下拉列表|向下删除时|Static|

您可以创建`CComboBox`通过对话框模板或直接在代码中的对象。 在这两种情况下，首次调用构造函数`CComboBox`来构造`CComboBox`对象; 然后调用[创建](#create)成员函数来创建控件并将其附加到`CComboBox`对象。

如果你想要处理 Windows 通知消息发送到其父组合框 (从派生的类通常`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。

每个消息映射条目采用以下形式：

**ON_** 通知 **(**`id`**，**`memberFxn`**)**

其中`id`指定将通知发送到该组合框控件的子窗口 ID 和`memberFxn`是您编写以处理通知的父成员函数的名称。

父项的函数原型如下所示：

**afx_msg** `void` `memberFxn` **（);**

无法预测将发送某些通知的顺序。 具体而言，如果之前或之后 CBN_CLOSEUP 通知，则可能会出现 CBN_SELCHANGE 通知。

潜在的消息映射条目如下所示：

- ON_CBN_CLOSEUP (Windows 3.1 和更高版本。)组合框的列表框已关闭。 已对组合框不发送此通知消息[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

- ON_CBN_DBLCLK 用户双击某个字符串的组合框的列表框中。 此通知消息仅发送具有 CBS_SIMPLE 样式组合框。 使用组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，不能出现一次双击因为一次单击隐藏列表框。

- ON_CBN_DROPDOWN 即将下拉组合框的列表框 （成为可见）。 仅为具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 样式的组合框会出现此通知消息。

- ON_CBN_EDITCHANGE 用户已采取的操作可能已更改的组合框的编辑控件部分中的文本。 CBN_EDITUPDATE 消息，与 Windows 更新屏幕后发送此消息。 它不会发送如果组合框具有 CBS_DROPDOWNLIST 样式。

- ON_CBN_EDITUPDATE 组合框的编辑控件部分即将更改的显示文本。 控件设置文本格式之后，但其显示文本之前发送此通知消息。 它不会发送如果组合框具有 CBS_DROPDOWNLIST 样式。

- ON_CBN_ERRSPACE 组合框无法分配足够的内存来满足特定的请求。

- ON_CBN_SELENDCANCEL (Windows 3.1 和更高版本。)指示应取消用户的选择。 用户单击某个项，然后单击另一个窗口或控件，隐藏的组合框的列表框。 此通知消息发送之前 CBN_CLOSEUP 通知消息，指示应忽略用户的选择。 即使 CBN_CLOSEUP 通知消息不会发送 （对于具有 CBS_SIMPLE 样式的组合框） 发送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知消息。

- ON_CBN_SELENDOK 用户选择某个项，然后按 ENTER 键或单击向下箭头键，若要隐藏的组合框的列表框。 之前，应考虑用户的选择有效的 CBN_CLOSEUP 消息发送此通知消息。 即使 CBN_CLOSEUP 通知消息不会发送 （对于具有 CBS_SIMPLE 样式的组合框） 发送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知消息。

- ON_CBN_KILLFOCUS 组合框正在失去输入的焦点。

- ON_CBN_SELCHANGE 组合框列表框中的选择是由于用户在列表框中单击或使用箭头键更改所选内容而更改。 在处理此消息时，在组合框编辑控件中的文本，仅可以通过检索`GetLBText`或另一个类似的函数。 `GetWindowText` 无法使用。

- ON_CBN_SETFOCUS 组合框接收到输入的焦点。

如果您创建`CComboBox`（通过对话框资源） 对话框中的对象`CComboBox`在用户关闭对话框时自动销毁对象。

如果在嵌入`CComboBox`对象在另一个窗口中的对象，不需要将其销毁。 如果您创建`CComboBox`对象在堆栈上被自动销毁。 如果您创建`CComboBox`通过使用堆上的对象**新**函数，必须调用**删除**上要销毁 Windows 组合框时对其进行销毁的对象。

**请注意**如果你想要处理 WM_KEYDOWN 和 WM_CHAR 消息，则必须为子类组合框的编辑和列表框控件中，派生类从`CEdit`和`CListBox`，并将这些消息的处理程序添加到派生的类。 有关详细信息，请参阅[ http://support.microsoft.com/default.aspxscid=kb;Q174667](http://support.microsoft.com/default.aspxscid=kb;q174667)并[CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="addstring"></a>  Ccombobox:: Addstring

将字符串添加到组合框的列表框。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向要添加的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

如果返回值是大于或等于 0，它是到列表框中的字符串的从零开始的索引。 返回值是 CB_ERR，如果发生错误;如果没有足够空间可用于存储新字符串，返回值将为 CB_ERRSPACE。

### <a name="remarks"></a>备注

如果不通过创建列表框[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则字符串添加到列表的末尾。 否则为该字符串插入到列表中，并且对列表进行排序。

> [!NOTE]
>  此函数不受 Windows`ComboBoxEx`控件。 有关此控件的详细信息，请参阅[ComboBoxEx 控件](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。

若要将一个字符串插入到列表中的特定位置，请使用[InsertString](#insertstring)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>  CComboBox::CComboBox

构造 `CComboBox` 对象。

```
CComboBox();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>  CComboBox::Clear

删除 （清除） 当前选定内容，如果有，组合框编辑控件中。

```
void Clear();
```

### <a name="remarks"></a>备注

若要删除当前所选内容并放置到剪贴板上已删除的内容，请使用[剪切](#cut)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>  CComboBox::CompareItem

由框架调用以确定新项的已排序的所有者描述组合框的列表框部分中的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lpCompareItemStruct*<br/>
指向的长指针[COMPAREITEMSTRUCT](../../mfc/reference/compareitemstruct-structure.md)结构。

### <a name="return-value"></a>返回值

指示中所述的两个项目的相对位置`COMPAREITEMSTRUCT`结构。 它可以是以下值之一：

|“值”|含义|
|-----------|-------------|
|- 1|第 1 项进行排序项 2 之前。|
|0|第 1 项和项 2 排序相同。|
|1|在项 2 之后，第 1 项进行排序。|

请参阅[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)有关的说明`COMPAREITEMSTRUCT`。

### <a name="remarks"></a>备注

默认情况下，此成员函数没有任何影响。 如果使用 LBS_SORT 样式创建所有者描述组合框，必须重写此成员函数以帮助对新项添加到列表框排序的框架。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>  CComboBox::Copy

如果有，CF_TEXT 格式在剪贴板上组合框编辑控件中，将复制当前选定内容。

```
void Copy();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>  CComboBox::Create

创建组合框，并将其附加到`CComboBox`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定组合框的样式。 应用的任意组合[组合框样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)给数字显示框。

*rect*<br/>
指向的位置和大小的组合框。 可以是[RECT 结构](../../mfc/reference/rect-structure1.md)或`CRect`对象。

*pParentWnd*<br/>
指定组合框的父窗口 (通常`CDialog`)。 它不能为 NULL。

*nID*<br/>
指定组合框控件 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

构造`CComboBox`两个步骤中的对象。 首先，调用构造函数，然后调用`Create`，它创建 Windows 组合框，并将其附加到`CComboBox`对象。

当`Create`执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，并且[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)用于组合框的消息。

默认情况下处理这些消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，以及[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，从派生类`CComboBox`、 将消息映射添加到新类和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要执行的一个新类所需的初始化。

将以下内容应用[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到组合框控件。 :

- WS_CHILD 始终

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 将添加到组合框中的列表框的垂直滚动

- WS_HSCROLL 将添加到组合框中的列表框的水平滚动

- WS_GROUP 与组控件

- WS_TABSTOP 到按 tab 键顺序包括组合框

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>  CComboBox::Cut

删除 （剪切） 当前选定内容，如果任何组合框中编辑控件和 CF_TEXT 格式复制到剪贴板上删除的文本。

```
void Cut();
```

### <a name="remarks"></a>备注

若要删除当前所选内容，但不将剪贴板上删除的文本，调用[清除](#clear)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>  CComboBox::DeleteItem

当用户从所有者描述删除项时由框架调用`CComboBox`对象或销毁组合框。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lpDeleteItemStruct*<br/>
指向 Windows 的长指针[DELETEITEMSTRUCT](../../mfc/reference/deleteitemstruct-structure.md)结构，其中包含有关已删除的项的信息。 请参阅[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)有关此结构的说明。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数可根据需要重绘组合框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>  CComboBox::DeleteString

删除位置中的项*nIndex*从组合框。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定为要删除的字符串的索引。

### <a name="return-value"></a>返回值

如果返回值是大于或等于 0，它是在列表中剩余的字符串的计数。 如果，则返回值为 CB_ERR *nIndex*指定列表中的索引大于项的数目。

### <a name="remarks"></a>备注

后面的所有项*nIndex*现在将下移一个位置。 例如，如果组合框包含两个项，则删除的第一项将导致剩余的项现在位于第一个位置。 *nIndex*= 0 中的第一个位置的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>  CComboBox::Dir

将文件名或驱动器的列表添加到组合框的列表框。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是任何组合**enum**值中所述[cfile:: Getstatus](../../mfc/reference/cfile-class.md#getstatus)或以下值的任意组合：

- 可以读取或写入到 DDL_READWRITE 文件。

- 可以从读取但不是会写入到 DDL_READONLY 文件。

- DDL_HIDDEN 文件处于隐藏状态，并且未出现在目录列表。

- DDL_SYSTEM 文件是系统文件。

- 指定的名称 DDL_DIRECTORY *lpszWildCard*指定的目录。

- 已存档 DDL_ARCHIVE 文件。

- DDL_DRIVES 包含由指定的名称匹配的所有驱动器*lpszWildCard*。

- DDL_EXCLUSIVE 独占标志。 如果设置了排他的标志，列出了仅指定类型的文件。 否则，除了"normal"的文件都列出了指定类型的文件。

*lpszWildCard*<br/>
指向文件规范的字符串。 该字符串可包含通配符 (例如，*。\*)。

### <a name="return-value"></a>返回值

如果返回值是大于或等于 0，它是最后一个文件名添加到列表中的从零开始的索引。 返回值是 CB_ERR，如果发生错误;如果没有足够空间可用于存储新字符串，返回值将为 CB_ERRSPACE。

### <a name="remarks"></a>备注

此函数不受 Windows`ComboBoxEx`控件。 有关此控件的详细信息，请参阅[ComboBoxEx 控件](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>  CComboBox::DrawItem

由框架在所有者描述组合框中更改的可视方面时调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
一个指向[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关绘图所需的类型的信息。

### <a name="remarks"></a>备注

`itemAction`的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 请参阅[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)有关此结构的说明。

默认情况下，此成员函数没有任何影响。 重写此成员函数以实现绘制所有者描述的`CComboBox`对象。 此成员函数将终止之前，应用程序应还原所有图形设备接口 (GDI) 对象的显示上下文中提供选定*lpDrawItemStruct*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>  Ccombobox:: Findstring

找到，但不会选择第一个字符串中包含一个组合框的列表框中指定的前缀。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nStartAfter*。 如果为-1，从开始处搜索整个列表框。

*lpszString*<br/>
指向包含要搜索的前缀的以 null 结尾的字符串。 搜索是区分，因此此字符串可以包含任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

如果返回值是大于或等于 0，它是匹配项的从零开始的索引。 如果搜索未成功，则 CB_ERR。

### <a name="remarks"></a>备注

此函数不受 Windows`ComboBoxEx`控件。 有关此控件的详细信息，请参阅[ComboBoxEx 控件](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>  CComboBox::FindStringExact

调用`FindStringExact`成员函数以查找第一个列表框中的字符串 （组合框） 中指定的字符串匹配*lpszFind*。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndexStart*<br/>
指定要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nIndexStart*。 如果*nIndexStart*为-1，从开始处搜索整个列表框。

*lpszFind*<br/>
指向要搜索的以 null 结尾的字符串。 此字符串可以包含完整的文件名，将该扩展。 搜索不区分大小写，因此此字符串可以包含任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

CB_ERR 如果搜索未成功的匹配项的从零开始的索引。

### <a name="remarks"></a>备注

如果组合框但没有创建所有者绘制样式[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式`FindStringExact`尝试匹配的值的双字值*lpszFind*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>  CComboBox::GetComboBoxInfo

检索信息`CComboBox`对象。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>参数

*pcbi*<br/>
一个指向[COMBOBOXINFO](/windows/desktop/api/winuser/ns-winuser-tagcomboboxinfo)结构。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此成员函数模拟的功能[CB_GETCOMBOBOXINFO](/windows/desktop/Controls/cb-getcomboboxinfo)消息，如 Windows SDK 中所述。

##  <a name="getcount"></a>  CComboBox::GetCount

调用此成员函数以检索在组合框的列表框部分中的项的数目。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

项的数目。 返回的计数是一个大于 （索引为从零开始） 的最后一项的索引值。 如果发生错误，则 CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>  CComboBox::GetCueBanner

获取组合框控件显示的提示文本。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpszText*|[out]指向该缓冲区用于接收的提示标志文本。|
|*cchText*|[in]缓冲区的大小， *lpszText*参数指向。|

### <a name="return-value"></a>返回值

在第一个重载中， [CString](../../atl-mfc-shared/using-cstring.md)对象，其中包含的提示标志文本，如果存在; 否则为`CString`长度为零的对象。

或

在第二个重载中，TRUE，如果此方法成功;否则为 FALSE。

### <a name="remarks"></a>备注

提示文本是组合框控件的输入区域中显示的提示。 用户提供输入才显示提示文本。

此方法将发送[CB_GETCUEBANNER](/windows/desktop/Controls/cb-getcuebanner)消息，Windows SDK 中所述。

##  <a name="getcursel"></a>  CComboBox::GetCurSel

调用此成员函数可确定选择哪一项组合框中。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

一个组合框或 CB_ERR 如果未不选择任何项的列表框中当前选定项的从零开始的索引。

### <a name="remarks"></a>备注

`GetCurSel` 返回列表中的一个索引。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>  CComboBox::GetDroppedControlRect

调用`GetDroppedControlRect`成员函数以检索可见 （删除下） 列表框的下拉组合框的屏幕坐标。

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>参数

*lprect*<br/>
指向[RECT 结构](../../mfc/reference/rect-structure1.md)，是否要接收坐标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>  CComboBox::GetDroppedState

调用`GetDroppedState`成员函数来确定一个下拉组合框列表框是否可见的 （下降）。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>返回值

如果列表框是否可见，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>  CComboBox::GetDroppedWidth

调用此函数可检索的最小允许宽度，以像素为单位的组合框的列表框。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>返回值

如果成功，最小允许宽度，以像素为单位;否则为 CB_ERR。

### <a name="remarks"></a>备注

此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

默认情况下的下拉列表框的最小允许宽度为 0。 可以通过调用设置的最小允许宽度[SetDroppedWidth](#setdroppedwidth)。 显示组合框的列表框部分时，其宽度为较大的最小允许宽度或组合框的宽度。

### <a name="example"></a>示例

  有关示例，请参阅[SetDroppedWidth](#setdroppedwidth)。

##  <a name="geteditsel"></a>  CComboBox::GetEditSel

获取当前选择的组合框编辑控件中的起始和结束字符位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>返回值

一个 32 位值，该值包含高序位字中的选定内容的结尾后的低序位字中的起始位置和未选定的第一个字符的位置。 如果没有一个编辑控件组合框上使用此函数，则返回 CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>  CComboBox::GetExtendedUI

调用`GetExtendedUI`成员函数以确定组合框具有默认用户界面或扩展的用户界面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>返回值

组合框具有扩展的用户界面中; 如果非零值否则为 0。

### <a name="remarks"></a>备注

可以按以下方式标识扩展的用户界面：

- 单击静态控件将显示仅与组合框的列表框[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

- 按向下键显示列表框 （禁用 F4）。

项列表不可见 （箭头键处于禁用状态） 时，静态控件中滚动才被禁用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>  CComboBox::GetHorizontalExtent

从组合框检索以像素为单位的组合框的列表框部分可以进行水平滚动的宽度。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

可滚动列表框部分的组合框，以像素为单位的宽度。

### <a name="remarks"></a>备注

这是仅适用于组合框的列表框部分具有水平滚动条。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>  CComboBox::GetItemData

检索与指定的组合框项关联的应用程序提供 32 位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含组合框的列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

如果发生错误的项或 CB_ERR 与关联的 32 位值。

### <a name="remarks"></a>备注

32 位值可以设置与*dwItemData*的参数[SetItemData](#setitemdata)成员函数调用。 使用`GetItemDataPtr`成员函数要检索的 32 位值是否为指针 (**void** <strong>\*</strong>)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>  CComboBox::GetItemDataPtr

检索与指定的组合框项作为指针关联的应用程序提供 32 位值 (**void** <strong>\*</strong>)。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含组合框的列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

检索一个指针，则为-1，如果发生错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>  CComboBox::GetItemHeight

调用`GetItemHeight`成员函数以检索在组合框的列表项的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定组合框的高度是要检索的组件。 如果*nIndex*参数为-1，就会检索在组合框的编辑控件 （或静态文本） 部分的高度。 如果组合框[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式*nIndex*指定其高度是要检索的列表项的从零开始的索引。 否则为*nIndex*应设置为 0。

### <a name="return-value"></a>返回值

以像素为单位，组合框中指定的项的高度。 如果发生错误，则返回值是 CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>  CComboBox::GetLBText

从组合框的列表框中获取的字符串。

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
包含要复制的列表框中字符串的从零开始的索引。

*lpszText*<br/>
指向将接收字符串的缓冲区。 缓冲区必须有足够的空间的字符串和终止 null 字符。

*rString*<br/>
对 `CString` 的引用。

### <a name="return-value"></a>返回值

不包括终止 null 字符的字符串长度 （以字节为单位）。 如果*nIndex*未指定有效的索引，则返回值是 CB_ERR。

### <a name="remarks"></a>备注

此成员的第二种形式函数填充`CString`具有项的文本对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>  CComboBox::GetLBTextLen

在组合框的列表框中获取字符串的长度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含列表框中字符串的从零开始的索引。

### <a name="return-value"></a>返回值

以字节为单位，不包括终止 null 字符的字符串的长度。 如果*nIndex*未指定有效的索引，则返回值是 CB_ERR。

### <a name="example"></a>示例

  有关示例，请参阅[CComboBox::GetLBText](#getlbtext)。

##  <a name="getlocale"></a>  CComboBox::GetLocale

检索使用组合框的区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

组合框中字符串的区域设置标识符 (LCID) 值。

### <a name="remarks"></a>备注

使用区域设置是，例如，若要确定已排序的组合框中字符串的排序顺序。

### <a name="example"></a>示例

  有关示例，请参阅[CComboBox::SetLocale](#setlocale)。

##  <a name="getminvisible"></a>  CComboBox::GetMinVisible

获取当前组合框控件的下拉列表中可见的项的最小数目。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>返回值

当前的下拉列表中的可见项的最小数量。

### <a name="remarks"></a>备注

此方法将发送[CB_GETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible)消息，Windows SDK 中所述。

##  <a name="gettopindex"></a>  CComboBox::GetTopIndex

检索在组合框的列表框部分中的第一个可见项的从零开始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，该组合框的列表框部分中的第一个可见项的从零开始的索引; 否则为 CB_ERR。

### <a name="remarks"></a>备注

最初，0 项位于顶部的列表框中，但如果滚动列表框中，另一项可能会在顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>  CComboBox::InitStorage

用于存储列表框项的组合框的列表框部分中分配内存。

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

如果成功，最大的组合框的列表框部分可以存储在内存重新分配之前的项很有需要否则为 CB_ERRSPACE，这不意味着足够的内存。

### <a name="remarks"></a>备注

将大量的项添加到列表框部分之前调用此函数`CComboBox`。

仅 Windows 95/98: *wParam*参数最多为 16 位值。 这意味着列表框不能包含超过 32,767 个项。 项的数目受到限制，尽管列表框中的项的总大小仅受可用内存。

此函数可帮助加快有大量的项 (超过 100) 的列表框中的初始化。 预先分配指定的数量的内存以便将后续[AddString](#addstring)， [InsertString](#insertstring)，并[Dir](#dir)函数采用最短的时间。 您可以对参数使用估计值。 如果您要估计得高一些，一些额外的内存分配;如果你低估，进行一般分配用于超过预先分配的量的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>  CComboBox::InsertString

将字符串插入组合框的列表框。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含一个索引（该索引从零开始），该索引指向列表框中将接收字符串的位置。 如果此参数为-1，则字符串被添加到列表的末尾。

*lpszString*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 如果发生错误，则返回值是 CB_ERR。 如果没有足够空间可用于存储新字符串，返回值将为 CB_ERRSPACE。

### <a name="remarks"></a>备注

与不同[AddString](#addstring)成员函数`InsertString`成员函数不会导致与列表[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式进行排序。

> [!NOTE]
>  此函数不受 Windows`ComboBoxEx`控件。 有关此控件的详细信息，请参阅[ComboBoxEx 控件](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>  CComboBox::LimitText

限制用户可以向组合框编辑控件中输入的文本的长度以字节为单位。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>参数

*nMaxChars*<br/>
指定的用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0，文本长度设置为 65,535 字节。

### <a name="return-value"></a>返回值

如果成功，则非零值。 如果调用组合框样式[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或而无需编辑控件组合框，则返回值是 CB_ERR。

### <a name="remarks"></a>备注

如果组合框没有样式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，设置文本限制比在编辑控件的大小要大不起任何作用。

`LimitText` 仅限制用户可以输入的文本。 它不会影响任何文本中已有的编辑控件时发送消息，也不会影响时所选列表框中的字符串复制到编辑控件的文本的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>  CComboBox::MeasureItem

创建所有者绘制样式组合框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lpMeasureItemStruct*<br/>
指向的长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。

### <a name="remarks"></a>备注

默认情况下，此成员函数没有任何影响。 重写此成员函数，并填充`MEASUREITEMSTRUCT`结构以通知 Windows 的维度的列表框在组合框中。 如果使用创建组合框[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，框架将调用此成员函数为每个项的列表框中。 否则，只有一次调用此成员。

使用所有者描述组合框中使用 CBS_OWNERDRAWFIXED 样式创建[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成员函数的`CWnd`需要进一步编程的考虑因素。 请参阅中的讨论[技术注意 14](../../mfc/tn014-custom-controls.md)。

请参阅[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)有关的说明`MEASUREITEMSTRUCT`结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>  CComboBox::Paste

将数据从剪贴板插入到当前光标位置处的组合框编辑控件。

```
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板包含 CF_TEXT 格式的数据插入数据。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>  CComboBox::ResetContent

删除所有项从列表框和编辑组合框控件。

```
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>  CComboBox::SelectString

组合框中，在列表框中的字符串搜索，并找到该字符串，如果在列表框中选择该字符串并将其复制到编辑控件。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nStartAfter*<br/>
包含要搜索的第一项之前的项的从零开始索引。 如果搜索到达列表框的底部，它将继续从列表框的顶部到由指定的项*nStartAfter*。 如果为-1，从开始处搜索整个列表框。

*lpszString*<br/>
指向包含要搜索的前缀的以 null 结尾的字符串。 搜索是区分，因此此字符串可以包含任何组合的大写和小写字母。

### <a name="return-value"></a>返回值

如果已找到该字符串的选定项的从零开始的索引。 如果搜索不成功，则返回值是 CB_ERR 和当前所选内容不会更改。

### <a name="remarks"></a>备注

一个字符串，仅当其初始字符 （从起始点） 与匹配的前缀字符串中的字符选择。

请注意，`SelectString`并`FindString`成员函数查找字符串，但`SelectString`成员函数还将选择字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>  CComboBox::SetCueBanner

设置为一个组合框控件显示的提示文本。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpszText*|[in]指向以 null 结尾的缓冲区，其中包含提示文本。|

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

提示文本是组合框控件的输入区域中显示的提示。 用户提供输入才显示提示文本。

此方法将发送[CB_SETCUEBANNER](/windows/desktop/Controls/cb-setcuebanner)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_combobox*，即用于以编程方式访问组合框控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

下面的代码示例设置提示标志的组合框控件。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>  CComboBox::SetCurSel

在组合框的列表框中选择一个字符串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*请选择*<br/>
指定要选择的字符串的从零开始的索引。 如果为-1，删除任何当前所选内容的列表框中，并清除编辑控件。

### <a name="return-value"></a>返回值

如果消息是成功的选定项的从零开始的索引。 如果，则返回值为 CB_ERR*请选择*大于列表中的项的数目或如果*请选择*设置为-1，这会清除所选内容。

### <a name="remarks"></a>备注

如有必要，列表框将在字符串 （如果列表框是否可见的） 滚动到视图。 组合框编辑控件中的文本更改以反映新的选择。 删除任何之前的选择列表框中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>  CComboBox::SetDroppedWidth

调用此函数可设置的最小允许宽度，以像素为单位的组合框的列表框。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
组合框，以像素为单位的列表框部分的最小允许宽度。

### <a name="return-value"></a>返回值

如果成功，列表框中，否则为 CB_ERR 的新宽度。

### <a name="remarks"></a>备注

此函数仅适用于组合框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

默认情况下的下拉列表框的最小允许宽度为 0。 显示组合框的列表框部分时，其宽度为较大的最小允许宽度或组合框的宽度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>  CComboBox::SetEditSel

选择组合框编辑控件中的字符。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
指定的起始位置。 如果起始位置设置为-1，然后删除任何现有的选择。

*nEndChar*<br/>
指定的结束位置。 如果结束位置到最后一个设置为-1，然后从起始位置的所有文本选择编辑控件中的字符。

### <a name="return-value"></a>返回值

如果成功，则成员函数为非零值否则为 0。 如果是 CB_ERR`CComboBox`已[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式或不具有列表框。

### <a name="remarks"></a>备注

从零开始的位置。 若要选择的编辑控件的第一个字符，则指定起始位置为 0。 若要选择的最后一个字符之后的字符是结束位置。 例如，若要选择的编辑控件的前四个字符，将使用的起始位置为 0 和 4 的结束位置。

> [!NOTE]
>  此函数不受 Windows`ComboBoxEx`控件。 有关此控件的详细信息，请参阅[ComboBoxEx 控件](/windows/desktop/Controls/comboboxex-controls)Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CComboBox::GetEditSel](#geteditsel)。

##  <a name="setextendedui"></a>  CComboBox::SetExtendedUI

调用`SetExtendedUI`成员函数以选择默认用户界面或组合框具有扩展的用户界面[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>参数

*bExtended*<br/>
指定组合框是否应使用扩展的用户界面或默认用户界面。 值为 TRUE 将选择扩展的用户界面中;如果值为 FALSE 选择标准用户界面。

### <a name="return-value"></a>返回值

如果操作成功，CB_OKAY 或 CB_ERR 如果发生错误。

### <a name="remarks"></a>备注

可以按以下方式标识扩展的用户界面：

- 单击静态控件显示仅使用 CBS_DROPDOWNLIST 样式组合框的列表框。

- 按向下键显示列表框 （禁用 F4）。

静态控件中滚动项列表不可见时才被禁用 （禁用箭头键）。

### <a name="example"></a>示例

  有关示例，请参阅[CComboBox::GetExtendedUI](#getextendedui)。

##  <a name="sethorizontalextent"></a>  CComboBox::SetHorizontalExtent

设置以像素为单位，组合框的列表框部分可以进行水平滚动的宽度。

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>参数

*nExtent*<br/>
指定组合框的列表框部分可以进行水平滚动的像素数。

### <a name="remarks"></a>备注

如果列表框的宽度小于此值，水平滚动条将水平滚动列表框中的项。 如果列表框的宽度大于等于或大于此值，则会隐藏水平滚动条或组合框是否[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，已禁用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>  CComboBox::SetItemData

设置与组合框中指定的项关联的 32 位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的项的从零开始索引。

*dwItemData*<br/>
包含要与项关联的新值。

### <a name="return-value"></a>返回值

如果发生错误，CB_ERR。

### <a name="remarks"></a>备注

使用`SetItemDataPtr`成员函数，如果 32 位项，则为指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>  CComboBox::SetItemDataPtr

设置与组合框，为指定的指针中的指定项关联的 32 位值 (**void** <strong>\*</strong>)。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含项的从零开始索引。

*pData*<br/>
包含要与项关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，CB_ERR。

### <a name="remarks"></a>备注

此指针保持有效的组合框中，生命周期，即使添加或删除项时，可能会更改项的组合框中的相对位置。 因此，可以更改框中的项的索引，但指针保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>  CComboBox::SetItemHeight

调用`SetItemHeight`成员函数的组合框或组合框编辑控件 （或静态文本） 部分的高度设置列表项的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定是否设置列表项的高度或组合框的编辑控件 （或静态文本） 部分的高度。

如果组合框[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式*nIndex*指定设置; 否则为其高度的列表项的从零开始索引*nIndex*必须为 0并将设置所有列表项的高度。

如果*nIndex*为-1，在编辑控件的高度或组合框的静态文本部分将进行设置。

*cyItemHeight*<br/>
指定的高度，以像素为单位的标识的组合框组件*nIndex*。

### <a name="return-value"></a>返回值

如果索引或高度无效;，CB_ERR否则为 0。

### <a name="remarks"></a>备注

独立于列表项的高度设置组合框编辑控件 （或静态文本） 部分的高度。 应用程序必须确保编辑控件 （或静态文本） 部分的高度不小于特定的列表框项的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>  CComboBox::SetLocale

设置此组合框的区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*nNewLocale*<br/>
新区域设置标识符 (LCID) 要设置的值的组合框。

### <a name="return-value"></a>返回值

此组合框的上一个区域设置标识符 (LCID) 值。

### <a name="remarks"></a>备注

如果`SetLocale`未调用，默认值从系统获取区域设置。 此系统默认区域设置可以修改通过使用控制面板中的区域 （或国际） 应用程序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>  CComboBox::SetMinVisibleItems

设置可见项的最小数目的当前组合框下拉列表框控件中。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iMinVisible*|[in]指定可见项的最小数目。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[CB_SETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_combobox*，即用于以编程方式访问组合框控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

下面的代码示例将 20 个项插入到组合框控件的下拉列表。 然后，它指定当用户按下的下拉箭头，显示最少 10 个项。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>  CComboBox::SetTopIndex

确保特定项的组合框的列表框部分中可见。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则为零或 CB_ERR 如果发生错误。

### <a name="remarks"></a>备注

系统之前指定的任意一项滚动列表框*nIndex*显示顶部的列表框或最大滚动范围达到了。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>  CComboBox::ShowDropDown

显示或隐藏具有一个组合框的列表框[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>参数

*bShowIt*<br/>
指定是否要显示或隐藏下拉列表框。 TRUE 值显示在列表框。 如果值为 FALSE 将隐藏列表框。

### <a name="remarks"></a>备注

默认情况下，此样式的组合框将显示在列表框。

此成员函数具有与创建一个组合框不会影响[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式。

### <a name="example"></a>示例

  有关示例，请参阅[CComboBox::GetDroppedState](#getdroppedstate)。

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
