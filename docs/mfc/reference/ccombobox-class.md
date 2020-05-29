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
ms.openlocfilehash: dc803fb4ce137b256f4197afaec7bc3327e1e85a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754830"
---
# <a name="ccombobox-class"></a>CComboBox 类

提供 Windows 组合框功能。

## <a name="syntax"></a>语法

```
class CComboBox : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComboBox：CComboBox](#ccombobox)|构造 `CComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|将字符串添加到组合框的列表框中或具有CBS_SORT样式的列表框的排序位置。|
|[CComboBox：清除](#clear)|删除（清除）编辑控件中的当前选择（如果有）。|
|[CComboBox：比较项目](#compareitem)|由框架调用以确定新列表项在排序的所有者绘制组合框中的相对位置。|
|[CComboBox：复制](#copy)|以CF_TEXT格式将当前选择（如果有）复制到剪贴板上。|
|[CComboBox：创建](#create)|创建组合框并将其附加到`CComboBox`对象。|
|[CComboBox：切割](#cut)|删除（剪切）编辑控件中的当前选择（如果有），并将删除的文本以CF_TEXT格式复制到剪贴板。|
|[CComboBox：:Delete项目](#deleteitem)|当从所有者绘制的组合框中删除列表项时，由框架调用。|
|[CComboBox：:DeleteString](#deletestring)|从组合框的列表框中删除字符串。|
|[CComboBox：:Dir](#dir)|将文件名列表添加到组合框的列表框中。|
|[CComboBox：:D原始项目](#drawitem)|当所有者绘制的组合框的可视方面发生更改时，由框架调用。|
|[CComboBox：：查找字符串](#findstring)|在组合框的列表框中查找包含指定前缀的第一个字符串。|
|[CComboBox：：查找字符串精确](#findstringexact)|查找与指定字符串匹配的第一个列表框字符串（在组合框中）。|
|[CComboBox：获取ComboBox信息](#getcomboboxinfo)|检索有关`CComboBox`对象的信息。|
|[CComboBox：获取计数](#getcount)|检索组合框列表框中的项目数。|
|[CComboBox：GetCueBanner](#getcuebanner)|获取为组合框控件显示的提示文本。|
|[CComboBox：获取CurSel](#getcursel)|在组合框的列表框中检索当前选定项（如果有）的索引。|
|[CComboBox：获取已放弃控制](#getdroppedcontrolrect)|检索下拉组合框的可见（下拉）列表框的屏幕坐标。|
|[CComboBox：获取放弃状态](#getdroppedstate)|确定下拉组合框的列表框是否可见（下拉）。|
|[CComboBox：获取删除宽度](#getdroppedwidth)|检索组合框的下拉列表框部分的最小允许宽度。|
|[CComboBox：获取编辑塞尔](#geteditsel)|在组合框的编辑控件中获取当前选择的起始和结束字符位置。|
|[CComboBox：获取扩展 UI](#getextendedui)|确定组合框是否具有默认用户界面或扩展的用户界面。|
|[CComboBox：获取横向范围](#gethorizontalextent)|返回组合框的列表框部分可以水平滚动的宽度。|
|[CComboBox：获取项目数据](#getitemdata)|检索与指定的组合框项关联的应用程序提供的 32 位值。|
|[CComboBox：获取项目数据Ptr](#getitemdataptr)|检索与指定的组合框项关联的应用程序提供的 32 位指针。|
|[CComboBox：获取项目高度](#getitemheight)|检索组合框中列表项的高度。|
|[CComboBox：获取LBText](#getlbtext)|从组合框的列表框中获取字符串。|
|[CComboBox：获取LBTextLen](#getlbtextlen)|获取组合框列表框中字符串的长度。|
|[CComboBox：获取本地化](#getlocale)|检索组合框的区域设置标识符。|
|[CComboBox：获取可见](#getminvisible)|获取当前组合框下拉列表中的最小可见项数。|
|[CComboBox：获取TopIndex](#gettopindex)|返回组合框列表框部分中第一个可见项的索引。|
|[CComboBox：：在内存储](#initstorage)|预分配组合框列表框部分中的项和字符串的内存块。|
|[CComboBox::InsertString](#insertstring)|将字符串插入组合框的列表框。|
|[CComboBox：限制文本](#limittext)|限制用户可以输入到组合框的编辑控件中的文本长度。|
|[CComboBox：测量项目](#measureitem)|由框架调用，以确定创建所有者绘制组合框时组合框尺寸。|
|[CComboBox：:Paste](#paste)|将剪辑板中的数据插入到当前光标位置的编辑控件中。 仅当剪贴板以CF_TEXT格式包含数据时，才会插入数据。|
|[CComboBox：重置内容](#resetcontent)|从列表框中删除所有项目，并编辑组合框控件。|
|[CComboBox：选择字符串](#selectstring)|在组合框的列表框中搜索字符串，如果找到该字符串，则选择列表框中的字符串并将该字符串复制到编辑控件。|
|[CComboBox：：SetCueBanner](#setcuebanner)|设置为组合框控件显示的提示文本。|
|[CComboBox：：SetCurSel](#setcursel)|在组合框的列表框中选择字符串。|
|[CComboBox：：设置丢弃宽度](#setdroppedwidth)|设置组合框的下拉列表框部分的最小允许宽度。|
|[CComboBox：设置编辑塞尔](#seteditsel)|选择组合框的编辑控件中的字符。|
|[CComboBox：：设置扩展UI](#setextendedui)|为具有CBS_DROPDOWN或CBS_DROPDOWNLIST样式的组合框选择默认用户界面或扩展用户界面。|
|[CComboBox：：设置水平范围](#sethorizontalextent)|设置组合框的列表框部分可以水平滚动的像素宽度。|
|[CComboBox：：设置项目数据](#setitemdata)|在组合框中设置与指定项关联的 32 位值。|
|[CComboBox：：设置项目数据Ptr](#setitemdataptr)|在组合框中设置与指定项关联的 32 位指针。|
|[CComboBox：：设置项目高度](#setitemheight)|设置组合框中列表项的高度或组合框的编辑控件（或静态文本）部分的高度。|
|[CComboBox：：设置本地](#setlocale)|设置组合框的区域设置标识符。|
|[CComboBox：设置明目数项目](#setminvisibleitems)|设置当前组合框下拉列表中的最小可见项数。|
|[CComboBox：：SetTopIndex](#settopindex)|告诉组合框的列表框部分以显示顶部具有指定索引的项。|
|[CComboBox：：显示下拉](#showdropdown)|显示或隐藏具有CBS_DROPDOWN或CBS_DROPDOWNLIST样式的组合框的列表框。|

## <a name="remarks"></a>备注

组合框由列表框与静态控件或编辑控件结合而成。 控件的列表框部分可能随时显示，也可能仅在用户选择控件旁边的下拉箭头时下拉。

列表框中当前选定的项目（如果有）显示在静态控件或编辑控件中。 此外，如果组合框具有下拉列表样式，用户可以键入列表中某一项的初始字符，如果显示列表框将突出显示具有该初始字符的下一个项目。

下表比较了三种组合框[样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|样式|何时是列表框可见|静态或编辑控件|
|-----------|-------------------------------|-----------------------------|
|简单|始终|编辑|
|Drop-down|下落时|编辑|
|下拉列表|下落时|静态|

可以从对话框模板或`CComboBox`直接在代码中创建对象。 在这两种情况下，首先调用构造函数`CComboBox`来构造`CComboBox`对象;否则，请先调用构造函数来构造该对象。然后调用[Create](#create)成员函数以创建控件并将其附加到`CComboBox`对象。

如果要处理组合框发送到其父级的 Windows 通知消息（通常是派生自`CDialog`的类），则会为每个邮件向父类添加消息映射条目和消息处理程序成员函数。

每个消息映射条目采用以下形式：

**打开\_**_通知_**（ID** _id_，_成员Fxn_ **）**

其中`id`指定发送通知的组合框控件的子窗口 ID，以及`memberFxn`您为处理通知而编写的父成员函数的名称。

父函数原型如下所示：

**afx_msg** `void` afx_msg `memberFxn` **（ ）;**

无法预测发送某些通知的顺序。 特别是，CBN_SELCHANGE通知可能发生在通知CBN_CLOSEUP之前或之后。

潜在的消息映射条目如下：

- ON_CBN_CLOSEUP（Windows 3.1 及更高版本）。组合框的列表框已关闭。 对于具有[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框，不会发送此通知消息。

- ON_CBN_DBLCLK 用户双击组合框列表框中的字符串。 此通知消息仅为具有CBS_SIMPLE样式的组合框发送。 对于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框，无法双击，因为单击将隐藏列表框。

- ON_CBN_DROPDOWN 组合框的列表框即将下拉（可见）。 此通知消息只能针对具有CBS_DROPDOWN或CBS_DROPDOWNLIST风格的组合框。

- ON_CBN_EDITCHANGE用户已执行的操作可能更改了组合框的编辑控制部分中的文本。 与CBN_EDITUPDATE消息不同，此消息是在 Windows 更新屏幕后发送的。 如果组合框具有CBS_DROPDOWNLIST样式，则不发送该组合框。

- ON_CBN_EDITUPDATE 组合框的编辑控制部分即将显示更改的文本。 此通知消息在控件格式化文本后发送，但在显示文本之前发送。 如果组合框具有CBS_DROPDOWNLIST样式，则不发送该组合框。

- ON_CBN_ERRSPACE 组合框无法分配足够的内存以满足特定请求。

- ON_CBN_SELENDCANCEL（Windows 3.1 及更高版本）。指示应取消用户的选择。 用户单击某个项目，然后单击另一个窗口或控件以隐藏组合框的列表框。 此通知消息在CBN_CLOSEUP通知消息之前发送，以指示应忽略用户的选择。 即使未发送CBN_CLOSEUP通知消息（例如，具有CBS_SIMPLE样式的组合框），也会发送CBN_SELENDCANCEL或CBN_SELENDOK通知消息。

- ON_CBN_SELENDOK 用户选择项目，然后按 ENTER 键或单击向下箭头键以隐藏组合框的列表框。 此通知消息在CBN_CLOSEUP消息之前发送，以指示用户的选择应被视为有效。 即使未发送CBN_CLOSEUP通知消息（例如，具有CBS_SIMPLE样式的组合框），也会发送CBN_SELENDCANCEL或CBN_SELENDOK通知消息。

- ON_CBN_KILLFOCUS组合框正在失去输入焦点。

- ON_CBN_SELCHANGE 组合框的列表框中的选择将因用户单击列表框或使用箭头键更改所选内容而更改。 处理此消息时，只能通过`GetLBText`或其他类似函数检索组合框的编辑控件中的文本。 `GetWindowText`无法使用。

- ON_CBN_SETFOCUS组合框接收输入焦点。

如果在对话框中创建`CComboBox`对象（通过对话框资源），则当用户关闭对话框时，`CComboBox`该对象将自动销毁。

如果将对象嵌入到另`CComboBox`一个窗口对象中，则无需销毁它。 如果在堆栈上`CComboBox`创建对象，则会自动销毁该对象。 如果使用新函数在`CComboBox`堆上创建对象，则必须调用**new**对象**上的 delete**以在销毁 Windows 组合框时销毁该对象。

**注意**如果要处理WM_KEYDOWN和WM_CHAR消息，必须对组合框的编辑和列表框控件进行子类，从 派生`CEdit`类派生类，`CListBox`并将这些消息的处理程序添加到派生类。 有关详细信息，请参阅[CWnd：：子类窗口](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox：：添加String

将字符串添加到组合框的列表框中。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
指向要添加的 null 终止字符串。

### <a name="return-value"></a>返回值

如果返回值大于或等于 0，则它是列表框中字符串的零基索引。 如果发生错误，返回值CB_ERR;如果没有足够的空间来存储新字符串，则返回值CB_ERRSPACE。

### <a name="remarks"></a>备注

如果未使用[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建列表框，则字符串将添加到列表的末尾。 否则，字符串将插入到列表中，并排序列表。

> [!NOTE]
> Windows`ComboBoxEx`控件不支持此功能。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

若要将字符串插入到列表中的特定位置，请使用[InsertString](#insertstring)成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox：CComboBox

构造 `CComboBox` 对象。

```
CComboBox();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox：清除

删除（清除）组合框的编辑控件中的当前选择（如果有）。

```cpp
void Clear();
```

### <a name="remarks"></a>备注

要删除当前选择并将已删除的内容放在剪贴板上，请使用["剪切](#cut)"成员功能。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox：比较项目

由框架调用以确定新项目在排序的所有者绘制组合框的列表框部分的相对位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>参数

*lp比较项目结构*<br/>
指向[比较结构](/windows/win32/api/winuser/ns-winuser-compareitemstruct)的长指针。

### <a name="return-value"></a>返回值

指示结构中描述的两个项目的相对`COMPAREITEMSTRUCT`位置。 可以是以下任一值：

|“值”|含义|
|-----------|-------------|
|- 1|项目 1 在项目 2 之前排序。|
|0|项目 1 和项目 2 排序相同。|
|1|项目 1 在项目 2 之后排序。|

有关 的说明，请参阅[CWnd：OnCompare 项目](../../mfc/reference/cwnd-class.md#oncompareitem)`COMPAREITEMSTRUCT`。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 如果创建具有LBS_SORT样式的所有者绘制组合框，则必须重写此成员函数，以帮助框架对添加到列表框的新项进行排序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox：复制

以CF_TEXT格式将组合框的编辑控件中的当前选择（如果有）复制到剪贴板。

```cpp
void Copy();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox：创建

创建组合框并将其附加到`CComboBox`对象。

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

*矩形*<br/>
指向组合框的位置和大小。 可以是[RECT 结构](/windows/win32/api/windef/ns-windef-rect)或`CRect`对象。

*pparentwnd*<br/>
指定组合框的父窗口（通常为 。 `CDialog` 值不得为 NULL。

*nID*<br/>
指定组合框的控制 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两步`CComboBox`构造对象。 首先，调用构造函数，然后调用`Create`，这将创建 Windows 组合框并将其附加到`CComboBox`对象。

执行`Create`时，Windows 会将[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息发送到组合框。 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)

默认情况下，这些消息`CWnd`由基类中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数处理。 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate) [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) 要扩展默认消息处理，从`CComboBox`派生类，向新类添加消息映射，并重写前面的消息处理程序成员函数。 例如`OnCreate`，重写以执行新类所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于组合框控件。 :

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL 添加组合框中列表框的垂直滚动

- WS_HSCROLL 添加组合框中列表框的水平滚动

- WS_GROUP组控件

- WS_TABSTOP要将组合框包括在制表顺序中

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox：切割

删除（剪切）组合框编辑控件中的当前选择（如果有），以CF_TEXT格式将删除的文本复制到剪贴板中。

```cpp
void Cut();
```

### <a name="remarks"></a>备注

要删除当前选择而不将删除的文本放在剪贴板上，请调用["清除](#clear)"成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox：:Delete项目

当用户从所有者绘制`CComboBox`对象中删除项目或销毁组合框时，由框架调用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>参数

*lp 删除项目已删除*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)结构的长指针，其中包含有关已删除项的信息。 有关此结构的说明，请参阅[CWnd：onDeleteItem。](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 根据需要重写此函数以重绘组合框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox：:DeleteString

从组合框中删除位置*nIndex*中的项目。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要删除的字符串的索引。

### <a name="return-value"></a>返回值

如果返回值大于或等于 0，则它是列表中剩余字符串的计数。 如果*nIndex*指定的索引大于列表中的项数，则返回值CB_ERR。

### <a name="remarks"></a>备注

*nIndex*之后的所有项目现在向下移动一个位置。 例如，如果组合框包含两个项目，删除第一个项将导致其余项现在处于第一个位置。 *nIndex*#0 表示第一个位置中的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox：:Dir

将文件名或驱动器的列表添加到组合框的列表框中。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>参数

*attr*<br/>
可以是 CFile 中描述的**枚举**值的任意组合[：获取状态](../../mfc/reference/cfile-class.md#getstatus)或以下值的任意组合：

- DDL_READWRITE 文件可以从读取或写入。

- DDL_READONLY 文件可以从读取，但不能写入。

- DDL_HIDDEN文件是隐藏的，并且不会显示在目录列表中。

- DDL_SYSTEM 文件是一个系统文件。

- DDL_DIRECTORY *lpszWildCard*指定的名称指定一个目录。

- DDL_ARCHIVE文件已存档。

- DDL_DRIVES 包括与*lpszWildCard*指定的名称匹配的所有驱动器。

- DDL_EXCLUSIVE专用标志。 如果设置了独占标志，则仅列出指定类型的文件。 否则，除了"正常"文件外，还列出指定类型的文件。

*lpsz通配符*<br/>
指向文件规范字符串。 字符串可以包含通配符（例如 ，*.\*

### <a name="return-value"></a>返回值

如果返回值大于或等于 0，则它是添加到列表中的姓氏的零基索引。 如果发生错误，返回值CB_ERR;如果没有足够的空间来存储新字符串，则返回值CB_ERRSPACE。

### <a name="remarks"></a>备注

Windows`ComboBoxEx`控件不支持此功能。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox：:D原始项目

当所有者绘制组合框的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。 有关此结构的说明，请参阅[CWnd：onDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者绘制对象的绘图`CComboBox`。 在此成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox：：查找字符串

查找但不选择在组合框的列表框中包含指定前缀的第一个字符串。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>参数

*n 开始后*<br/>
包含要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nStartAfter*指定的项。 如果为 -1，则从一开始就搜索整个列表框。

*lpszString*<br/>
指向包含要搜索的前缀的 null 终止字符串。 搜索是独立于大小写，因此此字符串可以包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

如果返回值大于或等于 0，则它是匹配项的零基索引。 如果搜索不成功，则CB_ERR。

### <a name="remarks"></a>备注

Windows`ComboBoxEx`控件不支持此功能。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox：：查找字符串精确

调用`FindStringExact`成员函数查找与*lpszFind*中指定的字符串匹配的第一个列表框字符串（在组合框中）。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>参数

*nIndex 开始*<br/>
指定要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nIndexStart*指定的项。 如果*nIndexStart*为 -1，则从一开始就搜索整个列表框。

*lpszFind*<br/>
指向要搜索的 null 终止字符串。 此字符串可以包含完整的文件名，包括扩展名。 搜索不区分大小写，因此此字符串可以包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

匹配项的零基索引，如果搜索不成功，CB_ERR。

### <a name="remarks"></a>备注

如果组合框创建具有所有者绘制样式，但没有[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，`FindStringExact`则尝试将双字值与*lpszFind*的值匹配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox：获取ComboBox信息

检索`CComboBox`对象的信息。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>参数

*多吉*<br/>
指向[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo)结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟[CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo)消息的功能，如 Windows SDK 中所述。

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox：获取计数

调用此成员函数以检索组合框列表框部分中的项目数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

项数。 返回的计数大于最后一个项的索引值（索引为零）。 如果发生错误，CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox：GetCueBanner

获取为组合框控件显示的提示文本。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpszText*|[出]指向接收提示横幅文本的缓冲区的指针。|
|*cchText*|[在]*lpszText*参数指向的缓冲区的大小。|

### <a name="return-value"></a>返回值

在第一个重载中，包含提示横幅文本的[CString](../../atl-mfc-shared/using-cstring.md)对象（如果存在）;否则，长度`CString`为零的对象。

-或-

在第二个重载中，如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

提示文本是显示在组合框控件的输入区域中的提示。 提示文本显示，直到用户提供输入。

此方法发送[CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner)消息，这在 Windows SDK 中介绍。

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox：获取CurSel

调用此成员函数以确定选择了组合框中的哪个项。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

组合框列表框中当前选定项的零索引，如果未选择任何项，则CB_ERR。

### <a name="remarks"></a>备注

`GetCurSel`将索引返回到列表中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox：获取已放弃控制

调用`GetDroppedControlRect`成员函数以检索下拉组合框的可见（下拉）列表框的屏幕坐标。

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>参数

*lprect*<br/>
指向接收坐标的[RECT 结构](/windows/win32/api/windef/ns-windef-rect)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox：获取放弃状态

调用`GetDroppedState`成员函数以确定下拉组合框的列表框是否可见（下拉）。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>返回值

如果列表框可见，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox：获取删除宽度

调用此函数以检索组合框列表框的最小允许宽度（以像素为单位）。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>返回值

如果成功，最小允许宽度（以像素为单位）;否则，CB_ERR。

### <a name="remarks"></a>备注

此功能仅适用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框。

默认情况下，下拉列表框的最小允许宽度为 0。 最小允许宽度可以通过调用[SetDroppedWidth](#setdroppedwidth)来设置。 显示组合框的列表框部分时，其宽度是最小允许宽度或组合框宽度的较大部分。

### <a name="example"></a>示例

  请参阅["设置放弃宽度"](#setdroppedwidth)的示例。

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox：获取编辑塞尔

在组合框的编辑控件中获取当前选择的起始和结束字符位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>返回值

包含低阶单词中的起始位置和高阶单词中所选内容结束后第一个未选择字符的位置的 32 位值。 如果在没有编辑控件的组合框中使用此函数，则返回CB_ERR。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox：获取扩展 UI

调用`GetExtendedUI`成员函数以确定组合框是否具有默认用户界面或扩展的用户界面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>返回值

如果组合框具有扩展的用户界面，则非零;否则 0。

### <a name="remarks"></a>备注

扩展的用户界面可通过以下方式进行标识：

- 单击静态控件仅显示具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框的列表框。

- 按下"向下箭头"键将显示列表框（已禁用 F4）。

当项目列表不可见时，将禁用静态控件中的滚动（禁用箭头键）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox：获取横向范围

从组合框检索可水平滚动组合框列表框部分的宽度（以像素为单位）。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>返回值

组合框列表框部分的可滚动宽度（以像素为单位）。

### <a name="remarks"></a>备注

仅当组合框的列表框部分具有水平滚动条时，才适用此选项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox：获取项目数据

检索与指定的组合框项关联的应用程序提供的 32 位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在组合框的列表框中包含项的零基索引。

### <a name="return-value"></a>返回值

与项关联的 32 位值，如果发生错误，CB_ERR。

### <a name="remarks"></a>备注

32 位值可以使用[SetItemData](#setitemdata)成员函数调用的*dwItemData*参数进行设置。 如果要检索`GetItemDataPtr`的 32 位值是指针 **（void），**<strong>\*</strong>请使用成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox：获取项目数据Ptr

检索与指定组合框项关联的应用程序提供的 32 位值作为指针（**空**<strong>\*</strong>）。

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在组合框的列表框中包含项的零基索引。

### <a name="return-value"></a>返回值

如果发生错误，则检索指针，或 -1。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox：获取项目高度

调用`GetItemHeight`成员函数以检索组合框中列表项的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要检索其高度的组合框的组件。 如果*nIndex*参数为 -1，则检索组合框的编辑控制（或静态文本）部分的高度。 如果组合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式 *，nIndex*指定要检索其高度的列表项的零基索引。 否则 *，nIndex*应设置为 0。

### <a name="return-value"></a>返回值

组合框中指定项目的高度（以像素为单位）。 返回值是 CB_ERR 如果发生错误。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox：获取LBText

从组合框的列表框中获取字符串。

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
包含要复制的列表框字符串的零基索引。

*lpszText*<br/>
指向要接收字符串的缓冲区。 缓冲区必须有足够的空间用于字符串和终止空字符。

*rString*<br/>
对 `CString` 的引用。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止空字符。 如果*nIndex*未指定有效的索引，则返回值将CB_ERR。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用项的文本填充`CString`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox：获取LBTextLen

获取组合框列表框中字符串的长度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含列表框字符串的零基索引。

### <a name="return-value"></a>返回值

字符串的长度（以字节为单位），不包括终止空字符。 如果*nIndex*未指定有效的索引，则返回值将CB_ERR。

### <a name="example"></a>示例

  请参阅[CComboBox 的示例：获取LBText](#getlbtext)。

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox：获取本地化

检索组合框使用区域设置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>返回值

组合框中字符串区域设置标识符 （LCID） 值。

### <a name="remarks"></a>备注

例如，区域设置用于确定排序组合框中字符串的排序顺序。

### <a name="example"></a>示例

  请参阅[CComboBox 的示例：：设置区域设置](#setlocale)。

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox：获取可见

获取当前组合框控件的下拉列表中的最小可见项数。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>返回值

当前下拉列表中的可见项的最小数量。

### <a name="remarks"></a>备注

此方法发送[CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)消息，这在 Windows SDK 中介绍。

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox：获取TopIndex

检索组合框列表框部分中第一个可见项的零基索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>返回值

如果成功，组合框列表框部分中第一个可见项的零基索引（如果成功）CB_ERR否则。

### <a name="remarks"></a>备注

最初，项目 0 位于列表框的顶部，但如果滚动列表框，则另一项可能位于顶部。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox：：在内存储

分配内存以将列表框项存储在组合框的列表框部分。

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

如果成功，则组合框的列表框部分在需要重新分配内存之前可以存储的最大项数，否则CB_ERRSPACE，这意味着内存不足。

### <a name="remarks"></a>备注

在将大量项添加到 的清单框部分之前，请调用此函数`CComboBox`。

仅限 Windows 95/98：wParam 参数限制为 16 位值。 *wParam* 这意味着列表框不能包含超过 32，767 个项目。 尽管项目数受到限制，但列表框中项目的总大小仅受可用内存的限制。

此功能有助于加快初始化具有大量项（超过 100 个）的列表框。 它预分配指定的内存量，以便后续[的 AddString、InsertString](#addstring)和[Dir](#dir)函数花费尽可能短的时间。 [InsertString](#insertstring) 您可以使用参数的估计值。 如果高估，将分配一些额外的内存;如果估计过高，则分配一些额外的内存。如果低估，则正常分配用于超过预分配金额的物料。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox：插入字符串

将字符串插入组合框的列表框。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含一个索引（该索引从零开始），该索引指向列表框中将接收字符串的位置。 如果此参数为 -1，则字符串将添加到列表的末尾。

*lpszString*<br/>
指向要插入的以 null 结尾的字符串。

### <a name="return-value"></a>返回值

插入该字符串的位置的索引（索引从零开始）。 返回值是 CB_ERR 如果发生错误。 如果没有足够空间可用于存储新的字符串，则返回值为 CB_ERRSPACE。

### <a name="remarks"></a>备注

与 [AddString](#addstring) 成员函数不同， `InsertString` 成员函数不会导致对一个列表的 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 样式进行排序。

> [!NOTE]
> Windows`ComboBoxEx`控件不支持此功能。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox：限制文本

限制用户可以输入到组合框的编辑控件中的文本长度（ 以字节为单位）。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>参数

*nMaxChars*<br/>
指定用户可以输入的文本的长度（以字节为单位）。 如果此参数为 0，则文本长度设置为 65，535 字节。

### <a name="return-value"></a>返回值

如果成功，则为非零。 如果调用具有样式[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)组合框或没有编辑控件的组合框，则返回值CB_ERR。

### <a name="remarks"></a>备注

如果组合框没有[样式CBS_AUTOHSCROLL，](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)则将文本限制设置为大于编辑控件的大小将不起作用。

`LimitText`仅限制用户可以输入的文本。 它在发送邮件时对编辑控件中已有的任何文本没有影响，也不会影响在选择列表框中的字符串时复制到编辑控件的文本的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox：测量项目

创建具有所有者绘制样式的组合框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lp 测量项目结构*<br/>
指向[测量结构](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的长指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 覆盖此成员函数并填充`MEASUREITEMSTRUCT`结构，以通知 Windows 组合框中列表框的尺寸。 如果组合框使用[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建，则框架将针对列表框中的每个项目调用此成员函数。 否则，仅调用此成员一次。

使用与[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成员函数创建的所有者绘制组合框中的CBS_OWNERDRAWFIXED样式`CWnd`涉及进一步的编程注意事项。 请参阅[技术说明 14](../../mfc/tn014-custom-controls.md)中的讨论。

有关`MEASUREITEMSTRUCT`结构的说明，请参阅[CWnd：onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox：:Paste

将剪贴板中的数据插入到当前光标位置组合框的编辑控件中。

```cpp
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板以CF_TEXT格式包含数据时，才会插入数据。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox：重置内容

从列表框中删除所有项目，并编辑组合框控件。

```cpp
void ResetContent();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox：选择字符串

在组合框的列表框中搜索字符串，如果找到该字符串，则选择列表框中的字符串并将其复制到编辑控件。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*n 开始后*<br/>
包含要搜索的第一个项之前项的零基索引。 当搜索到达列表框的底部时，它将从列表框的顶部继续到*nStartAfter*指定的项。 如果为 -1，则从一开始就搜索整个列表框。

*lpszString*<br/>
指向包含要搜索的前缀的 null 终止字符串。 搜索是独立于大小写，因此此字符串可以包含大写字母和小写字母的任意组合。

### <a name="return-value"></a>返回值

如果找到字符串，则所选项的零基索引。 如果搜索不成功，则返回值CB_ERR，并且当前选择不会更改。

### <a name="remarks"></a>备注

仅当字符串的初始字符（从起始点）与前缀字符串中的字符匹配时，才会选择字符串。

请注意，`SelectString`和`FindString`成员函数都找到字符串，`SelectString`但成员函数也选择字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox：：SetCueBanner

设置为组合框控件显示的提示文本。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpszText*|[在]指向包含提示文本的 null 端接缓冲区的指针。|

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

提示文本是显示在组合框控件的输入区域中的提示。 提示文本显示，直到用户提供输入。

此方法发送[CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问组合框控件的变量*m_combobox*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

以下代码示例设置组合框控件的提示横幅。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox：：SetCurSel

在组合框的列表框中选择字符串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>参数

*n选择*<br/>
指定要选择的字符串的零基索引。 如果 -1，则删除列表框中的任何当前选择并清除编辑控件。

### <a name="return-value"></a>返回值

如果消息成功，则选择的项的零基索引。 如果*nSelect*大于列表中的项数，或者*nSelect*设置为 -1（清除所选内容），则返回值为 CB_ERR。

### <a name="remarks"></a>备注

如有必要，列表框将字符串滚动到视图中（如果列表框可见）。 组合框的编辑控件中的文本将更改为反映新选择。 删除列表框中的任何以前的选择。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox：：设置丢弃宽度

调用此函数可设置组合框列表框的最小允许宽度（以像素为单位）。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
组合框列表框部分的最小允许宽度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则列表框的新宽度，否则CB_ERR。

### <a name="remarks"></a>备注

此功能仅适用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框。

默认情况下，下拉列表框的最小允许宽度为 0。 显示组合框的列表框部分时，其宽度是最小允许宽度或组合框宽度的较大部分。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox：设置编辑塞尔

选择组合框的编辑控件中的字符。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
指定起始位置。 如果起始位置设置为 -1，则删除任何现有选择。

*nEndChar*<br/>
指定结束位置。 如果结束位置设置为 -1，则选择从起始位置到编辑控件中最后一个字符的所有文本。

### <a name="return-value"></a>返回值

如果成员函数成功，则非零;否则 0。 如果`CComboBox`[CBS_DROPDOWNLIST样式或](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)没有列表框，则CB_ERR。

### <a name="remarks"></a>备注

仓位为零。 要选择编辑控件的第一个字符，请指定起始位置为 0。 结束位置是在最后一个字符之后。 例如，要选择编辑控件的前四个字符，请使用起始位置 0 和结束位置 4。

> [!NOTE]
> Windows`ComboBoxEx`控件不支持此功能。 有关此控件的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>示例

  请参阅[CComboBox 的示例：：获取编辑塞尔](#geteditsel)。

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox：：设置扩展UI

调用`SetExtendedUI`成员函数，为具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框选择默认用户界面或扩展用户界面。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>参数

*b 扩展*<br/>
指定组合框应使用扩展的用户界面还是默认用户界面。 TRUE 的值选择扩展的用户界面;FALSE 的值选择标准用户界面。

### <a name="return-value"></a>返回值

如果操作成功，CB_OKAY，如果发生错误，则CB_ERR。

### <a name="remarks"></a>备注

扩展的用户界面可通过以下方式进行标识：

- 单击静态控件仅显示具有CBS_DROPDOWNLIST样式的组合框的列表框。

- 按下"向下箭头"键将显示列表框（已禁用 F4）。

当项目列表不可见（箭头键被禁用）时，将禁用静态控件中的滚动。

### <a name="example"></a>示例

  请参阅[CComboBox 的示例：获取扩展 UI](#getextendedui)。

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox：：设置水平范围

设置以像素为单位的宽度，通过该宽度可以水平滚动组合框的列表框部分。

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>参数

*n 范围*<br/>
指定可以水平滚动组合框的列表框部分的像素数。

### <a name="remarks"></a>备注

如果列表框的宽度小于此值，则水平滚动条将水平滚动列表框中的项目。 如果列表框的宽度等于或大于此值，则水平滚动条将隐藏，或者如果组合框具有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则禁用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox：：设置项目数据

在组合框中设置与指定项关联的 32 位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含要设置的项的零基索引。

*dwItemData*<br/>
包含要与项关联的新值。

### <a name="return-value"></a>返回值

如果发生错误，CB_ERR。

### <a name="remarks"></a>备注

如果`SetItemDataPtr`32 位项为指针，请使用成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox：：设置项目数据Ptr

将组合框中与指定项关联的 32 位值设置为指定的指针 **（void）。** <strong>\*</strong>

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含项的零索引。

*pData*<br/>
包含要与项关联的指针。

### <a name="return-value"></a>返回值

如果发生错误，CB_ERR。

### <a name="remarks"></a>备注

此指针在组合框的生命周期内仍然有效，即使项目在组合框中的相对位置可能会随着项目添加或删除而改变。 因此，框中的项索引可以更改，但指针保持可靠。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox：：设置项目高度

调用`SetItemHeight`成员函数以设置组合框中列表项的高度或组合框的编辑控制（或静态文本）部分的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定是设置列表项的高度还是组合框的编辑控制（或静态文本）部分的高度。

如果组合框具有CBS_OWNERDRAWVARIABLE样式 *，nIndex*指定要设置其高度的列表项的零基索引;如果组合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式，则指定要设置其高度的列表项的零基索引。否则 *，nIndex*必须为 0，并将设置所有列表项的高度。

如果*nIndex*为 -1，则要设置组合框的编辑控制或静态文本部分的高度。

*cyItemHeight*<br/>
指定*nIndex*标识的组合框组件的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果索引或高度无效，CB_ERR;否则 0。

### <a name="remarks"></a>备注

组合框的编辑控制（或静态文本）部分的高度设置独立于列表项的高度。 应用程序必须确保编辑控件（或静态文本）部分的高度不小于特定列表框项的高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox：：设置本地

设置此组合框的区域设置标识符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>参数

*n 新地*<br/>
要为组合框设置的新区域设置标识符 （LCID） 值。

### <a name="return-value"></a>返回值

此组合框的上一个区域设置标识符 （LCID） 值。

### <a name="remarks"></a>备注

如果未`SetLocale`调用，则从系统获取默认区域设置。 此系统默认区域设置可以使用控制面板的区域（或国际）应用程序进行修改。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox：设置明目数项目

设置当前组合框控件的下拉列表中的最小可见项数。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iMin可见*|[在]指定可见项的最小数量。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问组合框控件的变量*m_combobox*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>示例

以下代码示例将 20 个项目插入到组合框控件的下拉列表中。 然后，它指定当用户按下下拉箭头时，至少显示 10 个项目。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox：：SetTopIndex

确保特定项目在组合框的列表框部分中可见。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定列表框项的零基索引。

### <a name="return-value"></a>返回值

如果成功，则为零，如果发生错误，则CB_ERR。

### <a name="remarks"></a>备注

系统滚动列表框，直到*nIndex*指定的项显示在列表框的顶部或已达到最大滚动范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox：：显示下拉

显示或隐藏具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式的组合框的列表框。

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>参数

*b显示它*<br/>
指定下拉列表框是显示还是隐藏。 "TRUE"值显示列表框。 FALSE 的值将隐藏列表框。

### <a name="remarks"></a>备注

默认情况下，此样式的组合框将显示列表框。

此成员函数对使用[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)样式创建的组合框没有影响。

### <a name="example"></a>示例

  请参阅[CComboBox 的示例：获取放弃状态](#getdroppedstate)。

## <a name="see-also"></a>请参阅

[MFC 样品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
