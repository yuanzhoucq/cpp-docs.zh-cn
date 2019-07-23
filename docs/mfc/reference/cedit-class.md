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
ms.openlocfilehash: a66597f7a43e0730ae8b32369235ac860f51a0f1
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375857"
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
|[CEdit::CEdit](#cedit)|`CEdit`构造控件对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|确定是否可以撤消编辑控件操作。|
|[CEdit::CharFromPos](#charfrompos)|检索距离指定位置最近的字符的行和字符索引。|
|[CEdit::Clear](#clear)|删除 (清除) 编辑控件中的当前选择 (如果有)。|
|[CEdit::Copy](#copy)|以 CF_TEXT 格式将编辑控件中的当前选定内容 (如果有) 复制到剪贴板。|
|[CEdit::Create](#create)|创建 Windows 编辑控件, 并将其附加到`CEdit`对象。|
|[CEdit::Cut](#cut)|删除编辑控件中的当前选定内容 (如果有), 并以 CF_TEXT 格式将删除的文本复制到剪贴板。|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重置 (清除) 编辑控件的撤消标志。|
|[CEdit::FmtLines](#fmtlines)|设置在多行编辑控件中包含软换行符字符。|
|[CEdit::GetCueBanner](#getcuebanner)|当控件为空且不具有焦点时, 检索作为文本提示或提示显示在编辑控件中的文本。|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|确定编辑控件中最顶层的可见行。|
|[CEdit::GetHandle](#gethandle)|检索当前为多行编辑控件分配的内存的句柄。|
|[CEdit::GetHighlight](#gethighlight)|获取在当前编辑控件中突出显示的文本范围内的起始字符和结束字符的索引。|
|[CEdit::GetLimitText](#getlimittext)|获取此`CEdit`可包含的最大文本量。|
|[CEdit::GetLine](#getline)|从编辑控件中检索一行文本。|
|[CEdit::GetLineCount](#getlinecount)|检索多行编辑控件中的行数。|
|[CEdit::GetMargins](#getmargins)|获取此`CEdit`的左边距和右边距。|
|[CEdit::GetModify](#getmodify)|确定编辑控件的内容是否已被修改。|
|[CEdit::GetPasswordChar](#getpasswordchar)|检索用户输入文本时在编辑控件中显示的密码字符。|
|[CEdit::GetRect](#getrect)|获取编辑控件的格式设置矩形。|
|[CEdit::GetSel](#getsel)|获取编辑控件中当前选定内容的第一个和最后一个字符位置。|
|[CEdit::HideBalloonTip](#hideballoontip)|隐藏与当前编辑控件关联的任何气球状提示。|
|[CEdit::LimitText](#limittext)|限制用户可输入到编辑控件中的文本的长度。|
|[CEdit::LineFromChar](#linefromchar)|检索包含指定字符索引的行的行号。|
|[CEdit::LineIndex](#lineindex)|检索多行编辑控件中的行的字符索引。|
|[CEdit::LineLength](#linelength)|检索编辑控件中的行的长度。|
|[CEdit::LineScroll](#linescroll)|滚动多行编辑控件的文本。|
|[CEdit::Paste](#paste)|将剪贴板中的数据插入到当前光标位置的编辑控件中。 仅当剪贴板包含 CF_TEXT 格式的数据时, 才插入数据。|
|[CEdit::PosFromChar](#posfromchar)|检索指定字符索引的左上角的坐标。|
|[CEdit::ReplaceSel](#replacesel)|用指定的文本替换编辑控件中的当前选定内容。|
|[CEdit::SetCueBanner](#setcuebanner)|设置当控件为空且不具有焦点时, 在编辑控件中显示为文本提示或提示的文本。|
|[CEdit::SetHandle](#sethandle)|将句柄设置为多行编辑控件将使用的本地内存。|
|[CEdit::SetHighlight](#sethighlight)|突出显示当前编辑控件中显示的文本范围。|
|[CEdit::SetLimitText](#setlimittext)|设置此`CEdit`可包含的最大文本量。|
|[CEdit::SetMargins](#setmargins)|为此`CEdit`设置左边距和右边距。|
|[CEdit::SetModify](#setmodify)|设置或清除编辑控件的修改标志。|
|[CEdit::SetPasswordChar](#setpasswordchar)|设置或删除用户输入文本时在编辑控件中显示的密码字符。|
|[CEdit::SetReadOnly](#setreadonly)|设置编辑控件的只读状态。|
|[CEdit::SetRect](#setrect)|设置多行编辑控件的格式设置矩形并更新控件。|
|[CEdit::SetRectNP](#setrectnp)|设置多行编辑控件的格式设置矩形, 而不重绘控件窗口。|
|[CEdit::SetSel](#setsel)|选择编辑控件中的一系列字符。|
|[CEdit::SetTabStops](#settabstops)|在多行编辑控件中设置制表位。|
|[CEdit::ShowBalloonTip](#showballoontip)|显示与当前编辑控件关联的气球状提示。|
|[CEdit::Undo](#undo)|反转最后一个编辑控件操作。|

## <a name="remarks"></a>备注

编辑控件是一个矩形子窗口, 用户可以在其中输入文本。

你可以从对话框模板或直接在代码中创建 "编辑" 控件。 在这两种情况下, 首先`CEdit`调用构造函数`CEdit`来构造对象, 然后调用[create](#create)成员函数以创建 Windows `CEdit`编辑控件并将其附加到对象。

构造可以是从派生的`CEdit`类中的一个单步过程。 编写派生类的构造函数, 并从`Create`构造函数中调用。

`CEdit`从继承重要的`CWnd`功能。 若`CEdit`要设置和检索对象中的文本, 请`CWnd`使用成员函数[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext), 它设置或获取编辑控件的全部内容, 即使它是多行控件也是如此。 多行控件中的文本行由 "\r\n" 字符序列分隔。 此外, 如果编辑控件为多行, 则通过调用`CEdit`成员函数[GetLine](#getline)、 [SetSel](#setsel)、 [GetSel](#getsel)和[ReplaceSel](#replacesel)来获取和设置控件文本的部分文本。

如果要将编辑控件发送的 Windows 通知消息处理到其父级 (通常是派生自`CDialog`的类), 请将消息映射项和消息处理程序成员函数添加到每条消息的父类。

每个消息映射项都采用以下形式:

  **ON_** _NOTIFICATION_ **(** _id_ **,** _memberFxn_ **)**

其中`id`指定了发送通知的编辑控件的子窗口 ID `memberFxn` , 是您编写的用于处理通知的父成员函数的名称。

父的函数原型如下所示:

**afx_msg** void memberFxn **();**

下面是可能的消息映射项的列表, 以及要将它们发送到父级的情况的说明:

- ON_EN_CHANGE 用户执行了一项操作, 该操作可能会更改编辑控件中的文本。 与 EN_UPDATE 通知消息不同, 此通知消息在 Windows 更新显示后发送。

- ON_EN_ERRSPACE 编辑控件无法分配足够的内存来满足特定的请求。

- ON_EN_HSCROLL 用户单击编辑控件的水平滚动条。 更新屏幕之前, 会通知父窗口。

- ON_EN_KILLFOCUS 编辑控件丢失输入焦点。

- ON_EN_MAXTEXT 当前插入超出了编辑控件的指定字符数, 已被截断。 当编辑控件没有 ES_AUTOHSCROLL 样式并且要插入的字符数超过编辑控件的宽度时, 也会发送。 当编辑控件没有 ES_AUTOVSCROLL 样式, 并且文本插入导致的行总数超出编辑控件的高度时, 也会发送。

- ON_EN_SETFOCUS 在编辑控件接收输入焦点时发送。

- ON_EN_UPDATE 编辑控件即将显示已更改的文本。 在控件设置文本格式之后但在屏幕上发出文本后发送, 以便可以更改窗口大小 (如有必要)。

- ON_EN_VSCROLL 用户单击编辑控件的垂直滚动条。 更新屏幕之前, 会通知父窗口。

如果在对话框中`CEdit`创建一个对象, 则当用户`CEdit`关闭对话框时, 该对象会自动销毁。

如果使用对话框编辑器`CEdit`从对话框资源创建对象`CEdit` , 则当用户关闭对话框时, 对象会自动销毁。

如果在窗口中`CEdit`创建对象, 则可能还需要销毁它。 如果在堆栈上`CEdit`创建对象, 则该对象会自动销毁。 如果通过使用`CEdit` **新**函数在堆上创建对象, 则必须对对象调用**delete** , 以便在用户终止 Windows 编辑控件时销毁该对象。 如果在`CEdit`对象中分配任何内存, 请`CEdit`重写析构函数以释放分配。

若要修改编辑控件中的某些样式 (如 ES_READONLY), 必须将特定消息发送到控件, 而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 请参阅 Windows SDK 中的[编辑控件样式](/windows/desktop/Controls/edit-control-styles)。

有关的详细信息`CEdit`, 请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

调用此函数可确定是否可以撤消上一个编辑操作。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>返回值

如果通过调用`Undo`成员函数可以撤消最后一个编辑操作, 则为非零; 如果无法撤消, 则为0。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[EM_CANUNDO](/windows/desktop/Controls/em-canundo) 。

### <a name="example"></a>示例

  请参阅[CEdit:: Undo](#undo)的示例。

##  <a name="cedit"></a>CEdit:: CEdit

构造 `CEdit` 对象。

```
CEdit();
```

### <a name="remarks"></a>备注

使用[Create](#create)构造 Windows 编辑控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>CEdit:: CharFromPos

调用此函数可检索此`CEdit`控件中最接近指定点的字符的从零开始的行和字符索引

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>参数

*pt*<br/>
此`CEdit`对象的工作区中某个点的坐标。

### <a name="return-value"></a>返回值

低序位字中的字符索引和高位字中的行索引。

### <a name="remarks"></a>备注

> [!NOTE]
>  从 Windows 95 和 Windows NT 4.0 开始, 此成员函数可用。

有关详细信息, 请参阅 Windows SDK 中的[EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>CEdit:: Clear

调用此函数可删除 (清除) 编辑控件中的当前选择 (如果有)。

```
void Clear();
```

### <a name="remarks"></a>备注

`Clear`可以通过调用[Undo](#undo)成员函数来撤消执行的删除操作。

若要删除当前所选内容并将删除的内容放入剪贴板, 请调用[Cut](#cut)成员函数。

有关详细信息, 请参阅 Windows SDK 中的[WM_CLEAR](/windows/desktop/dataxchg/wm-clear) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

调用此函数可将编辑控件中的当前选择 (如果有) 要复制为 CF_TEXT 格式的剪贴板。

```
void Copy();
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[WM_COPY](/windows/desktop/dataxchg/wm-copy) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>CEdit:: Create

创建 Windows 编辑控件, 并将其附加到`CEdit`对象。

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

*rect*<br/>
指定编辑控件的大小和位置。 可以是`CRect`对象或`RECT`结构。

*pParentWnd*<br/>
指定编辑控件的父窗口 (通常为`CDialog`)。 它不能为 NULL。

*nID*<br/>
指定编辑控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过`CEdit`两个步骤构造对象。 首先, 调用`CEdit`构造函数, 然后调用`Create`, 它创建 Windows 编辑控件`CEdit`并将其附加到对象。

执行`Create`时, Windows 会将[WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate)、 [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize)、 [WM_CREATE](/windows/desktop/winmsg/wm-create)和[WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo)消息发送到编辑控件。

默认情况下, 将`CWnd`通过基类中的[OnNcCreate](cwnd-class.md#onnccreate)、 [OnNcCalcSize](cwnd-class.md#onnccalcsize)、 [OnCreate](cwnd-class.md#oncreate)和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成员函数来处理这些消息。 若要扩展默认消息处理, 请从`CEdit`派生类, 将消息映射添加到新类, 并重写上述消息处理程序成员函数。 例如`OnCreate`, 重写, 以便为新类执行所需的初始化。

将以下[窗口样式](styles-used-by-mfc.md#window-styles)应用于编辑控件。

- WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 极少

- WS_GROUP 到分组控件

- 按 tab 键顺序包含编辑控件的 WS_TABSTOP

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>CEdit:: Cut

调用此函数可删除 (剪切) 编辑控件中的当前选定内容 (如果有), 并以 CF_TEXT 格式将删除的文本复制到剪贴板。

```
void Cut();
```

### <a name="remarks"></a>备注

`Cut`可以通过调用[Undo](#undo)成员函数来撤消执行的删除操作。

若要删除当前所选内容而不将删除的文本放入剪贴板, 请调用[Clear](#clear)成员函数。

有关详细信息, 请参阅 Windows SDK 中的[WM_CUT](/windows/desktop/dataxchg/wm-cut) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

调用此函数可重置 (清除) 编辑控件的撤消标志。

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>备注

编辑控件现在无法撤消上一个操作。 只要编辑控件中的操作可以撤消, 就会设置 undo 标志。

调用[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle) `CWnd`成员函数时, 会自动清除 undo 标志。

有关详细信息, 请参阅 Windows SDK 中的[EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>CEdit:: FmtLines

调用此函数可设置在多行编辑控件中包含软换行符字符。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>参数

*bAddEOL*<br/>
指定是否要插入软换行字符。 如果值为 TRUE, 则插入字符;如果值为 FALSE, 则将其删除。

### <a name="return-value"></a>返回值

如果出现任何格式设置, 则为非零值;否则为0。

### <a name="remarks"></a>备注

软换行符由两个回车符和插入到由于换行而中断的行尾插入的换行。 硬分行符包含一个回车符和一个换行符。 以硬分行符结尾的行不受影响`FmtLines`。

仅当对象为多行`CEdit`编辑控件时, Windows 才会响应。

`FmtLines`仅影响由[GetHandle](#gethandle)返回的缓冲区和[WM_GETTEXT](/windows/desktop/winmsg/wm-gettext)返回的文本。 它不会影响编辑控件中的文本显示。

有关详细信息, 请参阅 Windows SDK 中的[EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

当控件为空时, 检索在编辑控件中显示为文本提示或提示的文本。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
弄指向包含提示文本的字符串的指针。

*cchText*<br/>
中可接收的字符数。 此数字包括终止 NULL 字符。

### <a name="return-value"></a>返回值

对于第一个重载, 如果方法成功, 则为 TRUE;否则为 FALSE。

对于第二个重载, 是指如果方法成功, 则为包含提示文本的[CString](../../atl-mfc-shared/using-cstring.md) ;否则为空字符串 ("")。

### <a name="remarks"></a>备注

此方法发送[EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner)消息, 如 Windows SDK 中所述。 有关详细信息, 请参阅[Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext)宏。

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

调用此函数可确定编辑控件中最顶层的可见行。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>返回值

最顶部可见行的从零开始的索引。 对于单行编辑控件, 返回值为0。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

调用此函数可检索当前为多行编辑控件分配的内存的句柄。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>返回值

一个本地内存句柄, 用于标识保存编辑控件内容的缓冲区。 如果发生错误, 如将消息发送到单行编辑控件, 则返回值为0。

### <a name="remarks"></a>备注

该句柄是一个本地内存句柄, 可由将本地内存句柄作为参数的任何**本地**Windows 内存函数使用。

`GetHandle`仅由多行编辑控件处理。

仅`GetHandle`当使用 DS_LOCALEDIT 样式标志设置创建对话框时, 才在对话框中为多行编辑控件调用。 如果未设置 DS_LOCALEDIT 样式, 则仍将获得一个非零返回值, 但你将无法使用返回值。

> [!NOTE]
> `GetHandle`不会与 Windows 95/98 一起使用。 如果在 Windows `GetHandle` 95/98 中调用, 它将返回 NULL。 `GetHandle`将按 Windows NT 版本3.51 及更高版本中所述的方式运行。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>CEdit:: GetHighlight

获取在当前编辑控件中突出显示的文本范围中的第一个字符和最后一个字符的索引。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pichStart*|弄突出显示的文本范围中第一个字符的从零开始的索引。|
|*pichEnd*|弄突出显示的文本范围中最后一个字符的从零开始的索引。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[EM_GETHILITE](/windows/desktop/Controls/em-gethilite)消息, 如 Windows SDK 中所述。 `SetHighlight` 和`GetHighlight`当前仅对 UNICODE 版本启用。

##  <a name="getlimittext"></a>  CEdit::GetLimitText

调用此成员函数以获取此`CEdit`对象的文本限制。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>返回值

此`CEdit`对象的当前文本限制 (在 TCHARs 中)。

### <a name="remarks"></a>备注

"文本限制" 是编辑控件可以接受的最大文本量 (以 TCHARs)。

> [!NOTE]
>  从 Windows 95 和 Windows NT 4.0 开始, 此成员函数可用。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

调用此函数可从编辑控件中检索一行文本, 并将其放在*lpszBuffer*中。

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
指定要从多行编辑控件中检索的行号。 行号从零开始;值0指定第一行。 单行编辑控件将忽略此参数。

*lpszBuffer*<br/>
指向接收行的副本的缓冲区。 缓冲区的第一个字必须指定可复制到缓冲区的最大 TCHARs 数。

*nMaxLength*<br/>
指定可以复制到缓冲区的最大 TCHAR 字符数。 `GetLine`在调用 Windows 之前, 将此值放在*lpszBuffer*的第一个字中。

### <a name="return-value"></a>返回值

实际复制的字符数。 如果*nIndex*指定的行号大于编辑控件中的行数, 则返回值为0。

### <a name="remarks"></a>备注

复制的行不包含 null 终止字符。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETLINE](/windows/desktop/Controls/em-getline) 。

### <a name="example"></a>示例

  请参阅[CEdit:: GetLineCount](#getlinecount)的示例。

##  <a name="getlinecount"></a>  CEdit::GetLineCount

调用此函数可检索多行编辑控件中的行数。

```
int GetLineCount() const;
```

### <a name="return-value"></a>返回值

一个整数, 其中包含多行编辑控件中的行数。 如果未在编辑控件中输入文本, 则返回值为1。

### <a name="remarks"></a>备注

`GetLineCount`仅由多行编辑控件处理。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>CEdit:: GetMargins

调用此成员函数以检索此编辑控件的左边距和右边距。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>返回值

低序位字中左边距的宽度和高位字中右边距的宽度。

### <a name="remarks"></a>备注

边距以像素为单位进行度量。

> [!NOTE]
>  从 Windows 95 和 Windows NT 4.0 开始, 此成员函数可用。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) 。

### <a name="example"></a>示例

  请参阅[CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)的示例。

##  <a name="getmodify"></a>  CEdit::GetModify

调用此函数可确定编辑控件的内容是否已被修改。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>返回值

如果编辑控件的内容已被修改, 则为非零值;如果保持不变, 则为0。

### <a name="remarks"></a>备注

Windows 将维护一个内部标志, 指示编辑控件的内容是否已更改。 当编辑控件是首次创建的, 并且还可以通过调用[SetModify](#setmodify)成员函数清除时, 清除此标志。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

调用此函数可检索用户输入文本时在编辑控件中显示的密码字符。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>返回值

指定要显示的字符而不是用户键入的字符。 如果不存在密码字符, 则返回值为 NULL。

### <a name="remarks"></a>备注

如果创建的编辑控件具有 ES_PASSWORD 样式, 则支持该控件的 DLL 决定默认密码字符。 清单或[nativemethods.initcommoncontrolsex](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)方法决定哪个 DLL 支持编辑控件。 如果 user32 支持编辑控件, 则默认密码字符为星号 ("*", U + 002A)。 如果 comctl32.dll 版本6支持编辑控件, 则默认字符为黑色圆圈 ("●"、U + 25CF)。 有关支持公共控件的 DLL 和版本的详细信息, 请参阅[Shell 和公共控件版本](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))。

此方法发送[EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

调用此函数可获取编辑控件的格式设置矩形。

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向接收格式设置矩形的结构。`RECT`

### <a name="remarks"></a>备注

格式设置矩形是文本的限制矩形, 它与编辑控件窗口的大小无关。

可以通过[SetRect](#setrect)和[SetRectNP](#setrectnp)成员函数修改多行编辑控件的格式设置矩形。

有关详细信息, 请参阅 Windows SDK 中的[EM_GETRECT](/windows/desktop/Controls/em-getrect) 。

### <a name="example"></a>示例

  请参阅[CEdit:: LimitText](#limittext)的示例。

##  <a name="getsel"></a>  CEdit::GetSel

调用此函数可通过使用返回值或参数, 获取编辑控件中当前所选内容 (如果有) 的起始字符位置和结束字符位置。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>参数

*nStartChar*<br/>
引用一个整数, 该整数将接收当前选定内容中第一个字符的位置。

*nEndChar*<br/>
引用一个整数, 该整数将接收超出当前选定内容末尾的第一个 nonselected 字符的位置。

### <a name="return-value"></a>返回值

返回 DWORD 的版本返回一个值, 该值包含低序位字中的起始位置, 以及在高位字中选定内容末尾后的第一个 nonselected 字符的位置。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[EM_GETSEL](/windows/desktop/Controls/em-getsel) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

隐藏与当前编辑控件关联的任何气球状提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此函数发送[EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip)消息, 如 Windows SDK 中所述。

##  <a name="limittext"></a>  CEdit::LimitText

调用此函数可限制用户可在编辑控件中输入的文本的长度。

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>参数

*nChars*<br/>
指定用户可输入的文本的长度 (在 TCHARs 中)。 如果此参数为 0, 则文本长度设置为 UINT_MAX 个字节。 这是默认行为。

### <a name="remarks"></a>备注

更改文本限制仅限制用户可输入的文本。 它不会影响编辑控件中已有的任何文本, 也不会影响中`CWnd`的[SetWindowText](cwnd-class.md#setwindowtext)成员函数复制到编辑控件中的文本长度。 如果应用程序使用`SetWindowText`函数将更多的文本放入编辑控件中`LimitText`, 而不是调用中指定的, 则用户可以删除编辑控件中的任何文本。 但是, 文本限制会阻止用户将现有文本替换为新文本, 除非删除当前所选内容会导致文本小于文本限制。

> [!NOTE]
>  在 Win32 (Windows NT 和 Windows 95/98) 中, [SetLimitText](#setlimittext)将替换此函数。

有关详细信息, 请参阅 Windows SDK 中的[EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>CEdit:: LineFromChar

调用此函数可检索包含指定字符索引的行的行号。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
包含编辑控件文本中所需字符的从零开始的索引值, 或包含-1。 如果*nIndex*为-1, 则它指定当前行, 即包含插入符号的行。

### <a name="return-value"></a>返回值

包含由*nIndex*指定的字符索引的行的从零开始的行号。 如果*nIndex*为-1, 则返回包含所选内容的第一个字符的行号。 如果未选择任何内容, 则返回当前行号。

### <a name="remarks"></a>备注

字符索引是编辑控件开头的字符数。

此成员函数仅由多行编辑控件使用。

有关详细信息, 请参阅 Windows SDK 中的[EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

调用此函数可检索多行编辑控件中的行的字符索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*nLine*<br/>
在编辑控件的文本中包含所需行的索引值, 或包含-1。 如果*n 第*为-1, 则它指定当前行, 即包含插入符号的行。

### <a name="return-value"></a>返回值

在*n 第*中指定的行的字符索引, 如果指定的行号大于编辑控件中的行数, 则为-1。

### <a name="remarks"></a>备注

字符索引是从编辑控件开始到指定行的字符数。

此成员函数只由多行编辑控件处理。

有关详细信息, 请参阅 Windows SDK 中的[EM_LINEINDEX](/windows/desktop/controls/em-lineindex) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>CEdit:: LineLength

检索编辑控件中的行的长度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>参数

*nLine*<br/>
要检索其长度的行中的字符的从零开始的索引。 默认值为 -1。

### <a name="return-value"></a>返回值

对于单行编辑控件, 返回值为 TCHARs 中的文本在编辑控件中的长度。

对于多行编辑控件, 返回值为 TCHARs 中由*n 第*参数指定的行的长度。 对于 ANSI 文本, 长度为行中的字节数;对于 Unicode 文本, 长度为行中的字符数。 长度不包括行尾的回车符。

如果*n 第*参数大于控件中的字符数, 则返回值为零。

如果*n 第*参数为-1, 则返回值为包含所选字符的行中未选择的字符数。 例如, 如果所选内容从一行的第四个字符到下一行末尾的第八个字符, 则返回值为10。 这就是, 第一行中有三个字符, 接下来是七个字符。

有关 TCHAR 类型的详细信息, 请参阅[Windows 数据类型](/windows/desktop/WinProg/windows-data-types)表中的 TCHAR 行。

### <a name="remarks"></a>备注

[EM_LINELENGTH](/windows/desktop/Controls/em-linelength)消息支持此方法, 该消息在 Windows SDK 中进行了介绍。

### <a name="example"></a>示例

  请参阅[CEdit:: LineIndex](#lineindex)的示例。

##  <a name="linescroll"></a>CEdit:: LineScroll

调用此函数可滚动多行编辑控件的文本。

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>参数

*nLines*<br/>
指定垂直滚动的行数。

*nChars*<br/>
指定要水平滚动的字符位置数。 如果编辑控件具有 ES_RIGHT 或 ES_CENTER 样式, 则将忽略此值。

### <a name="remarks"></a>备注

仅多行编辑控件处理此成员函数。

编辑控件不会垂直滚动于编辑控件中的最后一行文本。 如果当前行加上*nLines*指定的行数超过了编辑控件中的总行数, 则将调整该值, 以便将编辑控件的最后一行滚动到编辑控件窗口的顶部。

`LineScroll`可用于水平滚动越过任意行的最后一个字符。

有关详细信息, 请参阅 Windows SDK 中的[EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) 。

### <a name="example"></a>示例

  请参阅[CEdit:: GetFirstVisibleLine](#getfirstvisibleline)的示例。

##  <a name="paste"></a>CEdit::P aste

调用此函数可将剪贴板`CEdit`中的数据插入到中的插入点处。

```
void Paste();
```

### <a name="remarks"></a>备注

仅当剪贴板包含 CF_TEXT 格式的数据时, 才插入数据。

有关详细信息, 请参阅 Windows SDK 中的[WM_PASTE](/windows/desktop/dataxchg/wm-paste) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

调用此函数可获取此`CEdit`对象内给定字符的位置 (左上角)。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>参数

*nChar*<br/>
指定字符的从零开始的索引。

### <a name="return-value"></a>返回值

由*nChar*指定的字符的左上角的坐标。

### <a name="remarks"></a>备注

字符是通过提供其从零开始的索引值来指定的。 如果*nChar*大于此`CEdit`对象中最后一个字符的索引, 则返回值指定紧随此`CEdit`对象中最后一个字符的字符位置的坐标。

> [!NOTE]
>  从 Windows 95 和 Windows NT 4.0 开始, 此成员函数可用。

有关详细信息, 请参阅 Windows SDK 中的[EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) 。

### <a name="example"></a>示例

  请参阅[CEdit:: LineFromChar](#linefromchar)的示例。

##  <a name="replacesel"></a>  CEdit::ReplaceSel

调用此函数可将编辑控件中的当前选定内容替换为*lpszNewText*指定的文本。

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>参数

*lpszNewText*<br/>
指向以 null 结尾的字符串, 该字符串包含替换文本。

*bCanUndo*<br/>
若要指定此函数可以撤消, 请将此参数的值设置为 TRUE。 默认值是 FALSE。

### <a name="remarks"></a>备注

仅替换编辑控件中的部分文本。 如果要替换所有文本, 请使用[CWnd:: SetWindowText](cwnd-class.md#setwindowtext)成员函数。

如果当前没有选定内容, 则将在当前光标位置插入替换文本。

有关详细信息, 请参阅 Windows SDK 中的[EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) 。

### <a name="example"></a>示例

  请参阅[CEdit:: LineIndex](#lineindex)的示例。

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

当控件为空时, 将显示的文本设置为 "编辑" 控件中的文本提示或提示。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
中指向字符串的指针, 该字符串包含要在编辑控件中显示的提示。

*fDrawWhenFocused*<br/>
中如果为 FALSE, 则当用户在编辑控件中单击并向控件提供焦点时不绘制提示横幅。

如果为 TRUE, 则即使控件具有焦点, 也会绘制提示横幅。 当用户开始在控件中键入时, 提示横幅就会消失。

默认值是 FALSE。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner)消息, 如 Windows SDK 中所述。 有关详细信息, 请参阅[Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)宏。

### <a name="example"></a>示例

下面的示例演示了[CEdit:: SetCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

调用此函数可将句柄设置为多行编辑控件将使用的本地内存。

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>参数

*hBuffer*<br/>
包含本地内存的句柄。 此句柄必须已通过对使用 LMEM_MOVEABLE 标志的[LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) Windows 函数的先前调用创建。 假定内存包含以 null 结尾的字符串。 如果不是这种情况, 则分配的内存的第一个字节应设置为0。

### <a name="remarks"></a>备注

然后, 编辑控件将使用此缓冲区来存储当前显示的文本, 而不是分配其自己的缓冲区。

仅多行编辑控件处理此成员函数。

在应用程序设置新的内存句柄之前, 它应使用[GetHandle](#gethandle)成员函数获取当前内存缓冲区的句柄, 并使用`LocalFree` Windows 函数释放该内存。

`SetHandle`清除撤消缓冲区 ( [CanUndo](#canundo)成员函数随后返回 0) 和内部修改标志 ( [GetModify](#getmodify)成员函数返回 0)。 重绘编辑控件窗口。

只有在创建了具有 DS_LOCALEDIT 样式标志的对话框后, 才可以在对话框的多行编辑控件中使用此成员函数。

> [!NOTE]
> `GetHandle`不会与 Windows 95/98 一起使用。 如果在 Windows `GetHandle` 95/98 中调用, 它将返回 NULL。 `GetHandle`将按 Windows NT 版本3.51 及更高版本中所述的方式运行。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETHANDLE](/windows/desktop/Controls/em-sethandle)、 [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)和[LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>CEdit:: SetHighlight

突出显示当前编辑控件中显示的文本范围。

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*ichStart*|中要突出显示的文本范围中第一个字符的从零开始的索引。|
|*ichEnd*|中要突出显示的文本范围中最后一个字符的从零开始的索引。|

### <a name="remarks"></a>备注

此方法发送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)消息, 如 Windows SDK 中所述。  此方法发送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)消息, 如 Windows SDK 中所述。 `SetHighlight` 和`GetHighlight`仅对 UNICODE 生成启用。

##  <a name="setlimittext"></a>  CEdit::SetLimitText

调用此成员函数以设置此`CEdit`对象的文本限制。

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
新文本限制 (字符)。

### <a name="remarks"></a>备注

"文本限制" 是编辑控件可以接受的最大文本量 (字符数)。

更改文本限制仅限制用户可输入的文本。 它不会影响编辑控件中已有的任何文本, 也不会影响中`CWnd`的[SetWindowText](cwnd-class.md#setwindowtext)成员函数复制到编辑控件中的文本长度。 如果应用程序使用`SetWindowText`函数将更多的文本放入编辑控件中`LimitText`, 而不是调用中指定的, 则用户可以删除编辑控件中的任何文本。 但是, 文本限制会阻止用户将现有文本替换为新文本, 除非删除当前所选内容会导致文本小于文本限制。

此函数替换 Win32 中的[LimitText](#limittext) 。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) 。

### <a name="example"></a>示例

  请参阅[CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)的示例。

##  <a name="setmargins"></a>CEdit:: SetMargins

调用此方法可设置此编辑控件的左边距和右边距。

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>参数

*nLeft*<br/>
新左边距的宽度 (以像素为单位)。

*nRight*<br/>
新右边缘的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

> [!NOTE]
>  从 Windows 95 和 Windows NT 4.0 开始, 此成员函数可用。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) 。

### <a name="example"></a>示例

  请参阅[CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)的示例。

##  <a name="setmodify"></a>  CEdit::SetModify

调用此函数可设置或清除编辑控件的修改标志。

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*bModified*<br/>
如果值为 TRUE, 则表示文本已修改, 值为 FALSE 表示未修改该文本。 默认情况下, 已修改的标志设置为。

### <a name="remarks"></a>备注

修改后的标志指示编辑控件中的文本是否已被修改。 每当用户更改文本时, 将自动设置该设置。 可以通过[GetModify](#getmodify)成员函数检索其值。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) 。

### <a name="example"></a>示例

  请参阅[CEdit:: GetModify](#getmodify)的示例。

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

调用此函数可设置或删除用户键入文本时在编辑控件中显示的密码字符。

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>参数

*ch*<br/>
指定要显示的字符, 以代替用户键入的字符。 如果*ch*为 0, 则显示用户键入的实际字符。

### <a name="remarks"></a>备注

如果设置了密码字符, 则会为用户键入的每个字符显示该字符。

此成员函数对于多行编辑控件不起作用。

调用成员函数时, `CEdit`将使用 ch 指定的字符重绘所有可见字符。  `SetPasswordChar`

如果使用[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)样式创建编辑控件, 则默认密码字符将设置为星号 ( <strong>\*</strong>)。 如果`SetPasswordChar`在*ch*设置为0的情况下调用, 则删除此样式。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

调用此函数可设置编辑控件的只读状态。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>参数

*bReadOnly*<br/>
指定是设置还是删除编辑控件的只读状态。 如果值为 TRUE, 则将状态设置为只读;如果值为 FALSE, 则将状态设置为读/写。

### <a name="return-value"></a>返回值

如果操作成功, 则为非零; 如果发生错误, 则为0。

### <a name="remarks"></a>备注

可以通过在[CWnd:: GetStyle](cwnd-class.md#getstyle)的返回值中测试[ES_READONLY](styles-used-by-mfc.md#edit-styles)标志来找到当前设置。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

调用此函数可使用指定的坐标设置矩形的尺寸。

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向结构或对象, `CRect`该结构或对象指定格式设置矩形的新尺寸。 `RECT`

### <a name="remarks"></a>备注

仅多行编辑控件处理此成员。

用于`SetRect`设置多行编辑控件的格式设置矩形。 格式设置矩形是文本的限制矩形, 它与编辑控件窗口的大小无关。 首次创建编辑控件时, 格式设置矩形与编辑控件窗口的工作区相同。 使用`SetRect`成员函数, 应用程序可以使格式设置矩形大于或小于编辑控件窗口。

如果编辑控件没有滚动条, 则在设置格式设置的矩形比窗口大时, 将会对文本进行剪裁, 而不会换行。 如果编辑控件包含边框, 则格式设置矩形会按边框大小减小。 如果调整由`GetRect`成员函数返回的矩形, 则在将该矩形传递到`SetRect`之前, 必须先删除边框的大小。

调用`SetRect`时, 还会重新格式化并重新显示编辑控件的文本。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETRECT](/windows/desktop/Controls/em-setrect) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

调用此函数可设置多行编辑控件的格式设置矩形。

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向指定矩形的新`CRect`尺寸的结构或对象。`RECT`

### <a name="remarks"></a>备注

格式设置矩形是文本的限制矩形, 它与编辑控件窗口的大小无关。

`SetRectNP`与`SetRect`成员函数相同, 只不过不重绘编辑控件窗口。

首次创建编辑控件时, 格式设置矩形与编辑控件窗口的工作区相同。 通过调用`SetRectNP`成员函数, 应用程序可以使格式设置矩形大于或小于编辑控件窗口。

如果编辑控件没有滚动条, 则在设置格式设置的矩形比窗口大时, 将会对文本进行剪裁, 而不会换行。

仅多行编辑控件处理此成员。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) 。

### <a name="example"></a>示例

  请参阅[CEdit:: SetRect](#setrect)的示例。

##  <a name="setsel"></a>  CEdit::SetSel

调用此函数可选择编辑控件中的一系列字符。

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
指定低序位字中的起始位置和高位字中的结束位置。 如果低序位字为 0, 高序位字为-1, 则将选中 "编辑" 控件中的所有文本。 如果低序位字为-1, 则将删除当前选择的内容。

*bNoScroll*<br/>
指示插入符号是否应滚动到视图中。 如果为 FALSE, 则在视图中滚动插入符号。 如果为 TRUE, 则不滚动插入符号。

*nStartChar*<br/>
指定起始位置。 如果*nStartChar*为 0, *nEndChar*为-1, 则将选中 "编辑" 控件中的所有文本。 如果*nStartChar*为-1, 则将删除当前选择的内容。

*nEndChar*<br/>
指定结束位置。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[EM_SETSEL](/windows/desktop/Controls/em-setsel) 。

### <a name="example"></a>示例

  请参阅[CEdit:: GetSel](#getsel)的示例。

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
指定要在每个*cxEachStop*对话框单位设置制表位。

*nTabStops*<br/>
指定包含在*rgTabStops*中的制表位的数目。 此数字必须大于1。

*rgTabStops*<br/>
指向指定对话框单位中的制表位的无符号整数数组。 对话单位为水平或垂直距离。 一个水平对话框单位等于当前 "对话框基本宽度单位" 的四分之一, 1 个垂直对话单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 `GetDialogBaseUnits` Windows 函数以像素为单位返回当前的对话框基本单位。

### <a name="return-value"></a>返回值

如果设置了选项卡, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当文本复制到多行编辑控件时, 文本中的任何制表符都将导致生成空间, 直到下一个制表位。

若要将制表位设置为默认大小32对话单位, 请调用此成员函数的无参数版本。 若要将制表位设置为32以外的其他大小, 请使用*cxEachStop*参数调用该版本。 若要将制表位设置为大小数组, 请使用具有两个参数的版本。

此成员函数只由多行编辑控件处理。

`SetTabStops`不会自动重绘编辑窗口。 如果更改了编辑控件中已有文本的制表位, 请调用[CWnd:: InvalidateRect](cwnd-class.md#invalidaterect)以重新绘制编辑窗口。

有关详细信息, 请参阅 Windows SDK 中的[EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops)和[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) 。

### <a name="example"></a>示例

  请参阅[CEditView:: SetTabStops](ceditview-class.md#settabstops)的示例。

##  <a name="showballoontip"></a>CEdit:: ShowBalloonTip

显示与当前编辑控件关联的气球状提示。

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
|*pEditBalloonTip*|中指向[EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)结构的指针, 该结构描述了气球提示。|
|*lpszTitle*|中指向一个 Unicode 字符串的指针, 该字符串包含气球状提示的标题。|
|*lpszText*|中指向包含气球提示文本的 Unicode 字符串的指针。|
|*ttiIcon*|中一个**INT** , 指定与气球状提示相关联的图标类型。 默认值为 TTI_NONE。 有关详细信息, 请参阅`ttiIcon` [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)结构的成员。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此函数发送[EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip)消息, 如 Windows SDK 中所述。 有关详细信息, 请参阅[Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip)宏。

### <a name="example"></a>示例

下面的代码示例定义了一个用于`m_cedit`访问当前编辑控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>示例

下面的代码示例显示了编辑控件的气球提示。 [CEdit:: ShowBalloonTip](#showballoontip)方法指定标题和气球提示文本。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>CEdit:: Undo

调用此函数可撤消最后一个编辑控件操作。

```
BOOL Undo();
```

### <a name="return-value"></a>返回值

对于单行编辑控件, 返回值始终为非零值。 对于多行编辑控件, 如果撤消操作成功, 则返回值为非零; 如果撤消操作失败, 则返回0。

### <a name="remarks"></a>备注

撤消操作还可以撤消。 例如, 你可以在首次调用`Undo`时还原已删除的文本。 只要没有干预编辑操作, 就可以使用第二次调用`Undo`删除文本。

有关详细信息, 请参阅 Windows SDK 中的[EM_UNDO](/windows/desktop/Controls/em-undo) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](cwnd-class.md)<br/>
[CButton 类](cbutton-class.md)<br/>
[CComboBox 类](ccombobox-class.md)<br/>
[CListBox 类](clistbox-class.md)<br/>
[CScrollBar 类](cscrollbar-class.md)<br/>
[CStatic 类](cstatic-class.md)<br/>
[CDialog 类](cdialog-class.md)
