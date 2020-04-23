---
title: C按钮类
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 74b07dc8144e853714ea73c8235f1259538a0c12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752753"
---
# <a name="cbutton-class"></a>C按钮类

提供 Windows 按钮控件功能。

## <a name="syntax"></a>语法

```
class CButton : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C按钮：：C按钮](#cbutton)|构造 `CButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C按钮：：创建](#create)|创建 Windows 按钮控件并将其附加到`CButton`对象。|
|[CButton：:D原始项目](#drawitem)|覆盖以绘制所有者绘制`CButton`的对象。|
|[C按钮：：获取位图](#getbitmap)|检索以前使用[SetBitmap](#setbitmap)设置的位图的句柄。|
|[C按钮：：获取按钮样式](#getbuttonstyle)|检索有关按钮控制样式的信息。|
|[C按钮：：获取检查](#getcheck)|检索按钮控件的检查状态。|
|[C按钮：：获取光标](#getcursor)|检索以前使用[SetCursor](#setcursor)设置的游标图像的句柄。|
|[C按钮：：获取图标](#geticon)|检索以前使用[SetIcon](#seticon)设置的图标的句柄。|
|[C按钮：：获取理想尺寸](#getidealsize)|检索按钮控件的理想大小。|
|[C按钮：获取图片列表](#getimagelist)|检索按钮控件的图像列表。|
|[C按钮：：获取笔记](#getnote)|检索当前命令链接控件的注释组件。|
|[C按钮：：获取注释长度](#getnotelength)|检索当前命令链接控件的注释文本的长度。|
|[C按钮：：获取拆分字形](#getsplitglyph)|检索与当前拆分按钮控件关联的字形。|
|[C按钮：获取拆分图像列表](#getsplitimagelist)|检索当前拆分按钮控件的图像列表。|
|[C按钮：获取拆分信息](#getsplitinfo)|检索定义当前拆分按钮控件的信息。|
|[C按钮：：获取拆分大小](#getsplitsize)|检索当前拆分按钮控件的下拉组件的边界矩形。|
|[C按钮：：获取拆分样式](#getsplitstyle)|检索定义当前拆分按钮控件的拆分按钮样式。|
|[C按钮：：获取状态](#getstate)|检索按钮控件的检查状态、突出显示状态和对焦状态。|
|[C按钮：：获取文本保证金](#gettextmargin)|检索按钮控件的文本边距。|
|[C按钮：：设置位图](#setbitmap)|指定要显示在按钮上的位图。|
|[C按钮：：设置按钮样式](#setbuttonstyle)|更改按钮的样式。|
|[C按钮：：设置检查](#setcheck)|设置按钮控件的检查状态。|
|[CButton：：设置光标](#setcursor)|指定要显示在按钮上的光标图像。|
|[C按钮：：设置下拉状态](#setdropdownstate)|设置当前拆分按钮控件的下拉状态。|
|[C按钮：：设置图标](#seticon)|指定要显示在按钮上的图标。|
|[C按钮：：设置图像列表](#setimagelist)|设置按钮控件的图像列表。|
|[C按钮：：设置注](#setnote)|在当前命令链接控件上设置注释。|
|[C按钮：：设置分割字形](#setsplitglyph)|将指定的字形与当前拆分按钮控件关联。|
|[CButton：：设置拆分图像列表](#setsplitimagelist)|将图像列表与当前拆分按钮控件关联。|
|[CButton：：设置拆分信息](#setsplitinfo)|指定定义当前拆分按钮控件的信息。|
|[C按钮：：设置拆分大小](#setsplitsize)|设置当前拆分按钮控件的下拉组件的边界矩形。|
|[C按钮：：设置拆分样式](#setsplitstyle)|设置当前拆分按钮控件的样式。|
|[C按钮：：设置状态](#setstate)|设置按钮控件的突出显示状态。|
|[C按钮：：设置文本边缘](#settextmargin)|设置按钮控件的文本边距。|

## <a name="remarks"></a>备注

按钮控件是可单击和关闭的小型矩形子窗口。 按钮可以单独使用，也可以单独使用，也可以单独使用，也可以在没有文本的情况下显示。 当用户单击按钮时，按钮通常会更改外观。

典型的按钮是复选框、单选按钮和按钮。 根据`CButton` [Create](#create)成员函数在初始化时指定的[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)，对象可以成为其中任何一个。

此外，派生自的`CButton` [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)类支持创建带有位图图像而不是文本标记的按钮控件。 可以为`CBitmapButton`按钮的上、下、焦点和禁用状态提供单独的位图。

可以从对话框模板或直接在代码中创建按钮控件。 在这两种情况下，首先调用构造函数`CButton`来构造`CButton`对象;否则，请先调用构造函数来构造该对象。然后调用`Create`成员函数以创建 Windows 按钮控件并将其附加到`CButton`对象。

构造可以是派生自`CButton`的类中的一个步骤。 为派生类编写一个构造函数，并从`Create`构造函数内部调用。

如果要处理按钮控件发送到其父级的 Windows 通知消息（通常是从[CDialog](../../mfc/reference/cdialog-class.md)派生的类），则为每个消息向父类添加消息映射条目和消息处理程序成员函数。

每个消息映射条目采用以下形式：

**打开\_**_通知_**（ID** _id_，_成员Fxn_ **）**

*其中 ID*指定发送通知的控件的子窗口 ID，*而成员Fxn*是您为处理通知而编写的父成员函数的名称。

父函数原型如下所示：

`afx_msg void memberFxn();`

潜在的消息映射条目如下所示：

|映射条目|何时发送给父级...|
|---------------|----------------------------|
|ON_BN_CLICKED|用户单击按钮。|
|ON_BN_DOUBLECLICKED|用户双击按钮。|

如果从对话框资源`CButton`创建对象，则当用户关闭对话框`CButton`时，该对象将自动销毁。

如果在窗口中创建`CButton`对象，则可能需要销毁它。 如果使用新函数在`CButton`堆上创建对象，则必须调用**new**对象**上的 delete**以在用户关闭 Windows 按钮控件时销毁该对象。 如果在堆栈上`CButton`创建对象，或者该对象嵌入到父对话框对象中，则会自动销毁该对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>C按钮：：C按钮

构造 `CButton` 对象。

```
CButton();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>C按钮：：创建

创建 Windows 按钮控件并将其附加到`CButton`对象。

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*lpszCaption*<br/>
指定按钮控件的文本。

*dwStyle*<br/>
指定按钮控件的样式。 将[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)的任意组合应用于按钮。

*矩形*<br/>
指定按钮控件的大小和位置。 它可以是`CRect`对象或`RECT`结构。

*pparentwnd*<br/>
指定按钮控件的父窗口（通常为 。 `CDialog` 值不得为 NULL。

*nID*<br/>
指定按钮控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两步`CButton`构造对象。 首先，调用构造函数，然后调用`Create`，这将创建 Windows 按钮控件并将其附加到`CButton`对象。

如果提供了WS_VISIBLE样式，Windows 将发送按钮控件激活并显示按钮所需的所有消息。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于按钮控件：

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP组控件

- WS_TABSTOP 在制表顺序中包含按钮

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton：:D原始项目

当所有者绘制按钮的可视方面已更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针。 结构包含有关要绘制的项和所需绘图类型的信息。

### <a name="remarks"></a>备注

所有者绘制的按钮已设置BS_OWNERDRAW样式。 重写此成员函数以实现所有者绘制`CButton`对象的绘图。 应用程序应还原在成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

另请参阅[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)样式值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>C按钮：：获取位图

调用此成员函数获取与按钮关联的位图的句柄，该位图以前使用[SetBitmap](#setbitmap)设置。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>返回值

位图的句柄。 如果以前未指定位图，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>C按钮：：获取按钮样式

检索有关按钮控制样式的信息。

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>返回值

返回此`CButton`对象的按钮样式。 此函数仅返回[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)样式值，而不是返回任何其他窗口样式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>C按钮：：获取检查

检索单选按钮或复选框的复选框。

```
int GetCheck() const;
```

### <a name="return-value"></a>返回值

使用BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON或BS_3STATE样式创建的按钮控件的返回值是以下值之一：

|“值”|含义|
|-----------|-------------|
|BST_UNCHECKED|未选中按钮状态。|
|BST_CHECKED|选中按钮状态。|
|BST_INDETERMINATE|按钮状态不确定（仅当按钮具有BS_3STATE或BS_AUTO3STATE样式时才适用）。|

如果按钮具有任何其他样式，则返回值BST_UNCHECKED。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>C按钮：：获取光标

调用此成员函数以获取以前使用[SetCursor](#setcursor)设置的与按钮关联的游标的句柄。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>返回值

光标图像的句柄。 如果以前未指定游标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>C按钮：：获取图标

调用此成员函数以获取以前使用[SetIcon](#seticon)设置的与按钮关联的图标的句柄。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>返回值

图标的图柄。 如果以前未指定任何图标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>C按钮：：获取理想尺寸

检索按钮控件的理想大小。

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>参数

*psize*<br/>
指向按钮当前大小的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟BCM_GETIDEALSIZE消息的功能，如 Windows SDK 的["按钮"](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>C按钮：获取图片列表

调用此方法从按钮控件获取图像列表。

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>参数

*p按钮图像列表*<br/>
指向对象图像列表的`CButton`指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟BCM_GETIMAGELIST消息的功能，如 Windows SDK 的["按钮"](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttongetnote"></a><a name="getnote"></a>C按钮：：获取笔记

检索与当前命令链接控件关联的注释文本。

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpszNote*|[出]指向缓冲区的指针，调用方负责分配和释放缓冲区。 如果返回值为 TRUE，缓冲区将包含与当前命令链接控件关联的注释文本;如果返回值为 TRUE，则缓冲区包含与当前命令链接控件关联的注释文本。否则，缓冲区将保持不变。|
|*cchNote*|[进出]指向无符号整数变量的指针。<br /><br /> 调用此方法时，变量包含*lpszNote*参数指定的缓冲区的大小。<br /><br /> 当此方法返回时，如果返回值为 TRUE，则变量包含与当前命令链接控件关联的注释的大小。 如果返回值为 FALSE，则变量包含包含注释所需的缓冲区大小。|

### <a name="return-value"></a>返回值

在第一个重载中，包含与当前命令链接控件关联的注释文本的[CString](../../atl-mfc-shared/using-cstring.md)对象。

-或-

在第二个重载中，如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

仅对按钮样式为BS_COMMANDLINK或BS_DEFCOMMANDLINK的控件使用此方法。

此方法发送[BCM_GETNOTE](/windows/win32/Controls/bcm-getnote)消息，这在 Windows SDK 中介绍。

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>C按钮：：获取注释长度

检索当前命令链接控件的注释文本的长度。

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>返回值

当前命令链接控件的注释文本的长度（以 16 位 Unicode 字符表示）。

### <a name="remarks"></a>备注

仅对按钮样式为BS_COMMANDLINK或BS_DEFCOMMANDLINK的控件使用此方法。

此方法发送[BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength)消息，这在 Windows SDK 中介绍。

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>C按钮：：获取拆分字形

检索与当前拆分按钮控件关联的字形。

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>返回值

与当前拆分按钮控件关联的字形字符。

### <a name="remarks"></a>备注

字形是特定字体中字符的物理表示形式。 例如，拆分按钮控件可能用 Unicode 复选标记字符 （U+2713） 的字形进行修饰。

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

此方法使用BCSIF_GLYPH标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法从结构`himlGlyph`的成员中检索字形。

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>C按钮：获取拆分图像列表

检索当前拆分按钮控件[的图像列表](../../mfc/reference/cimagelist-class.md)。

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

此方法使用BCSIF_IMAGE标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法从结构`himlGlyph`的成员检索图像列表。

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>C按钮：获取拆分信息

检索确定 Windows 如何绘制当前拆分按钮控件的参数。

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pInfo*|[出]指向接收有关当前拆分按钮控件的信息[的BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的指针。 调用方负责分配结构。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

此方法发送[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息，这在 Windows SDK 中介绍。

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>C按钮：：获取拆分大小

检索当前拆分按钮控件的下拉组件的边界矩形。

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pSize*|[出]指向接收矩形描述的[SIZE](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

展开拆分按钮控件时，它可以显示下拉组件，如列表控件或寻呼器控件。 此方法检索包含下拉组件的边界矩形。

此方法使用BCSIF_SIZE标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法从结构`size`的成员检索边界矩形。

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>C按钮：：获取拆分样式

检索定义当前拆分按钮控件的拆分按钮样式。

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>返回值

拆分按钮样式的位组合。 有关详细信息，请参阅`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

拆分按钮样式指定 Windows 绘制拆分按钮图标的对齐、纵横比和图形格式。

此方法使用BCSIF_STYLE标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法从结构`uSplitStyle`的成员中检索拆分按钮样式。

## <a name="cbuttongetstate"></a><a name="getstate"></a>C按钮：：获取状态

检索按钮控件的状态。

```
UINT GetState() const;
```

### <a name="return-value"></a>返回值

包含指示按钮控件当前状态的值组合的位字段。 下表列出了可能的值。

|按钮状态|“值”|说明|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|初始状态。|
|BST_CHECKED|0x0001|检查按钮控件。|
|BST_INDETERMINATE|0x0002|状态不确定（仅当按钮控件具有三种状态时才可能）。|
|BST_PUSHED|0x0004|按下按钮控件。|
|BST_FOCUS|0x0008|按钮控件具有焦点。|

### <a name="remarks"></a>备注

具有BS_3STATE或BS_AUTO3STATE按钮样式的按钮控件将创建一个复选框，该复选框具有第三个状态，称为不确定状态。 不确定状态表示未选中或未选中复选框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>C按钮：：获取文本保证金

调用此方法获取`CButton`对象的文本边距。

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>参数

*pmargin*<br/>
指向对象的文本边距的`CButton`指针。

### <a name="return-value"></a>返回值

返回文本边距。

### <a name="remarks"></a>备注

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟BCM_GETTEXTMARGIN消息的功能，如 Windows SDK 的["按钮"](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>C按钮：：设置位图

调用此成员函数以将新的位图与按钮关联。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
位图的句柄。

### <a name="return-value"></a>返回值

以前与按钮关联的位图的句柄。

### <a name="remarks"></a>备注

位图将自动放置在按钮的面上，默认情况下居中。 如果位图对于按钮太大，则该位图将在任一侧剪切。 您可以选择其他对齐选项，包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

与每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)不同，`SetBitmap`每个按钮仅使用一个位图。 按下按钮时，位图将显示向下和向右移动。

完成位图后，您有责任释放它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>C按钮：：设置按钮样式

更改按钮的样式。

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
指定[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

*bredraw*<br/>
指定是否要重绘按钮。 非零值重绘按钮。 0 值不会重绘按钮。 默认情况下，该按钮将重绘。

### <a name="remarks"></a>备注

使用`GetButtonStyle`成员函数检索按钮样式。 完整按钮样式的低阶字是特定于按钮的样式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>C按钮：：设置检查

设置或重置单选按钮或复选框的复选框。

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>参数

*n检查*<br/>
指定检查状态。 此参数可以是以下项之一：

|“值”|含义|
|-----------|-------------|
|BST_UNCHECKED|将按钮状态设置为取消选中。|
|BST_CHECKED|将按钮状态设置为选中。|
|BST_INDETERMINATE|将按钮状态设置为不确定。 仅当按钮具有BS_3STATE或BS_AUTO3STATE样式时，才能使用此值。|

### <a name="remarks"></a>备注

此成员函数对按钮没有影响。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton：：设置光标

调用此成员函数以将新光标与按钮关联。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>参数

*h光标*<br/>
光标的句柄。

### <a name="return-value"></a>返回值

以前与按钮关联的游标的句柄。

### <a name="remarks"></a>备注

光标将自动放置在按钮的面上，默认情况下居中。 如果光标太大，无法用于按钮，则该光标将在任一侧被剪切。 您可以选择其他对齐选项，包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

与每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)不同，`SetCursor`每个按钮只使用一个光标。 按下按钮时，光标将向下和向右移动。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>C按钮：：设置下拉状态

设置当前拆分按钮控件的下拉状态。

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*f向下*|[在]TRUE 设置为BST_DROPDOWNPUSHED状态;否则，FALSE。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

拆分按钮控件具有BS_SPLITBUTTON或BS_DEFSPLITBUTTON样式，其右侧由按钮和下拉箭头组成。 有关详细信息，请参阅[按钮样式](/windows/win32/Controls/button-styles)。 通常，当用户单击下拉箭头时，将设置下拉状态。 使用此方法以编程方式设置控件的下拉状态。 下拉箭头绘制为下拉箭头，以指示状态。

此方法发送[BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问拆分按钮控件的变量*m_splitButton*。 以下示例使用此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

以下代码示例设置拆分按钮控件的状态，以指示按下下拉箭头。

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>C按钮：：设置所需的提升

将当前按钮控件的状态设置为`elevation required`，这是控件显示提升的安全图标所必需的。

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*f 海拔要求*|[在]设置为"TRUE"`elevation required`状态;否则，FALSE。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果按钮或命令链接控件需要提升的安全权限才能执行操作，则将控件设置为`elevation required`状态。 随后，Windows 会在控件上显示用户帐户控制 （UAC） 屏蔽图标。 有关详细信息，请参阅[MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507)的"用户帐户控制"。

此方法发送[BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield)消息，这在 Windows SDK 中介绍。

## <a name="cbuttonseticon"></a><a name="seticon"></a>C按钮：：设置图标

调用此成员函数将新图标与按钮关联。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
图标的句柄。

### <a name="return-value"></a>返回值

以前与按钮关联的图标的句柄。

### <a name="remarks"></a>备注

该图标将自动放置在按钮的面上，默认情况下居中。 如果图标太大，无法用于按钮，则该图标将在任一侧被剪切。 您可以选择其他对齐选项，包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

与每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)不同，`SetIcon`每个按钮只使用一个图标。 按下按钮时，图标将显示向下和向右移动。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>C按钮：：设置图像列表

调用此方法以设置`CButton`对象的图像列表。

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>参数

*p按钮图像列表*<br/>
指向新图像列表的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟BCM_SETIMAGELIST消息的功能，如 Windows SDK 的["按钮"](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttonsetnote"></a><a name="setnote"></a>C按钮：：设置注

设置当前命令链接控件的注释文本。

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpszNote*|[在]指向 Unicode 字符串的指针，该字符串设置为命令链接控件的注释文本。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

仅对按钮样式为BS_COMMANDLINK或BS_DEFCOMMANDLINK的控件使用此方法。

此方法发送[BCM_SETNOTE](/windows/win32/Controls/bcm-setnote)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问命令链接控件的变量*m_cmdLink*。 以下示例使用此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

以下代码示例设置命令链接控件的注释文本。

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>C按钮：：设置分割字形

将指定的字形与当前拆分按钮控件关联。

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*chGlyph*|[在]指定用作分割按钮下拉箭头的字形的字符。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

仅对具有按钮样式BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用此方法。

字形是特定字体中字符的物理表示形式。 *chGlyph*参数不用作字形，而是用于从一组系统定义的字形中选择字形。 默认下拉箭头字形由字符"6"指定，类似于 Unicode 字符"黑色向下-点角图"（U+25BC）。

此方法使用BCSIF_GLYPH标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员，使用*chGlyph* `himlGlyph`参数来初始化该结构，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton：：设置拆分图像列表

将[图像列表](../../mfc/reference/cimagelist-class.md)与当前拆分按钮控件关联。

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*p拆分图像列表*|[在]指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针，以分配给当前拆分按钮控件。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

此方法使用BCSIF_IMAGE标志和`mask`*pSplitImageList*参数初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构`himlGlyph`的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton：：设置拆分信息

指定确定 Windows 如何绘制当前拆分按钮控件的参数。

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pInfo*|[在]指向定义当前拆分按钮控件[的BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

此方法发送[BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_splitButton`拆分按钮控件的变量 。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

以下代码示例更改用于拆分按钮下拉箭头的字形。 该示例将向上的三角形字形替换为默认的向下指向三角形字形。 显示的字形取决于您在`himlGlyph``BUTTON_SPLITINFO`结构成员中指定的字符。 向下指向三角形字形由字符"6"指定，上指三角形字形由字符"5"指定。 有关比较，请参阅方便方法[CButton：：setSplitGlyph](#setsplitglyph)。

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>C按钮：：设置拆分大小

设置当前拆分按钮控件的下拉组件的边界矩形。

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pSize*|[在]指向描述边界矩形的[SIZE](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

展开拆分按钮控件时，它可以显示下拉组件，如列表控件或寻呼器控件。 此方法指定包含下拉组件的边界矩形的大小。

此方法使用 BCSIF_SIZE 标志`mask`和*pSize*参数初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构`size`的成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_splitButton`拆分按钮控件的变量 。 以下示例使用此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

以下代码示例将拆分按钮下拉箭头的大小加倍。

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>C按钮：：设置拆分样式

设置当前拆分按钮控件的样式。

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*uSplit样式*|[在]拆分按钮样式的位组合。 有关详细信息，请参阅`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法仅对按钮样式为BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控件使用。

拆分按钮样式指定 Windows 绘制拆分按钮图标的对齐、纵横比和图形格式。 有关详细信息，请参阅`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的成员。

此方法使用BCSIF_STYLE标志初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构`uSplitStyle`的成员，使用*uSplitStyle*参数来初始化该结构，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_splitButton`拆分按钮控件的变量 。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

以下代码示例设置拆分按钮下拉箭头的样式。 BCSS_ALIGNLEFT样式显示按钮左侧的箭头，BCSS_STRETCH样式在调整按钮大小时保留下拉箭头的比例。

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>C按钮：：设置状态

设置按钮控件是否突出显示。

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>参数

*b 高光*<br/>
指定按钮是否突出显示。 非零值突出显示按钮;非零值突出显示按钮。0 值删除任何突出显示。

### <a name="remarks"></a>备注

突出显示会影响按钮控件的外部。 它对单选按钮或复选框的复选框的复选框没有影响。

当用户单击并持有鼠标左键时，按钮控件会自动突出显示。 当用户释放鼠标按钮时，将删除突出显示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>C按钮：：设置文本边缘

调用此方法以设置`CButton`对象的文本边距。

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>参数

*pmargin*<br/>
指向新文本边距的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟BCM_SETTEXTMARGIN消息的功能，如 Windows SDK 的["按钮"](/windows/win32/controls/buttons)部分所述。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CBitmap按钮类](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
