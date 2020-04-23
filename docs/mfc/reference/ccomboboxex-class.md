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
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754820"
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
|[CComboBoxEx：CComboBoxEx](#ccomboboxex)|构造 `CComboBoxEx` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComboBoxEx：创建](#create)|创建组合框并将其附加到`CComboBoxEx`对象。|
|[CComboBoxEx：创建Ex](#createex)|创建具有指定 Windows 扩展样式的组合框并将其附加到`ComboBoxEx`对象。|
|[CComboBoxEx：:Delete项目](#deleteitem)|从控件中删除项`ComboBoxEx`。|
|[CComboBoxEx：获取ComboBoxCtrl](#getcomboboxctrl)|检索指向子组合框控件的指针。|
|[CComboBoxEx：获取编辑](#geteditctrl)|检索控件的编辑控件部分的`ComboBoxEx`句柄。|
|[CComboBoxEx：获取扩展样式](#getextendedstyle)|检索控件正在使用的`ComboBoxEx`扩展样式。|
|[CComboBoxEx：获取图片列表](#getimagelist)|检索分配给控件的图像列表的`ComboBoxEx`指针。|
|[CComboBoxEx：获取项目](#getitem)|检索给定`ComboBoxEx`项的项信息。|
|[CComboBoxEx：：已编辑](#haseditchanged)|通过键入确定用户是否更改了`ComboBoxEx`编辑控件的内容。|
|[CComboBoxEx：插入项目](#insertitem)|在控件中`ComboBoxEx`插入新项目。|
|[CComboBoxEx：：设置扩展样式](#setextendedstyle)|在`ComboBoxEx`控件中设置扩展样式。|
|[CComboBoxEx：：设置图像列表](#setimagelist)|为`ComboBoxEx`控件设置图像列表。|
|[CComboBoxEx：设置项目](#setitem)|设置`ComboBoxEx`控件中项的属性。|
|[CComboBoxEx：：设置窗口主题](#setwindowtheme)|设置扩展组合框控件的视觉样式。|

## <a name="remarks"></a>备注

通过使用`CComboBoxEx`创建组合框控件，您不再需要实现自己的图像绘制代码。 而是使用`CComboBoxEx`来访问图像列表中的图像。

## <a name="image-list-support"></a>图像列表支持

在标准组合框中，组合框的所有者负责通过将组合框创建为所有者绘制控件来绘制图像。 使用`CComboBoxEx`时，不需要将绘图样式CBS_OWNERDRAWFIXED设置，并且CBS_HASSTRINGS，因为它们是隐含的。 否则，必须编写代码以执行绘图操作。 控件`CComboBoxEx`每项目最多支持三个图像：一个用于选定状态，一个用于未选中状态，一个用于叠加图像。

## <a name="styles"></a>样式

`CComboBoxEx`支持CBS_SIMPLE、CBS_DROPDOWN、CBS_DROPDOWNLIST和WS_CHILD样式。 控件将忽略创建窗口时传递的所有其他样式。 创建窗口后，可以通过调用`CComboBoxEx`成员函数[SetExtendedStyle](#setextendedstyle)提供其他组合框样式。 使用这些样式，您可以：

- 将列表中的字符串搜索设置为区分大小写。

- 创建组合框控件，该控件使用斜杠 （'/'）、反斜杠\\（''） 和句点 （'.'） 字符作为单词分隔符。 这允许用户使用键盘快捷键 CTRL+ 箭头从一字跳一字。

- 将组合框控件设置为显示或不显示图像。 如果未显示图像，组合框可以删除容纳图像的文本缩进。

- 创建一个狭窄的组合框控件，包括调整大小，以便它剪辑它包含的更宽组合框。

这些样式标志在[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)中进一步描述。

## <a name="item-retention-and-callback-item-attributes"></a>项目保留和回调项目属性

项目信息（如项和图像的索引、缩进值和文本字符串）存储在 Win32 结构[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)中，如 Windows SDK 中所述。 结构还包含对应于回调标志的成员。

有关详细的概念性讨论，请参阅[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx：CComboBoxEx

调用此成员函数以创建对象`CComboBoxEx`。

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx：创建

创建组合框并将其附加到`CComboBoxEx`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于组合框的组合框样式的组合。 有关样式的详细信息，请参阅下面的**备注**。

*矩形*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，即组合框的位置和大小。

*pparentwnd*<br/>
指向作为组合框的父窗口（通常为 ）`CDialog`的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。 值不得为 NULL。

*nID*<br/>
指定组合框的控制 ID。

### <a name="return-value"></a>返回值

如果对象已成功创建，则非零;否则 0。

### <a name="remarks"></a>备注

通过两`CComboBoxEx`个步骤创建对象：

1. 调用[CComboBoxEx](#ccomboboxex)构造`CComboBoxEx`对象。

1. 调用此成员函数，该函数创建扩展的 Windows 组合框并将其附加到`CComboBoxEx`对象。

调用 时`Create`，MFC 将初始化公共控件。

创建组合框时，可以指定以下任何或所有组合框样式：

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

创建窗口时传递的所有其他样式将被忽略。 该`ComboBoxEx`控件还支持提供其他功能的扩展样式。 这些样式在[ComboBoxEx 控件扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)中（Windows SDK）中描述。 通过调用 Set[扩展样式](#setextendedstyle)来设置这些样式。

如果要将扩展窗口样式与控件一起使用，请调用[CreateEx](#createex) `Create`而不是 。

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx：创建Ex

调用此函数以创建扩展组合框控件（子窗口），并将其与`CComboBoxEx`对象关联。

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
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
组合框控件的样式。 请参阅[创建](#create)样式列表。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是`Create`应用扩展的 Windows 样式，由 Windows 扩展样式前言**WS_EX_** 指定。

`CreateEx`使用*dwExStyle*指定的扩展 Windows 样式创建控件。 您必须使用[Set 扩展样式](#setextendedstyle)设置特定于扩展组合框控件的扩展样式。 例如，用于`CreateEx`将此类样式设置为WS_EX_CONTEXTHELP，但用于`SetExtendedStyle`将此类样式设置为CBES_EX_CASESENSITIVE。 有关详细信息，请参阅 Windows SDK 中的主题[ComboBoxEx 控件扩展样式中描述的样式](/windows/win32/Controls/comboboxex-control-extended-styles)。

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx：:Delete项目

从控件中删除项`ComboBoxEx`。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
要删除的项的从零开始索引。

### <a name="return-value"></a>返回值

控件中剩余的项数。 如果*iIndex*无效，则函数将返回CB_ERR。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)的功能，如 Windows SDK 中所述。 当您调用 DeleteItem 时，带有CBEN_DELETEITEM通知[的WM_NOTIFY](/windows/win32/controls/wm-notify)消息将发送到父窗口。

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx：获取ComboBoxCtrl

调用此成员函数以获取指向对象中的组合框控件的`CComboBoxEx`指针。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>返回值

一个指向 `CComboBox` 对象的指针。

### <a name="remarks"></a>备注

该`CComboBoxEx`控件由父窗口组成，该窗口封装 了`CComboBox`。

返回`CComboBox`值指向的对象是临时对象，并在下一个空闲处理期间销毁。

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx：获取编辑

调用此成员函数以获取指向组合框的编辑控件的指针。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>返回值

指向[CEdit](../../mfc/reference/cedit-class.md)对象的指针。

### <a name="remarks"></a>备注

使用`CComboBoxEx`CBS_DROPDOWN样式创建控件时，将使用编辑框。

返回`CEdit`值指向的对象是临时对象，并在下一个空闲处理期间销毁。

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx：获取扩展样式

调用此成员函数获取用于控件的`CComboBoxEx`扩展样式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

包含用于组合框控件的扩展样式的 DWORD 值。

### <a name="remarks"></a>备注

有关这些样式的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)。

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx：获取图片列表

调用此成员函数以获取指向控件使用的图像列表的`CComboBoxEx`指针。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。 如果失败，此成员函数将返回 NULL。

### <a name="remarks"></a>备注

返回`CImageList`值指向的对象是临时对象，并在下一个空闲处理期间销毁。

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx：获取项目

检索给定`ComboBoxEx`项的项信息。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCB项目*<br/>
指向将接收物料信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)的功能，如 Windows SDK 中所述。

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx：：已编辑

通过键入确定用户是否更改了`ComboBoxEx`编辑控件的内容。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>返回值

如果用户在控件的编辑框中键入了非零;如果用户在控件的编辑框中键入了"非零";否则 0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)的功能，如 Windows SDK 中所述。

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx：插入项目

在控件中`ComboBoxEx`插入新项目。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCB项目*<br/>
指向将接收物料信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。 此结构包含项的回调标志值。

### <a name="return-value"></a>返回值

如果成功，则插入新项目的索引;否则 -1。

### <a name="remarks"></a>备注

调用`InsertItem`时，将发送带有[CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem)通知[WM_NOTIFY](/windows/win32/controls/wm-notify)消息到父窗口。

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx：：设置扩展样式

调用此成员函数以设置用于组合框扩展控件的扩展样式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>参数

*dwExMask*<br/>
DWORD 值，指示*dwExStyles*中的哪些样式将受到影响。 只有*dwExMask*中的扩展样式才会更改。 所有其他样式将保持不变。 如果此参数为零，则*dwExStyles*中的所有样式都将受到影响。

*dwExStyles*<br/>
包含组合框控件扩展样式的 DWORD 值，用于为控件设置。

### <a name="return-value"></a>返回值

包含以前用于控件的扩展样式的 DWORD 值。

### <a name="remarks"></a>备注

有关这些样式的详细信息，请参阅 Windows SDK 中的[ComboBoxEx 控件扩展样式](/windows/win32/Controls/comboboxex-control-extended-styles)。

要使用扩展窗口样式创建组合框扩展控件，请使用[CreateEx](#createex)。

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx：：设置图像列表

为`ComboBoxEx`控件设置图像列表。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向包含要与`CImageList`控件一起使用的图像的对象的`CComboBoxEx`指针。

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针，其中包含`CComboBoxEx`控件以前使用的图像。 如果以前未设置任何图像列表，则为 NULL。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)的功能，如 Windows SDK 中所述。 如果更改默认编辑控件的高度，请调用 Win32 函数[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)来调整调用`SetImageList`后控件的大小，否则控件将无法正确显示。

返回`CImageList`值指向的对象是临时对象，并在下一个空闲处理期间销毁。

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx：设置项目

设置`ComboBoxEx`控件中项的属性。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>参数

*pCB项目*<br/>
指向将接收物料信息的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的指针。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数实现消息[CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)的功能，如 Windows SDK 中所述。

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx：：设置窗口主题

设置扩展组合框控件的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pssSubApp名称*<br/>
指向要设置的扩展组合框可视样式的 Unicode 字符串的指针。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme)消息的功能，如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)
