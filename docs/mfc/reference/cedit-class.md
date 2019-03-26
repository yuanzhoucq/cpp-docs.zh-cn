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
ms.openlocfilehash: e1ca69382591dc7d3afe9b5871dfdebd64aedce4
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416996"
---
# <a name="cedit-class"></a>CEdit Class

提供 Windows 编辑控件功能。

## <a name="syntax"></a>语法

```
class CEdit : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|构造`CEdit`控件对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|确定是否可撤消的编辑控件的操作。|
|[CEdit::CharFromPos](#charfrompos)|检索与指定的位置最接近的字符的行和字符索引。|
|[CEdit::Clear](#clear)|删除 （清除） 中编辑当前选择 （如果有） 控制。|
|[CEdit::Copy](#copy)|将复制当前所选内容 （如果有） 中的编辑控件到 CF_TEXT 格式剪贴板。|
|[CEdit::Create](#create)|创建 Windows 编辑控件，并将其附加到`CEdit`对象。|
|[CEdit::Cut](#cut)|删除 （剪切） 中编辑当前选择 （如果有） 控制，并复制到剪贴板 CF_TEXT 中删除的文本设置格式。|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重置 （清除） 撤消标志的编辑控件。|
|[CEdit::FmtLines](#fmtlines)|打开或关闭多行编辑控件中设置包含软换行字符。|
|[CEdit::GetCueBanner](#getcuebanner)|检索作为文本提示或提示，当该控件为空且不具有焦点的编辑控件中显示的文本。|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|确定一个编辑控件中最顶层可见的行。|
|[CEdit::GetHandle](#gethandle)|检索多行编辑控件的当前分配的内存的句柄。|
|[CEdit::GetHighlight](#gethighlight)|获取起始和结束当前编辑控件中突出显示的文本范围中的字符的索引。|
|[CEdit::GetLimitText](#getlimittext)|获取文本的最长这`CEdit`可以包含。|
|[CEdit::GetLine](#getline)|从一个编辑控件中检索文本行。|
|[CEdit::GetLineCount](#getlinecount)|检索多行编辑控件中的行数。|
|[CEdit::GetMargins](#getmargins)|获取此左右边距`CEdit`。|
|[CEdit::GetModify](#getmodify)|确定是否已修改一个编辑控件的内容。|
|[CEdit::GetPasswordChar](#getpasswordchar)|检索用户输入文本时显示的编辑控件中的密码字符。|
|[CEdit::GetRect](#getrect)|获取一个编辑控件的格式设置矩形。|
|[CEdit::GetSel](#getsel)|获取一个编辑控件中当前所选内容的第一个和最后一个字符位置。|
|[CEdit::HideBalloonTip](#hideballoontip)|隐藏任何与当前的编辑控件相关联的气球状提示。|
|[CEdit::LimitText](#limittext)|限制用户可以向一个编辑控件中输入文本的长度。|
|[CEdit::LineFromChar](#linefromchar)|检索包含指定的字符索引的行的行号。|
|[CEdit::LineIndex](#lineindex)|检索多行编辑控件中的行的字符索引。|
|[CEdit::LineLength](#linelength)|检索一个编辑控件中的行的长度。|
|[CEdit::LineScroll](#linescroll)|将多行编辑控件的文本滚动。|
|[CEdit::Paste](#paste)|将数据从剪贴板插入到当前光标位置处的编辑控件。 仅当剪贴板包含 CF_TEXT 格式的数据插入数据。|
|[CEdit::PosFromChar](#posfromchar)|检索指定的字符索引的左上角的坐标。|
|[CEdit::ReplaceSel](#replacesel)|替换指定的文本编辑控件中的当前所选内容。|
|[CEdit::SetCueBanner](#setcuebanner)|设置显示为文本提示或提示，当该控件为空且不具有焦点的编辑控件中的文本。|
|[CEdit::SetHandle](#sethandle)|设置的句柄将由多行编辑控件的本地内存。|
|[CEdit::SetHighlight](#sethighlight)|突出显示的范围内的当前显示的文本编辑控件。|
|[CEdit::SetLimitText](#setlimittext)|此设置文本的最长`CEdit`可以包含。|
|[CEdit::SetMargins](#setmargins)|设置此左右边距`CEdit`。|
|[CEdit::SetModify](#setmodify)|设置或清除编辑控件修改标志。|
|[CEdit::SetPasswordChar](#setpasswordchar)|设置或删除时用户输入的文本编辑控件中显示的密码字符。|
|[CEdit::SetReadOnly](#setreadonly)|设置一个编辑控件的只读状态。|
|[CEdit::SetRect](#setrect)|设置多行编辑控件的格式设置矩形并更新该控件。|
|[CEdit::SetRectNP](#setrectnp)|无需重绘控件窗口中设置多行编辑控件的矩形。|
|[CEdit::SetSel](#setsel)|选择的编辑控件中的字符范围。|
|[CEdit::SetTabStops](#settabstops)|集所有制表位中多行编辑控件。|
|[CEdit::ShowBalloonTip](#showballoontip)|显示与当前的编辑控件相关联的气球提示。|
|[CEdit::Undo](#undo)|反转的上一个编辑控件的操作。|

## <a name="remarks"></a>备注

一个编辑控件是用户可以在其中输入文本的矩形的子窗口。

从对话框模板或直接在代码中，可以创建一个编辑控件。 在这两种情况下，首次调用构造函数`CEdit`来构造`CEdit`对象，然后调用[创建](#create)成员函数来创建 Windows 编辑控件，并将其附加到`CEdit`对象。

构造可以是在派生类中的一步过程`CEdit`。 编写构造函数作为派生的类，并调用`Create`从构造函数内。

`CEdit` 继承中的重要功能`CWnd`。 若要设置和检索中的文本`CEdit`对象，请使用`CWnd`成员函数[SetWindowText](cwnd-class.md#setwindowtext)并[GetWindowText](cwnd-class.md#getwindowtext)，编辑的全部内容的 set 或 get 控制，即使它是一个多行控件。 在多行控件中的文本行分隔 \r\n 字符序列。 此外，如果多行编辑控件，获取和设置控件的文本的一部分通过调用`CEdit`成员函数[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，和[ReplaceSel](#replacesel)。

如果你想要处理 Windows 通知消息发送到其父级的编辑控件 (从派生的类通常`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。

