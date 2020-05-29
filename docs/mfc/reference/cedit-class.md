---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 94769a6fb3c5fceefda96b54cebb35b0533a8afa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753217"
---
# <a name="cedit-class"></a>CEdit Class

提供 Windows 编辑控件功能。

## <a name="syntax"></a>语法

```
class CEdit : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[编辑：编辑](#cedit)|构造`CEdit`控件对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[编辑：：CanUndo](#canundo)|确定是否可以撤消编辑控制操作。|
|[编辑：：查里波斯](#charfrompos)|检索最接近指定位置的字符的行和字符索引。|
|[编辑：清除](#clear)|删除（清除）编辑控件中的当前选择（如果有）。|
|[编辑：：复制](#copy)|以CF_TEXT格式将编辑控件中的当前选择（如果有）复制到剪贴板。|
|[编辑：：创建](#create)|创建 Windows 编辑控件并将其附加到`CEdit`对象。|
|[编辑：：切割](#cut)|删除（剪切）编辑控件中的当前选择（如果有），并将删除的文本以CF_TEXT格式复制到剪贴板。|
|[编辑：：空UndoBuffer](#emptyundobuffer)|重置（清除）编辑控件的撤消标志。|
|[编辑：：Fmtlines](#fmtlines)|设置多行编辑控件中软换行字符的包含。|
|[编辑：：GetCueBanner](#getcuebanner)|当控件为空且没有焦点时，检索在编辑控件中显示为文本提示或提示的文本。|
|[编辑：获取第一可见线](#getfirstvisibleline)|确定编辑控件中最上面可见的行。|
|[编辑：：获取手柄](#gethandle)|检索当前为多行编辑控件分配的内存的句柄。|
|[编辑：获取高光](#gethighlight)|获取当前编辑控件中突出显示的文本范围内的起始字符和结束字符的索引。|
|[编辑：：获取限制文本](#getlimittext)|获取可以`CEdit`包含的最大文本量。|
|[编辑：获取线](#getline)|从编辑控件检索一行文本。|
|[编辑：：获取线计数](#getlinecount)|检索多行编辑控件中的行数。|
|[编辑：：获取边缘](#getmargins)|获取此`CEdit`的左右边距。|
|[编辑：：获取修改](#getmodify)|确定编辑控件的内容是否已修改。|
|[编辑：：获取密码字符](#getpasswordchar)|当用户输入文本时，检索编辑控件中显示的密码字符。|
|[编辑：：获取 Rect](#getrect)|获取编辑控件的格式矩形。|
|[编辑：：GetSel](#getsel)|在编辑控件中获取当前所选内容的第一个和最后一个字符位置。|
|[编辑：：隐藏气球提示](#hideballoontip)|隐藏与当前编辑控件关联的任何气球提示。|
|[编辑：：限制文本](#limittext)|限制用户可以在编辑控件中输入的文本长度。|
|[编辑：：线从查尔](#linefromchar)|检索包含指定字符索引的行号的行号。|
|[编辑：线索引](#lineindex)|检索多行编辑控件中的行的字符索引。|
|[编辑：线长](#linelength)|检索编辑控件中的行的长度。|
|[编辑：：线滚动](#linescroll)|滚动多行编辑控件的文本。|
|[编辑：:Paste](#paste)|将剪辑板中的数据插入到当前光标位置的编辑控件中。 仅当剪贴板以CF_TEXT格式包含数据时，才会插入数据。|
|[编辑：:P从查尔](#posfromchar)|检索指定字符索引左上角的坐标。|
|[编辑：：替换塞尔](#replacesel)|将编辑控件中的当前选择替换为指定的文本。|
|[编辑：：设置库班](#setcuebanner)|设置当控件为空且没有焦点时，在编辑控件中显示为文本提示或提示的文本。|
|[编辑：：设置手](#sethandle)|将句柄设置到多行编辑控件将使用的本地内存。|
|[编辑：设置高光](#sethighlight)|突出显示当前编辑控件中显示的文本范围。|
|[编辑：：设置限制文本](#setlimittext)|设置可以`CEdit`包含的最大文本量。|
|[编辑：：设置边距](#setmargins)|为此设置左右边距`CEdit`。|
|[编辑：：设置修改](#setmodify)|设置或清除编辑控件的修改标志。|
|[编辑：：设置密码字符](#setpasswordchar)|设置或删除用户输入文本时在编辑控件中显示的密码字符。|
|[编辑：仅设置 Read](#setreadonly)|设置编辑控件的只读状态。|
|[编辑：：设置重新](#setrect)|设置多行编辑控件的格式矩形并更新该控件。|
|[编辑：：设置RectNP](#setrectnp)|设置多行编辑控件的格式矩形，而无需重新绘制控件窗口。|
|[编辑：：SetSel](#setsel)|在编辑控件中选择一系列字符。|
|[编辑：：设置标签](#settabstops)|在多行编辑控件中设置制表符停止。|
|[编辑：：显示气球提示](#showballoontip)|显示与当前编辑控件关联的气球提示。|
|[编辑：撤消](#undo)|反转上次编辑控制操作。|

## <a name="remarks"></a>备注

编辑控件是一个矩形子窗口，用户可以在其中输入文本。

可以从对话框模板或直接在代码中创建编辑控件。 在这两种情况下，首先调用构造`CEdit`函数构造`CEdit`对象，然后调用[Create](#create)成员函数以创建 Windows 编辑控件并将其附加到`CEdit`对象。

构造可以是派生自`CEdit`的类中的一个步骤。 为派生类编写一个构造函数，并从`Create`构造函数内部调用。

`CEdit`从 继承重要功能`CWnd`。 若要从`CEdit`对象设置和检索文本，请使用`CWnd`成员函数[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，它们设置或获取编辑控件的全部内容，即使它是多行控件。 多行控件中的文本行由"\r\n"字符序列分隔。 此外，如果编辑控件是多行的，则通过`CEdit`调用成员函数[GetLine、SetSel、GetSel](#getline)和[ReplaceSel](#replacesel)获取[GetSel](#getsel)和设置控件文本的一部分。 [SetSel](#setsel)

如果要处理由编辑控件发送到其父级（通常是派生自`CDialog`的类）的 Windows 通知消息，请为每个消息向父类添加消息映射条目和消息处理程序成员函数。

每个消息映射条目采用以下形式：

  **ON_**_通知_**（ID** _id_**，** _成员Fxn_ **）**

其中`id`指定发送通知的编辑控件的子窗口 ID，以及`memberFxn`您为处理通知而编写的父成员函数的名称。

父函数原型如下所示：

**afx_msg**无效成员Fxn **（ ;**

以下是潜在消息映射条目的列表，以及将它们发送到父项的情况说明：

- ON_EN_CHANGE用户已执行的操作可能更改了编辑控件中的文本。 与EN_UPDATE通知消息不同，此通知消息是在 Windows 更新显示后发送的。

- ON_EN_ERRSPACE 编辑控件无法分配足够的内存以满足特定请求。

- ON_EN_HSCROLL用户单击编辑控件的水平滚动条。 在更新屏幕之前，将通知父窗口。

- ON_EN_KILLFOCUS 编辑控件失去输入焦点。

- ON_EN_MAXTEXT当前插入已超过编辑控件的指定字符数，并且已被截断。 当编辑控件没有ES_AUTOHSCROLL样式且要插入的字符数超过编辑控件的宽度时，也会发送。 当编辑控件没有ES_AUTOVSCROLL样式，并且文本插入产生的行总数将超过编辑控件的高度时，也会发送。

- ON_EN_SETFOCUS编辑控件接收输入焦点时已发送。

- ON_EN_UPDATE 编辑控件即将显示更改的文本。 控件在控件格式化文本后发送，但在它筛选文本之前，以便在必要时可以更改窗口大小。

- ON_EN_VSCROLL用户单击编辑控件的垂直滚动条。 在更新屏幕之前，将通知父窗口。

如果在对话框中创建`CEdit`对象，则当用户关闭对话框时`CEdit`，该对象将自动销毁。

如果使用对话框编辑器从`CEdit`对话框资源创建对象，则当用户关闭对话框时，`CEdit`该对象将自动销毁。

如果在窗口中创建`CEdit`对象，则可能需要销毁它。 如果在堆栈上`CEdit`创建对象，则会自动销毁该对象。 如果使用**新**函数在`CEdit`堆上创建对象，**则必须调用删除**对象以在用户终止 Windows 编辑控件时销毁该对象。 如果在`CEdit`对象中分配任何内存，请重写`CEdit`析构函数以释放分配。

要修改编辑控件中的某些样式（如ES_READONLY），必须向控件发送特定消息，而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 请参阅 Windows SDK 中的[编辑控件样式](/windows/win32/Controls/edit-control-styles)。

有关 的详细信息`CEdit`，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>编辑：：CanUndo

调用此函数以确定是否可以撤消最后一个编辑操作。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>返回值

如果最后一个编辑操作可以通过调用`Undo`成员函数撤消，则非零;0，如果它不能撤消。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_CANUNDO。](/windows/win32/Controls/em-canundo)

### <a name="example"></a>示例

  请参阅[CEdit：：撤消的示例](#undo)。

## <a name="ceditcedit"></a><a name="cedit"></a>编辑：编辑

构造 `CEdit` 对象。

```
CEdit();
```

### <a name="remarks"></a>备注

使用["创建](#create)"构造 Windows 编辑控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>编辑：：查里波斯

调用此函数以检索离此`CEdit`控件中指定点的字符的零基线和字符索引

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
此`CEdit`对象工作区中点的坐标。

### <a name="return-value"></a>返回值

低阶 WORD 中的字符索引和高阶 WORD 中的线索引。

### <a name="remarks"></a>备注

> [!NOTE]
> 此成员功能从 Windows 95 和 Windows NT 4.0 开始可用。

有关详细信息，请参阅 Windows SDK 中的[EM_CHARFROMPOS。](/windows/win32/Controls/em-charfrompos)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>编辑：清除

调用此函数以删除（清除）编辑控件中的当前选择（如果有）。

```cpp
void Clear();
```

### <a name="remarks"></a>备注

可以通过调用[撤消](#undo)成员`Clear`函数撤消执行的删除。

要删除当前选择并将已删除的内容放入剪贴板，请调用["剪切](#cut)"成员函数。

有关详细信息，请参阅 Windows SDK 中的[WM_CLEAR。](/windows/win32/dataxchg/wm-clear)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>编辑：：复制

调用此函数以CF_TEXT格式将编辑控件中的当前选择（如果有）与剪贴板进行配合。

```cpp
void Copy();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[WM_COPY。](/windows/win32/dataxchg/wm-copy)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>编辑：：创建

