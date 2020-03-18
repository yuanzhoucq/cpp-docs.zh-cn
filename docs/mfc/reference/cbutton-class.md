---
title: CButton 类
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
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424571"
---
# <a name="cbutton-class"></a>CButton 类

提供 Windows 按钮控件功能。

## <a name="syntax"></a>语法

```
class CButton : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CButton：： CButton](#cbutton)|构造 `CButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CButton：： Create](#create)|创建 Windows 按钮控件并将其附加到 `CButton` 对象上。|
|[CButton：:D rawItem](#drawitem)|重写以绘制所有者描述的 `CButton` 对象。|
|[CButton：： GetBitmap](#getbitmap)|检索之前通过[SetBitmap](#setbitmap)设置的位图的句柄。|
|[CButton：： GetButtonStyle](#getbuttonstyle)|检索有关按钮控件样式的信息。|
|[CButton：： GetCheck](#getcheck)|检索按钮控件的检查状态。|
|[CButton：： GetCursor](#getcursor)|检索之前通过[SetCursor](#setcursor)设置的游标图像的句柄。|
|[CButton：： GetIcon](#geticon)|检索之前通过[SetIcon](#seticon)设置的图标的句柄。|
|[CButton：： GetIdealSize](#getidealsize)|检索按钮控件的理想大小。|
|[CButton：： GetImageList](#getimagelist)|检索按钮控件的图像列表。|
|[CButton：： GetNote](#getnote)|检索当前命令链接控件的便笺组件。|
|[CButton：： GetNoteLength](#getnotelength)|检索当前命令链接控件的注释文本的长度。|
|[CButton：： GetSplitGlyph](#getsplitglyph)|检索与当前拆分按钮控件关联的标志符号。|
|[CButton：： GetSplitImageList](#getsplitimagelist)|检索当前拆分按钮控件的图像列表。|
|[CButton：： GetSplitInfo](#getsplitinfo)|检索定义当前拆分按钮控件的信息。|
|[CButton：： GetSplitSize](#getsplitsize)|检索当前拆分按钮控件的下拉组件的边框。|
|[CButton：： GetSplitStyle](#getsplitstyle)|检索用于定义当前拆分按钮控件的拆分按钮样式。|
|[CButton：： GetState](#getstate)|检索按钮控件的检查状态、突出显示状态和焦点状态。|
|[CButton：： GetTextMargin](#gettextmargin)|检索按钮控件的文本边距。|
|[CButton：： SetBitmap](#setbitmap)|指定要在按钮上显示的位图。|
|[CButton：： SetButtonStyle](#setbuttonstyle)|更改按钮的样式。|
|[CButton：： SetCheck](#setcheck)|设置按钮控件的检查状态。|
|[CButton：： SetCursor](#setcursor)|指定要在按钮上显示的光标图像。|
|[CButton：： SetDropDownState](#setdropdownstate)|设置当前拆分按钮控件的下拉状态。|
|[CButton：： SetIcon](#seticon)|指定要在按钮上显示的图标。|
|[CButton：： SetImageList](#setimagelist)|设置按钮控件的图像列表。|
|[CButton：： SetNote](#setnote)|在当前命令链接控件上设置注释。|
|[CButton：： SetSplitGlyph](#setsplitglyph)|将指定的标志符号与当前拆分按钮控件相关联。|
|[CButton：： SetSplitImageList](#setsplitimagelist)|将图像列表与当前拆分按钮控件相关联。|
|[CButton：： SetSplitInfo](#setsplitinfo)|指定用于定义当前拆分按钮控件的信息。|
|[CButton：： SetSplitSize](#setsplitsize)|设置当前拆分按钮控件的下拉组件的边框。|
|[CButton：： SetSplitStyle](#setsplitstyle)|设置当前拆分按钮控件的样式。|
|[CButton：： SetState](#setstate)|设置按钮控件的突出显示状态。|
|[CButton：： SetTextMargin](#settextmargin)|设置按钮控件的边距。|

## <a name="remarks"></a>备注

按钮控件是一个可单击和关闭的小矩形子窗口。 按钮可以单独使用，也可以在组中使用，也可以标记或显示而不显示文本。 当用户单击按钮时，该按钮通常会改变外观。

典型的按钮包括复选框、单选按钮和按钮。 根据[Create](#create) member 函数在其初始化中指定的[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)，`CButton` 对象可以成为上述任意对象。

此外，派生自 `CButton` 的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)类支持创建用位图图像而不是文本标记的按钮控件。 `CBitmapButton` 可以为按钮的上、下、聚焦和禁用状态使用单独的位图。

你可以从对话框模板或直接在代码中创建按钮控件。 在这两种情况下，首先调用构造函数 `CButton` 来构造 `CButton` 对象;然后调用 `Create` 成员函数以创建 Windows 按钮控件并将其附加到 `CButton` 对象。

构造可以是派生自 `CButton`的类中的一个单步过程。 写入派生类的构造函数，并从构造函数内调用 `Create`。

如果要处理按钮控件发送给其父项的 Windows 通知消息（通常是派生自[CDialog](../../mfc/reference/cdialog-class.md)的类），请将消息映射项和消息处理程序成员函数添加到每条消息的父类。

每个消息映射项都采用以下形式：

**\_** _通知_ **（** _id_， _memberFxn_ **）**

其中， *id*指定发送通知的控件的子窗口 Id， *memberFxn*是您已编写的用于处理通知的父成员函数的名称。

父的函数原型如下所示：

`afx_msg void memberFxn();`

潜在的消息映射条目如下所示：

|映射条目|发送到父项的时间 。|
|---------------|----------------------------|
|ON_BN_CLICKED|用户单击按钮。|
|ON_BN_DOUBLECLICKED|用户双击某个按钮。|

如果从对话框资源创建 `CButton` 对象，则当用户关闭对话框时，`CButton` 对象将自动销毁。

如果在窗口中创建 `CButton` 对象，可能需要销毁它。 如果使用**new**函数在堆上创建 `CButton` 对象，则必须对对象调用**delete** ，以便在用户关闭 Windows 按钮控件时销毁该对象。 如果在堆栈上创建 `CButton` 对象，或将其嵌入父对话框对象中，则它会自动销毁。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cbutton"></a>CButton：： CButton

构造 `CButton` 对象。

```
CButton();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>CButton：： Create

创建 Windows 按钮控件并将其附加到 `CButton` 对象上。

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*lpszCaption*<br/>
指定按钮控件的文本。

*dwStyle*<br/>
指定按钮控件的样式。 将任意[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)组合应用于按钮。

*rect*<br/>
指定按钮控件的大小和位置。 它可以是 `CRect` 对象或 `RECT` 结构。

*pParentWnd*<br/>
指定按钮控件的父窗口，通常为 `CDialog`。 值不得为 NULL。

*nID*<br/>
指定按钮控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过两个步骤构造一个 `CButton` 对象。 首先，调用构造函数，然后调用 `Create`，这将创建 Windows 按钮控件并将其附加到 `CButton` 对象。

如果提供了 WS_VISIBLE 样式，则 Windows 将发送 "按钮" 控制激活和显示按钮所需的所有消息。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于 button 控件：

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

- WS_GROUP 分组控件

- WS_TABSTOP 以按 tab 键顺序包含按钮

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>CButton：:D rawItem

当所有者描述的按钮的视觉方面发生更改时由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>parameters

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针。 结构包含有关要绘制的项的信息以及所需的绘图类型。

### <a name="remarks"></a>备注

所有者描述的按钮具有 BS_OWNERDRAW 样式集。 重写此成员函数以实现所有者描述的 `CButton` 对象的绘制。 在成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

另请参阅[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)样式值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>CButton：： GetBitmap

调用此成员函数以获取与按钮关联的、以前设置了[SetBitmap](#setbitmap)的位图的句柄。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>返回值

位图的句柄。 如果以前未指定位图，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>CButton：： GetButtonStyle

检索有关按钮控件样式的信息。

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>返回值

返回此 `CButton` 对象的按钮样式。 此函数只返回[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)的样式值，而不是任何其他窗口样式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>CButton：： GetCheck

检索单选按钮或复选框的复选状态。

```
int GetCheck() const;
```

### <a name="return-value"></a>返回值

使用 "BS_AUTOCHECKBOX"、"BS_AUTORADIOBUTTON"、"BS_AUTO3STATE"、"BS_CHECKBOX"、"BS_RADIOBUTTON" 或 "BS_3STATE" 样式创建的 "按钮" 控件的返回值为下列值之一：

|值|含义|
|-----------|-------------|
|BST_UNCHECKED|按钮状态处于未选中状态。|
|BST_CHECKED|按钮状态处于选中状态。|
|BST_INDETERMINATE|按钮状态为 "不确定" （仅当按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式时才适用）。|

如果该按钮具有任何其他样式，则返回值为 BST_UNCHECKED。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>CButton：： GetCursor

调用此成员函数以获取与按钮关联的、以前设置了[SetCursor](#setcursor)的游标句柄。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>返回值

游标图像的句柄。 如果以前未指定游标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>CButton：： GetIcon

调用此成员函数以获取与按钮关联的、以前设置了[SetIcon](#seticon)的图标的句柄。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>返回值

图标的图柄。 如果以前未指定图标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>CButton：： GetIdealSize

检索按钮控件的理想大小。

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>parameters

*psize*<br/>
指向按钮当前大小的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟 BCM_GETIDEALSIZE 消息的功能，如 Windows SDK 的 "[按钮](/windows/win32/controls/buttons)" 一节中所述。

##  <a name="getimagelist"></a>CButton：： GetImageList

调用此方法可从 button 控件获取图像列表。

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>parameters

*pbuttonImagelist*<br/>
指向 `CButton` 对象的图像列表的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟 BCM_GETIMAGELIST 消息的功能，如 Windows SDK 的 "[按钮](/windows/win32/controls/buttons)" 一节中所述。

##  <a name="getnote"></a>CButton：： GetNote

检索与当前命令链接控件关联的注释文本。

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*lpszNote*|弄指向缓冲区的指针，调用方负责分配和解除分配。 如果返回值为 TRUE，则缓冲区包含与当前命令链接控件关联的注释文本;否则，缓冲区将保持不变。|
|*cchNote*|[in，out]指向无符号整数变量的指针。<br /><br /> 调用此方法时，变量包含由*lpszNote*参数指定的缓冲区大小。<br /><br /> 此方法返回时，如果返回值为 TRUE，则变量包含与当前命令链接控件关联的便笺的大小。 如果返回值为 FALSE，则该变量包含包含该注释所需的缓冲区大小。|

### <a name="return-value"></a>返回值

第一个重载中的[CString](../../atl-mfc-shared/using-cstring.md)对象，该对象包含与当前命令链接控件关联的注释文本。

-或-

在第二个重载中，如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控件。

此方法发送 Windows SDK 中描述的[BCM_GETNOTE](/windows/win32/Controls/bcm-getnote)消息。

##  <a name="getnotelength"></a>CButton：： GetNoteLength

检索当前命令链接控件的注释文本的长度。

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>返回值

当前命令链接控件的注释文本长度（16位 Unicode 字符）。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控件。

此方法发送 Windows SDK 中描述的[BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength)消息。

##  <a name="getsplitglyph"></a>CButton：： GetSplitGlyph

检索与当前拆分按钮控件关联的标志符号。

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>返回值

与当前拆分按钮控件关联的标志符号字符。

### <a name="remarks"></a>备注

标志符号是特定字体中的字符的物理表示形式。 例如，拆分按钮控件可能使用 Unicode 检查标记字符（U + 2713）的标志符号修饰。

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

此方法使用 BCSIF_GLYPH 标志初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法将从结构的 `himlGlyph` 成员中检索该标志符号。

##  <a name="getsplitimagelist"></a>CButton：： GetSplitImageList

检索当前拆分按钮控件的[图像列表](../../mfc/reference/cimagelist-class.md)。

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

此方法使用 BCSIF_IMAGE 标志初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法将从结构的 `himlGlyph` 成员检索图像列表。

##  <a name="getsplitinfo"></a>CButton：： GetSplitInfo

检索参数，这些参数确定 Windows 如何绘制当前拆分按钮控件。

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pInfo*|弄指向[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的指针，该结构接收当前拆分按钮控件的相关信息。 调用方负责分配结构。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

此方法发送 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息。

##  <a name="getsplitsize"></a>CButton：： GetSplitSize

检索当前拆分按钮控件的下拉组件的边框。

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pSize*|弄指向接收矩形说明的[大小](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

展开拆分按钮控件后，它可以显示一个下拉组件，如列表控件或页导航控件。 此方法检索包含下拉组件的边框。

此方法使用 BCSIF_SIZE 标志初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法将从结构的 `size` 成员检索边框。

##  <a name="getsplitstyle"></a>CButton：： GetSplitStyle

检索用于定义当前拆分按钮控件的拆分按钮样式。

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>返回值

拆分按钮样式的按位组合。 有关详细信息，请参阅[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `uSplitStyle` 成员。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

拆分按钮样式指定 Windows 用于绘制拆分按钮图标的对齐方式、纵横比和图形格式。

此方法使用 BCSIF_STYLE 标志初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。 当消息函数返回时，此方法将检索结构的 `uSplitStyle` 成员的拆分按钮样式。

##  <a name="getstate"></a>CButton：： GetState

检索按钮控件的状态。

```
UINT GetState() const;
```

### <a name="return-value"></a>返回值

一个位域，其中包含指示按钮控件的当前状态的值的组合。 下表列出了可能的值。

|按钮状态|值|说明|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|初始状态。|
|BST_CHECKED|0x0001|按钮控件处于选中状态。|
|BST_INDETERMINATE|0x0002|状态为 "不确定" （仅当按钮控件具有三种状态时可能）。|
|BST_PUSHED|0x0004|按钮控件处于按下状态。|
|BST_FOCUS|0x0008|按钮控件具有焦点。|

### <a name="remarks"></a>备注

具有 "BS_3STATE" 或 "BS_AUTO3STATE" 按钮样式的按钮控件创建一个具有第三个状态的复选框，该状态为 "不确定" 状态。 "不确定" 状态指示复选框既未选中也未取消选中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>CButton：： GetTextMargin

调用此方法可获取 `CButton` 对象的文本边距。

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>parameters

*pmargin*<br/>
指向 `CButton` 对象的文本边距的指针。

### <a name="return-value"></a>返回值

返回文本的边距。

### <a name="remarks"></a>备注

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数模拟 BCM_GETTEXTMARGIN 消息的功能，如 Windows SDK 的 "[按钮](/windows/win32/controls/buttons)" 一节中所述。

##  <a name="setbitmap"></a>CButton：： SetBitmap

调用此成员函数以将新位图与按钮相关联。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>parameters

*hBitmap*<br/>
位图的句柄。

### <a name="return-value"></a>返回值

先前与按钮关联的位图的句柄。

### <a name="remarks"></a>备注

该位图将自动置于按钮的图符上，默认居中。 如果位图对于按钮而言太大，则会将其剪裁到两侧。 您可以选择其他对齐选项，其中包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于使用每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，`SetBitmap` 每个按钮只使用一个位图。 按下该按钮时，将显示位图向下移动并向右移动。

完成后，你将负责释放位图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>CButton：： SetButtonStyle

更改按钮的样式。

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>parameters

*nStyle*<br/>
指定[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

*bRedraw*<br/>
指定是否要重新绘制该按钮。 非零值将重绘按钮。 0值不会重绘按钮。 默认情况下，此按钮将被重绘。

### <a name="remarks"></a>备注

使用 `GetButtonStyle` 成员函数检索按钮样式。 "完成" 按钮样式的低序位字是按钮特定样式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>CButton：： SetCheck

设置或重置单选按钮或复选框的复选状态。

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>parameters

*n*<br/>
指定复选状态。 此参数可以是以下项之一：

|值|含义|
|-----------|-------------|
|BST_UNCHECKED|将按钮状态设置为 "未选中"。|
|BST_CHECKED|将按钮状态设置为 "已选中"。|
|BST_INDETERMINATE|将按钮状态设置为 "不确定"。 仅当按钮具有 BS_3STATE 或 BS_AUTO3STATE 样式时，才可以使用此值。|

### <a name="remarks"></a>备注

此成员函数对按钮不起作用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>CButton：： SetCursor

调用此成员函数以将新的光标与按钮相关联。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>parameters

*hCursor*<br/>
游标的句柄。

### <a name="return-value"></a>返回值

先前与按钮关联的游标的句柄。

### <a name="remarks"></a>备注

光标将自动置于按钮的图符上，默认居中。 如果该按钮的光标太大，则会将其剪裁到两侧。 您可以选择其他对齐选项，其中包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于使用每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，`SetCursor` 每个按钮只使用一个游标。 按下该按钮时，光标将向下移动并向右移动。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>CButton：： SetDropDownState

设置当前拆分按钮控件的下拉状态。

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*fDropDown*|中若要设置 BST_DROPDOWNPUSHED 状态，则为 TRUE;否则为 FALSE。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

拆分按钮控件的样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON，由按钮和下拉箭头组成。 有关详细信息，请参阅[按钮样式](/windows/win32/Controls/button-styles)。 通常，当用户单击下拉箭头时，将设置下拉状态。 使用此方法以编程方式设置控件的下拉状态。 下拉箭头绘制为灰色，以指示状态。

此方法发送 Windows SDK 中描述的[BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问拆分按钮控件的变量*m_splitButton*。 下面的示例中使用了此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

下面的代码示例设置拆分按钮控件的状态，以指示按下下拉箭头。

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>CButton：： SetElevationRequired

将当前按钮控件的状态设置为 `elevation required`，控件在显示提升的安全图标时，这是必需的。

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*fElevationRequired*|中若要设置 `elevation required` 状态，则为 TRUE;否则为 FALSE。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果按钮或命令链接控件需要提升的安全权限才能执行某一操作，请将该控件设置为 `elevation required` 状态。 然后，Windows 将在控件上显示用户帐户控制（UAC）盾牌图标。 有关详细信息，请参阅[MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507)上的 "用户帐户控制"。

此方法发送 Windows SDK 中描述的[BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield)消息。

##  <a name="seticon"></a>CButton：： SetIcon

调用此成员函数以将新图标与按钮相关联。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>parameters

*hIcon*<br/>
图标的句柄。

### <a name="return-value"></a>返回值

先前与按钮关联的图标的句柄。

### <a name="remarks"></a>备注

该图标将自动置于按钮的图符上，默认居中。 如果此图标对于按钮而言太大，则会将其剪裁到两侧。 您可以选择其他对齐选项，其中包括：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于使用每个按钮使用四个位图的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)，`SetIcon` 每个按钮只使用一个图标。 按下该按钮时，图标会显示向下和向下移动。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>CButton：： SetImageList

调用此方法以设置 `CButton` 对象的图像列表。

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>parameters

*pbuttonImagelist*<br/>
指向新图像列表的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟 BCM_SETIMAGELIST 消息的功能，如 Windows SDK 的 "[按钮](/windows/win32/controls/buttons)" 一节中所述。

##  <a name="setnote"></a>CButton：： SetNote

设置当前命令链接控件的注释文本。

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*lpszNote*|中指向设置为命令链接控件的注释文本的 Unicode 字符串的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控件。

此方法发送 Windows SDK 中描述的[BCM_SETNOTE](/windows/win32/Controls/bcm-setnote)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问命令链接控件的变量*m_cmdLink*。 下面的示例中使用了此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

下面的代码示例设置命令链接控件的注释文本。

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>CButton：： SetSplitGlyph

将指定的标志符号与当前拆分按钮控件相关联。

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*chGlyph*|中一个字符，指定用作拆分按钮下拉箭头的标志符号。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

标志符号是特定字体中的字符的物理表示形式。 *ChGlyph*参数不用作标志符号，而是用于从一组系统定义的标志符号中选择一个标志符号。 默认的下拉箭头标志符号由字符 "6" 指定，类似于 Unicode 字符黑色下指三角形（U + 25BC）。

此方法使用带有*chGlyph*参数的 BCSIF_GLYPH 标志和 `himlGlyph` 成员初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 BCM_GETSPLITINFO 中描述的[Windows SDK](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

##  <a name="setsplitimagelist"></a>CButton：： SetSplitImageList

将[图像列表](../../mfc/reference/cimagelist-class.md)与当前拆分按钮控件相关联。

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pSplitImageList*|中指向要分配给当前拆分按钮控件的[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

此方法使用带有*pSplitImageList*参数的 BCSIF_IMAGE 标志和 `himlGlyph` 成员初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 BCM_GETSPLITINFO 中描述的[Windows SDK](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

##  <a name="setsplitinfo"></a>CButton：： SetSplitInfo

指定一些参数，这些参数确定 Windows 如何绘制当前拆分按钮控件。

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pInfo*|中指向定义当前拆分按钮控件的[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

此方法发送 Windows SDK 中描述的[BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问拆分按钮控件的变量 `m_splitButton`。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

下面的代码示例更改用于拆分按钮下拉箭头的标志符号。 该示例为默认的向下三角标志符号替换一个上指三角标志符号。 显示的标志符号取决于你在 `BUTTON_SPLITINFO` 结构的 `himlGlyph` 成员中指定的字符。 下指的三角形标志符号由字符 "6" 指定，向上的三角形标志符号由字符 "5" 指定。 若要进行比较，请参阅便捷方法[CButton：： SetSplitGlyph](#setsplitglyph)。

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>CButton：： SetSplitSize

设置当前拆分按钮控件的下拉组件的边框。

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pSize*|中指向描述边框的[大小](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

展开拆分按钮控件后，它可以显示一个下拉组件，如列表控件或页导航控件。 此方法指定包含下拉组件的边框的大小。

此方法使用带有*pSize*参数的 BCSIF_SIZE 标志和 `size` 成员初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 BCM_GETSPLITINFO 中描述的[Windows SDK](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问拆分按钮控件的变量 `m_splitButton`。 下面的示例中使用了此变量。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

下面的代码示例将拆分按钮下拉箭头的大小增加一倍。

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>CButton：： SetSplitStyle

设置当前拆分按钮控件的样式。

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*uSplitStyle*|中拆分按钮样式的按位组合。 有关详细信息，请参阅[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `uSplitStyle` 成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅将此方法用于按钮样式为 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控件。

拆分按钮样式指定 Windows 用于绘制拆分按钮图标的对齐方式、纵横比和图形格式。 有关详细信息，请参阅[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `uSplitStyle` 成员。

此方法使用带有*uSplitStyle*参数的 BCSIF_STYLE 标志和 `uSplitStyle` 成员初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)结构的 `mask` 成员，然后在 BCM_GETSPLITINFO 中描述的[Windows SDK](/windows/win32/Controls/bcm-getsplitinfo)消息中发送该结构。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问拆分按钮控件的变量 `m_splitButton`。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>示例

下面的代码示例设置拆分按钮下拉箭头的样式。 "BCSS_ALIGNLEFT" 样式显示按钮左侧的箭头，BCSS_STRETCH 样式在调整按钮大小时保留下拉箭头的比例。

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>CButton：： SetState

设置按钮控件是否突出显示。

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>parameters

*bHighlight*<br/>
指定是否突出显示该按钮。 非零值突出显示按钮;0值会删除任何突出显示。

### <a name="remarks"></a>备注

突出显示会影响按钮控件的外部。 它不会影响单选按钮或复选框的复选状态。

当用户单击并按住鼠标左键时，将自动突出显示按钮控件。 当用户释放鼠标按钮时，将移除突出显示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>CButton：： SetTextMargin

调用此方法以设置 `CButton` 对象的文本边距。

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>parameters

*pmargin*<br/>
指向新文本边距的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟 BCM_SETTEXTMARGIN 消息的功能，如 Windows SDK 的 "[按钮](/windows/win32/controls/buttons)" 一节中所述。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton 类](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