每个消息映射条目采用以下形式：

  **ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**

其中`id`指定发送通知的编辑控件的子窗口 ID 和`memberFxn`是您编写以处理通知的父成员函数的名称。

父项的函数原型如下所示：

**afx_msg** void memberFxn **( );**

下面是可能的消息映射条目和的情况下，将向父级发送说明的列表：

- ON_EN_CHANGE 用户已采取的操作可能已更改的编辑控件中的文本。 与不同 EN_UPDATE 通知消息之后 Windows 更新显示, 发送此通知消息。

- ON_EN_ERRSPACE 编辑控件无法分配足够的内存来满足特定的请求。

- ON_EN_HSCROLL 用户单击一个编辑控件的水平滚动条。 更新屏幕之前，会收到通知父窗口。

- ON_EN_KILLFOCUS 编辑控件失去输入的焦点。

- ON_EN_MAXTEXT 当前插入已超出指定的编辑控件的字符数，已被截断。 一个编辑控件不具有 ES_AUTOHSCROLL 样式和要插入的字符数将超过编辑控件的宽度时，还发送。 一个编辑控件不具有 ES_AUTOVSCROLL 样式和总导致的文本插入的行数将超过编辑控件的高度时，还发送。

- ON_EN_SETFOCUS 发送时的编辑控件接收到输入的焦点。

- ON_EN_UPDATE 编辑控件即将显示更改文本。 控件设置文本格式之后，但它屏幕文本，以便可以更改窗口大小，如有必要之前发送。

- ON_EN_VSCROLL 用户单击一个编辑控件的垂直滚动条。 更新屏幕之前，会收到通知父窗口。

如果您创建`CEdit`对话框中，在对象`CEdit`在用户关闭对话框时自动销毁对象。

如果您创建`CEdit`通过使用对话框编辑器中，对话框资源的对象`CEdit`在用户关闭对话框时自动销毁对象。

如果您创建`CEdit`对象内一个窗口，您可能还需要将其销毁。 如果您创建`CEdit`对象在堆栈上被自动销毁。 如果您创建`CEdit`通过使用堆上的对象**新**函数，必须调用**删除**用户终止 Windows 时销毁该对象上编辑控件。 如果分配任何内存`CEdit`对象，请重写`CEdit`析构函数释放的分配。

若要修改某些样式 （如 ES_READONLY) 的编辑控件中必须将特定消息发送到控件而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 请参阅[编辑控件样式](/windows/desktop/Controls/edit-control-styles)Windows SDK 中。

有关详细信息`CEdit`，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

调用此函数可确定是否可撤消的上一个编辑操作。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>返回值