创建 Windows 编辑控件并将其附加到`CEdit`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定编辑控件的样式。 将[编辑样式](styles-used-by-mfc.md#edit-styles)的任意组合应用于控件。

*矩形*<br/>
指定编辑控件的大小和位置。 可以是`CRect`对象或`RECT`结构。

*pparentwnd*<br/>
指定编辑控件的父窗口（通常为 。 `CDialog` 值不得为 NULL。

*nID*<br/>
指定编辑控件的 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

分两步`CEdit`构造对象。 首先调用`CEdit`构造函数，然后调用`Create`，这将创建 Windows 编辑控件并将其附加到`CEdit`对象。

执行`Create`时，Windows 会将[WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)WM_NCCREATE、WM_NCCALCSIZE、WM_CREATE 和[WM_GETMINMAXINFO消息发送到](/windows/win32/winmsg/wm-getminmaxinfo)编辑控件。 [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize) [WM_CREATE](/windows/win32/winmsg/wm-create)

默认情况下，这些消息由`CWnd`基类中的[OnNcCreate、OnNcCalcsize、OnCreate](cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成员函数处理。 [OnNcCalcSize](cwnd-class.md#onnccalcsize) [OnCreate](cwnd-class.md#oncreate) 要扩展默认消息处理，从`CEdit`派生类，向新类添加消息映射，并重写上述消息处理程序成员函数。 例如`OnCreate`，重写以执行新类所需的初始化。

将以下[窗口样式](styles-used-by-mfc.md#window-styles)应用于编辑控件。

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP组控件

- WS_TABSTOP在制表顺序中包括编辑控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>编辑：：切割

调用此函数以删除（剪切）编辑控件中的当前选择（如果有），并将删除的文本以CF_TEXT格式复制到剪贴板。

```cpp
void Cut();
```

### <a name="remarks"></a>备注

可以通过调用[撤消](#undo)成员`Cut`函数撤消执行的删除。

要删除当前选择而不将删除的文本放入剪贴板，请调用["清除](#clear)"成员函数。

有关详细信息，请参阅 Windows SDK 中的[WM_CUT。](/windows/win32/dataxchg/wm-cut)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>编辑：：空UndoBuffer

调用此函数以重置（清除）编辑控件的撤消标志。

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>备注

编辑控件现在将无法撤消最后一个操作。 每当可以撤消编辑控件中的操作时，都会设置撤消标志。

每当调用[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle)`CWnd`成员函数时，将自动清除撤消标志。

有关详细信息，请参阅 Windows SDK 中的[EM_EMPTYUNDOBUFFER。](/windows/win32/Controls/em-emptyundobuffer)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>编辑：：Fmtlines

调用此函数可设置在多行编辑控件中包含软换行字符。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>参数

*bAddEOL*<br/>
指定是否要插入软换行符。 TRUE 的值插入字符;如果 "TRUE"值插入字符。FALSE 的值删除它们。

### <a name="return-value"></a>返回值

如果发生任何格式，则非零;否则 0。

### <a name="remarks"></a>备注

软换行符由两个回车和插入行尾的换行符组成，该换行由于文字包装而断开。 硬线中断由一个回车和一条换行件组成。 以硬线中断结尾的行不受 的影响`FmtLines`。

仅当对象是多行编辑`CEdit`控件时，Windows 才会响应。

`FmtLines`仅影响[GetHandle](#gethandle)返回的缓冲区和[WM_GETTEXT](/windows/win32/winmsg/wm-gettext)返回的文本。 它不会影响编辑控件中文本的显示。

有关详细信息，请参阅 Windows SDK 中的[EM_FMTLINES。](/windows/win32/Controls/em-fmtlines)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>编辑：：GetCueBanner

检索当控件为空时，在编辑控件中显示为文本提示或提示的文本。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[出]指向包含提示文本的字符串的指针。

*cchText*<br/>
[在]可以接收的字符数。 此数字包括终止 NULL 字符。

### <a name="return-value"></a>返回值

对于第一个重载，如果方法成功，则为 TRUE;否则 FALSE。

对于第二个重载，如果方法成功，则包含提示文本的[CString;](../../atl-mfc-shared/using-cstring.md)否则，空字符串 （""）。

### <a name="remarks"></a>备注

此方法发送[EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner)消息，这在 Windows SDK 中介绍。 有关详细信息，请参阅[Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)宏。

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>编辑：获取第一可见线

调用此函数以确定编辑控件中最上面可见的行。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>返回值

最上面可见线的零基索引。 对于单行编辑控件，返回值为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_GETFIRSTVISIBLELINE。](/windows/win32/Controls/em-getfirstvisibleline)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>编辑：：获取手柄

调用此函数以检索当前为多行编辑控件分配的内存的句柄。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>返回值

标识保存编辑控件内容的缓冲区的本地内存句柄。 如果发生错误（如将消息发送到单行编辑控件），则返回值为 0。

### <a name="remarks"></a>备注

该句柄是本地内存句柄，可用于任何将本地内存句柄作为参数的**本地**Windows 内存函数。

`GetHandle`仅由多行编辑控件处理。

仅当`GetHandle`对话框使用DS_LOCALEDIT样式标志集创建时，才在对话框中调用多行编辑控件。 如果未设置DS_LOCALEDIT样式，您仍将获得非零返回值，但您将无法使用返回的值。

> [!NOTE]
> `GetHandle`不适用于 Windows 95/98。 如果您在 Windows `GetHandle` 95/98 中调用，它将返回 NULL。 `GetHandle`将工作在 Windows NT，版本 3.51 和更高版本中记录。

有关详细信息，请参阅 windows SDK 中的[EM_GETHANDLE。](/windows/win32/Controls/em-gethandle)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>编辑：获取高光

获取当前编辑控件中突出显示的文本范围内第一个字符和最后一个字符的索引。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pich开始*|[出]突出显示的文本范围内第一个字符的基于零的索引。|
|*pichEnd*|[出]突出显示的文本范围内最后一个字符的基于零的索引。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[EM_GETHILITE](/windows/win32/Controls/em-gethilite)消息，这在 Windows SDK 中介绍。 和`SetHighlight``GetHighlight`当前都只为 UNICODE 生成启用。

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>编辑：：获取限制文本

调用此成员函数以获取此`CEdit`对象的文本限制。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>返回值

此`CEdit`对象的当前文本限制（在 TCHA 中）。

### <a name="remarks"></a>备注

文本限制是编辑控件可以接受的最大文本量（在 TCHA 中）。

> [!NOTE]
> 此成员功能从 Windows 95 和 Windows NT 4.0 开始可用。

有关详细信息，请参阅在 Windows SDK 中的[EM_GETLIMITTEXT。](/windows/win32/Controls/em-getlimittext)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>编辑：获取线

调用此函数从编辑控件检索文本行并将其置于*lpszBuffer*中。

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定要从多行编辑控件检索的行号。 行号为零;值 0 指定第一行。 单行编辑控件将忽略此参数。

*lpszBuffer*<br/>
指向接收行副本的缓冲区。 缓冲区的第一个单词必须指定可复制到缓冲区的最大 TCHAR 数。

*n 最大长度*<br/>
指定可复制到缓冲区的最大 TCHAR 字符数。 `GetLine`在调用 Windows 之前，将此值放在*lpszBuffer*的第一个单词中。

### <a name="return-value"></a>返回值

实际复制的字符数。 如果*nIndex*指定的行号大于编辑控件中的行数，则返回值为 0。

### <a name="remarks"></a>备注

复制的行不包含空终止字符。

有关详细信息，请参阅 windows SDK 中的[EM_GETLINE。](/windows/win32/Controls/em-getline)

### <a name="example"></a>示例

  请参阅[CEdit：：获取线计数的示例](#getlinecount)。

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>编辑：：获取线计数

调用此函数以检索多行编辑控件中的行数。

```
int GetLineCount() const;
```

### <a name="return-value"></a>返回值

包含多行编辑控件中的行数的整数。 如果编辑控件中未输入文本，则返回值为 1。

### <a name="remarks"></a>备注

`GetLineCount`仅由多行编辑控件处理。

有关详细信息，请参阅 Windows SDK 中的[EM_GETLINECOUNT。](/windows/win32/Controls/em-getlinecount)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>编辑：：获取边缘

调用此成员函数以检索此编辑控件的左右边距。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>返回值

低阶 WORD 中左边距的宽度和高阶 WORD 中右边距的宽度。

### <a name="remarks"></a>备注

边距以像素为单位进行测量。

> [!NOTE]
> 此成员功能从 Windows 95 和 Windows NT 4.0 开始可用。

有关详细信息，请参阅 Windows SDK 中的[EM_GETMARGINS。](/windows/win32/Controls/em-getmargins)

### <a name="example"></a>示例

  请参阅[CEditView 的示例：获取编辑Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditgetmodify"></a><a name="getmodify"></a>编辑：：获取修改

调用此函数以确定编辑控件的内容是否已修改。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>返回值

如果编辑控制内容已修改，则非零;0，如果他们保持不变。

### <a name="remarks"></a>备注

Windows 维护一个内部标志，指示编辑控件的内容是否已更改。 首次创建编辑控件时，将清除此标志，也可以通过调用[SetModify](#setmodify)成员函数清除。

有关详细信息，请参阅 Windows SDK 中的[EM_GETMODIFY。](/windows/win32/Controls/em-getmodify)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>编辑：：获取密码字符

调用此函数以检索用户输入文本时在编辑控件中显示的密码字符。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>返回值

指定要显示的字符，而不是用户键入的字符。 如果没有密码字符，则返回值为 NULL。

### <a name="remarks"></a>备注

如果使用ES_PASSWORD样式创建编辑控件，则支持该控件的 DLL 将确定默认密码字符。 清单或[Init 公共控制Ex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)方法确定哪个 DLL 支持编辑控件。 如果用户32.dll支持编辑控件，则默认密码字符为 ASTERISK （'*， U+002A）。 如果 comctl32.dll 版本 6 支持编辑控件，则默认字符为"黑色 CIRCLE"（"*"，U+25CF）。 有关哪些 DLL 和版本支持常见控件的详细信息，请参阅[命令程序版本和通用控件版本](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))。

此方法发送[EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>编辑：：获取 Rect

调用此函数以获取编辑控件的格式矩形。

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向接收格式`RECT`矩形的结构。

### <a name="remarks"></a>备注

格式矩形是文本的限制矩形，与编辑控制窗口的大小无关。

多行编辑控件的格式矩形可以由[SetRect 和 SetRectNP](#setrect)成员函数修改。 [SetRectNP](#setrectnp)

有关详细信息，请参阅 Windows SDK 中的[EM_GETRECT。](/windows/win32/Controls/em-getrect)

### <a name="example"></a>示例

  请参阅[CEdit：：限制文本的示例](#limittext)。

## <a name="ceditgetsel"></a><a name="getsel"></a>编辑：：GetSel

调用此函数，使用返回值或参数获取编辑控件中当前所选内容（如果有）的起始和结束字符位置。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
引用将接收当前所选内容中第一个字符位置的整数。

*nEndChar*<br/>
引用一个整数，该整数将接收当前所选内容末尾的第一个未选择字符的位置。

### <a name="return-value"></a>返回值

返回 DWORD 的版本返回一个值，该值包含低阶单词中的起始位置，以及高阶单词中所选内容结束后第一个未选中字符的位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_GETSEL。](/windows/win32/Controls/em-getsel)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>编辑：：隐藏气球提示

隐藏与当前编辑控件关联的任何气球提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此功能发送[EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip)消息，这在 Windows SDK 中介绍。

## <a name="ceditlimittext"></a><a name="limittext"></a>编辑：：限制文本

调用此函数以限制用户可以输入到编辑控件的文本长度。

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>参数

*n查尔斯*<br/>
指定用户可以输入的文本的长度（在 TCHA 中）。 如果此参数为 0，则文本长度设置为UINT_MAX字节。 此选项为默认行为。

### <a name="remarks"></a>备注

更改文本限制仅限制用户可以输入的文本。 它对编辑控件中已有的任何文本没有影响，也不会影响 在 中`CWnd` [SetWindowText](cwnd-class.md#setwindowtext)成员函数复制到编辑控件的文本的长度。 如果应用程序使用 函数`SetWindowText`将更多的文本放入编辑控件中，而不是调用 中`LimitText`指定的文本，则用户可以删除编辑控件中的任何文本。 但是，文本限制将阻止用户用新文本替换现有文本，除非删除当前选择会导致文本低于文本限制。

> [!NOTE]
> 在 Win32（Windows NT 和 Windows 95/98）中[，SetLimitText](#setlimittext)将替换此功能。

有关详细信息，请参阅 Windows SDK 中的[EM_LIMITTEXT。](/windows/win32/Controls/em-limittext)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>编辑：：线从查尔

调用此函数以检索包含指定字符索引的行号的行号。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
在编辑控件的文本中包含所需字符的零基索引值，或包含 -1。 如果*nIndex*为 -1，则指定当前线，即包含 caret 的行。

### <a name="return-value"></a>返回值

包含*nIndex*指定的字符索引的行的零基行号。 如果*nIndex*为 -1，则返回包含所选内容的第一个字符的行数。 如果没有选择，则返回当前行号。

### <a name="remarks"></a>备注

字符索引是编辑控件开头的字符数。

此成员函数仅由多行编辑控件使用。

有关详细信息，请参阅 Windows SDK 中的[EM_LINEFROMCHAR。](/windows/win32/Controls/em-linefromchar)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>编辑：线索引

调用此函数以检索多行编辑控件中的行的字符索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*n 线*<br/>
在编辑控件的文本中包含所需行的索引值，或包含 -1。 如果*nLine*为 -1，则指定当前线，即包含 caret 的行。

### <a name="return-value"></a>返回值

如果指定的行号大于编辑控件中的行数，则以*nLine*或 -1 指定的行的字符索引。

### <a name="remarks"></a>备注

字符索引是从编辑控件的开头到指定行的字符数。

此成员函数仅由多行编辑控件处理。

有关详细信息，请参阅 Windows SDK 中的[EM_LINEINDEX。](/windows/win32/controls/em-lineindex)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>编辑：线长

检索编辑控件中的行的长度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*n 线*<br/>
要检索长度的行中字符的零基索引。 默认值为 -1。

### <a name="return-value"></a>返回值

对于单行编辑控件，返回值是编辑控件中文本的长度（在 TCHA 中）。

对于多行编辑控件，返回值是*nLine*参数指定的行的长度（在 TCHAR 中）。 对于 ANSI 文本，长度是行中的字节数;对于 Unicode 文本，长度是行中的字符数。 长度不包括行尾的回车字符。

如果*nLine*参数大于控件中的字符数，则返回值为零。

如果*nLine*参数为 -1，则返回值是包含选定字符的行中未选中的字符数。 例如，如果所选内容从一行的第四个字符延伸到下一行末尾的第八个字符，则返回值为 10。 也就是说，第一行有三个字符，下一行有七个字符。

有关 TCHAR 类型的详细信息，请参阅[Windows 数据类型](/windows/win32/WinProg/windows-data-types)表中的 TCHAR 行。

### <a name="remarks"></a>备注

此方法受[EM_LINELENGTH](/windows/win32/Controls/em-linelength)消息的支持，该消息在 Windows SDK 中介绍。

### <a name="example"></a>示例

  请参阅[CEdit：：lineIndex 的示例](#lineindex)。

## <a name="ceditlinescroll"></a><a name="linescroll"></a>编辑：：线滚动

调用此函数滚动多行编辑控件的文本。

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>参数

*n线*<br/>
指定要垂直滚动的行数。

*n查尔斯*<br/>
指定要水平滚动的字符位置数。 如果编辑控件具有ES_RIGHT或ES_CENTER样式，则忽略此值。

### <a name="remarks"></a>备注

此成员函数仅由多行编辑控件处理。

编辑控件不会垂直滚动超过编辑控件中的最后一行文本。 如果当前行加上*nLines*指定的行数超过编辑控件中的行总数，则调整该值，以便编辑控件的最后一行滚动到编辑控制窗口的顶部。

`LineScroll`可用于水平滚动超过任何行的最后一个字符。

有关详细信息，请参阅 Windows SDK 中的[EM_LINESCROLL。](/windows/win32/Controls/em-linescroll)

### <a name="example"></a>示例

  请参阅[CEdit：：获取第一可见线的示例](#getfirstvisibleline)。

## <a name="ceditpaste"></a><a name="paste"></a>编辑：:Paste

调用此功能以将数据从剪贴板插入到插入`CEdit`点。

```cpp
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板以CF_TEXT格式包含数据时，才会插入数据。

有关详细信息，请参阅 Windows SDK 中的[WM_PASTE。](/windows/win32/dataxchg/wm-paste)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>编辑：:P从查尔

调用此函数以获取此`CEdit`对象中给定字符的位置（左上角）。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>参数

*n查尔*<br/>
指定字符的零基索引。

### <a name="return-value"></a>返回值

*nChar*指定的字符的左上角的坐标。

### <a name="remarks"></a>备注

该字符通过给出其零基索引值来指定。 如果*nChar*大于此`CEdit`对象中最后一个字符的索引，则返回值将指定刚刚经过此`CEdit`对象中最后一个字符的字符位置的坐标。

> [!NOTE]
> 此成员功能从 Windows 95 和 Windows NT 4.0 开始可用。

有关详细信息，请参阅 Windows SDK 中的[EM_POSFROMCHAR。](/windows/win32/Controls/em-posfromchar)

### <a name="example"></a>示例

  请参阅[CEdit：：LineFromChar](#linefromchar)的示例。

## <a name="ceditreplacesel"></a><a name="replacesel"></a>编辑：：替换塞尔

调用此函数以将编辑控件中的当前选择替换为*lpszNewText*指定的文本。

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>参数

*lpsz 新文本*<br/>
指向包含替换文本的 null 端接字符串。

*bCanUndo*<br/>
要指定可以撤消此函数，请为此参数的值设置为 TRUE 。 默认值是 FALSE。

### <a name="remarks"></a>备注

仅替换编辑控件中文本的一部分。 如果要替换所有文本，请使用[CWnd：setWindowText](cwnd-class.md#setwindowtext)成员函数。

如果没有当前选择，则替换文本将插入到当前光标位置。

有关详细信息，请参阅 Windows SDK 中的[EM_REPLACESEL。](/windows/win32/Controls/em-replacesel)

### <a name="example"></a>示例

  请参阅[CEdit：：lineIndex 的示例](#lineindex)。

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>编辑：：设置库班

设置当控件为空时，在编辑控件中显示为文本提示或提示的文本。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[在]指向包含要在编辑控件中显示的提示的字符串的指针。

*fDraw 时聚焦*<br/>
[在]如果 FALSE，则当用户单击编辑控件并给出控件焦点时，不会绘制提示横幅。

如果为 TRUE，则即使控件具有焦点，也会绘制提示横幅。 当用户开始键入控件时，提示横幅将消失。

默认值是 FALSE。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

此方法发送[EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner)消息，这在 Windows SDK 中介绍。 有关详细信息，请参阅[Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)宏。

### <a name="example"></a>示例

下面的示例演示了[CEdit：setCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>编辑：：设置手

调用此函数以将句柄设置为多行编辑控件将使用的本地内存。

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>参数

*hBuffer*<br/>
包含本地内存的句柄。 此句柄必须由以前使用 LMEM_MOVEABLE 标志对[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 函数的调用创建。 假定内存包含 null 终止的字符串。 如果不是这样，则分配的内存的第一个字节应设置为 0。

### <a name="remarks"></a>备注

然后，编辑控件将使用此缓冲区存储当前显示的文本，而不是分配自己的缓冲区。

此成员函数仅由多行编辑控件处理。

在应用程序设置新的内存句柄之前，它应该使用[GetHandle](#gethandle)成员函数将句柄获取到当前内存缓冲区，并使用`LocalFree`Windows 函数释放该内存。

`SetHandle`清除撤消缓冲区（然后返回 0[的 CanUndo](#canundo)成员函数）和内部修改标志[（GetModify](#getmodify)成员函数则返回 0）。 重新绘制编辑控制窗口。

仅当已创建带有DS_LOCALEDIT样式标志集的对话框时，才能在对话框中的多行编辑控件中使用此成员函数。

> [!NOTE]
> `GetHandle`不适用于 Windows 95/98。 如果您在 Windows `GetHandle` 95/98 中调用，它将返回 NULL。 `GetHandle`将工作在 Windows NT，版本 3.51 和更高版本中记录。

有关详细信息，请参阅 windows SDK 中的[EM_SETHANDLE、](/windows/win32/Controls/em-sethandle)[本地 Alloc](/windows/win32/api/winbase/nf-winbase-localalloc)和[本地自由](/windows/win32/api/winbase/nf-winbase-localfree)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>编辑：设置高光

突出显示当前编辑控件中显示的文本范围。

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*ichStart*|[在]要突出显示的文本范围内第一个字符的基于零的索引。|
|*ichEnd*|[在]要突出显示的文本范围内最后一个字符的零索引。|

### <a name="remarks"></a>备注

此方法发送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)消息，这在 Windows SDK 中介绍。  此方法发送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)消息，这在 Windows SDK 中介绍。 和`SetHighlight``GetHighlight`都仅为 UNICODE 生成启用。

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>编辑：：设置限制文本

调用此成员函数以设置此`CEdit`对象的文本限制。

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
新的文本限制，以字符表示。

### <a name="remarks"></a>备注

文本限制是编辑控件可以接受的最大文本量（以字符表示）。

更改文本限制仅限制用户可以输入的文本。 它对编辑控件中已有的任何文本没有影响，也不会影响 在 中`CWnd` [SetWindowText](cwnd-class.md#setwindowtext)成员函数复制到编辑控件的文本的长度。 如果应用程序使用 函数`SetWindowText`将更多的文本放入编辑控件中，而不是调用 中`LimitText`指定的文本，则用户可以删除编辑控件中的任何文本。 但是，文本限制将阻止用户用新文本替换现有文本，除非删除当前选择会导致文本低于文本限制。

此功能替换 Win32 中的["限制文本](#limittext)"。

有关详细信息，请参阅 Windows SDK 中的[EM_SETLIMITTEXT。](/windows/win32/Controls/em-setlimittext)

### <a name="example"></a>示例

  请参阅[CEditView 的示例：获取编辑Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditsetmargins"></a><a name="setmargins"></a>编辑：：设置边距

调用此方法以设置此编辑控件的左右边距。

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>参数

*n 左*<br/>
新左边距的宽度（以像素为单位）。

*nRight*<br/>
新右边距的宽度（以像素为单位）。

### <a name="remarks"></a>备注

> [!NOTE]
> 此成员功能从 Windows 95 和 Windows NT 4.0 开始可用。

有关详细信息，请参阅 Windows SDK 中的[EM_SETMARGINS。](/windows/win32/Controls/em-setmargins)

### <a name="example"></a>示例

  请参阅[CEditView 的示例：获取编辑Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditsetmodify"></a><a name="setmodify"></a>编辑：：设置修改

调用此函数以设置或清除编辑控件的修改标志。

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*b 修改*<br/>
TRUE 的值表示文本已被修改，FALSE 值表示未修改。 默认情况下，将设置修改后的标志。

### <a name="remarks"></a>备注

修改后的标志指示编辑控件中的文本是否已修改。 每当用户更改文本时，都会自动设置它。 可以使用[GetModify](#getmodify)成员函数检索其值。

有关详细信息，请参阅 Windows SDK 中的[EM_SETMODIFY。](/windows/win32/Controls/em-setmodify)

### <a name="example"></a>示例

  请参阅[CEdit：：获取修改的示例](#getmodify)。

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>编辑：：设置密码字符

调用此函数以设置或删除用户键入文本时在编辑控件中显示的密码字符。

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>参数

*ch*<br/>
指定要显示的字符，以代替用户键入的字符。 如果*ch*为 0，将显示用户键入的实际字符。

### <a name="remarks"></a>备注

设置密码字符时，该字符将针对用户键入的每个字符显示。

此成员函数对多行编辑控件没有影响。

调用`SetPasswordChar`成员函数时，`CEdit`将使用*ch*指定的字符重新绘制所有可见字符。

如果使用[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)样式创建编辑控件，则默认密码字符将设置为星号 （）。 <strong>\*</strong> 如果`SetPasswordChar`使用*ch*设置为 0 调用此样式，则将删除此样式。

有关详细信息，请参阅 Windows SDK 中的[EM_SETPASSWORDCHAR。](/windows/win32/Controls/em-setpasswordchar)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>编辑：仅设置 Read

调用此函数以设置编辑控件的只读状态。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>参数

*b 只读*<br/>
指定是设置还是删除编辑控件的只读状态。 TRUE 的值将状态设为只读状态;如果 "TRUE"值将状态设为只读状态。FALSE 的值将状态设置为读/写。

### <a name="return-value"></a>返回值

如果操作成功，则为非零;如果发生错误，则为 0。

### <a name="remarks"></a>备注

可以通过测试[CWnd：：getStyle](cwnd-class.md#getstyle)返回值中的[ES_READONLY](styles-used-by-mfc.md#edit-styles)标志来找到当前设置。

有关详细信息，请参阅 Windows SDK 中的[EM_SETREADONLY。](/windows/win32/Controls/em-setreadonly)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>编辑：：设置重新

调用此函数以使用指定的坐标设置矩形的尺寸。

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向指定格式`RECT`矩形的新`CRect`尺寸的结构或对象。

### <a name="remarks"></a>备注

此成员仅由多行编辑控件处理。

用于`SetRect`设置多行编辑控件的格式矩形。 格式矩形是文本的限制矩形，与编辑控制窗口的大小无关。 首次创建编辑控件时，格式矩形与编辑控制窗口的工作区相同。 通过使用`SetRect`成员函数，应用程序可以使格式矩形大于或小于编辑控制窗口。

如果编辑控件没有滚动条，则如果格式矩形大于窗口，则文本将被剪切，而不是换行。 如果编辑控件包含边框，则格式矩形将减小为边框的大小。 如果调整成员函数返回的`GetRect`矩形，则必须在将矩形传递给`SetRect`之前删除边框的大小。

调用`SetRect`时，编辑控件的文本也会重新格式化并重新显示。

有关详细信息，请参阅 Windows SDK 中的[EM_SETRECT。](/windows/win32/Controls/em-setrect)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>编辑：：设置RectNP

调用此函数以设置多行编辑控件的格式矩形。

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向指定矩形`RECT`新尺寸`CRect`的结构或对象。

### <a name="remarks"></a>备注

格式矩形是文本的限制矩形，与编辑控制窗口的大小无关。

`SetRectNP`与`SetRect`成员函数相同，只不过编辑控制窗口不重绘。

首次创建编辑控件时，格式矩形与编辑控制窗口的工作区相同。 通过调用`SetRectNP`成员函数，应用程序可以使格式矩形大于或小于编辑控制窗口。

如果编辑控件没有滚动条，则如果格式矩形大于窗口，则文本将被剪切，而不是换行。

此成员仅由多行编辑控件处理。

有关详细信息，请参阅 Windows SDK 中的[EM_SETRECTNP。](/windows/win32/Controls/em-setrectnp)

### <a name="example"></a>示例

  请参阅[CEdit：：SetRect](#setrect)的示例。

## <a name="ceditsetsel"></a><a name="setsel"></a>编辑：：SetSel

调用此函数以选择编辑控件中的字符范围。

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>参数

*dw选择*<br/>
指定低阶单词中的起始位置和高阶单词的结束位置。 如果低阶单词为 0，高阶单词为 -1，则选择编辑控件中的所有文本。 如果低阶单词为 -1，则删除任何当前选择。

*bNoScroll*<br/>
指示是否应将插入者滚动到视图中。 如果 FALSE，则 care 将滚动到视图中。 如果为 TRUE，则不会滚动到视图中。

*nStartChar*<br/>
指定起始位置。 如果*nStartChar*为*0，nEndChar*为 -1，则选择编辑控件中的所有文本。 如果*nStartChar*为 -1，则删除任何当前选择。

*nEndChar*<br/>
指定结束位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_SETSEL。](/windows/win32/Controls/em-setsel)

### <a name="example"></a>示例

  请参阅[CEdit：：GetSel](#getsel)的示例。

## <a name="ceditsettabstops"></a><a name="settabstops"></a>编辑：：设置标签

调用此函数以在多行编辑控件中设置制表位。

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>参数

*cxEachStop*<br/>
指定在每个*cxEachStop*对话框单元上设置制表符止动器。

*nTabStops*<br/>
指定*rgTabStops*中包含的制表位数。 此数字必须大于 1。

*rgTabStops*<br/>
指向指定在对话框单元中指定的制表符止动器的无符号整数数组。 对话框单位是水平或垂直距离。 一个水平对话框单位等于当前对话框基本宽度单位的四分之一，1 个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 Windows`GetDialogBaseUnits`函数返回当前以像素为单位的当前对话框基本单位。

### <a name="return-value"></a>返回值

设置选项卡时非零;否则 0。

### <a name="remarks"></a>备注

将文本复制到多行编辑控件时，文本中的任何选项卡字符都将导致将空间生成到下一个制表位。

要将制表符停止设置为 32 个对话框单位的默认大小，请调用此成员函数的无参数版本。 要将制表符停止设置为大小小于 32，请使用*cxEachStop*参数调用版本。 要将制表符停止设置为大小数组，请使用具有两个参数的版本。

此成员函数仅由多行编辑控件处理。

`SetTabStops`不会自动重绘编辑窗口。 如果更改编辑控件中已有文本的制表位，请致电[CWnd：：ininrect](cwnd-class.md#invalidaterect)以重新绘制编辑窗口。

有关详细信息，请参阅 windows SDK 中的[EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops)和[GetDialogBase单位](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits)。

### <a name="example"></a>示例

  请参阅[CEditView 示例：：设置 TabStop。](ceditview-class.md#settabstops)

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>编辑：：显示气球提示

显示与当前编辑控件关联的气球提示。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pEdit气球提示*|[在]指向描述气球尖端的[EDITBALLTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)结构的指针。|
|*lpszTitle*|[在]指向包含气球提示标题的 Unicode 字符串的指针。|
|*lpszText*|[在]指向包含气球提示文本的 Unicode 字符串的指针。|
|*蒂图标*|[在]指定要与气球提示关联的图标类型的**INT。** 默认值为TTI_NONE。 有关详细信息，请参阅`ttiIcon`[EDITBALLTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)结构的成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此功能发送[EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip)消息，这在 Windows SDK 中介绍。 有关详细信息，请参阅[Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)宏。

### <a name="example"></a>示例

以下代码示例定义用于访问当前编辑控件`m_cedit`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>示例

以下代码示例显示编辑控件的气球提示。 [CEdit：：Show气球提示](#showballoontip)方法指定标题和气球提示文本。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>编辑：撤消

调用此函数以撤消上次编辑控制操作。

```
BOOL Undo();
```

### <a name="return-value"></a>返回值

对于单行编辑控件，返回值始终为非零。 对于多行编辑控件，如果撤消操作成功，返回值为非零;如果撤消操作失败，则返回值为 0。

### <a name="remarks"></a>备注

撤消操作也可以撤消。 例如，可以使用第一次调用 还原已删除的文本`Undo`。 只要没有干预编辑操作，就可以使用第二个调用`Undo`再次删除文本。

有关详细信息，请参阅 Windows SDK 中的[EM_UNDO。](/windows/win32/Controls/em-undo)

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](cwnd-class.md)<br/>
[C按钮类](cbutton-class.md)<br/>
[CComboBox 类](ccombobox-class.md)<br/>
[CListBox 类](clistbox-class.md)<br/>
[CScrollBar 类](cscrollbar-class.md)<br/>
[CStatic 类](cstatic-class.md)<br/>
[CDialog 类](cdialog-class.md)
