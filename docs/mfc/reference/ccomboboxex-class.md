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
ms.openlocfilehash: 92a81e318c74f1acd39fbfe870a7ad1277b25125
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501629"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx 类

通过为图像列表提供支持扩展组合框控件。

## <a name="syntax"></a>语法

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|构造 `CComboBoxEx` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|创建组合框，并将其附加到`CComboBoxEx`对象。|
|[CComboBoxEx::CreateEx](#createex)|创建一个组合框具有指定的 Windows 扩展样式并将其附加到`ComboBoxEx`对象。|
|[CComboBoxEx::DeleteItem](#deleteitem)|移除的项从`ComboBoxEx`控件。|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|检索指向子组合框控件。|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|检索的句柄的编辑控件部分`ComboBoxEx`控件。|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|检索正在使用的扩展的样式`ComboBoxEx`控件。|
|[CComboBoxEx::GetImageList](#getimagelist)|检索指向分配给的图像列表的`ComboBoxEx`控件。|
|[CComboBoxEx::GetItem](#getitem)|检索项信息给定`ComboBoxEx`项。|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|确定用户是否已更改的内容`ComboBoxEx`键入内容来编辑控件。|
|[CComboBoxEx::InsertItem](#insertitem)|将插入新项目在`ComboBoxEx`控件。|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|设置扩展的样式内`ComboBoxEx`控件。|
|[CComboBoxEx::SetImageList](#setimagelist)|设置图像列表的`ComboBoxEx`控件。|
|[CComboBoxEx::SetItem](#setitem)|设置中的项的特性`ComboBoxEx`控件。|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|设置的视觉样式的扩展组合框控件。|

## <a name="remarks"></a>备注

通过使用`CComboBoxEx`若要创建组合框控件，不再需要实现你自己的图像绘制代码。 请改用`CComboBoxEx`从图像列表的访问映像。

## <a name="image-list-support"></a>图像列表支持

在标准组合框中，组合框的所有者负责通过创建作为所有者描述控件的组合框绘制图像。 当你使用`CComboBoxEx`，不需要设置 CBS_OWNERDRAWFIXED 和 CBS_HASSTRINGS 的绘制样式，因为它们隐式。 否则，必须编写代码来执行绘制操作。 一个`CComboBoxEx`控件支持每个项的最多三个映像： 一个用于所选的状态、 未选中状态，覆盖图像。

## <a name="styles"></a>样式

`CComboBoxEx` 支持 CBS_SIMPLE、 CBS_DROPDOWN、 CBS_DROPDOWNLIST 和 WS_CHILD 的样式。 创建窗口时传递的所有其他样式将忽略由该控件。 创建窗口后，你可以提供其他组合框样式通过调用`CComboBoxEx`成员函数[SetExtendedStyle](#setextendedstyle)。 使用这些样式，您可以：

- 设置在列表中要区分大小写的字符串搜索。

- 创建一个组合框控件使用斜杠 （/）、 反斜杠 (\\)，和句点 (。) 作为词分隔符的字符。 这允许用户跳转到字使用键盘快捷方式 CTRL + 箭头。

- 设置组合框控件以显示或不显示的图像。 如果不显示任何图像，组合框可以删除可容纳映像的文本缩进。

- 创建包括调整其大小，使剪辑更广的组合框，它包含一个窄组合框控件。

可以进一步说明了这些样式标记[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="item-retention-and-callback-item-attributes"></a>项目的保留时间和回调项属性

项信息，如索引的项和图像、 缩进值和文本字符串存储在 Win32 结构[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)，如 Windows SDK 中所述。 结构还包含对应于回调标志的成员。

有关详细的概念介绍，请参阅[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

调用此成员函数来创建`CComboBoxEx`对象。

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

创建组合框，并将其附加到`CComboBoxEx`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于组合框的组合框样式的组合。 请参阅**备注**下面有关样式的详细信息。

*rect*<br/>
对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它是位置和组合框的大小。

*pParentWnd*<br/>
一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象，它是组合框的父窗口 (通常`CDialog`)。 它不能为 NULL。

*nID*<br/>
指定组合框控件 id。

### <a name="return-value"></a>返回值

如果成功，则创建对象时，非零值否则为 0。

### <a name="remarks"></a>备注

创建`CComboBoxEx`对象中两个步骤：

1. 调用[CComboBoxEx](#ccomboboxex)构造`CComboBoxEx`对象。

1. 调用此成员函数，将创建扩展的 Windows 组合框，并将其附加到`CComboBoxEx`对象。

当您调用`Create`，MFC 初始化公共控件。

在创建组合框时，可以指定任何或所有以下组合框样式：

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

创建窗口时传递的所有其他样式将被忽略。 `ComboBoxEx`控件还支持提供了其他功能的扩展的样式。 这些样式中所述[ComboBoxEx 控件扩展的样式](/windows/desktop/Controls/comboboxex-control-extended-styles)，Windows SDK 中。 通过调用设置这些样式[SetExtendedStyle](#setextendedstyle)。

如果你想要在控件中使用扩展的 windows 样式，则调用[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CComboBoxEx::CreateEx

调用此函数可创建扩展的组合框控件 （子窗口），并将其与`CComboBoxEx`对象。

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
组合框控件的样式。 请参阅[创建](#create)有关样式的列表。

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

`CreateEx` 创建使用指定的扩展 Windows 样式的控件*dwExStyle*。 您必须设置扩展的样式特定于扩展的组合框控件使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`来将此类样式设置为 WS_EX_CONTEXTHELP，但使用`SetExtendedStyle`若要将此类样式设置为 CBES_EX_CASESENSITIVE。 有关详细信息，请参阅本主题中所述的样式[ComboBoxEx 控件扩展样式](/windows/desktop/Controls/comboboxex-control-extended-styles)Windows SDK 中。

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

移除的项从`ComboBoxEx`控件。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
要删除的项的从零开始索引。

### <a name="return-value"></a>返回值

在控件中剩余的项目数。 如果*iIndex*是无效的该函数将返回 CB_ERR。

### <a name="remarks"></a>备注

此成员函数实现消息的功能[CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem)，如 Windows SDK 中所述。 当调用 DeleteItem [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) CBEN_DELETEITEM 通知消息将发送到父窗口。

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

调用此成员函数以向组合框控件中获取的指针`CComboBoxEx`对象。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>返回值

指向 `CComboBox` 对象的指针。

### <a name="remarks"></a>备注

`CComboBoxEx`控件包含一个父窗口，其中封装`CComboBox`。

`CComboBox`返回值指向的对象是临时对象并在下一步的空闲处理期间被销毁。

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

调用此成员函数以获取指向组合框编辑控件。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>返回值

一个指向[CEdit](../../mfc/reference/cedit-class.md)对象。

### <a name="remarks"></a>备注

一个`CComboBoxEx`控件创建 CBS_DROPDOWN 样式时使用的编辑框。

`CEdit`返回值指向的对象是临时对象并在下一步的空闲处理期间被销毁。

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

调用此成员函数以获取有关所用的扩展的样式`CComboBoxEx`控件。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

包含用于组合框控件的扩展的样式 DWORD 值。

### <a name="remarks"></a>备注

请参阅[ComboBoxEx 控件扩展样式](/windows/desktop/Controls/comboboxex-control-extended-styles)适用于这些样式有关的详细信息的 Windows SDK 中。

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

调用此成员函数可使用的映像列表中获取指向`CComboBoxEx`控件。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。 如果失败，此成员函数将返回 NULL。

### <a name="remarks"></a>备注

`CImageList`返回值指向的对象是临时对象并在下一步的空闲处理期间被销毁。

##  <a name="getitem"></a>  CComboBoxEx::GetItem

检索项信息给定`ComboBoxEx`项。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCBItem*<br/>
一个指向[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)将收到的项信息的结构。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

此成员函数实现消息的功能[CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem)，如 Windows SDK 中所述。

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

确定用户是否已更改的内容`ComboBoxEx`键入内容来编辑控件。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>返回值

如果用户已在控件的编辑框中; 键入非零值否则为 0。

### <a name="remarks"></a>备注

此成员函数实现消息的功能[CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged)，如 Windows SDK 中所述。

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

将插入新项目在`ComboBoxEx`控件。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCBItem*<br/>
一个指向[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)将收到的项信息的结构。 此结构包含回调项的标志值。

### <a name="return-value"></a>返回值

如果成功，则在其中插入新项的索引否则为-1。

### <a name="remarks"></a>备注

当您调用`InsertItem`、 一个[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)消息[CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem)将向父窗口发送通知。

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

调用此成员函数可设置用于扩展控件的组合框的扩展的样式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>参数

*dwExMask*<br/>
DWORD 值，该值指示在哪种样式*dwExStyles*会受到影响。 中的扩展的样式*dwExMask*将会更改。 是，将保持所有其他样式。 如果此参数为零，则所有中的样式*dwExStyles*会受到影响。

*dwExStyles*<br/>
一个包含组合框控件的 DWORD 值扩展为控件设置的样式。

### <a name="return-value"></a>返回值

一个 DWORD 值，该值包含之前用于控件的扩展的样式。

### <a name="remarks"></a>备注

请参阅[ComboBoxEx 控件扩展样式](/windows/desktop/Controls/comboboxex-control-extended-styles)适用于这些样式有关的详细信息的 Windows SDK 中。

若要创建扩展以扩展的 windows 样式的控件的组合框，请使用[CreateEx](#createex)。

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

设置图像列表的`ComboBoxEx`控件。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
一个指向`CImageList`对象，其中包含要用于映像`CComboBoxEx`控件。

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，其中包含以前使用过的映像`CComboBoxEx`控件。 如果任何图像列表之前已不设置为 NULL。

### <a name="remarks"></a>备注

此成员函数实现消息的功能[CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist)，如 Windows SDK 中所述。 如果更改默认编辑控件的高度，调用 Win32 函数[SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos)来调整控件大小调用后`SetImageList`，或不会正确显示。

`CImageList`返回值指向的对象是临时对象并在下一步的空闲处理期间被销毁。

##  <a name="setitem"></a>  CComboBoxEx::SetItem

设置中的项的特性`ComboBoxEx`控件。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCBItem*<br/>
一个指向[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)将收到的项信息的结构。

### <a name="return-value"></a>返回值

如果操作成功，则非零值否则为 0。

### <a name="remarks"></a>备注

此成员函数实现消息的功能[CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem)，如 Windows SDK 中所述。

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

设置的视觉样式的扩展组合框控件。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pszSubAppName*<br/>
指向包含扩展的组合框的视觉样式设置的 Unicode 字符串的指针。

### <a name="return-value"></a>返回值

不使用返回的值。

### <a name="remarks"></a>备注

此成员函数模拟的功能[CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme)消息，如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 MFCIE](../../visual-cpp-samples.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)
