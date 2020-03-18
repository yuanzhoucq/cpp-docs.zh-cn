---
title: CComboBoxEx 类
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425987"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx 类

通过为图像列表提供支持扩展组合框控件。

## <a name="syntax"></a>语法

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComboBoxEx：： CComboBoxEx](#ccomboboxex)|构造 `CComboBoxEx` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComboBoxEx：： Create](#create)|创建组合框并将其附加到 `CComboBoxEx` 对象上。|
|[CComboBoxEx：： CreateEx](#createex)|创建具有指定的 Windows 扩展样式的组合框，并将其附加到 `ComboBoxEx` 的对象。|
|[CComboBoxEx：:D eleteItem](#deleteitem)|删除 `ComboBoxEx` 控件中的项。|
|[CComboBoxEx：： GetComboBoxCtrl](#getcomboboxctrl)|检索指向子组合框控件的指针。|
|[CComboBoxEx：： GetEditCtrl](#geteditctrl)|检索 `ComboBoxEx` 控件的编辑控件部分的句柄。|
|[CComboBoxEx：： GetExtendedStyle](#getextendedstyle)|检索用于 `ComboBoxEx` 控件的扩展样式。|
|[CComboBoxEx：： GetImageList](#getimagelist)|检索指向分配给 `ComboBoxEx` 控件的图像列表的指针。|
|[CComboBoxEx：： GetItem](#getitem)|检索给定 `ComboBoxEx` 项的项信息。|
|[CComboBoxEx：： HasEditChanged](#haseditchanged)|确定用户是否已通过键入更改了 `ComboBoxEx` 编辑控件的内容。|
|[CComboBoxEx：： InsertItem](#insertitem)|在 `ComboBoxEx` 控件中插入新项。|
|[CComboBoxEx：： SetExtendedStyle](#setextendedstyle)|在 `ComboBoxEx` 控件内设置扩展样式。|
|[CComboBoxEx：： SetImageList](#setimagelist)|设置 `ComboBoxEx` 控件的图像列表。|
|[CComboBoxEx：： SetItem](#setitem)|设置 `ComboBoxEx` 控件中的项的特性。|
|[CComboBoxEx：： SetWindowTheme](#setwindowtheme)|设置扩展组合框控件的视觉样式。|

## <a name="remarks"></a>备注

使用 `CComboBoxEx` 创建组合框控件后，不再需要实现自己的图像绘制代码。 相反，请使用 `CComboBoxEx` 从图像列表中访问图像。

## <a name="image-list-support"></a>映像列表支持

在标准组合框中，组合框的所有者负责通过创建组合框作为所有者描述控件来绘制图像。 使用 `CComboBoxEx`时，无需将绘图样式设置 CBS_OWNERDRAWFIXED 和 CBS_HASSTRINGS，因为它们是隐含的。 否则，你必须编写代码来执行绘制操作。 `CComboBoxEx` 控件每个项最多支持三个图像：一个用于选定状态，一个用于未选定状态，另一个用于覆盖图像。

## <a name="styles"></a>样式

`CComboBoxEx` 支持 CBS_SIMPLE、CBS_DROPDOWN、CBS_DROPDOWNLIST 和 WS_CHILD 样式。 在您创建窗口时传递的所有其他样式将被控件忽略。 创建窗口后，可以通过调用 `CComboBoxEx` 成员函数[SetExtendedStyle](#setextendedstyle)来提供其他组合框样式。 利用这些样式，您可以：

- 在列表中将字符串搜索设置为区分大小写。

- 创建一个组合框控件，该控件使用斜杠（"/"）、反斜杠（"\\"）和句点（"."）字符作为单词分隔符。 这允许用户使用键盘快捷方式 CTRL + 箭头在 word 之间跳转。

- 将组合框控件设置为显示或不显示图像。 如果未显示任何图像，则组合框可以删除容纳图像的文本缩进。

- 创建一个窄的组合框控件，其中包括调整其大小，使其剪辑包含的更大组合框。

[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)中进一步介绍了这些样式标志。

## <a name="item-retention-and-callback-item-attributes"></a>项保留项和回叫项特性

项信息（例如项和图像的索引、缩进值和文本字符串）存储在 Win32 结构[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)中，如 Windows SDK 中所述。 该结构还包含与回调标志对应的成员。

有关详细的概念讨论，请参阅[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="ccomboboxex"></a>CComboBoxEx：： CComboBoxEx

调用此成员函数以创建 `CComboBoxEx` 对象。

```
CComboBoxEx();
```

##  <a name="create"></a>CComboBoxEx：： Create

创建组合框并将其附加到 `CComboBoxEx` 对象上。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwStyle*<br/>
指定应用于组合框的组合框样式的组合。 有关样式的详细信息，请参阅下面的**备注**。

*rect*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，它是组合框的位置和大小。

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是组合框的父窗口（通常为 `CDialog`）。 值不得为 NULL。

*nID*<br/>
指定组合框的控件 ID。

### <a name="return-value"></a>返回值

如果成功创建对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

通过两个步骤创建一个 `CComboBoxEx` 对象：

1. 调用[CComboBoxEx](#ccomboboxex)构造 `CComboBoxEx` 的对象。

1. 调用此成员函数，该函数将创建扩展的 Windows 组合框并将其附加到 `CComboBoxEx` 对象上。

调用 `Create`时，MFC 将初始化公共控件。

创建组合框时，可以指定以下任意或所有组合框样式：

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

创建窗口时传递的所有其他样式都将被忽略。 `ComboBoxEx` 控件还支持提供附加功能的扩展样式。 Windows SDK 中的[ComboBoxEx 控件扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)中介绍了这些样式。 通过调用[SetExtendedStyle](#setextendedstyle)来设置这些样式。

如果要在控件中使用扩展的 windows 样式，请调用[CreateEx](#createex)而不是 `Create`。

##  <a name="createex"></a>CComboBoxEx：： CreateEx

调用此函数可创建扩展组合框控件（子窗口），并将其与 `CComboBoxEx` 对象相关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwExStyle*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
组合框控件的样式。 有关样式列表，请参阅[创建](#create)。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构描述要创建的窗口的大小和位置（以*pParentWnd*的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用 `CreateEx` 而不是 `Create` 来应用扩展 Windows 样式，该样式由 Windows 扩展样式指定为在**WS_EX_** 。

`CreateEx` 使用*dwExStyle*指定的扩展 Windows 样式创建控件。 必须使用[SetExtendedStyle](#setextendedstyle)设置特定于扩展组合框控件的扩展样式。 例如，使用 `CreateEx` 将此类样式设置 WS_EX_CONTEXTHELP，但使用 `SetExtendedStyle` 将此类样式设置为 "CBES_EX_CASESENSITIVE"。 有关详细信息，请参阅主题中的[ComboBoxEx 控件扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)Windows SDK 中所述的样式。

##  <a name="deleteitem"></a>CComboBoxEx：:D eleteItem

删除 `ComboBoxEx` 控件中的项。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>parameters

*iIndex*<br/>
要移除的项的从零开始的索引。

### <a name="return-value"></a>返回值

控件中剩余的项数。 如果*iIndex*无效，则该函数将返回 CB_ERR。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)的功能，如 Windows SDK 中所述。 调用 Deleteitem.php 时，将向父窗口发送 CBEN_DELETEITEM 通知的[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

##  <a name="getcomboboxctrl"></a>CComboBoxEx：： GetComboBoxCtrl

调用此成员函数以获取指向 `CComboBoxEx` 对象内的组合框控件的指针。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>返回值

一个指向 `CComboBox` 对象的指针。

### <a name="remarks"></a>备注

`CComboBoxEx` 控件由一个用于封装 `CComboBox`的父窗口组成。

返回值指向的 `CComboBox` 对象是临时对象，并在下一个空闲处理时间被销毁。

##  <a name="geteditctrl"></a>CComboBoxEx：： GetEditCtrl

调用此成员函数以获取指向组合框的编辑控件的指针。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>返回值

指向[CEdit](../../mfc/reference/cedit-class.md)对象的指针。

### <a name="remarks"></a>备注

当使用 CBS_DROPDOWN 样式创建 `CComboBoxEx` 控件时，该控件使用编辑框。

返回值指向的 `CEdit` 对象是临时对象，并在下一个空闲处理时间被销毁。

##  <a name="getextendedstyle"></a>CComboBoxEx：： GetExtendedStyle

调用此成员函数以获取用于 `CComboBoxEx` 控件的扩展样式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

包含用于组合框控件的扩展样式的 DWORD 值。

### <a name="remarks"></a>备注

有关这些样式的详细信息，请参阅 ComboBoxEx 控件中 Windows SDK 的[扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)。

##  <a name="getimagelist"></a>CComboBoxEx：： GetImageList

调用此成员函数以获取指向 `CComboBoxEx` 控件使用的图像列表的指针。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。 如果失败，此成员函数将返回 NULL。

### <a name="remarks"></a>备注

返回值指向的 `CImageList` 对象是临时对象，并在下一个空闲处理时间被销毁。

##  <a name="getitem"></a>CComboBoxEx：： GetItem

检索给定 `ComboBoxEx` 项的项信息。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>parameters

*pCBItem*<br/>
指向将接收项信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。

### <a name="return-value"></a>返回值

如果操作成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)的功能，如 Windows SDK 中所述。

##  <a name="haseditchanged"></a>CComboBoxEx：： HasEditChanged

确定用户是否已通过键入更改了 `ComboBoxEx` 编辑控件的内容。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>返回值

如果用户已在控件的编辑框中键入，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)的功能，如 Windows SDK 中所述。

##  <a name="insertitem"></a>CComboBoxEx：： InsertItem

在 `ComboBoxEx` 控件中插入新项。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>parameters

*pCBItem*<br/>
指向将接收项信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。 此结构包含该项的回调标志值。

### <a name="return-value"></a>返回值

如果成功，则为其插入新项的索引;否则为-1。

### <a name="remarks"></a>备注

调用 `InsertItem`时，将向父窗口发送[CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem)通知[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

##  <a name="setextendedstyle"></a>CComboBoxEx：： SetExtendedStyle

调用此成员函数可设置用于组合框扩展控件的扩展样式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>parameters

*dwExMask*<br/>
一个 DWORD 值，指示要对*dwExStyles*中的哪些样式产生影响。 仅更改*dwExMask*中的扩展样式。 所有其他样式将按原样维护。 如果此参数为零，则将影响*dwExStyles*中的所有样式。

*dwExStyles*<br/>
一个 DWORD 值，该值包含要为控件设置的组合框控件扩展样式。

### <a name="return-value"></a>返回值

一个 DWORD 值，该值包含以前用于控件的扩展样式。

### <a name="remarks"></a>备注

有关这些样式的详细信息，请参阅 ComboBoxEx 控件中 Windows SDK 的[扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)。

若要创建具有扩展 windows 样式的组合框扩展控件，请使用[CreateEx](#createex)。

##  <a name="setimagelist"></a>CComboBoxEx：： SetImageList

设置 `ComboBoxEx` 控件的图像列表。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>parameters

*pImageList*<br/>
指向 `CImageList` 对象的指针，该对象包含要用于 `CComboBoxEx` 控件的图像。

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针，该对象包含 `CComboBoxEx` 控件以前使用的图像。 如果以前未设置图像列表，则为 NULL。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)的功能，如 Windows SDK 中所述。 如果更改默认编辑控件的高度，请在调用 `SetImageList`之后调用 Win32 函数[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)以调整控件大小，否则它将不会正确显示。

返回值指向的 `CImageList` 对象是临时对象，并在下一个空闲处理时间被销毁。

##  <a name="setitem"></a>CComboBoxEx：： SetItem

设置 `ComboBoxEx` 控件中的项的特性。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>parameters

*pCBItem*<br/>
指向将接收项信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。

### <a name="return-value"></a>返回值

如果操作成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)的功能，如 Windows SDK 中所述。

##  <a name="setwindowtheme"></a>CComboBoxEx：： SetWindowTheme

设置扩展组合框控件的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>parameters

*pszSubAppName*<br/>
指向一个 Unicode 字符串的指针，该字符串包含要设置的扩展组合框视觉样式。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme)消息的功能，如 Windows SDK 中所述。

## <a name="see-also"></a>另请参阅

[MFC 示例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)