如果可以通过调用撤消上一个编辑操作，非零值`Undo`成员函数; 如果无法撤消，则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_CANUNDO](/windows/desktop/Controls/em-canundo) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::Undo](#undo)。

##  <a name="cedit"></a>  CEdit::CEdit

构造 `CEdit` 对象。

```
CEdit();
```

### <a name="remarks"></a>备注

使用[创建](#create)构造 Windows 编辑控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

调用此函数可检索的从零开始的行和最接近指定点在此字符的字符索引`CEdit`控件

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
此工作区中的点的坐标`CEdit`对象。

### <a name="return-value"></a>返回值

在低序位字中的字符索引和高序位字中的行索引。

### <a name="remarks"></a>备注

> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始支持。

有关详细信息，请参阅[EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

调用此函数可删除 （清除） 当前选定内容 （如果有） 中的编辑控件。

```
void Clear();
```

### <a name="remarks"></a>备注

删除由`Clear`可以通过调用撤消[撤消](#undo)成员函数。

若要删除当前所选内容并将已删除的内容放到剪贴板，请调用[剪切](#cut)成员函数。

有关详细信息，请参阅[WM_CLEAR](/windows/desktop/dataxchg/wm-clear) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

调用此函数，若要复制当前所选内容 （如果有） 到剪贴板中 CF_TEXT 格式编辑控件中。

```
void Copy();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[WM_COPY](/windows/desktop/dataxchg/wm-copy) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

创建 Windows 编辑控件，并将其附加到`CEdit`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定编辑控件的样式。 应用的任意组合[编辑样式](styles-used-by-mfc.md#edit-styles)到控件。

*rect*<br/>
指定编辑控件的大小和位置。 可以是`CRect`对象或`RECT`结构。

*pParentWnd*<br/>
指定编辑控件的父窗口 (通常`CDialog`)。 它不能为 NULL。

*nID*<br/>
指定编辑控件的 id。

### <a name="return-value"></a>返回值

如果初始化成功，则非零值否则为 0。

### <a name="remarks"></a>备注

构造`CEdit`两个步骤中的对象。 首先，调用`CEdit`构造函数，然后调用`Create`，它创建 Windows 编辑控件并将其附加到`CEdit`对象。

当`Create`执行时，Windows 将发送[WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate)， [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize)， [WM_CREATE](/windows/desktop/winmsg/wm-create)，并且[WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo)在编辑控件的消息。

默认情况下处理这些消息[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，以及[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，从派生类`CEdit`、 将消息映射添加到新的类，并重写上面的消息处理程序成员函数。 重写`OnCreate`，例如，若要执行的新类所需的初始化。

将以下内容应用[的窗口样式](styles-used-by-mfc.md#window-styles)到编辑控件。

- WS_CHILD 始终

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_GROUP 与组控件

- WS_TABSTOP 要包含在 tab 键顺序中的编辑控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>  CEdit::Cut

编辑控件中当前所选内容 （如果有） 调用此函数可删除 （剪切） 并将已删除的文本复制到剪贴板中 CF_TEXT 格式。

```
void Cut();
```

### <a name="remarks"></a>备注

删除由`Cut`可以通过调用撤消[撤消](#undo)成员函数。

若要删除当前所选内容，而无需将已删除的文本放入剪贴板，请调用[清除](#clear)成员函数。

有关详细信息，请参阅[WM_CUT](/windows/desktop/dataxchg/wm-cut) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

调用此函数可重置 （清除） 的编辑控件的撤消标志。

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>备注

编辑控件现在将不能撤消上一操作。 只要编辑控件中的某个操作可撤消设置还原标志。

撤消标志将自动清除每当[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle) `CWnd`调用成员函数。

有关详细信息，请参阅[EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

调用此函数可在多行编辑控件内包含的软换行字符设置为 on 或 off。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>参数

*bAddEOL*<br/>
指定是否要插入软换行字符。 值为 TRUE 将插入以下字符:;如果值为 FALSE 会将它们删除。

### <a name="return-value"></a>返回值

如果任何非零值设置格式的时间;否则为 0。

### <a name="remarks"></a>备注

软换行符包含两个回车符和自动换行由于中断的行的末尾插入一个换行符。 硬盘分行符组成一个回车符和换行符。 以一个硬盘换行符结尾的行不受`FmtLines`。

如果仅将响应 Windows`CEdit`对象是一个多行编辑控件。

`FmtLines` 只会影响返回的缓冲区[GetHandle](#gethandle)和返回的文本[WM_GETTEXT](/windows/desktop/winmsg/wm-gettext)。 它将不会影响对内编辑控件中文本的显示。

有关详细信息，请参阅[EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

检索作为文本提示或提示，该控件为空时的编辑控件中显示的文本。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[out]指向包含提示文本的字符串的指针。

*cchText*<br/>
[in]可以接收的字符数。 此数字包括终止 NULL 字符。

### <a name="return-value"></a>返回值

用于第一个重载，真正的成功，则该方法是否否则为 FALSE。

对于第二个重载[CString](../../atl-mfc-shared/using-cstring.md) ，包含提示文本，该方法是否成功; 否则为空字符串 ("")。

### <a name="remarks"></a>备注

此方法将发送[EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner)消息，Windows SDK 中所述。 有关详细信息，请参阅[Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext)宏。

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

调用此函数可确定的编辑控件中可见的最上面一行。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>返回值

最顶层的可见行的从零开始的索引。 对于单行编辑控件，则返回值为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

调用此函数可检索的句柄为多行编辑控件当前分配的内存。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>返回值

本地内存句柄，用于标识保存的编辑控件内容的缓冲区。 如果发生错误，例如将消息发送到一个单行编辑控件，则返回值为 0。

### <a name="remarks"></a>备注

句柄是本地内存句柄和任何可能使用**本地**采用本地内存的 Windows 内存函数处理作为参数。

`GetHandle` 仅由多行编辑控件处理。

调用`GetHandle`对话框才具有 DS_LOCALEDIT 风格标记集创建对话框框中的多行编辑控件。 如果未设置 DS_LOCALEDIT 样式，也仍然可获得非零返回值，但您将不能使用返回的值。

> [!NOTE]
> `GetHandle` 不会使用 Windows 95/98。 如果调用`GetHandle`在 Windows 95/98，它将返回 NULL。 `GetHandle` 将按下 Windows NT 版本 3.51 及更高版本记录工作。

有关详细信息，请参阅[EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

获取当前的编辑控件中突出显示的文本范围中的第一个和最后一个字符的索引。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pichStart*|[out]突出显示的文本范围中的第一个字符的从零开始索引。|
|*pichEnd*|[out]突出显示的文本范围中的最后一个字符的从零开始索引。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[EM_GETHILITE](/windows/desktop/Controls/em-gethilite)消息，Windows SDK 中所述。 这两`SetHighlight`和`GetHighlight`实现 UNICODE 仅生成当前已启用。

##  <a name="getlimittext"></a>  CEdit::GetLimitText

调用此成员函数可获取此文本限制`CEdit`对象。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>返回值

当前文本中的限制，TCHARs，此`CEdit`对象。

### <a name="remarks"></a>备注

文本限制为文本，请在 TCHARs，编辑控件可以接受的最长。

> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始支持。

有关详细信息，请参阅[EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

调用此函数可从一个编辑控件检索文本行，并将其放入*lpszBuffer*。

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
指定要检索多行的行号的编辑控件。 行号是从零开始;值为 0 指定第一行。 单行编辑控件将忽略此参数。

*lpszBuffer*<br/>
指向用于接收缓冲区的行的副本。 缓冲区的第一个单词必须指定 TCHARs，可复制到缓冲区的最大数目。

*nMaxLength*<br/>
指定的最大 TCHAR 可以复制到缓冲区的字符数。 `GetLine` 中的第一个单词放入此值*lpszBuffer*之前 Windows 在调用。

### <a name="return-value"></a>返回值

实际复制的字符数。 返回值为 0，如果指定的行号，则*nIndex*大于编辑控件中的行数。

### <a name="remarks"></a>备注

复制的行不包含 null 终止字符。

有关详细信息，请参阅[EM_GETLINE](/windows/desktop/Controls/em-getline) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::GetLineCount](#getlinecount)。

##  <a name="getlinecount"></a>  CEdit::GetLineCount

调用此函数可检索多行编辑控件中的行数。

```
int GetLineCount() const;
```

### <a name="return-value"></a>返回值

一个包含多行中的行数的整数的编辑控件。 如果已在编辑控件中不输入任何文本，则返回值为 1。

### <a name="remarks"></a>备注

`GetLineCount` 只能处理由多行编辑控件。

有关详细信息，请参阅[EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

调用此成员函数以检索此编辑控件的左侧和右侧的边距。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>返回值

在低序位字和高位字的右边距的宽度左边距的宽度。

### <a name="remarks"></a>备注

以像素为单位测量边距。

> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始支持。

有关详细信息，请参阅[EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="getmodify"></a>  CEdit::GetModify

调用此函数可确定是否已修改一个编辑控件的内容。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>返回值

如果编辑控件内容已被修改; 非零值如果它们保持 0 不变。

### <a name="remarks"></a>备注

Windows 维护，该值指示是否已更改的编辑控件内容的内部标志。 编辑控件第一次创建，并还可以通过调用清除时清除此标志[SetModify](#setmodify)成员函数。

有关详细信息，请参阅[EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

调用此函数可检索用户输入文本时显示的编辑控件中的密码字符。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>返回值

指定要显示而不是用户键入的字符的字符。 如果没有密码字符存在，则返回值为 NULL。

### <a name="remarks"></a>备注

如果使用 ES_PASSWORD 样式创建编辑控件，支持控件的 DLL 将确定默认密码字符。 清单或[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)方法确定将哪个 DLL 支持编辑控件。 如果 user32.dll 支持编辑控件，默认密码字符是星号 (*，U + 002A)。 如果 comctl32.dll 版本 6 支持编辑控件的默认字符是黑色圆圈 （U + 25CF ●）。 详细了解哪些 DLL 和版本支持的公共控件，请参阅[Shell 和公共控件版本](https://msdn.microsoft.com/library/windows/desktop/bb776779)。

此方法将发送[EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar)消息，Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

调用此函数可获取一个编辑控件的格式设置矩形。

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`接收格式化矩形的结构。

### <a name="remarks"></a>备注

格式化矩形是大小的文本，这是大小的独立的编辑控件窗口的限制。

可以通过修改多行编辑控件的格式设置矩形[SetRect](#setrect)并[SetRectNP](#setrectnp)成员函数。

有关详细信息，请参阅[EM_GETRECT](/windows/desktop/Controls/em-getrect) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::LimitText](#limittext)。

##  <a name="getsel"></a>  CEdit::GetSel

调用此函数可获取的起始和结束字符位置的一个编辑控件，使用返回值或参数中的当前选择 （如果有）。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
对一个整数，它将当前选定内容中收到的第一个字符的位置引用。

*nEndChar*<br/>
对一个整数，将收到超出当前所选内容末尾的第一个未选定字符的位置引用。

### <a name="return-value"></a>返回值

返回一个 dword 值的版本返回一个值，包含的高序位字中的选定内容结尾后的低序位字中的起始位置和未选定的第一个字符的位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_GETSEL](/windows/desktop/Controls/em-getsel) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

隐藏任何与当前的编辑控件相关联的气球状提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此函数发送[EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip)消息，Windows SDK 中所述。

##  <a name="limittext"></a>  CEdit::LimitText

调用此函数，以限制用户可以输入到编辑控件的文本的长度。

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>参数

*nChars*<br/>
指定用户可以输入的文本的长度 （以 TCHARs)。 如果此参数为 0，则将文本长度设置为 UINT_MAX 字节。 这是默认行为。

### <a name="remarks"></a>备注

更改文本限制将限制用户可以输入文本。 它不会影响任何文本中已有的编辑控件，也不会影响复制到由编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数以将更多的文本放入一个编辑控件比对的调用中指定`LimitText`，用户可以删除任何编辑控件中的文本。 但是，文本限制将阻止用户的现有文本替换为新文本，除非删除当前所选内容会导致文本以低于文本限制。

> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)替换此函数。

有关详细信息，请参阅[EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

调用此函数可检索包含指定的字符索引的行的行号。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含的从零开始的索引值的文本编辑控件中所需字符或包含-1。 如果*nIndex*为-1，它指定当前行，即，包含脱字号的行。

### <a name="return-value"></a>返回值

包含由指定的字符索引的行的从零开始的行号*nIndex*。 如果*nIndex*为-1，返回包含所选内容的第一个字符的行数。 如果不未做任何选择，则返回当前行号。

### <a name="remarks"></a>备注

字符索引是从在编辑控件的开始的字符数。

此成员函数仅供多行编辑控件。

有关详细信息，请参阅[EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

调用此函数可检索多行编辑控件中的行的字符索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*nLine*<br/>
包含在文本编辑控件中所需的行的索引值或包含-1。 如果*n 行*为-1，它指定当前行，即，包含脱字号的行。

### <a name="return-value"></a>返回值

在指定的行的字符索引*n 行*则为-1 指定的行数是否大于编辑控件中的行数。

### <a name="remarks"></a>备注

字符索引是从在编辑控件的开始到指定行的字符数。

此成员函数仅由多行编辑控件处理。

有关详细信息，请参阅[EM_LINEINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761611) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

检索一个编辑控件中的行的长度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*nLine*<br/>
其长度是要检索的行中的字符从零开始索引。 默认值为 -1。

### <a name="return-value"></a>返回值

对于单行编辑控件的返回值是文本的编辑控件中的长度，以 TCHARs。

对于多行编辑控件，则返回值是由指定的行的长度，以 TCHARs， *n 行*参数。 对于 ANSI 文本长度是行; 中的字节数对于 Unicode 文本，长度为行中的字符数。 长度不包括位于行末尾处的回车字符。

如果*n 行*参数为多个控件中的字符数，返回值为零。

如果*n 行*参数是-1，返回值是未选定字符中包含所选的字符的行数。 例如，如果所选内容覆盖从一行到下一行末尾的八个字符的第四个字符，则返回值为 10。 它是三个字符的第一行和七个下一步。

TCHAR 类型有关的详细信息，请参阅中的表中的 TCHAR 一行[Windows 数据类型](/windows/desktop/WinProg/windows-data-types)。

### <a name="remarks"></a>备注

此方法支持通过[EM_LINELENGTH](/windows/desktop/Controls/em-linelength)消息，Windows SDK 中所述。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::LineIndex](#lineindex)。

##  <a name="linescroll"></a>  CEdit::LineScroll

调用此函数可滚动的多行编辑控件的文本。

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>参数

*nLines*<br/>
指定垂直滚动行的数。

*nChars*<br/>
指定水平滚动的字符位置的数。 如果编辑控件具有 ES_RIGHT 或 ES_CENTER 样式，将忽略此值。

### <a name="remarks"></a>备注

此成员函数仅由多行编辑控件处理。

编辑控件不垂直滚动过去的文本编辑控件中的最后一行。 如果当前行以及由指定的行数*nLines*超过编辑控件中的总行数，以便编辑控件的最后一行滚动到编辑控件窗口的顶部调整值。

`LineScroll` 可用于水平滚动过去的任意行的最后一个字符。

有关详细信息，请参阅[EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。

##  <a name="paste"></a>  CEdit::Paste

调用此函数可将数据从剪贴板粘贴到`CEdit`插入点处。

```
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板包含 CF_TEXT 格式的数据插入数据。

有关详细信息，请参阅[WM_PASTE](/windows/desktop/dataxchg/wm-paste) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

调用此函数可获取在此给定的字符的位置 （左上角）`CEdit`对象。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>参数

*nChar*<br/>
指定字符的从零开始的索引。

### <a name="return-value"></a>返回值

指定的字符的左上角的坐标*nChar*。

### <a name="remarks"></a>备注

通过提供的从零开始的索引值指定的字符。 如果*nChar*大于此中的最后一个字符的索引`CEdit`对象，返回值在此指定的刚超出最后一个字符的字符位置的坐标`CEdit`对象。

> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始支持。

有关详细信息，请参阅[EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::LineFromChar](#linefromchar)。

##  <a name="replacesel"></a>  CEdit::ReplaceSel

调用此函数可在编辑控件中的当前所选内容替换为指定的文本*lpszNewText*。

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>参数

*lpszNewText*<br/>
指向包含替换文本的以 null 结尾的字符串。

*bCanUndo*<br/>
若要指定此函数可撤消，设置此参数的值为 TRUE。 默认值是 FALSE。

### <a name="remarks"></a>备注

将替换仅为一部分的编辑控件中的文本。 如果你想要替换的所有文本，使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成员函数。

如果当前没有选定内容，在当前光标位置插入替换文本。

有关详细信息，请参阅[EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::LineIndex](#lineindex)。

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

设置显示为文本提示或提示，在编辑控件时该控件为空的文本。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[in]包含提示在编辑控件中显示的字符串指针。

*fDrawWhenFocused*<br/>
[in]如果为 FALSE，当用户编辑控件中单击，并使控件具有焦点时不绘制提示标志。

如果为 TRUE，即使在控件有焦点时绘制提示标志。 当用户开始在控件中键入时，提示标志将消失。

默认值是 FALSE。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner)消息，Windows SDK 中所述。 有关详细信息，请参阅[Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)宏。

### <a name="example"></a>示例

下面的示例演示[CEdit::SetCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

调用此函数可设置为多行编辑控件将使用的本地内存的句柄。

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>参数

*hBuffer*<br/>
包含的句柄的本地内存。 此句柄必须通过以前调用创建[LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) Windows 函数使用 LMEM_MOVEABLE 标志。 假定内存包含以 null 结尾的字符串。 如果这不是这种情况，则已分配的内存的第一个字节应设置为 0。

### <a name="remarks"></a>备注

然后，编辑控件将使用此缓冲区来存储当前显示的文本而不是分配自己的缓冲区。

此成员函数仅由多行编辑控件处理。

应用程序在设置新的内存句柄之前，应使用[GetHandle](#gethandle)成员函数来获取当前的内存缓冲区句柄并释放该内存使用`LocalFree`Windows 函数。

`SetHandle` 清除撤消缓冲区 ( [CanUndo](#canundo)成员函数则返回 0) 和内部修改标志 ( [GetModify](#getmodify)成员函数则返回 0)。 编辑控件窗口会重新绘制。

仅当您使用 DS_LOCALEDIT 风格标记集创建了对话框中，可以在对话框中使用此成员函数在多行编辑控件。

> [!NOTE]
> `GetHandle` 不会使用 Windows 95/98。 如果调用`GetHandle`在 Windows 95/98，它将返回 NULL。 `GetHandle` 将按下 Windows NT 版本 3.51 及更高版本记录工作。

有关详细信息，请参阅[EM_SETHANDLE](/windows/desktop/Controls/em-sethandle)， [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)，并[LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

突出显示的范围内的当前显示的文本编辑控件。

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*ichStart*|[in]要突出显示的文本范围中的第一个字符的从零开始索引。|
|*ichEnd*|[in]要突出显示的文本范围中的最后一个字符的从零开始索引。|

### <a name="remarks"></a>备注

此方法将发送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)消息，Windows SDK 中所述。  此方法将发送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)消息，Windows SDK 中所述。 这两`SetHighlight`和`GetHighlight`启用了 UNICODE 仅生成。

##  <a name="setlimittext"></a>  CEdit::SetLimitText

调用此成员函数以设置此文本限制`CEdit`对象。

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
新文本限制，以字符为单位。

### <a name="remarks"></a>备注

文本限制为文本，请在编辑控件可以接受的字符的最长。

更改文本限制将限制用户可以输入文本。 它不会影响任何文本中已有的编辑控件，也不会影响复制到由编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数以将更多的文本放入一个编辑控件比对的调用中指定`LimitText`，用户可以删除任何编辑控件中的文本。 但是，文本限制将阻止用户的现有文本替换为新文本，除非删除当前所选内容会导致文本以低于文本限制。

此函数将替换[LimitText](#limittext)在 Win32 中。

有关详细信息，请参阅[EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="setmargins"></a>  CEdit::SetMargins

调用此方法以将此编辑控件的左侧和右侧的页边距设置。

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>参数

*nLeft*<br/>
新的左边距，以像素为单位的宽度。

*nRight*<br/>
新的右边距，以像素为单位的宽度。

### <a name="remarks"></a>备注

> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始支持。

有关详细信息，请参阅[EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="setmodify"></a>  CEdit::SetModify

调用此函数可设置或清除编辑控件的已修改的标志。

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*bModified*<br/>
值为 TRUE 指示已修改的文本，值为 FALSE 指示它未被修改。 默认情况下，设置已修改的标志。

### <a name="remarks"></a>备注

修改的标志指示已修改的文本编辑控件中。 它将自动设置的每当用户更改的文本。 其值可能会检索与[GetModify](#getmodify)成员函数。

有关详细信息，请参阅[EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::GetModify](#getmodify)。

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

调用此函数可设置或删除用户键入的文本时显示的编辑控件中的密码字符。

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>参数

*ch*<br/>
指定要显示替代用户键入的字符的字符。 如果*ch*为 0，则显示用户键入的实际字符。

### <a name="remarks"></a>备注

设置密码字符时，该角色将会显示有关每个字符的用户类型。

此成员函数具有多行编辑控件没有影响。

当`SetPasswordChar`调用成员函数时，`CEdit`将重绘所有可见的字符使用指定的字符*ch*。

如果使用创建编辑控件[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)样式，默认密码字符设置为星号 ( <strong>\*</strong>)。 如果删除此样式`SetPasswordChar`使用调用*ch*设置为 0。

有关详细信息，请参阅[EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

调用此函数可设置一个编辑控件的只读状态。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>参数

*bReadOnly*<br/>
指定是否设置或删除的编辑控件的只读状态。 值为 TRUE 将状态设置为只读的;FALSE 的值设置为读/写状态。

### <a name="return-value"></a>返回值

非零，如果操作成功，则为 0，如果错误发生。

### <a name="remarks"></a>备注

可以通过测试发现的当前设置[ES_READONLY](styles-used-by-mfc.md#edit-styles)中的返回值的标志[CWnd::GetStyle](cwnd-class.md#getstyle)。

有关详细信息，请参阅[EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

调用此函数可设置使用指定的坐标的矩形的尺寸。

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象，它指定格式设置矩形的新维度。

### <a name="remarks"></a>备注

此成员仅由多行编辑控件处理。

使用`SetRect`若要设置的格式设置矩形的多行编辑控件。 格式化矩形是大小的文本，这是大小的独立的编辑控件窗口的限制。 当首次创建编辑控件时，格式化矩形是编辑控件窗口的客户端区域相同。 通过使用`SetRect`成员函数，大于或小于编辑控件窗口，应用程序可以进行格式化的矩形。

如果编辑控件具有没有滚动条，文本将剪辑任何内容，不换行，如果超出窗口进行格式化的矩形。 如果编辑控件包含一个边框，由边框的大小减少格式化矩形。 如果调整返回的矩形`GetRect`成员函数之前，必须删除边框的大小将传递到矩形`SetRect`。

当`SetRect`调用时，编辑控件的文本还重新格式化和重新显示。

有关详细信息，请参阅[EM_SETRECT](/windows/desktop/Controls/em-setrect) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

调用此函数可设置多行编辑控件的格式设置的矩形。

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`RECT`结构或`CRect`对象，它指定新矩形的尺寸。

### <a name="remarks"></a>备注

格式化矩形是大小的文本，这是大小的独立的编辑控件窗口的限制。

`SetRectNP` 等同于`SetRect`成员函数，只不过编辑控件窗口不会重新绘制。

当首次创建编辑控件时，格式化矩形是编辑控件窗口的客户端区域相同。 通过调用`SetRectNP`成员函数，大于或小于编辑控件窗口，应用程序可以进行格式化的矩形。

如果编辑控件具有没有滚动条，文本将剪辑任何内容，不换行，如果超出窗口进行格式化的矩形。

此成员仅由多行编辑控件处理。

有关详细信息，请参阅[EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::SetRect](#setrect)。

##  <a name="setsel"></a>  CEdit::SetSel

调用此函数可在一个编辑控件中选择一系列字符。

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>参数

*dwSelection*<br/>
指定低序位字中的起始位置和高序位字中的结束位置。 如果低序位字是 0，高序位字是-1，则选择编辑控件中的所有文本。 如果低序位字为-1，则会删除任何当前所选内容。

*bNoScroll*<br/>
指示是否应将插入符号滚动到视图。 如果为 FALSE，则将插入符号滚动到视图。 如果为 TRUE，将插入符号不会滚动到视图。

*nStartChar*<br/>
指定的起始位置。 如果*nStartChar*为 0 并*nEndChar*为-1，所有选定的文本编辑控件中。 如果*nStartChar*为-1，删除任何当前所选内容。

*nEndChar*<br/>
指定的结束位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_SETSEL](/windows/desktop/Controls/em-setsel) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEdit::GetSel](#getsel)。

##  <a name="settabstops"></a>  CEdit::SetTabStops

调用此函数可在多行编辑控件中设置制表位。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>参数

*cxEachStop*<br/>
指定要在设置制表位每*cxEachStop*对话框单元为单位。

*nTabStops*<br/>
指定的制表位中包含数目*rgTabStops*。 此数字必须是大于 1。

*rgTabStops*<br/>
以对话框单元停止指向数组的指定选项卡上的无符号整数。 对话框单位是水平或垂直距离。 一个水平对话框单位等于 1 / 4 的当前对话框基本宽度单位，和 1 个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 `GetDialogBaseUnits` Windows 函数以像素为单位返回当前对话框基本单位。

### <a name="return-value"></a>返回值

设置选项卡; 如果非零值否则为 0。

### <a name="remarks"></a>备注

文本复制到多行编辑控件，在文本中的任何制表符会导致空间来生成最多的下一步的制表位。

若要设置制表位到 32 个对话框单位的默认大小，调用此成员函数的无参数版本。 若要设置制表位到 32 以外的大小，调用的版本与*cxEachStop*参数。 若要设置制表位大小的数组，使用含有两个参数的版本。

此成员函数仅由多行编辑控件处理。

`SetTabStops` 不会自动刷新编辑窗口。 如果更改已在编辑控件中的文本的制表位，请调用[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重绘编辑窗口。

有关详细信息，请参阅[EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops)并[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CEditView::SetTabStops](ceditview-class.md#settabstops)。

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

显示与当前的编辑控件相关联的气球提示。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pEditBalloonTip*|[in]指向[EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)结构描述的气球状提示。|
|*lpszTitle*|[in]包含标题的气球状提示的 Unicode 字符串指针。|
|*lpszText*|[in]包含气球状提示文本的 Unicode 字符串指针。|
|*ttiIcon*|[in]**INT**指定类型的图标的气球状提示相关联。 默认值为 TTI_NONE。 有关详细信息，请参阅`ttiIcon`的成员[EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)结构。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此函数发送[EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip)消息，Windows SDK 中所述。 有关详细信息，请参阅[Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip)宏。

### <a name="example"></a>示例

下面的代码示例定义一个变量， `m_cedit`，即用于访问当前的编辑控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>示例

下面的代码示例显示一个编辑控件的气球提示。 [CEdit::ShowBalloonTip](#showballoontip)方法指定标题和气球状提示文本。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

调用此函数可撤消的上一个编辑控件的操作。

```
BOOL Undo();
```

### <a name="return-value"></a>返回值

对于单行编辑控件，则返回值始终是非零值。 对于多行编辑控件，返回值不为零如果撤消操作成功，或如果撤消操作失败，则为 0。

### <a name="remarks"></a>备注

撤消操作还可以撤消。 例如，可以还原已删除的文本与首次调用`Undo`。 只要没有干预编辑操作，可以删除再次通过第二个调用文本`Undo`。

有关详细信息，请参阅[EM_UNDO](/windows/desktop/Controls/em-undo) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CALCDRIV](../../visual-cpp-samples.md)<br/>
[MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](cwnd-class.md)<br/>
[CButton 类](cbutton-class.md)<br/>
[CComboBox 类](ccombobox-class.md)<br/>
[CListBox 类](clistbox-class.md)<br/>
[CScrollBar 类](cscrollbar-class.md)<br/>
[CStatic 类](cstatic-class.md)<br/>
[CDialog 类](cdialog-class.md)
