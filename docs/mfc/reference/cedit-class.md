---
title: "CEdit 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEdit
dev_langs:
- C++
helpviewer_keywords:
- separators, in multiline edit controls
- text editors
- controls [MFC], edit
- text editors, CEdit class
- edit controls, classes
- multiline edit control
- CEdit class
- line separators in multiline edit controls
- edit controls
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9c782e77b1fdb9026ee030238413955ba4d537e9
ms.lasthandoff: 02/24/2017

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
|[CEdit::CEdit](#cedit)|构造`CEdit`控件对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|确定是否可以撤消的编辑控件的操作。|  
|[CEdit::CharFromPos](#charfrompos)|检索距离指定位置最近的字符的行和字符索引。|  
|[CEdit::Clear](#clear)|删除 （清除） 中编辑的当前选定 （如果有） 控制。|  
|[CEdit::Copy](#copy)|将当前所选内容 （如果有） 中的编辑控件到剪贴板中**CF_TEXT**格式。|  
|[CEdit::Create](#create)|创建 Windows 编辑控件，并将其附加到`CEdit`对象。|  
|[CEdit::Cut](#cut)|删除 （剪切） 中编辑的当前选定 （如果有） 控制，并将已删除的文本复制到剪贴板中**CF_TEXT**格式。|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重置 （清除） 编辑操作的撤消标志控制。|  
|[CEdit::FmtLines](#fmtlines)|在多行编辑控件中打开或关闭软换行字符的包含设置。|  
|[CEdit::GetCueBanner](#getcuebanner)|检索作为文本提示或提示，控制为空或没有焦点时编辑控件中的显示的文本。|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|确定一个编辑控件中最顶层可见的行。|  
|[CEdit::GetHandle](#gethandle)|检索多行编辑控件的当前分配的内存的句柄。|  
|[CEdit::GetHighlight](#gethighlight)|获取起始和结束当前编辑控件中突出显示的文本范围内的字符的索引。|  
|[CEdit::GetLimitText](#getlimittext)|获取文本的最大量此`CEdit`可以包含。|  
|[CEdit::GetLine](#getline)|从一个编辑控件中检索一行文本。|  
|[CEdit::GetLineCount](#getlinecount)|检索多行编辑控件中的行数。|  
|[CEdit::GetMargins](#getmargins)|获取左边距和右边距此`CEdit`。|  
|[CEdit::GetModify](#getmodify)|确定是否已修改一个编辑控件的内容。|  
|[CEdit::GetPasswordChar](#getpasswordchar)|检索时用户输入的文本编辑控件中显示的密码字符。|  
|[CEdit::GetRect](#getrect)|获取编辑控件的格式设置矩形。|  
|[CEdit::GetSel](#getsel)|获取编辑控件中当前所选内容的第一个和最后一个字符位置。|  
|[CEdit::HideBalloonTip](#hideballoontip)|隐藏任何与当前的编辑控件相关联的气球提示。|  
|[CEdit::LimitText](#limittext)|限制用户可以输入在编辑控件的文本的长度。|  
|[CEdit::LineFromChar](#linefromchar)|检索包含指定的字符索引的行的行号。|  
|[CEdit::LineIndex](#lineindex)|检索多行编辑控件内的行的字符索引。|  
|[CEdit::LineLength](#linelength)|检索一个编辑控件中的行的长度。|  
|[CEdit::LineScroll](#linescroll)|执行滚动操作使得多行编辑控件的文本。|  
|[CEdit::Paste](#paste)|将数据从剪贴板插入到当前光标位置的编辑控件。 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。|  
|[CEdit::PosFromChar](#posfromchar)|检索指定的字符索引窗口左上角的坐标。|  
|[CEdit::ReplaceSel](#replacesel)|替换指定的文本编辑控件中的当前所选内容。|  
|[CEdit::SetCueBanner](#setcuebanner)|设置为文本提示或提示，控制为空或没有焦点时编辑控件中的显示的文本。|  
|[CEdit::SetHandle](#sethandle)|设置多行编辑控件将使用的本地内存的句柄。|  
|[CEdit::SetHighlight](#sethighlight)|突出显示的范围内的当前显示的文本编辑控件。|  
|[CEdit::SetLimitText](#setlimittext)|这一设置的最大文本量`CEdit`可以包含。|  
|[CEdit::SetMargins](#setmargins)|设置左边距和右边距此`CEdit`。|  
|[CEdit::SetModify](#setmodify)|设置或清除编辑控件修改标志。|  
|[CEdit::SetPasswordChar](#setpasswordchar)|设置或删除时用户输入的文本编辑控件中显示的密码字符。|  
|[CEdit::SetReadOnly](#setreadonly)|设置一个编辑控件的只读状态。|  
|[CEdit::SetRect](#setrect)|设置多行编辑控件的格式设置矩形并更新该控件。|  
|[CEdit::SetRectNP](#setrectnp)|无需重绘控制窗口中设置多行编辑控件的格式设置矩形。|  
|[CEdit::SetSel](#setsel)|编辑控件中选择某个范围的字符。|  
|[CEdit::SetTabStops](#settabstops)|设置制表位的多个行中的编辑控件。|  
|[CEdit::ShowBalloonTip](#showballoontip)|显示与当前的编辑控件相关联的气球提示。|  
|[CEdit::Undo](#undo)|反转的最后一个编辑控件的操作。|  
  
## <a name="remarks"></a>备注  
 编辑控件是用户可以在其中输入文本的矩形的子窗口。  
  
 从对话框模板或直接在代码中，可以创建一个编辑控件。 在这两种情况下，第一次调用构造函数`CEdit`构造`CEdit`对象，然后调用[创建](#create)成员函数来创建 Windows 编辑控件，并将其附加到`CEdit`对象。  
  
 构造可能是在派生类中的单步进程`CEdit`。 编写构造函数以及该派生的类调用**创建**从构造函数内。  
  
 `CEdit`继承中的重要功能`CWnd`。 用于设置和检索来自文本`CEdit`对象，请使用`CWnd`成员函数[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，该设置或获取编辑控件的整个内容，即使它是多行控件。 在多行控件中的文本行隔开 '\r\n' 字符序列。 此外，如果多行编辑控件，获取和设置控件的文本的一部分调用`CEdit`成员函数[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，和[ReplaceSel](#replacesel)。  
  
 如果你想要处理 Windows 通知消息发送到其父级的编辑控件 (通常派生自该类`CDialog`)，将消息映射条目和消息处理程序成员函数添加到每个消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 **ON_**通知**(** *id、 f x n***)**  
  
 其中`id`指定发送通知，此编辑控件的子窗口 ID 和`memberFxn`留下来处理通知的父成员函数的名称。  
  
 父元素的函数原型是，如下所示︰  
  
 **afx_msg** void f x n **（);**  
  
 以下是潜在的消息映射条目，并会对父发送的用例的说明的列表︰  
  
- **ON_EN_CHANGE**用户已执行可能更改编辑控件中的文本的操作。 与不同**EN_UPDATE**通知消息时，此通知消息后发送 Windows 更新显示。  
  
- **ON_EN_ERRSPACE**编辑控件无法分配足够的内存来满足特定的请求。  
  
- **ON_EN_HSCROLL**用户单击编辑控件的水平滚动条。 更新屏幕之前，将通知父窗口。  
  
- **ON_EN_KILLFOCUS**编辑控件失去输入的焦点。  
  
- **ON_EN_MAXTEXT**当前插入已超出指定的数量的编辑控件的字符，已被截断。 编辑控件没有时，也发送**ES_AUTOHSCROLL**样式和要插入的字符数将超过编辑控件的宽度。 编辑控件没有时，也发送**ES_AUTOVSCROLL**样式和所得文本插入的行的总数超过编辑控件的高度。  
  
- **ON_EN_SETFOCUS**编辑控件接收到输入的焦点时发送。  
  
- **ON_EN_UPDATE**编辑控件位于来显示更改后的文本。 发送该控件设置文本格式之后，但之前它屏幕文本，以便可以更改窗口大小，如有必要。  
  
- **ON_EN_VSCROLL**用户单击编辑控件的垂直滚动条。 更新屏幕之前，将通知父窗口。  
  
 如果您创建`CEdit`的对话框内的对象`CEdit`当用户关闭对话框中，将自动销毁对象。  
  
 如果您创建`CEdit`对话框资源使用对话框编辑器中，从对象`CEdit`当用户关闭对话框中，将自动销毁对象。  
  
 如果您创建`CEdit`对象在窗口中，您可能还需要将其销毁。 如果您创建`CEdit`对象在堆栈上，自动被销毁。 如果您创建`CEdit`使用堆上的对象**新**函数，则必须调用**删除**对象以将其销毁，当用户终止 Windows 编辑控件。 如果分配任何内存`CEdit`对象，请重写`CEdit`析构函数释放的分配。  
  
 若要修改的编辑控件中的某些样式 (如**ES_READONLY**) 必须将特定的消息发送到控件而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 请参阅[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息`CEdit`，请参阅︰  
  
- [控件](../../mfc/controls-mfc.md)  
  
-   知识库文章 Q259949︰ 信息︰ SetCaretPos() 是不适合用 CEdit 或 CRichEditCtrl 控件  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecanundoa--ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo  
 调用此函数可确定是否上一个编辑操作可用于撤消。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果上一个编辑操作可以撤消的对的调用，则为非**撤消**成员函数; 如果不能撤消，将 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::Undo](#undo)。  
  
##  <a name="a-namecedita--ceditcedit"></a><a name="cedit"></a>CEdit::CEdit  
 构造 `CEdit` 对象。  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>备注  
 使用[创建](#create)来构建 Windows 编辑控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&1;](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="a-namecharfromposa--ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos  
 调用此函数可检索的从零开始的行和在此指定的点最近的字符的字符索引`CEdit`控件  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 此工作区中的点的坐标`CEdit`对象。  
  
### <a name="return-value"></a>返回值  
 在低序位的字符索引**WORD**，高顺序中的行索引和**WORD**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&3;](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="a-namecleara--ceditclear"></a><a name="clear"></a>CEdit::Clear  
 调用此函数可删除 (clear) 当前所选内容 （如果有） 中的编辑控件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 删除由执行**清除**会通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容并将已删除的内容放入剪贴板，请调用[剪切](#cut)成员函数。  
  
 有关详细信息，请参阅[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&4;](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="a-namecopya--ceditcopy"></a><a name="copy"></a>CEdit::Copy  
 调用此函数可对若要复制当前所选内容 （如果有） 到剪贴板中的编辑控件中**CF_TEXT**格式。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&5;](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="a-namecreatea--ceditcreate"></a><a name="create"></a>CEdit::Create  
 创建 Windows 编辑控件，并将其附加到`CEdit`对象。  
  
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
 如果初始化成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CEdit`两个步骤中的对象。 首先，调用`CEdit`构造函数，然后调用**创建**，它创建 Windows 编辑控件并将其附加到`CEdit`对象。  
  
 当**创建**执行时，Windows 将发送[WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635)， [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634)， [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619)，和[WM_GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626)的编辑控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CEdit`、 将消息映射添加到新的类，并重写上面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](window-styles.md)向一个编辑控件。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**控件组合  
  
- **WS_TABSTOP**按 tab 键顺序包括编辑控件  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&2;](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="a-namecuta--ceditcut"></a><a name="cut"></a>CEdit::Cut  
 编辑控件中当前所选内容 （如果有） 调用此函数可删除 （剪切），并将已删除的文本复制到剪贴板中**CF_TEXT**格式。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 删除由执行**剪切**会通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容，而无需将已删除的文本放入剪贴板，调用[清除](#clear)成员函数。  
  
 有关详细信息，请参阅[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&6;](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="a-nameemptyundobuffera--ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer  
 调用此函数可重置 （清除） 编辑控件的撤消标志。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>备注  
 编辑控件现在将不能撤消上一操作。 只要编辑控件中的操作可用于撤消，则设置还原标志。  
  
 撤消标志将自动清除每当[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle) `CWnd`成员函数的调用。  
  
 有关详细信息，请参阅[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&7;](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="a-namefmtlinesa--ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines  
 调用此函数以将软换行字符包含在多行编辑控件中打开或关闭设置。  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>参数  
 *bAddEOL*  
 指定是否要插入软换行字符。 值为**TRUE**将插入以下字符:; 值为**FALSE**中删除它们。  
  
### <a name="return-value"></a>返回值  
 如果任何非零设置格式的时间;否则为 0。  
  
### <a name="remarks"></a>备注  
 软换行符组成两个回车和换行插入到由于自动换行中断的行的末尾。 硬盘换行符组成一个回车符和换行符。 以一个硬盘的换行符结束行不受`FmtLines`。  
  
 如果仅将响应 Windows`CEdit`对象都是多行编辑控件。  
  
 `FmtLines`只会影响返回的缓冲区[GetHandle](#gethandle)和返回的文本[WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627)。 它不起作用的文本编辑控件中的显示。  
  
 有关详细信息，请参阅[EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&8;](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="a-namegetcuebannera--ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner  
 检索作为文本提示或提示，该控件为空时的编辑控件中显示的文本。  
  
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
 对于第一个重载`true`如果方法成功，否则为`false`。  
  
 对于第二个重载， [CString](../../atl-mfc-shared/using-cstring.md) ，包含提示文本，如果该方法是成功; 否则为空字符串 ("")。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅[Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695)宏。  
  
##  <a name="a-namegetfirstvisiblelinea--ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine  
 调用此函数可确定的编辑控件中最顶层的可见的行。  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>返回值  
 最顶层的可见行的从零开始的索引。 对于单行编辑控件，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&9;](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="a-namegethandlea--ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle  
 调用此函数可检索为多行编辑控件当前分配的内存的句柄。  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 标识保存编辑控件的内容的缓冲区的本地内存句柄。 如果发生错误，如将消息发送到一个单行编辑控件，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 句柄是本地内存句柄，而可能由任一**本地**采用本地内存的 Windows 内存函数处理作为参数。  
  
 **GetHandle**仅由多行编辑控件处理。  
  
 调用**GetHandle**为多行编辑控件在对话框中，如果使用对话框中创建了仅**DS_LOCALEDIT**样式标志设置。 如果**DS_LOCALEDIT**样式未设置，您仍将看到一个非零返回值，但不是将能够使用返回的值。  
  
> [!NOTE]
> **GetHandle**不适用于 Windows 95/98。 如果调用**GetHandle**在 Windows 95/98 中，它将返回**NULL**。 **GetHandle**将记录在 Windows NT 版本 3.51 及更高版本下正常工作。  
  
 有关详细信息，请参阅[EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&10;](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="a-namegethighlighta--ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight  
 获取在当前的编辑控件中突出显示的文本范围中第一个和最后一个字符的索引。  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pichStart`|将突出显示的文本范围中的第一个字符的从零开始索引。|  
|[out] `pichEnd`|将突出显示的文本范围内的最后一个字符的从零开始索引。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetlimittexta--ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText  
 调用此成员函数以获取此文本限制`CEdit`对象。  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前文本限制，以字节为单位，此`CEdit`对象。  
  
### <a name="remarks"></a>备注  
 文本限制为文本，以字节为单位，编辑控件可接受的最大量。  
  
> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&11;](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="a-namegetlinea--ceditgetline"></a><a name="getline"></a>CEdit::GetLine  
 调用此函数可从一个编辑控件中检索文本行并将其置于`lpszBuffer`。  
  
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
 指定要检索从多个行的行号的编辑控件。 行号是从零开始;值为 0 指定第一行。 由单行编辑控件，则忽略此参数。  
  
 `lpszBuffer`  
 指向用于接收缓冲区的行的副本。 缓冲区的第一个单词必须指定最大可以复制到缓冲区的字符数。  
  
 `nMaxLength`  
 指定最大可以复制到缓冲区的字节数。 `GetLine`将此值放在第一个单词的`lpszBuffer`之前 Windows 在调用。  
  
### <a name="return-value"></a>返回值  
 实际复制的字节数。 返回值为 0，如果由指定的行号`nIndex`大于编辑控件中的行数。  
  
### <a name="remarks"></a>备注  
 复制的行不包含 null 终止字符。  
  
 有关详细信息，请参阅[EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetLineCount](#getlinecount)。  
  
##  <a name="a-namegetlinecounta--ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount  
 调用此函数可检索多行编辑控件中的行数。  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含多行中的行数的整数的编辑控件。 如果已在编辑控件中不输入任何文本，则返回值为 1。  
  
### <a name="remarks"></a>备注  
 `GetLineCount`仅由多行编辑控件处理。  
  
 有关详细信息，请参阅[EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&12;](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="a-namegetmarginsa--ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins  
 调用此成员函数可检索此编辑控件的左侧和右侧边距。  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>返回值  
 在低序位的左边距的宽度**WORD**和高顺序的右边距的宽度**WORD**。  
  
### <a name="remarks"></a>备注  
 以像素为单位测量边距。  
  
> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namegetmodifya--ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify  
 调用此函数可确定是否已修改一个编辑控件的内容。  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果编辑控件内容已被修改;0，如果它们保持不变。  
  
### <a name="remarks"></a>备注  
 Windows 维护内部标记，指示是否已更改编辑控件的内容。 此标志已清除编辑控件第一次创建时创建，也可能会通过调用被清除[SetModify](#setmodify)成员函数。  
  
 有关详细信息，请参阅[EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&13;](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="a-namegetpasswordchara--ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar  
 调用此函数可检索时用户输入的文本编辑控件中显示的密码字符。  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定要显示而不是用户键入的字符的字符。 返回值是`NULL`如果密码字符都不存在。  
  
### <a name="remarks"></a>备注  
 如果您创建与编辑控件**ES_PASSWORD**样式，该 DLL 的支持控件确定默认的密码字符。 清单或[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)方法确定将哪个 DLL 支持编辑控件。 如果 user32.dll 支持编辑控件，默认的密码字符是星号 (*，U +&002;A)。 如果 comctl32.dll 版本 6 支持的编辑控件，默认字符是实心圆 （U + 25CF ●）。 有关哪些 DLL 和版本支持的公共控件，请参阅[Shell 和公共控件版本](http://msdn.microsoft.com/library/windows/desktop/bb776779)。  
  
 此方法可发送[EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&14;](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="a-namegetrecta--ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect  
 调用此函数可获取编辑控件的格式设置矩形。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构，它接收的格式设置的矩形。  
  
### <a name="remarks"></a>备注  
 格式设置矩形是大小的文本编辑控件窗口无关的限制矩形。  
  
 可以通过修改多行编辑控件的格式设置矩形[SetRect](#setrect)和[SetRectNP](#setrectnp)成员函数。  
  
 有关详细信息，请参阅[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LimitText](#limittext)。  
  
##  <a name="a-namegetsela--ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel  
 调用此函数可获取的起始和结束字符位置的编辑控件，使用返回值或参数中的当前选定 （如果有）。  
  
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
 对一个整数，它将接收当前所选内容的末尾的第一个未选定字符的位置的引用。  
  
### <a name="return-value"></a>返回值  
 返回的版本`DWORD`返回一个值，包含在高序位字中的选定内容结束后的低序位字中的起始位置和未选定的第一个字符的位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&15;](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="a-namehideballoontipa--cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip  
 隐藏任何与当前的编辑控件相关联的气球提示。  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此函数可将发送[EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namelimittexta--ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText  
 调用此函数，以限制用户可以输入在编辑控件的文本的长度。  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nChars`  
 指定的用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0，文本长度设置为**UINT_MAX**字节。 这是默认行为。  
  
### <a name="remarks"></a>备注  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数放到不是对的调用中指定的编辑控件的更多文本`LimitText`，用户可以删除任何内编辑控件的文本。 但是，文本限制将阻止用户使用新文本替换现有文本，除非删除当前所选内容，否则将导致要低于短限制的文本。  
  
> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)替换此函数。  
  
 有关详细信息，请参阅[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&17;](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="a-namelinefromchara--ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromChar  
 调用此函数可检索包含指定的字符索引的行的行号。  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含的文本编辑控件中的所需字符的从零开始的索引值或包含为-1。 如果`nIndex`为 –&1;，它指定当前行，即包含光标的行。  
  
### <a name="return-value"></a>返回值  
 包含由指定的字符索引的行的从零开始的行号`nIndex`。 如果`nIndex`为 –&1;，返回包含所选内容的第一个字符的行数。 如果没有选定，则返回当前行号。  
  
### <a name="remarks"></a>备注  
 字符索引是从开始处编辑控件的字符数。  
  
 此成员函数仅供多个行编辑控件。  
  
 有关详细信息，请参阅[EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&18;](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="a-namelineindexa--ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex  
 调用此函数可检索多行编辑控件内的行的字符索引。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 包含所需的行的文本编辑控件中的索引值或包含为-1。 如果`nLine`为 –&1;，它指定当前行，即包含光标的行。  
  
### <a name="return-value"></a>返回值  
 在指定的行的字符索引`nLine`则返回 –&1; 指定的行号是否大于编辑控件中的行数。  
  
### <a name="remarks"></a>备注  
 字符索引是从编辑控件的开头到指定的行的字符数。  
  
 此成员函数仅由多行编辑控件处理。  
  
 有关详细信息，请参阅[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&19;](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="a-namelinelengtha--ceditlinelength"></a><a name="linelength"></a>CEdit::LineLength  
 检索一个编辑控件中的行的长度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 其长度为要检索的行中的字符的从零开始的索引。 默认值为 -1。  
  
### <a name="return-value"></a>返回值  
 对于单行编辑控件，则返回值是长度，在`TCHAR`s，编辑控件中的文本。  
  
 对于多行编辑控件，则返回值是长度，在`TCHAR`s，由指定的行的`nLine`参数。 有关[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]文本，长度是在行中的字节数; 对于 Unicode 文本，长度是一行中的字符数。 长度不包括位于行末尾处的回车符字符。  
  
 如果`nLine`参数为多个控件中的字符数，返回值为零。  
  
 如果`nLine`参数为 –&1;，返回值是在包含选定的字符的行中未选定字符数。 例如，如果所选内容覆盖从一行到下一行的结尾八个字符的第四个字符，则返回值为 10。 它是三个字符的第一行和七个下一步。  
  
 有关详细信息`TCHAR`类型，请参阅`TCHAR`在表中的一行[Windows 数据类型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
### <a name="remarks"></a>备注  
 此方法支持通过[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="a-namelinescrolla--ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll  
 调用此函数可滚动的多行编辑控件的文本。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nLines`  
 指定要垂直滚动行的数。  
  
 `nChars`  
 指定要水平滚动字符位置的数。 如果已经进行的编辑控件，则忽略此值**ES_RIGHT**或**ES_CENTER**样式。  
  
### <a name="remarks"></a>备注  
 此成员函数仅由多行编辑控件处理。  
  
 编辑控件不垂直滚动过的文本编辑控件中的最后一行。 如果当前行加上由指定的行数`nLines`超过 edit 控件中的行的总数，以便编辑控件的最后一行滚动到编辑控件窗口的顶部，将调整值。  
  
 `LineScroll`可以用于水平滚动条越过数据的任意行的最后一个字符。  
  
 有关详细信息，请参阅[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="a-namepastea--ceditpaste"></a><a name="paste"></a>CEdit::Paste  
 调用此函数可将数据插入从剪贴板粘贴到`CEdit`的插入点处。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含中的数据插入数据**CF_TEXT**格式。  
  
 有关详细信息，请参阅[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&20;](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="a-nameposfromchara--ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosFromChar  
 调用此函数可获取在此给定的字符的位置 （左上角）`CEdit`对象。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 指定字符的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 由指定的字符的左上角的坐标`nChar`。  
  
### <a name="remarks"></a>备注  
 通过为相应的从零开始的索引值指定的字符。 如果`nChar`大于最后一个字符在此索引`CEdit`对象，则返回值在此指定的坐标刚好超出最后一个字符的字符位置的`CEdit`对象。  
  
> [!NOTE]
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineFromChar](#linefromchar)。  
  
##  <a name="a-namereplacesela--ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel  
 调用此函数可将替换为指定的文本编辑控件中的当前所选内容`lpszNewText`。  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `lpszNewText`  
 指向以 null 结尾的字符串包含替换文本。  
  
 `bCanUndo`  
 若要指定此函数可用于撤消，将设置为此参数的值**TRUE** 。 默认值是**FALSE**。  
  
### <a name="remarks"></a>备注  
 将替换仅编辑控件中的文本的一部分。 如果你想要替换的所有文本，使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成员函数。  
  
 如果没有当前没有选定内容，在当前光标位置插入替换文本。  
  
 有关详细信息，请参阅[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::LineIndex](#lineindex)。  
  
##  <a name="a-namesetcuebannera--ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner  
 设置显示为文本提示，或提示，在编辑来控制该控件为空时的文本。  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 包含要在编辑控件中显示的提示的字符串指针。  
  
 [in] `fDrawWhenFocused`  
 如果`false`，当用户单击编辑控件中并使该控件具有焦点时不会绘制提示标志。  
  
 如果`true`，即使在控件有焦点绘制提示标志。 当用户开始在控件中键入时，提示标志将消失。  
  
 默认值为 `false`。  
  
### <a name="return-value"></a>返回值  
 `true`如果成功，则此方法否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅[Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703)宏。  
  
### <a name="example"></a>示例  
 下面的示例演示[CEdit::SetCueBanner](#setcuebanner)方法。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="a-namesethandlea--ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle  
 调用此函数可将该句柄设置为多行编辑控件将使用的本地内存。  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>参数  
 *hBuffer*  
 包含本地内存的句柄。 此句柄必须由以前调用[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) Windows 函数使用**LMEM_MOVEABLE**标志。 内存假定为包含以 null 结尾的字符串。 如果这不是这种情况，则分配的内存的第一个字节应设置为 0。  
  
### <a name="remarks"></a>备注  
 然后，编辑控件将使用此缓冲区来存储当前显示的文本，而不是分配它自己的缓冲区。  
  
 此成员函数仅由多行编辑控件处理。  
  
 应用程序设置了新的内存句柄之前，它应使用[GetHandle](#gethandle)成员函数来获取当前的内存缓冲区句柄并释放该内存使用**LocalFree** Windows 函数。  
  
 `SetHandle`将清除撤消缓冲区 ( [CanUndo](#canundo)成员函数则返回 0) 和内部修改标志 ( [GetModify](#getmodify)成员函数则返回 0)。 在重绘编辑控件窗口。  
  
 您可以在对话框中使用多行编辑控件中的该成员函数，仅当您已创建与对话框**DS_LOCALEDIT**样式标志设置。  
  
> [!NOTE]
> **GetHandle**不适用于 Windows 95/98。 如果调用**GetHandle**在 Windows 95/98 中，它将返回**NULL**。 **GetHandle**将记录在 Windows NT 版本 3.51 及更高版本下正常工作。  
  
 有关详细信息，请参阅[EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641)， [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)，和[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&22;](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="a-namesethighlighta--ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight  
 突出显示的范围内的当前显示的文本编辑控件。  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `ichStart`|要突出显示的文本范围中的第一个字符的从零开始索引。|  
|[in] `ichEnd`|要突出显示的文本范围中的最后一个字符的从零开始索引。|  
  
### <a name="remarks"></a>备注  
 此方法可发送[EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetlimittexta--ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText  
 调用此成员函数以设置此文本限制`CEdit`对象。  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>参数  
 `nMax`  
 新文本限制，以字符为单位。  
  
### <a name="remarks"></a>备注  
 文本限制为文本，请在编辑控件可以接受的字符的最大量。  
  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数放到不是对的调用中指定的编辑控件的更多文本`LimitText`，用户可以删除任何内编辑控件的文本。 但是，文本限制将阻止用户使用新文本替换现有文本，除非删除当前所选内容，否则将导致要低于短限制的文本。  
  
 此函数将替换[LimitText](#limittext) Win32 中。  
  
 有关详细信息，请参阅[EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namesetmarginsa--ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins  
 调用此方法来设置此编辑控件的左侧和右侧边距。  
  
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
>  此成员函数是 Windows 95 和 Windows NT 4.0 开始提供。  
  
 有关详细信息，请参阅[EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。  
  
##  <a name="a-namesetmodifya--ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify  
 调用此函数可设置或清除编辑控件的已修改的标记。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 值为**TRUE**指出文本已修改，值为**FALSE**指示它不会进行修改。 默认情况下，设置已修改的标志。  
  
### <a name="remarks"></a>备注  
 修改后的标志指示修改了在编辑控件中的文本。 它将自动设置的每当用户更改的文本。 可能会检索其值与[GetModify](#getmodify)成员函数。  
  
 有关详细信息，请参阅[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetModify](#getmodify)。  
  
##  <a name="a-namesetpasswordchara--ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar  
 调用此函数可设置或删除时用户键入的文本编辑控件中显示的密码字符。  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>参数  
 *ch*  
 指定要由用户键入的字符的位置上显示的字符。 如果*ch*为 0，则显示用户键入的实际字符。  
  
### <a name="remarks"></a>备注  
 当设置的密码字符时，该角色将会显示为每个字符的用户类型。  
  
 此成员函数有多行编辑控件没有影响。  
  
 当`SetPasswordChar`调用成员函数，`CEdit`将重绘所有可见的字符使用由指定的字符*ch*。  
  
 如果使用创建编辑控件[ES_PASSWORD](edit-styles.md)样式中，默认的密码字符设置为星号 ( ** \* **)。 在这种样式时删除`SetPasswordChar`调用*ch*设置为 0。  
  
 有关详细信息，请参阅[EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&16;](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="a-namesetreadonlya--ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly  
 调用此函数可设置一个编辑控件的只读状态。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bReadOnly`  
 指定是否设置或删除此编辑控件的只读状态。 值为**TRUE**将状态设置为只读; 如果值为**FALSE**设置为读/写的状态。  
  
### <a name="return-value"></a>返回值  
 非零，如果操作成功，则为 0，如果错误发生。  
  
### <a name="remarks"></a>备注  
 可以通过测试发现的当前设置[ES_READONLY](edit-styles.md)中的返回值的标志[CWnd::GetStyle](cwnd-class.md#getstyle)。  
  
 有关详细信息，请参阅[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit 第&23;](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="a-namesetrecta--ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect  
 调用此函数可设置使用指定的坐标的矩形的尺寸。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构或`CRect`对象，它指定新格式设置的矩形的尺寸。  
  
### <a name="remarks"></a>备注  
 此成员仅由多行编辑控件处理。  
  
 使用`SetRect`若要设置的格式设置矩形的多行编辑控件。 格式设置矩形是大小的文本编辑控件窗口无关的限制矩形。 首次创建编辑控件时, 格式化矩形是编辑控件窗口的客户端区域相同。 通过使用`SetRect`成员函数，大于或小于编辑控件窗口中，应用程序可以进行格式化的矩形。  
  
 如果编辑控件具有没有滚动条，文本将剪辑元素，不换行，如果超过窗口的大小进行格式化的矩形。 如果编辑控件包含一个边框，边框的大小减去格式化的矩形。 如果您调整返回的矩形`GetRect`成员函数之前，必须删除边框的大小将传递到该矩形`SetRect`。  
  
 当`SetRect`调用时，此编辑控件的文本还重新格式化，并重新显示。  
  
 有关详细信息，请参阅[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&24;](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="a-namesetrectnpa--ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP  
 调用此函数可设置多行编辑控件的格式设置矩形。  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构或`CRect`对象，它指定新矩形的尺寸。  
  
### <a name="remarks"></a>备注  
 格式设置矩形是大小的文本编辑控件窗口无关的限制矩形。  
  
 `SetRectNP`等同于`SetRect`成员函数除了，编辑控件窗口中不重绘。  
  
 首次创建编辑控件时, 格式化矩形是编辑控件窗口的客户端区域相同。 通过调用`SetRectNP`成员函数，大于或小于编辑控件窗口中，应用程序可以进行格式化的矩形。  
  
 如果编辑控件具有没有滚动条，文本将剪辑元素，不换行，如果超过窗口的大小进行格式化的矩形。  
  
 此成员仅由多行编辑控件处理。  
  
 有关详细信息，请参阅[EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::SetRect](#setrect)。  
  
##  <a name="a-namesetsela--ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel  
 调用此函数可在一个编辑控件中选择某个范围的字符。  
  
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
 指定低序位字中的起始位置和高序位字中的结束位置。 如果低序位字是 0，高序位字为 – 1，则选择此编辑控件中的所有文本。 如果低序位字为 –&1;，则会删除任何当前所选内容。  
  
 *bNoScroll*  
 指示是否应插入符号移动滚动到视图。 如果**FALSE**，插入符号移动滚动到视图。 如果**TRUE**，插入符号不滚动到视图。  
  
 `nStartChar`  
 指定的起始位置。 如果`nStartChar`为 0 和`nEndChar`为 – 1，所有选定的文本编辑控件中。 如果`nStartChar`为 –&1;，删除任何当前所选内容。  
  
 `nEndChar`  
 指定的结束位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEdit::GetSel](#getsel)。  
  
##  <a name="a-namesettabstopsa--ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops  
 调用此函数可在多行编辑控件中设置制表位。  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>参数  
 `cxEachStop`  
 指定是否要在设置制表位每个`cxEachStop`对话框单位。  
  
 `nTabStops`  
 指定的数中包含的制表位`rgTabStops`。 此数字必须是大于 1。  
  
 `rgTabStops`  
 对话框单位中的停止点指向数组的指定选项卡上的无符号整数。 对话框单位是一个水平或垂直距离。 一个水平对话框单位等于当前对话框基本宽度单位 （） 的 1 / 4 和 1 个垂直对话框单位等于当前对话框基本高度单位的八分之一。 对话框基本单位根据当前系统字体的高度和宽度计算。 **GetDialogBaseUnits** Windows 函数以像素为单位返回当前对话框基本单位。  
  
### <a name="return-value"></a>返回值  
 如果设置了选项卡; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 当文本复制到多行编辑控件中时，文本中任何选项卡上的字符将导致空间来生成到下一个制表位。  
  
 若要设置制表位到 32 个对话框单位的默认大小，在调用无参数版本的该成员函数。 若要设置制表位到 32 以外的大小，调用的版本与`cxEachStop`参数。 若要设置制表位大小的数组，包含两个参数使用的版本。  
  
 此成员函数仅由多行编辑控件处理。  
  
 `SetTabStops`不会自动刷新编辑窗口中。 如果更改已在编辑控件的文本的制表位，请调用[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重绘编辑窗口中。  
  
 有关详细信息，请参阅[EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663)和[GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CEditView::SetTabStops](ceditview-class.md#settabstops)。  
  
##  <a name="a-nameshowballoontipa--ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip  
 显示与当前的编辑控件相关联的气球提示。  
  
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
|[in] `pEditBalloonTip`|指向[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)结构描述的气球提示。|  
|[in] `lpszTitle`|指向包含标题的气球提示的 Unicode 字符串指针。|  
|[in] `lpszText`|包含的气球提示文本的 Unicode 字符串指针。|  
|[in] `ttiIcon`|`INT` ，它指定要将与气球状提示相关联的图标的类型。 默认值为 `TTI_NONE`。 有关详细信息，请参阅`ttiIcon`的成员[EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466)结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此函数可将发送[EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 有关详细信息，请参阅[Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707)宏。  
  
### <a name="example"></a>示例  
 下面的代码示例定义一个变量， `m_cedit`，也就是说，用来访问当前的编辑控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例显示一个编辑控件的气球提示。 [CEdit::ShowBalloonTip](#showballoontip)方法指定标题和气球的提示文本。  
  
 [!code-cpp[NVC_MFC_CEdit_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="a-nameundoa--ceditundo"></a><a name="undo"></a>CEdit::Undo  
 调用此函数可撤消的上一个编辑控件的操作。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>返回值  
 对于单行编辑控件，则返回值始终为非零。 对于多行编辑控件，返回值不为零如果撤消操作成功，则为 0，如果撤消操作将失败。  
  
### <a name="remarks"></a>备注  
 撤消操作还可用于撤消。 例如，将还原已删除的文本与首次调用**撤消**。 只要没有任何干预的编辑操作，您可以删除再次用到第二次调用的文本**撤消**。  
  
 有关详细信息，请参阅[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CEdit #&25;](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>另请参阅  
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

