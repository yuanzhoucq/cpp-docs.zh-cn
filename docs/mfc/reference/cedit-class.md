---
title: "CEdit 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4418f20b267218b761dd6637762df1b420e9ac6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CEdit::CanUndo](#canundo)|确定是否可以撤消运算编辑控件。|  
|[CEdit::CharFromPos](#charfrompos)|检索距离指定位置最近的字符的行和字符索引。|  
|[CEdit::Clear](#clear)|删除 （清除） 中编辑的当前选择 （如果有的话） 控制。|  
|[CEdit::Copy](#copy)|复制当前选定内容 （如果有） 中的编辑控件到剪贴板中**CF_TEXT**格式。|  
|[CEdit::Create](#create)|创建 Windows 编辑控件并将其附加到`CEdit`对象。|  
|[CEdit::Cut](#cut)|删除 （操作会剪切） 中编辑的当前选择 （如果有的话） 控制，并将已删除的文本复制到剪贴板中**CF_TEXT**格式。|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重置 （清除） 编辑的撤消标志控制。|  
|[CEdit::FmtLines](#fmtlines)|打开或关闭多行编辑控件中设置软换行字符的包含。|  
|[CEdit::GetCueBanner](#getcuebanner)|检索作为文本提示或提示，当控件是空的不具有焦点的编辑控件中显示的文本。|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|确定在编辑控件中最顶层可见的行。|  
|[CEdit::GetHandle](#gethandle)|检索当前为多行编辑控件分配的内存的句柄。|  
|[CEdit::GetHighlight](#gethighlight)|获取起始和结束当前编辑控件中突出显示的文本范围内的字符的索引。|  
|[CEdit::GetLimitText](#getlimittext)|获取最大的文本量此`CEdit`可以包含。|  
|[CEdit::GetLine](#getline)|从一个编辑控件中检索文本行。|  
|[CEdit::GetLineCount](#getlinecount)|检索多行编辑控件中的行数。|  
|[CEdit::GetMargins](#getmargins)|获取此左边距和右边距`CEdit`。|  
|[CEdit::GetModify](#getmodify)|确定是否已修改编辑控件的内容。|  
|[CEdit::GetPasswordChar](#getpasswordchar)|检索时用户输入的文本编辑控件中显示的密码字符。|  
|[CEdit::GetRect](#getrect)|获取编辑控件的格式设置矩形。|  
|[CEdit::GetSel](#getsel)|获取编辑控件中的当前选择的第一个和最后一个字符位置。|  
|[CEdit::HideBalloonTip](#hideballoontip)|隐藏任何与当前的编辑控件相关联的气球状提示。|  
|[CEdit::LimitText](#limittext)|限制用户可以输入在编辑控件的文本的长度。|  
|[CEdit::LineFromChar](#linefromchar)|检索包含指定的字符索引的行的行号。|  
|[CEdit::LineIndex](#lineindex)|检索多行编辑控件内的行的字符索引。|  
|[CEdit::LineLength](#linelength)|检索一个编辑控件中的行的长度。|  
|[CEdit::LineScroll](#linescroll)|滚动的多行编辑控件的文本。|  
|[CEdit::Paste](#paste)|将数据从剪贴板插入当前光标位置处的编辑控件。 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。|  
|[CEdit::PosFromChar](#posfromchar)|检索指定的字符索引的左上角的坐标。|  
|[CEdit::ReplaceSel](#replacesel)|在编辑控件中的当前所选内容替换为指定的文本。|  
|[CEdit::SetCueBanner](#setcuebanner)|设置为文本提示或提示，当控件是空的不具有焦点的编辑控件中显示的文本。|  
|[CEdit::SetHandle](#sethandle)|设置多行编辑控件将使用的本地内存的句柄。|  
|[CEdit::SetHighlight](#sethighlight)|突出显示了一个在当前显示的文本范围的编辑控件。|  
|[CEdit::SetLimitText](#setlimittext)|此设置文本的最长`CEdit`可以包含。|  
|[CEdit::SetMargins](#setmargins)|设置左边距和右边距此`CEdit`。|  
|[CEdit::SetModify](#setmodify)|设置或清除编辑控件的修改标志。|  
|[CEdit::SetPasswordChar](#setpasswordchar)|设置或删除时用户输入的文本编辑控件中显示的密码字符。|  
|[CEdit::SetReadOnly](#setreadonly)|设置一个编辑控件的只读状态。|  
|[CEdit::SetRect](#setrect)|设置多行编辑控件的格式设置的矩形和更新控件。|  
|[CEdit::SetRectNP](#setrectnp)|不重绘控件窗口的情况下设置多行编辑控件的格式设置矩形。|  
|[CEdit::SetSel](#setsel)|在编辑控件中选择某个范围的字符。|  
|[CEdit::SetTabStops](#settabstops)|设置制表位的多个行中编辑控件。|  
|[CEdit::ShowBalloonTip](#showballoontip)|显示与当前的编辑控件相关联的气球状提示。|  
|[CEdit::Undo](#undo)|反转的上一个编辑控件的操作。|  
  
## <a name="remarks"></a>备注  
 编辑控件是用户可以在其中输入文本矩形子窗口。  
  
 从对话框模板或直接在代码中，可以创建一个编辑控件。 在这两种情况下，第一次调用的构造函数`CEdit`构造`CEdit`对象，然后调用[创建](#create)成员函数来创建 Windows 编辑控件，并将其附加到`CEdit`对象。  
  
 构造可以是派生自类中的一步过程`CEdit`。 编写派生的类和调用构造函数**创建**从构造函数中。  
  
 `CEdit`继承中的重要功能`CWnd`。 若要设置和检索文本从`CEdit`对象，请使用`CWnd`成员函数[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，编辑的全部内容的 set 或 get 控制，即使它是一个多行控件。 由 \r\n 字符序列分隔的多行控件中的文本行。 此外，如果多行编辑控件，获取和设置控件的文本的一部分调用`CEdit`成员函数[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，和[ReplaceSel](#replacesel)。  
  
 如果你想要处理到其父发送的编辑控件的 Windows 通知消息 (通常从派生的类`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。  
  
 每个消息映射条目采用以下形式：  
  
 **ON_**通知**(** *id、 f x n***)**  
  
 其中`id`指定发送通知，编辑控件的子窗口 ID 和`memberFxn`是父成员函数编写以处理通知的名称。  
  
 父元素的函数原型如下所示：  
  
 **afx_msg** void f x n **（);**  
  
 以下是潜在的消息映射项和将给父级发送的用例的说明的列表：  
  
- **ON_EN_CHANGE**用户已执行可能更改编辑控件中的文本的操作。 与不同**EN_UPDATE**通知消息，此通知消息发送后 Windows 更新显示。  
  
- **ON_EN_ERRSPACE**编辑控件无法分配足够的内存来满足特定的请求。  
  
- **ON_EN_HSCROLL**用户单击编辑控件的水平滚动条。 更新屏幕之前，父窗口都会收到通知。  
  
- **ON_EN_KILLFOCUS**编辑控件失去输入的焦点。  
  
- **ON_EN_MAXTEXT**当前插入已超出指定的编辑控件的字符数，已被截断。 编辑控件不具有时，也发送**ES_AUTOHSCROLL**样式和要插入的字符数将超过编辑控件的宽度。 编辑控件不具有时，也发送**ES_AUTOVSCROLL**样式和文本插入导致总行数将超过编辑控件的高度。  
  
- **ON_EN_SETFOCUS**编辑控件接收到输入的焦点时发送。  
  
- **ON_EN_UPDATE**即将显示修改后的文本编辑控件。 发送控件设置文本格式之后，但之前它屏幕文本以便可更改窗口大小，如有必要。  
  
- **ON_EN_VSCROLL**用户单击编辑控件的垂直滚动条。 更新屏幕之前，父窗口都会收到通知。  
  
 如果你创建`CEdit`在对话框中，对象`CEdit`当用户关闭对话框中，将自动销毁对象。  
  
 如果你创建`CEdit`对话框资源使用对话框编辑器中，从对象`CEdit`当用户关闭对话框中，将自动销毁对象。  
  
 如果你创建`CEdit`对象在窗口中，你可能还需要将其销毁。 如果你创建`CEdit`对象在堆栈上，自动销毁。 如果你创建`CEdit`使用堆上的对象**新**函数，必须调用**删除**在对象销毁它，当用户终止 Windows 编辑控件。 如果分配任何内存`CEdit`对象，请重写`CEdit`析构函数，若要释放的分配。  
  
 若要修改的编辑控件中的某些样式 (如**ES_READONLY**) 必须将特定的消息发送到控件而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 请参阅[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)Windows SDK 中。  
  
 有关详细信息`CEdit`，请参阅：  
  
- [控件](../../mfc/controls-mfc.md)  
  
-   知识库文章 Q259949： 信息： SetCaretPos() 是不适合与 CEdit 或 CRichEditCtrl 控件  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="canundo"></a>CEdit::CanUndo  
 调用此函数可确定是否可以撤消上一个编辑操作。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以通过调用撤消上一个编辑操作则不为**撤消**成员函数; 如果它不能撤消则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::Undo](#undo)。  
  
##  <a name="cedit"></a>CEdit::CEdit  
 构造 `CEdit` 对象。  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>备注  
 使用[创建](#create)构造 Windows 编辑控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="charfrompos"></a>CEdit::CharFromPos  
 调用此函数可检索的从零开始的行和最近在此指定的点的字符的字符索引`CEdit`控件  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 此点的工作区的坐标`CEdit`对象。  
  
### <a name="return-value"></a>返回值  
 低顺序中的字符索引**WORD**，高顺序中的行索引和**WORD**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此成员函数是与 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="clear"></a>CEdit::Clear  
 调用此函数可删除 （清除） 当前所选内容 （如果有） 中的编辑控件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 删除由**清除**可以通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容并将已删除的内容放入剪贴板，调用[剪切](#cut)成员函数。  
  
 有关详细信息，请参阅[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="copy"></a>CEdit::Copy  
 调用此函数可对若要复制当前所选内容 （如果有） 到剪贴板中的编辑控件中**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="create"></a>CEdit::Create  
 创建 Windows 编辑控件并将其附加到`CEdit`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定编辑控件的样式。 应用的任意组合[编辑样式](edit-styles.md)到控件。  
  
 `rect`  
 指定编辑控件的大小和位置。 可以是`CRect`对象或`RECT`结构。  
  
 `pParentWnd`  
 指定编辑控件的父窗口 (通常`CDialog`)。 它不能**NULL**。  
  
 `nID`  
 指定编辑控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CEdit`两个步骤中的对象。 首先，调用`CEdit`构造函数，然后调用**创建**，它创建 Windows 编辑控件并将其附加到`CEdit`对象。  
  
 当**创建**执行 Windows 发送[WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635)， [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634)， [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619)，和[WM_GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626)的编辑控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，从派生类`CEdit`、 将消息映射添加到新的类中，和重写上面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](window-styles.md)向一个编辑控件。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**与组控件  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的编辑控件  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="cut"></a>CEdit::Cut  
 编辑控件中调用此函数可删除 （剪切） 当前所选内容 （如果有） 并将已删除的文本复制到剪贴板中**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 删除由**剪切**可以通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容，而无需将删除的文本放入剪贴板，调用[清除](#clear)成员函数。  
  
 有关详细信息，请参阅[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer  
 编辑控件的撤消标志调用此函数可重置 （清除）。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>备注  
 编辑控件现在将不能撤消上一操作。 编辑控件中的某个操作可用于撤消时，均设置还原标志。  
  
 撤消标志将自动清除每当[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle) `CWnd`成员函数的调用。  
  
 有关详细信息，请参阅[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="fmtlines"></a>CEdit::FmtLines  
 调用此函数可设置多行编辑控件内包含的软换行字符的打开或关闭。  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>参数  
 *bAddEOL*  
 指定是否要插入软换行字符。 值为**TRUE**插入以下字符:; 值为**FALSE**中删除它们。  
  
### <a name="return-value"></a>返回值  
 如果任何非零设置格式的时间;否则为 0。  
  
### <a name="remarks"></a>备注  
 软换行符由两个回车和换行的行中断因的自动换行的结尾处插入组成。 硬盘换行符组成一个回车符和换行符。 以硬盘换行符结尾的行不受`FmtLines`。  
  
 如果将只会响应 Windows`CEdit`对象是一个多行编辑控件。  
  
 `FmtLines`只会影响返回的缓冲区[GetHandle](#gethandle)和返回的文本[WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627)。 它不起作用的编辑控件中的文本的显示。  
  
 有关详细信息，请参阅[EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="getcuebanner"></a>CEdit::GetCueBanner  
 检索作为文本提示或提示，当为空时控件的编辑控件中显示的文本。  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `lpszText`  
 指向包含提示文本的字符串的指针。  
  
 [in] `cchText`  
 可接收的字符数。 此数字包括终止`NULL`字符。  
  
### <a name="return-value"></a>返回值  
 第一个重载，`true`如果方法成功，否则为`false`。  
  
 第二个重载， [CString](../../atl-mfc-shared/using-cstring.md) ，包含的提示文本，如果该方法是成功; 否则为空字符串 ("")。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572)消息，Windows SDK 中介绍。 有关详细信息，请参阅[Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695)宏。  
  
##  <a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine  
 调用此函数可确定在编辑控件中最顶层可见的行。  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>返回值  
 最顶层的可见行的从零开始索引。 对于单行编辑控件，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="gethandle"></a>CEdit::GetHandle  
 调用此函数可检索为多行编辑控件中当前分配的内存的句柄。  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 标识保存编辑控件的内容的缓冲区本地内存句柄。 如果发生错误，例如消息发送到的单行编辑控件，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 句柄本地内存句柄并且可能会使用的任何**本地**采用本地内存的 Windows 内存函数处理作为参数。  
  
 **GetHandle**仅由多个行编辑控件处理。  
  
 调用**GetHandle**仅当使用对话框中创建了一个对话框中的多行编辑控件**DS_LOCALEDIT**样式标志设置。 如果**DS_LOCALEDIT**样式未设置，你仍会收到一个非零返回值，但你将不能使用返回的值。  
  
> [!NOTE]
> **GetHandle**不会使用 Windows 95/98。 如果调用**GetHandle**在 Windows 95/98，它将返回**NULL**。 **GetHandle**将按下 Windows NT，3.51 及更高版本所述方式工作。  
  
 有关详细信息，请参阅[EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="gethighlight"></a>CEdit::GetHighlight  
 获取当前的编辑控件中突出显示的文本的一系列中的第一个和最后一个字符的索引。  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pichStart`|突出显示的文本范围中的第一个字符的从零开始索引。|  
|[out] `pichEnd`|突出显示的文本范围中的最后一个字符的从零开始索引。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578)消息，Windows SDK 中介绍。  
  
##  <a name="getlimittext"></a>CEdit::GetLimitText  
 调用此成员函数可获取此文本限制`CEdit`对象。  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前文本限制，以字节为单位，这`CEdit`对象。  
  
### <a name="remarks"></a>备注  
 文本限制为文本，以字节为单位，编辑控件可接受的最大量。  
  
> [!NOTE]
>  此成员函数是与 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="getline"></a>CEdit::GetLine  
 调用此函数可从一个编辑控件中检索一行文本，并将其置于`lpszBuffer`。  
  
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
 `nIndex`  
 指定要检索从多个行的行号的编辑控件。 行号是从零开始;值为 0 指定的第一行。 单行编辑控件忽略此参数。  
  
 `lpszBuffer`  
 指向接收一份行的缓冲区。 缓冲区的第一个单词必须指定的最大可以将复制到缓冲区的字符数。  
  
 `nMaxLength`  
 指定的最大可以将复制到缓冲区的字节数。 `GetLine`将此值放在第一个单词的`lpszBuffer`之后再进行对 Windows 的调用。  
  
### <a name="return-value"></a>返回值  
 实际复制的字节数。 返回值为 0，如果指定的行号`nIndex`大于编辑控件中的行数。  
  
### <a name="remarks"></a>备注  
 复制的行不包含 null 终止字符。  
  
 有关详细信息，请参阅[EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetLineCount](#getlinecount)。  
  
##  <a name="getlinecount"></a>CEdit::GetLineCount  
 调用此函数可检索的多行编辑控件中的行数。  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含多个行中的行数的整数编辑控件。 如果没有文本已输入到编辑控件，则返回值为 1。  
  
### <a name="remarks"></a>备注  
 `GetLineCount`仅处理由多个行编辑控件。  
  
 有关详细信息，请参阅[EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="getmargins"></a>CEdit::GetMargins  
 调用此成员函数可检索此编辑控件的左侧和右侧边距。  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>返回值  
 在低序位的左边距宽度**WORD**和右边距的高顺序宽度**WORD**。  
  
### <a name="remarks"></a>备注  
 以像素为单位测量边距。  
  
> [!NOTE]
>  此成员函数是与 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="getmodify"></a>CEdit::GetModify  
 调用此函数可确定是否已修改编辑控件的内容。  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果编辑控件内容已修改; 则为非 00 如果它们保持不变。  
  
### <a name="remarks"></a>备注  
 Windows 维护，该值指示是否已更改编辑控件的内容的内部标志。 当编辑控件首次创建也可能会通过调用被清除，时会清除此标志[SetModify](#setmodify)成员函数。  
  
 有关详细信息，请参阅[EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="getpasswordchar"></a>CEdit::GetPasswordChar  
 调用此函数可检索时用户输入的文本编辑控件中显示的密码字符。  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定要显示而不是用户键入的字符的字符。 返回值是`NULL`如果没有密码字符存在。  
  
### <a name="remarks"></a>备注  
 如果创建与编辑控件**ES_PASSWORD**样式，该 DLL 的支持控件确定默认的密码字符。 清单或[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)方法确定哪个 DLL 支持编辑控件。 如果 user32.dll 支持编辑控件，默认的密码字符是星号 (*，U + 002A)。 如果 comctl32.dll 版本 6 支持的编辑控件，则默认字符是黑色圆 （U + 25CF ●）。 有关哪些 DLL 和版本支持的公共控件，请参阅[Shell 和公共控件版本](http://msdn.microsoft.com/library/windows/desktop/bb776779)。  
  
 此方法可发送[EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="getrect"></a>CEdit::GetRect  
 调用此函数可获取编辑控件的格式设置矩形。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构，它接收的格式设置的矩形。  
  
### <a name="remarks"></a>备注  
 格式设置的矩形是大小的文本，这是大小的独立的编辑控件窗口限制矩形。  
  
 可通过修改的多行编辑控件的格式设置矩形[SetRect](#setrect)和[SetRectNP](#setrectnp)成员函数。  
  
 有关详细信息，请参阅[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LimitText](#limittext)。  
  
##  <a name="getsel"></a>CEdit::GetSel  
 调用此函数可获取的起始和结束字符位置的编辑控件，使用返回值或参数中的当前选择 （如果有）。  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartChar`  
 对一个整数，它将在当前所选内容中看到的第一个字符的位置的引用。  
  
 `nEndChar`  
 对一个整数，它将接收的当前所选内容的末尾的第一个未选中字符的位置的引用。  
  
### <a name="return-value"></a>返回值  
 返回的版本`DWORD`返回一个值，之后的高序位字中的选定内容的末尾包含低序位字中的起始位置和未选定的第一个字符的位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="hideballoontip"></a>CEdit::HideBalloonTip  
 隐藏任何与当前的编辑控件相关联的气球状提示。  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此函数将[EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604)消息，Windows SDK 中介绍。  
  
##  <a name="limittext"></a>CEdit::LimitText  
 调用此函数可限制用户可以输入在编辑控件的文本的长度。  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nChars`  
 指定用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0，文本长度设置为**UINT_MAX**字节。 这是默认行为。  
  
### <a name="remarks"></a>备注  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数将更多的文本放入比对的调用中指定的编辑控件`LimitText`，用户可以删除任何编辑控件中的文本。 但是，文本限制将阻止用户将现有的文本替换为新的文本，除非删除当前所选内容会导致将文本低于文本限制。  
  
> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)替换此函数。  
  
 有关详细信息，请参阅[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="linefromchar"></a>CEdit::LineFromChar  
 调用此函数可检索包含指定的字符索引的行的行号。  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含所需的字符的文本编辑控件中的从零开始的索引值或包含为-1。 如果`nIndex`为-1，它指定的当前行，即包含脱字号的行。  
  
### <a name="return-value"></a>返回值  
 包含指定的字符索引的行的从零开始的行号`nIndex`。 如果`nIndex`为-1，返回的包含所选内容的第一个字符的行数。 如果没有选择任何内容，则返回当前的行号。  
  
### <a name="remarks"></a>备注  
 字符索引是从开始处编辑控件的字符数。  
  
 此成员函数仅供多个行编辑控件。  
  
 有关详细信息，请参阅[EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="lineindex"></a>CEdit::LineIndex  
 调用此函数可检索的多行编辑控件内的行的字符索引。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 包含所需的行的文本编辑控件中的索引值或包含为-1。 如果`nLine`为-1，它指定的当前行，即包含脱字号的行。  
  
### <a name="return-value"></a>返回值  
 在指定的行的字符索引`nLine`; 如果指定的行数大于编辑控件中的行数-1。  
  
### <a name="remarks"></a>备注  
 字符索引是从编辑控件的开头到指定的行的字符数。  
  
 此成员函数仅处理由多个行编辑控件。  
  
 有关详细信息，请参阅[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="linelength"></a>CEdit::LineLength  
 检索一个编辑控件中的行的长度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 其长度是要检索的行中的字符的从零开始的索引。 默认值为 -1。  
  
### <a name="return-value"></a>返回值  
 对于单行编辑控件，则返回值是长度，在`TCHAR`s，编辑控件中的文本。  
  
 对于多行编辑控件，则返回值是长度，在`TCHAR`s，由指定的行的`nLine`参数。 有关[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]文本，长度为行中的字节数; 对于 Unicode 文本，长度为行中的字符数。 长度不包括位于行的末尾处的回车符的字符。  
  
 如果`nLine`参数大于控件中的字符数，则返回值为零。  
  
 如果`nLine`参数为-1，则返回值为未选中部分中的字符数包含选定的字符的行。 例如，如果所选内容覆盖从一行到下一行的结尾八个字符的第四个字符，则返回值为 10。 也就是说，三个字符的第一行和七个下一步。  
  
 有关详细信息`TCHAR`类型，请参阅`TCHAR`的表中的行[Windows 数据类型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>备注  
 此方法支持通过[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="linescroll"></a>CEdit::LineScroll  
 调用此函数可滚动的多行编辑控件的文本。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nLines`  
 指定垂直滚动的行的数。  
  
 `nChars`  
 指定水平滚动的字符位置的数。 如果编辑控件已忽略此值**ES_RIGHT**或**ES_CENTER**样式。  
  
### <a name="remarks"></a>备注  
 此成员函数仅由多个行编辑控件处理。  
  
 编辑控件不垂直滚动过的文本编辑控件中的最后一行。 如果当前行加上指定的行数`nLines`超过了总的编辑控件中的行数，以便编辑控件的最后一行滚动到编辑控件窗口的顶部，将调整值。  
  
 `LineScroll`可以使用水平滚动过去的任意行的最后一个字符。  
  
 有关详细信息，请参阅[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="paste"></a>CEdit::Paste  
 调用此函数可将数据插入从剪贴板粘贴到`CEdit`的插入点处。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。  
  
 有关详细信息，请参阅[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="posfromchar"></a>CEdit::PosFromChar  
 调用此函数可获取在此给定的字符的位置 （左上角）`CEdit`对象。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 指定的字符的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 由指定的字符的左上角的坐标`nChar`。  
  
### <a name="remarks"></a>备注  
 通过给的从零开始的索引值指定的字符。 如果`nChar`大于在此的最后一个字符的索引`CEdit`对象，返回的值在此指定刚超出最后一个字符的字符位置的坐标`CEdit`对象。  
  
> [!NOTE]
>  此成员函数是与 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineFromChar](#linefromchar)。  
  
##  <a name="replacesel"></a>CEdit::ReplaceSel  
 调用此函数可将替换为指定的文本编辑控件中的当前选定`lpszNewText`。  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `lpszNewText`  
 指向以 null 结尾的字符串包含替换文本。  
  
 `bCanUndo`  
 若要指定此函数可用于撤消，设置到此参数的值**TRUE** 。 默认值是**FALSE**。  
  
### <a name="remarks"></a>备注  
 将替换仅为一部分编辑控件中的文本。 如果你想要替换的所有文本，使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成员函数。  
  
 如果没有当前没有选定内容，替换文本将插入当前光标位置处。  
  
 有关详细信息，请参阅[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="setcuebanner"></a>CEdit::SetCueBanner  
 设置显示为文本提示，或提示，编辑控件时控件为空的文本。  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 指向包含编辑控件中显示的提示的字符串的指针。  
  
 [in] `fDrawWhenFocused`  
 如果`false`，当用户在编辑控件中单击，并使获得焦点的控件不绘制提示横幅。  
  
 如果`true`，即使在控件有焦点绘制提示横幅。 当用户开始在控件中键入时，就会消失提示横幅。  
  
 默认值为 `false`。  
  
### <a name="return-value"></a>返回值  
 `true`如果此方法成功，则否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639)消息，Windows SDK 中介绍。 有关详细信息，请参阅[Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703)宏。  
  
### <a name="example"></a>示例  
 下面的示例演示[CEdit::SetCueBanner](#setcuebanner)方法。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="sethandle"></a>CEdit::SetHandle  
 调用此函数可设置为多行编辑控件将使用的本地内存的句柄。  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>参数  
 *hBuffer*  
 包含本地内存的句柄。 此句柄必须通过以前调用创建[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) Windows 函数使用**LMEM_MOVEABLE**标志。 内存被假定包含以 null 结尾的字符串。 如果这不是这种情况，则分配的内存的第一个字节应设置为 0。  
  
### <a name="remarks"></a>备注  
 编辑控件然后将使用此缓冲区存储而不是分配自己缓冲区当前显示的文本。  
  
 此成员函数仅由多个行编辑控件处理。  
  
 应用程序设置新的内存句柄之前，应使用[GetHandle](#gethandle)成员函数到当前的内存缓冲区中获取其句柄并释放该内存使用**LocalFree** Windows 函数。  
  
 `SetHandle`清除撤消缓冲区 ( [CanUndo](#canundo)成员函数则返回 0) 和内部修改标志 ( [GetModify](#getmodify)成员函数则返回 0)。 在重绘编辑控件窗口。  
  
 你可以在对话框中使用此成员函数在多行编辑控件中的，仅当你已创建的对话框中**DS_LOCALEDIT**样式标志设置。  
  
> [!NOTE]
> **GetHandle**不会使用 Windows 95/98。 如果调用**GetHandle**在 Windows 95/98，它将返回**NULL**。 **GetHandle**将按下 Windows NT，3.51 及更高版本所述方式工作。  
  
 有关详细信息，请参阅[EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641)， [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)，和[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="sethighlight"></a>CEdit::SetHighlight  
 突出显示了一个在当前显示的文本范围的编辑控件。  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `ichStart`|要突出显示的文本范围中的第一个字符的从零开始索引。|  
|[in] `ichEnd`|要突出显示的文本范围中的最后一个字符的从零开始索引。|  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643)消息，Windows SDK 中介绍。  
  
##  <a name="setlimittext"></a>CEdit::SetLimitText  
 调用此成员函数可将此文本限制设置`CEdit`对象。  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>参数  
 `nMax`  
 新文本限制，以字符为单位。  
  
### <a name="remarks"></a>备注  
 文本限制为中文字符，编辑控件可接受的最大量。  
  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数将更多的文本放入比对的调用中指定的编辑控件`LimitText`，用户可以删除任何编辑控件中的文本。 但是，文本限制将阻止用户将现有的文本替换为新的文本，除非删除当前所选内容会导致将文本低于文本限制。  
  
 此函数将替换[LimitText](#limittext) Win32 中。  
  
 有关详细信息，请参阅[EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="setmargins"></a>CEdit::SetMargins  
 调用此方法以设置此编辑控件的左侧和右侧边距。  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>参数  
 *nLeft*  
 新的左边距，以像素为单位的宽度。  
  
 *nRight*  
 新的右边缘，以像素为单位的宽度。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此成员函数是与 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="setmodify"></a>CEdit::SetModify  
 调用此函数可设置或清除编辑控件的已修改的标志。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 值为**TRUE**指出文本已修改，值为**FALSE**指示它未被修改。 默认情况下，设置已修改的标志。  
  
### <a name="remarks"></a>备注  
 修改的标志指示编辑控件中的文本已被修改。 它会自动设置的每当用户更改的文本。 可能与检索其值[GetModify](#getmodify)成员函数。  
  
 有关详细信息，请参阅[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetModify](#getmodify)。  
  
##  <a name="setpasswordchar"></a>CEdit::SetPasswordChar  
 调用此函数可设置或删除时用户键入文本编辑控件中显示的密码字符。  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>参数  
 *ch*  
 指定要显示替代用户键入的字符的字符。 如果*ch*为 0，则显示用户键入的实际字符。  
  
### <a name="remarks"></a>备注  
 当设置的密码字符时，该角色将会显示为每个字符集的用户类型。  
  
 此成员函数具有不会影响多行编辑控件。  
  
 当`SetPasswordChar`调用成员函数，`CEdit`将重绘使用由指定的字符的所有可见字符*ch*。  
  
 如果使用编辑控件创建了[ES_PASSWORD](edit-styles.md)样式，默认的密码字符设置为星号 (  **\*** )。 如果删除此样式`SetPasswordChar`使用调用*ch*设置为 0。  
  
 有关详细信息，请参阅[EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="setreadonly"></a>CEdit::SetReadOnly  
 调用此函数可设置一个编辑控件的只读状态。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bReadOnly`  
 指定是否要设置或删除编辑控件的只读状态。 值为**TRUE**将状态设置为只读; 如果值为**FALSE**设置为读/写状态。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，或 0 如果检测到错误发生，则为非 0。  
  
### <a name="remarks"></a>备注  
 可通过测试找到当前设置[ES_READONLY](edit-styles.md)中的返回值标志[CWnd::GetStyle](cwnd-class.md#getstyle)。  
  
 有关详细信息，请参阅[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="setrect"></a>CEdit::SetRect  
 调用此函数可设置使用指定的坐标的矩形的尺寸。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构或`CRect`对象，它指定的格式设置的矩形的新维度。  
  
### <a name="remarks"></a>备注  
 此成员仅由多个行编辑控件处理。  
  
 使用`SetRect`若要设置格式的多个行的矩形编辑控件。 格式设置的矩形是大小的文本，这是大小的独立的编辑控件窗口限制矩形。 首次创建编辑控件时, 的格式设置的矩形是编辑控件窗口的客户端区域相同。 通过使用`SetRect`成员函数，大于或小于编辑控件的窗口，应用程序可以使格式设置的矩形。  
  
 如果编辑控件具有没有滚动条，文本将剪辑，不换行，如果超出窗口进行格式设置的矩形。 如果编辑控件包含一个边框，通过边框的大小减小的格式设置的矩形。 如果调整返回的矩形`GetRect`成员函数之前，必须删除边框的大小将传递到矩形`SetRect`。  
  
 当`SetRect`调用时，编辑控件的文本还重新格式化和重新显示。  
  
 有关详细信息，请参阅[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="setrectnp"></a>CEdit::SetRectNP  
 调用此函数可设置多行编辑控件的格式设置矩形。  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构或`CRect`对象，它指定矩形的新维度。  
  
### <a name="remarks"></a>备注  
 格式设置的矩形是大小的文本，这是大小的独立的编辑控件窗口限制矩形。  
  
 `SetRectNP`等同于`SetRect`成员函数，只不过编辑控件窗口不重绘。  
  
 首次创建编辑控件时, 的格式设置的矩形是编辑控件窗口的客户端区域相同。 通过调用`SetRectNP`成员函数，大于或小于编辑控件的窗口，应用程序可以使格式设置的矩形。  
  
 如果编辑控件具有没有滚动条，文本将剪辑，不换行，如果超出窗口进行格式设置的矩形。  
  
 此成员仅由多个行编辑控件处理。  
  
 有关详细信息，请参阅[EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::SetRect](#setrect)。  
  
##  <a name="setsel"></a>CEdit::SetSel  
 调用此函数可在编辑控件中选择某个范围的字符。  
  
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
 *dwSelection*  
 指定低序位字中的起始位置和高序位字中的结束位置。 如果低序位字是 0，高序位字为-1，则选择编辑控件中的所有文本。 如果低序位字为-1，将删除任何当前所选内容。  
  
 *bNoScroll*  
 指示是否将插入符号被滚动到视图。 如果**FALSE**，插入符号移动滚动到视图。 如果**TRUE**，插入符号不滚动到视图。  
  
 `nStartChar`  
 指定的起始位置。 如果`nStartChar`为 0 和`nEndChar`为-1，所有选择的文本编辑控件中。 如果`nStartChar`为-1，删除任何当前所选内容。  
  
 `nEndChar`  
 指定的结束位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetSel](#getsel)。  
  
##  <a name="settabstops"></a>CEdit::SetTabStops  
 调用此函数在多行编辑控件中设置制表位。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>参数  
 `cxEachStop`  
 指定制表位是若要设置在每个`cxEachStop`对话框单位。  
  
 `nTabStops`  
 指定的数中包含的制表位`rgTabStops`。 此数字必须大于 1。  
  
 `rgTabStops`  
 在对话框单位中停止指向数组的指定选项卡上的无符号整数。 对话框单位是水平或垂直距离。 一个水平对话框单位等于当前对话框基本宽度单位的四分之一和 1 个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 **GetDialogBaseUnits** Windows 函数以像素为单位返回当前对话框基本单位。  
  
### <a name="return-value"></a>返回值  
 如果已设置选项卡; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 当文本复制到多行编辑控件中时，任何 tab 字符文本中的将导致空间来生成到下一个制表位。  
  
 若要设置为 32 个对话框单位的默认大小的制表位，调用此成员函数的无参数版本。 若要设置为 32 以外大小的制表位，调用的版本与`cxEachStop`参数。 若要设置制表位大小的数组，包含两个参数使用版本。  
  
 此成员函数仅处理由多个行编辑控件。  
  
 `SetTabStops`不会自动刷新编辑窗口。 如果更改已在编辑控件的文本的制表位，调用[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重绘编辑窗口。  
  
 有关详细信息，请参阅[EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663)和[GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::SetTabStops](ceditview-class.md#settabstops)。  
  
##  <a name="showballoontip"></a>CEdit::ShowBalloonTip  
 显示与当前的编辑控件相关联的气球状提示。  
  
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
|[in] `pEditBalloonTip`|指向[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)描述的气球状提示的结构。|  
|[in] `lpszTitle`|指向包含标题的气球状提示的 Unicode 字符串的指针。|  
|[in] `lpszText`|指向包含的气球状提示文本的 Unicode 字符串的指针。|  
|[in] `ttiIcon`|`INT` ，它指定要将与气球状提示关联的图标的类型。 默认值为 `TTI_NONE`。 有关详细信息，请参阅`ttiIcon`的成员[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此函数将[EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668)消息，Windows SDK 中介绍。 有关详细信息，请参阅[Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707)宏。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_cedit`，即用于访问当前的编辑控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例显示一个编辑控件的气球状提示。 [CEdit::ShowBalloonTip](#showballoontip)方法指定的标题和气球状提示文本。  
  
 [!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="undo"></a>CEdit::Undo  
 调用此函数可撤消的上一个编辑控件的操作。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>返回值  
 对于单行编辑控件，返回值始终为非零。 对于多行编辑控件，则返回值是如果撤消操作成功，则为非 0 或 0 如果撤消操作失败。  
  
### <a name="remarks"></a>备注  
 撤消操作也可以撤消。 例如，可以还原已删除的文本与首次调用**撤消**。 只要没有任何干预的编辑操作，你可以删除再次通过第二个调用的文本**撤消**。  
  
 有关详细信息，请参阅[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CALCDRIV](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](cwnd-class.md)   
 [CButton 类](cbutton-class.md)   
 [CComboBox 类](ccombobox-class.md)   
 [CListBox 类](clistbox-class.md)   
 [CScrollBar 类](cscrollbar-class.md)   
 [CStatic 类](cstatic-class.md)   
 [CDialog 类](cdialog-class.md)
