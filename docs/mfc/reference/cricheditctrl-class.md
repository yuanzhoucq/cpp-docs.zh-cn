---
title: "CRichEditCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCtrl
- AFXCMN/CRichEditCtrl
- AFXCMN/CRichEditCtrl::CRichEditCtrl
- AFXCMN/CRichEditCtrl::CanPaste
- AFXCMN/CRichEditCtrl::CanRedo
- AFXCMN/CRichEditCtrl::CanUndo
- AFXCMN/CRichEditCtrl::CharFromPos
- AFXCMN/CRichEditCtrl::Clear
- AFXCMN/CRichEditCtrl::Copy
- AFXCMN/CRichEditCtrl::Create
- AFXCMN/CRichEditCtrl::CreateEx
- AFXCMN/CRichEditCtrl::Cut
- AFXCMN/CRichEditCtrl::DisplayBand
- AFXCMN/CRichEditCtrl::EmptyUndoBuffer
- AFXCMN/CRichEditCtrl::FindText
- AFXCMN/CRichEditCtrl::FindWordBreak
- AFXCMN/CRichEditCtrl::FormatRange
- AFXCMN/CRichEditCtrl::GetCharPos
- AFXCMN/CRichEditCtrl::GetDefaultCharFormat
- AFXCMN/CRichEditCtrl::GetEventMask
- AFXCMN/CRichEditCtrl::GetFirstVisibleLine
- AFXCMN/CRichEditCtrl::GetIRichEditOle
- AFXCMN/CRichEditCtrl::GetLimitText
- AFXCMN/CRichEditCtrl::GetLine
- AFXCMN/CRichEditCtrl::GetLineCount
- AFXCMN/CRichEditCtrl::GetModify
- AFXCMN/CRichEditCtrl::GetOptions
- AFXCMN/CRichEditCtrl::GetParaFormat
- AFXCMN/CRichEditCtrl::GetPunctuation
- AFXCMN/CRichEditCtrl::GetRect
- AFXCMN/CRichEditCtrl::GetRedoName
- AFXCMN/CRichEditCtrl::GetSel
- AFXCMN/CRichEditCtrl::GetSelectionCharFormat
- AFXCMN/CRichEditCtrl::GetSelectionType
- AFXCMN/CRichEditCtrl::GetSelText
- AFXCMN/CRichEditCtrl::GetTextLength
- AFXCMN/CRichEditCtrl::GetTextLengthEx
- AFXCMN/CRichEditCtrl::GetTextMode
- AFXCMN/CRichEditCtrl::GetTextRange
- AFXCMN/CRichEditCtrl::GetUndoName
- AFXCMN/CRichEditCtrl::GetWordWrapMode
- AFXCMN/CRichEditCtrl::HideSelection
- AFXCMN/CRichEditCtrl::LimitText
- AFXCMN/CRichEditCtrl::LineFromChar
- AFXCMN/CRichEditCtrl::LineIndex
- AFXCMN/CRichEditCtrl::LineLength
- AFXCMN/CRichEditCtrl::LineScroll
- AFXCMN/CRichEditCtrl::Paste
- AFXCMN/CRichEditCtrl::PasteSpecial
- AFXCMN/CRichEditCtrl::PosFromChar
- AFXCMN/CRichEditCtrl::Redo
- AFXCMN/CRichEditCtrl::ReplaceSel
- AFXCMN/CRichEditCtrl::RequestResize
- AFXCMN/CRichEditCtrl::SetAutoURLDetect
- AFXCMN/CRichEditCtrl::SetBackgroundColor
- AFXCMN/CRichEditCtrl::SetDefaultCharFormat
- AFXCMN/CRichEditCtrl::SetEventMask
- AFXCMN/CRichEditCtrl::SetModify
- AFXCMN/CRichEditCtrl::SetOLECallback
- AFXCMN/CRichEditCtrl::SetOptions
- AFXCMN/CRichEditCtrl::SetParaFormat
- AFXCMN/CRichEditCtrl::SetPunctuation
- AFXCMN/CRichEditCtrl::SetReadOnly
- AFXCMN/CRichEditCtrl::SetRect
- AFXCMN/CRichEditCtrl::SetSel
- AFXCMN/CRichEditCtrl::SetSelectionCharFormat
- AFXCMN/CRichEditCtrl::SetTargetDevice
- AFXCMN/CRichEditCtrl::SetTextMode
- AFXCMN/CRichEditCtrl::SetUndoLimit
- AFXCMN/CRichEditCtrl::SetWordCharFormat
- AFXCMN/CRichEditCtrl::SetWordWrapMode
- AFXCMN/CRichEditCtrl::StopGroupTyping
- AFXCMN/CRichEditCtrl::StreamIn
- AFXCMN/CRichEditCtrl::StreamOut
- AFXCMN/CRichEditCtrl::Undo
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class, common controls
- CRichEditCtrl class
- formatted text [C++]
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 262b2b8548f203a210b1aabbe149fe25cf6ad655
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="cricheditctrl-class"></a>CRichEditCtrl 类
提供 Rich Edit 控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](#cricheditctrl)|构造 `CRichEditCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](#canpaste)|确定当可以被剪贴板内容粘贴到此 rich edit 控件。|  
|[CRichEditCtrl::CanRedo](#canredo)|确定是否存在该控件的重做队列中的任何操作。|  
|[CRichEditCtrl::CanUndo](#canundo)|确定是否编辑操作可用于撤消。|  
|[CRichEditCtrl::CharFromPos](#charfrompos)|检索有关与编辑控件的工作区中的指定点最接近的字符的信息。|  
|[CRichEditCtrl::Clear](#clear)|清除当前的选择。|  
|[CRichEditCtrl::Copy](#copy)|将当前所选内容复制到剪贴板。|  
|[CRichEditCtrl::Create](#create)|创建 Windows rich edit 控件并将其与此关联`CRichEditCtrl`对象。|  
|[CRichEditCtrl::CreateEx](#createex)|创建 Windows rich edit 控件具有指定扩展窗口样式并将其与此关联`CRichEditCtrl`对象。|  
|[CRichEditCtrl::Cut](#cut)|剪切到剪贴板当前所选内容。|  
|[CRichEditCtrl::DisplayBand](#displayband)|显示此内容的一部分`CRichEditCtrl`对象。|  
|[CRichEditCtrl::EmptyUndoBuffer](#emptyundobuffer)|重置 （清除） 的撤消标志`CRichEditCtrl`对象。|  
|[CRichEditCtrl::FindText](#findtext)|查找文本在此`CRichEditCtrl`对象。|  
|[CRichEditCtrl::FindWordBreak](#findwordbreak)|查找下一步的 word 中断之前或之后的指定的字符位置，或检索该位置处字符的信息。|  
|[CRichEditCtrl::FormatRange](#formatrange)|设置的目标输出设备的文本范围的格式。|  
|[CRichEditCtrl::GetCharPos](#getcharpos)|确定给定字符在此位置`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetDefaultCharFormat](#getdefaultcharformat)|检索格式设置在此特性的当前默认字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetEventMask](#geteventmask)|检索此事件掩码`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetFirstVisibleLine](#getfirstvisibleline)|确定在此最顶层可见的行`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetIRichEditOle](#getiricheditole)|检索指向的`IRichEditOle`接口为此 rich edit 控件。|  
|[CRichEditCtrl::GetLimitText](#getlimittext)|获取限制上的用户可以键入的文本量`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetLine](#getline)|从这检索一行文本`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetLineCount](#getlinecount)|检索在此的行数`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetModify](#getmodify)|确定此内容`CRichEditCtrl`自上次保存后已更改对象。|  
|[CRichEditCtrl::GetOptions](#getoptions)|检索使用丰富的编辑控制选项。|  
|[CRichEditCtrl::GetParaFormat](#getparaformat)|检索段落格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetPunctuation](#getpunctuation)|检索 rich edit 控件的当前标点字符。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::GetRect](#getrect)|检索此格式设置的矩形`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetRedoName](#getredoname)|如果任何，该控件的重做队列中检索下一步操作的类型。|  
|[CRichEditCtrl::GetSel](#getsel)|获取开始和结束位置在此当前所选内容`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelectionCharFormat](#getselectioncharformat)|检索格式设置当前选定内容中此特性的字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelectionType](#getselectiontype)|检索当前选定内容中此内容的类型`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelText](#getseltext)|获取当前所选内容的文本中这`CRichEditCtrl`对象|  
|[CRichEditCtrl::GetTextLength](#gettextlength)|检索文本的长度，以字符为单位，在此`CRichEditCtrl`对象。 不包括终止 null 字符。|  
|[CRichEditCtrl::GetTextLengthEx](#gettextlengthex)|检索字符或丰富的编辑视图中的字节的数。 接受标志以指示确定 rich edit 控件中文本的长度的方法的列表|  
|[CRichEditCtrl::GetTextMode](#gettextmode)|检索 rich edit 控件的当前文本模式和撤消级别。|  
|[CRichEditCtrl::GetTextRange](#gettextrange)|检索指定的文本范围。|  
|[CRichEditCtrl::GetUndoName](#getundoname)|如果有，请检索的下一步的撤消操作的类型。|  
|[CRichEditCtrl::GetWordWrapMode](#getwordwrapmode)|检索当前的自动换行和 rich edit 控件的 word 换行选项。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::HideSelection](#hideselection)|显示或隐藏当前选定内容。|  
|[CRichEditCtrl::LimitText](#limittext)|限制的用户可以键入的文本量`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineFromChar](#linefromchar)|确定哪一行包含给定的字符。|  
|[CRichEditCtrl::LineIndex](#lineindex)|检索给定行中的字符索引`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineLength](#linelength)|检索在此给定行的长度`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineScroll](#linescroll)|将在此文本滚动`CRichEditCtrl`对象。|  
|[CRichEditCtrl::Paste](#paste)|将剪贴板的内容插入到此 rich edit 控件。|  
|[CRichEditCtrl::PasteSpecial](#pastespecial)|将剪贴板的内容插入到此 rich edit 控件中所指定的数据格式。|  
|[CRichEditCtrl::PosFromChar](#posfromchar)|检索指定的字符的编辑控件中的客户端区域坐标。|  
|[CRichEditCtrl::Redo](#redo)|重做控件的重做队列中的下一步操作。|  
|[CRichEditCtrl::ReplaceSel](#replacesel)|替换当前选定内容中这`CRichEditCtrl`具有指定文本的对象。|  
|[CRichEditCtrl::RequestResize](#requestresize)|强制将此`CRichEditCtrl`对象将请求重设大小通知发送。|  
|[CRichEditCtrl::SetAutoURLDetect](#setautourldetect)|指示自动 URL 检测是否在 rich edit 控件中处于活动状态。|  
|[CRichEditCtrl::SetBackgroundColor](#setbackgroundcolor)|在此设置的背景色`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetDefaultCharFormat](#setdefaultcharformat)|设置格式设置在此特性的当前默认字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetEventMask](#seteventmask)|设置此事件掩码`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetModify](#setmodify)|设置或清除此修改标志`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetOLECallback](#setolecallback)|集`IRichEditOleCallback`此 rich edit 控件的 COM 对象。|  
|[CRichEditCtrl::SetOptions](#setoptions)|设置此选项`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetParaFormat](#setparaformat)|设置的段落格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetPunctuation](#setpunctuation)|设置 rich edit 控件的标点字符。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::SetReadOnly](#setreadonly)|设置此只读选项`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetRect](#setrect)|此设置的格式设置的矩形`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetSel](#setsel)|在此设置选择`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetSelectionCharFormat](#setselectioncharformat)|设置字符格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetTargetDevice](#settargetdevice)|设置此目标输出设备`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetTextMode](#settextmode)|设置 rich edit 控件的文本模式或撤消级别。 如果控件包含文本，将失败消息。|  
|[CRichEditCtrl::SetUndoLimit](#setundolimit)|设置可以存储在撤消队列中的操作的最大数量。|  
|[CRichEditCtrl::SetWordCharFormat](#setwordcharformat)|设置格式设置特性在此则当前单词中的字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetWordWrapMode](#setwordwrapmode)|集丰富的自动换行和断字选项编辑控件。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::StopGroupTyping](#stopgrouptyping)|停止其他当前的撤消操作中键入操作从收集控件。 如果有的话，到撤消队列中的新操作，该控件将存储的下一步的键入操作。|  
|[CRichEditCtrl::StreamIn](#streamin)|将文本从输入流插入到此`CRichEditCtrl`对象。|  
|[CRichEditCtrl::StreamOut](#streamout)|将存储从该文本`CRichEditCtrl`到输出流的对象。|  
|[CRichEditCtrl::Undo](#undo)|反转的上一个编辑操作。|  
  
## <a name="remarks"></a>备注  
 "Rich edit 控件"是一个窗口，用户可以输入和编辑文本。 文本可以分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件用于设置文本格式提供一个编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 此 Windows 公共控件 (因此`CRichEditCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。 `CRichEditCtrl`类支持的版本 2.0 和 3.0 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] rich edit 控件。  
  
> [!CAUTION]
>  如果你使用 rich edit 控件在对话框中 (无论是否你的应用程序是 SDI、 MDI 还是基于对话框的)，必须调用[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)后对话框之前，会显示框。 调用此函数的一个典型位置位于程序的 `InitInstance` 成员函数中。 您无需在每次显示对话框时调用它，仅第一次需要。 如果您使用 `AfxInitRichEdit`，则不必调用 `CRichEditView`。  
  
 有关详细信息使用`CRichEditCtrl`，请参阅︰  
  
- [控件](../../mfc/controls-mfc.md)  
  
- [使用 CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   知识库文章 Q259949︰ 信息︰ SetCaretPos() 是不适合与 CEdit 或 CRichEditCtrl 控件  
  
 Rich edit 控件使用 MFC 应用程序中的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="canpaste"></a>CRichEditCtrl::CanPaste  
 确定 rich edit 控件可以粘贴指定的剪贴板格式。  
  
```  
BOOL CanPaste(UINT nFormat = 0) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFormat`  
 查询剪贴板数据格式。 此参数可以是预定义的剪贴板格式或返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)。  
  
### <a name="return-value"></a>返回值  
 如果可粘贴的剪贴板格式; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`nFormat`为 0，`CanPaste`将重试当前在剪贴板上的任何格式。  
  
 有关详细信息，请参阅[EM_CANPASTE](http://msdn.microsoft.com/library/windows/desktop/bb787993)消息和[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 1](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_1.cpp)]  
  
##  <a name="canredo"></a>CRichEditCtrl::CanRedo  
 确定是否重做队列包含任何操作。  
  
```  
BOOL CanRedo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果重做队列包含操作，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 若要发现的操作重做队列中的名称，调用[CRichEditCtrl::GetRedoName](#getredoname)。 若要重做最新的撤消操作，调用[重做](#redo)。  
  
 有关详细信息，请参阅[EM_CANREDO](http://msdn.microsoft.com/library/windows/desktop/bb787995)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="canundo"></a>CRichEditCtrl::CanUndo  
 确定是否可以撤消的上一个编辑操作。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以通过调用撤消上一个编辑操作则不为[撤消](#undo)成员函数; 如果它不能撤消则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 2](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_2.cpp)]  
  
##  <a name="charfrompos"></a>CRichEditCtrl::CharFromPos  
 检索有关由参数指定点处的字符的信息`pt`。  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含指定点的坐标。  
  
### <a name="return-value"></a>返回值  
 最接近指定的点字符的从零开始的字符索引。 如果指定的点不在控件中的最后一个字符，则返回值指示在控件中的最后一个字符。  
  
### <a name="remarks"></a>备注  
 此成员函数可与 rich edit 控件。 若要获取编辑控件的信息，请调用[CEdit::CharFromPos](../../mfc/reference/cedit-class.md#charfrompos)。  
  
 有关详细信息，请参阅[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="clear"></a>CRichEditCtrl::Clear  
 删除 （清除） 中当前选定内容 （如果有） 的丰富编辑控件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 删除由**清除**可以通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容并将放到剪贴板上的已删除的内容，调用[剪切](#cut)成员函数。  
  
 有关详细信息，请参阅[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 3](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_3.cpp)]  
  
##  <a name="copy"></a>CRichEditCtrl::Copy  
 将复制当前所选内容 （如果有） 在 rich edit 控件到剪贴板。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 4](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_4.cpp)]  
  
##  <a name="create"></a>CRichEditCtrl::Create  
 创建 Windows rich edit 控件并将其与此关联`CRichEditCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定编辑控件的样式。 应用中列出的窗口样式的组合**备注**以下部分，和[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)、 中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定编辑控件的大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](../../mfc/reference/rect-structure1.md)结构。  
  
 `pParentWnd`  
 指定编辑控件的父窗口 (通常[CDialog](../../mfc/reference/cdialog-class.md))。 它不能**NULL**。  
  
 `nID`  
 指定编辑控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为为 0。  
  
### <a name="remarks"></a>备注  
 构造`CRichEditCtrl`两个步骤中的对象。 首先，调用[CRichEditCtrl](#cricheditctrl)构造函数，然后调用**创建**，它创建 Windows 编辑控件并将其附加到`CRichEditCtrl`对象。  
  
 当使用此函数创建 rich edit 控件时，首先必须加载必要的公共控件库。 若要加载的库，调用全局函数[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)，这反过来初始化公共控件库。 你需要调用`AfxInitRichEdit`唯一一次是在你的过程。  
  
 当**创建**执行 Windows 发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)的编辑控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CRichEditCtrl`、 将消息映射添加到新的类中，和重写上面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)向一个编辑控件。  
  
- **WS_CHILD**始终。  
  
- **WS_VISIBLE**通常。  
  
- **WS_DISABLED**很少。  
  
- **WS_GROUP**与组控件。  
  
- **WS_TABSTOP**要包括在 tab 键顺序中的编辑控件。  
  
 窗口样式有关的详细信息，请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 5](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_5.cpp)]  
  
##  <a name="createex"></a>CRichEditCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CRichEditCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定编辑控件的样式。 应用中列出的窗口样式的组合**备注**部分[创建](#create)和[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)、 中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是**创建**将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="cricheditctrl"></a>CRichEditCtrl::CRichEditCtrl  
 构造 `CRichEditCtrl` 对象。  
  
```  
CRichEditCtrl();
```  
  
### <a name="remarks"></a>备注  
 使用[创建](#create)来构造 Windows rich edit 控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 6](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_6.cpp)]  
  
##  <a name="cut"></a>CRichEditCtrl::Cut  
 删除 （操作会剪切） 中当前选定内容 （如果有） 的丰富编辑控件，并将已删除的文本复制到剪贴板。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 删除由**剪切**可以通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容，而无需将删除的文本放入剪贴板，调用[清除](#clear)成员函数。  
  
 有关详细信息，请参阅[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 7](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_7.cpp)]  
  
##  <a name="displayband"></a>CRichEditCtrl::DisplayBand  
 显示按照前面设置格式的格式文本编辑控件 （文本和 OLE 项） 的内容的一部分[FormatRange](#formatrange)。  
  
```  
BOOL DisplayBand(LPRECT pDisplayRect);
```  
  
### <a name="parameters"></a>参数  
 `pDisplayRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的设备以显示文本的区域。  
  
### <a name="return-value"></a>返回值  
 如果带格式的文本的显示成功，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 文本和 OLE 项将被剪辑到由指针指定的区域`pDisplayRect`。  
  
 有关详细信息，请参阅[EM_DISPLAYBAND](http://msdn.microsoft.com/library/windows/desktop/bb787997)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::FormatRange](#formatrange)。  
  
##  <a name="emptyundobuffer"></a>CRichEditCtrl::EmptyUndoBuffer  
 重置 （清除） 此 rich edit 控件的撤消标志。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>备注  
 现在，该控件将无法撤消的上一个编辑操作。 Rich edit 控件中的某个操作可用于撤消时，均设置还原标志。  
  
 每次调用，将自动清除撤消标志[CWnd](../../mfc/reference/cwnd-class.md)成员函数[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 有关详细信息，请参阅[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 8](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_8.cpp)]  
  
##  <a name="findtext"></a>CRichEditCtrl::FindText  
 查找 rich edit 控件中的文本。  
  
```  
long FindText(
    DWORD dwFlags,  
    FINDTEXTEX* pFindText) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 有关可能的值的列表，请参阅`wParam`中[EM_FINDTEXTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788011)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *pFindText*  
 指向[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)结构为参数提供了搜索，并返回在其中找到匹配的范围。  
  
### <a name="return-value"></a>返回值  
 从零开始的字符位置的下一个匹配项;-如果没有更多的匹配项，则为 1。  
  
### <a name="remarks"></a>备注  
 你可以搜索其中之一向上或向下通过设置中的适当范围内参数[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构内**FINDTEXTEX**结构。  
  
 有关详细信息，请参阅[EM_FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb788011)消息和[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 9](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_9.cpp)]  
  
##  <a name="findwordbreak"></a>CRichEditCtrl::FindWordBreak  
 查找下一步的 word 中断之前或之后指定的位置`nStart`。  
  
```  
DWORD FindWordBreak(
    UINT nCode,  
    DWORD nStart) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCode`  
 指示要执行的操作。 有关可能的值的列表，请参见参数的说明`code`中**EM_FINDWORDBREAK**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nStart`  
 从其开始的从零开始的字符位置。  
  
### <a name="return-value"></a>返回值  
 基于参数`nCode`。 有关详细信息，请参阅[EM_FINDWORDBREAK](http://msdn.microsoft.com/library/windows/desktop/bb788018)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数可用于检索有关给定位置处的字符的信息。  
  
##  <a name="formatrange"></a>CRichEditCtrl::FormatRange  
 设置特定设备的 rich edit 控件中的文本范围的格式。  
  
```  
long FormatRange(
    FORMATRANGE* pfr,  
    BOOL bDisplay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pfr*  
 指向[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)结构，其中包含有关输出设备信息。 **NULL**指示 rich edit 控件中的缓存的信息可以被释放。  
  
 *bDisplay*  
 指示是否应呈现的文本。 如果**FALSE**，只需测量的文本。  
  
### <a name="return-value"></a>返回值  
 适合在区域加 1 中的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 通常情况下，此调用后跟调用[DisplayBand](#displayband)。  
  
 有关详细信息，请参阅[EM_FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb788020)消息和[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 10](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_10.cpp)]  
  
##  <a name="getcharpos"></a>CRichEditCtrl::GetCharPos  
 获取在此给定的字符的位置 （左上角）`CRichEditCtrl`对象。  
  
```  
CPoint GetCharPos(long lChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `lChar`  
 字符的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 由指定的字符的左上角的位置`lChar`。  
  
### <a name="remarks"></a>备注  
 通过给的从零开始的索引值指定的字符。 如果`lChar`大于在此的最后一个字符的索引`CRichEditCtrl`对象，返回的值在此指定刚超出最后一个字符的字符位置的坐标`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getdefaultcharformat"></a>CRichEditCtrl::GetDefaultCharFormat  
 获取格式设置此特性的默认字符`CRichEditCtrl`对象。  
  
```  
DWORD GetDefaultCharFormat(CHARFORMAT& cf) const;  DWORD GetDefaultCharFormat(CHARFORMAT2& cf) const;  
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针**CHARFORMAT**存放格式设置特性的默认字符结构。  
  
 在第二个版本中，指向的指针**CHARFORMAT2**结构，它是 Rich Edit 2.0 扩展到**CHARFORMAT**存放格式设置特性的默认字符的结构。  
  
### <a name="return-value"></a>返回值  
 **DwMask**数据成员的`cf`。 它指定格式设置特性的默认字符。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅**EM_GETCHARFORMAT**消息和**CHARFORMAT**和**CHARFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[SetDefaultCharFormat](#setdefaultcharformat)。  
  
##  <a name="geteventmask"></a>CRichEditCtrl::GetEventMask  
 获取此事件掩码`CRichEditCtrl`对象。  
  
```  
long GetEventMask() const;  
```  
  
### <a name="return-value"></a>返回值  
 此事件掩码`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 事件掩码指定对哪些通知邮件`CRichEditCtrl`对象发送到其父窗口。  
  
 有关详细信息，请参阅[EM_GETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb788032)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::SetEventMask](#seteventmask)。  
  
##  <a name="getfirstvisibleline"></a>CRichEditCtrl::GetFirstVisibleLine  
 确定在此最顶层可见的行`CRichEditCtrl`对象。  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此最顶部可见的行的从零开始索引`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 11](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_11.cpp)]  
  
##  <a name="getiricheditole"></a>CRichEditCtrl::GetIRichEditOle  
 访问**IRichEditOle**此接口`CRichEditCtrl`对象。  
  
```  
IRichEditOle* GetIRichEditOle() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向[IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306)接口可用来访问此`CRichEditCtrl`对象的 OLE 功能;**NULL**如果接口不可访问。  
  
### <a name="remarks"></a>备注  
 使用此接口来访问此`CRichEditCtrl`对象的 OLE 功能。  
  
 有关详细信息，请参阅[EM_GETOLEINTERFACE](http://msdn.microsoft.com/library/windows/desktop/bb788041)消息和[IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306)接口中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getlimittext"></a>CRichEditCtrl::GetLimitText  
 获取此文本限制`CRichEditCtrl`对象。  
  
```  
long GetLimitText() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前文本限制，以字节为单位，这`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 文本限制是文本，以字节为单位的最长可接受 rich edit 控件。  
  
 有关详细信息，请参阅[EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 12](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_12.cpp)]  
  
##  <a name="getline"></a>CRichEditCtrl::GetLine  
 从这检索一行文本`CRichEditCtrl`对象。  
  
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
 若要检索的行的从零开始索引。  
  
 `lpszBuffer`  
 指向要接收的文本的缓冲区。 缓冲区的第一个单词必须指定的最大可以复制到缓冲区的字节数。  
  
 `nMaxLength`  
 最大可以复制到的字符数`lpszBuffer`。 第二种形式的`GetLine`此值置于指定的缓冲区的第一个单词`lpszBuffer`。  
  
### <a name="return-value"></a>返回值  
 复制到的字符数`lpszBuffer`。  
  
### <a name="remarks"></a>备注  
 复制的行不包含终止 null 字符。  
  
> [!NOTE]
>  由于缓冲区的第一个单词存储要复制的字符数，请确保你的缓冲区至少 4 个字节。  
  
 有关详细信息，请参阅[EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetLineCount](#getlinecount)。  
  
##  <a name="getlinecount"></a>CRichEditCtrl::GetLineCount  
 检索中的行数`CRichEditCtrl`对象。  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此的行数`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 13](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_13.cpp)]  
  
##  <a name="getmodify"></a>CRichEditCtrl::GetModify  
 确定此内容`CRichEditCtrl`已修改对象。  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零的文本的`CRichEditCtrl`已修改对象; 否则为 0。  
  
### <a name="remarks"></a>备注  
 Windows 维护，该值指示是否已更改了 rich edit 控件的内容的内部标志。 当编辑控件首次创建，并且还可以通过调用清除时会清除此标志[SetModify](#setmodify)成员函数。  
  
 有关详细信息，请参阅[EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 14](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_14.cpp)]  
  
##  <a name="getoptions"></a>CRichEditCtrl::GetOptions  
 检索当前设置为 rich edit 控件的选项。  
  
```  
UINT GetOptions() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前选项标志值的组合。 有关这些值的列表，请参阅*fOptions*中的参数[EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getparaformat"></a>CRichEditCtrl::GetParaFormat  
 获取段落格式设置的当前所选内容的属性。  
  
```  
DWORD GetParaFormat(PARAFORMAT& pf) const;  DWORD GetParaFormat(PARAFORMAT2& pf) const;  
```  
  
### <a name="parameters"></a>参数  
 `pf`  
 在第一个版本中，指向的指针[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)结构，用于保存的段落格式设置的当前所选内容的属性。  
  
 在第二个版本中，指向的指针[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，它是 Rich Edit 2.0 扩展到**PARAFORMAT**存放格式设置特性的默认字符的结构。  
  
### <a name="return-value"></a>返回值  
 **DwMask**数据成员的`pf`。 它指定的段落格式设置的当前选择中一致的属性。  
  
### <a name="remarks"></a>备注  
 如果选择多个段落，则`pf`接收所选的第一个段落的特性。 返回值指定选择中一致的哪些属性。  
  
 有关详细信息，请参阅[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)消息和**PARAFORMAT**和**PARAFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::SetParaFormat](#setparaformat)。  
  
##  <a name="getpunctuation"></a>CRichEditCtrl::GetPunctuation  
 Rich edit 控件中获取当前的标点字符。  
  
```  
BOOL GetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc) const;  
```  
  
### <a name="parameters"></a>参数  
 `fType`  
 标点类型标志中, 所述`fType`参数[EM_GETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774184)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 指向的指针[标点](http://msdn.microsoft.com/library/windows/desktop/bb787944)结构中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 此成员函数时使用仅亚洲语言版本的操作系统。  
  
##  <a name="getrect"></a>CRichEditCtrl::GetRect  
 检索此格式设置的矩形`CRichEditCtrl`对象。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指向[RECT](../../mfc/reference/rect-structure1.md)接收的格式设置的矩形`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 格式设置的矩形是文本的边框。 此值的大小无关`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LimitText](#limittext)。  
  
##  <a name="getredoname"></a>CRichEditCtrl::GetRedoName  
 如果有的话，请检索重做队列中中的下一个可用操作的类型。  
  
```  
UNDONAMEID GetRedoName() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，`GetRedoName`返回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)枚举类型，该值指示控件的重做队列中的下一步操作的类型。 如果重做队列为空，或如果队列中的重做操作是未知类型，`GetRedoName`返回 0。  
  
### <a name="remarks"></a>备注  
 操作可撤消或重做的类型包括键入、 删除、 拖放、 剪切、 和粘贴操作。 此信息可用于提供撤消和重做操作，如下拉列表框 redoable 操作的扩展的用户界面的应用程序。  
  
##  <a name="getsel"></a>CRichEditCtrl::GetSel  
 检索在此当前所选内容的边界`CRichEditCtrl`对象。  
  
```  
void GetSel(CHARRANGE& cr) const;  
  
void GetSel(
    long& nStartChar,  
    long& nEndChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 引用[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构接收当前所选内容的边界。  
  
 `nStartChar`  
 中当前选择的第一个字符的从零开始索引。  
  
 `nEndChar`  
 当前所选内容中的最后一个字符的从零开始索引。  
  
### <a name="remarks"></a>备注  
 此函数的两种形式提供了备用方法来获取所选内容的边界。 请按照这些窗体的简要说明操作︰  
  
- **GetSel (** `cr` **)**此窗体使用**CHARRANGE**结构，其**cpMin**和**cpMax**成员返回界限。  
  
- **GetSel (** `nStartChar` **，** `nEndChar` **)**此窗体的参数中返回的界限`nStartChar`和`nEndChar`。  
  
 如果所选内容都将包括所有内容开头 ( **cpMin**或`nStartChar`) 是 0 和结束 ( **cpMax**或`nEndChar`) 是-1。  
  
 有关详细信息，请参阅[EM_EXGETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788001)消息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 15](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_15.cpp)]  
  
##  <a name="getselectioncharformat"></a>CRichEditCtrl::GetSelectionCharFormat  
 获取字符格式设置的当前所选内容的属性。  
  
```  
DWORD GetSelectionCharFormat(CHARFORMAT& cf) const;  DWORD GetSelectionCharFormat(CHARFORMAT2& cf) const;  
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构接收的字符格式设置的当前所选内容的属性。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是 Rich Edit 2.0 扩展到**CHARFORMAT**结构接收的字符格式设置的当前所选内容的属性。  
  
### <a name="return-value"></a>返回值  
 **DwMask**数据成员的`cf`。 它指定的字符格式设置的当前选择中一致的属性。  
  
### <a name="remarks"></a>备注  
 `cf`参数中当前选择接收的第一个字符的属性。 返回值指定选择中一致的哪些属性。  
  
 有关详细信息，请参阅[EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026)消息和**CHARFORMAT**和**CHARFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[SetSelectionCharFormat](#setselectioncharformat)。  
  
##  <a name="getselectiontype"></a>CRichEditCtrl::GetSelectionType  
 确定在此所选内容类型`CRichEditCtrl`对象。  
  
```  
WORD GetSelectionType() const;  
```  
  
### <a name="return-value"></a>返回值  
 标志，指示当前所选内容的内容。 以下标志的组合︰  
  
- `SEL_EMPTY`指示当前没有选定内容。  
  
- `SEL_TEXT`指示当前所选内容包含文本。  
  
- `SEL_OBJECT`指示当前所选内容包含至少一个 OLE 项。  
  
- `SEL_MULTICHAR`指示当前所选内容包含多个字符的文本。  
  
- `SEL_MULTIOBJECT`指示当前所选内容包含多个 OLE 对象。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_SELECTIONTYPE](http://msdn.microsoft.com/library/windows/desktop/bb774223)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 16](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_16.cpp)]  
  
##  <a name="getseltext"></a>CRichEditCtrl::GetSelText  
 从当前在此选择中检索文本`CRichEditCtrl`对象。  
  
```  
long GetSelText(LPSTR lpBuf) const;  CString GetSelText() const;  
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 指向要接收中当前选择的文本的缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 依赖于窗体︰  
  
- **GetSelText (** `lpBuf` **)**复制到的字符数`lpBuf`，不包括 null 终止。  
  
- **GetSelText （)**包含当前所选内容的字符串。  
  
### <a name="remarks"></a>备注  
 如果你使用第一个窗体， **GetSelText (** `lpBuf` **)**，你必须确保缓冲区足够大，它将接收的文本。 调用[GetSel](#getsel)以确定当前所选内容中的字符数。  
  
 有关详细信息，请参阅[EM_GETSELTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774190)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::GetSelectionType](#getselectiontype)。  
  
##  <a name="gettextlength"></a>CRichEditCtrl::GetTextLength  
 检索文本的长度，以字符为单位，在此`CRichEditCtrl`对象，不包括终止 null 字符。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此文本的长度`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_GETTEXTLENGTH](http://msdn.microsoft.com/library/windows/desktop/ms632628)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 17](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_17.cpp)]  
  
##  <a name="gettextlengthex"></a>CRichEditCtrl::GetTextLengthEx  
 计算 rich edit 控件中文本的长度。  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 指定该方法用于确定文本长度的值。 此成员可以是一个或多个值中的标志成员列出[GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `uCodePage`  
 翻译 (CP_ACP ANSI 代码页，适用于 Unicode 的 1200年) 的代码页。  
  
### <a name="return-value"></a>返回值  
 字符或编辑控件中的字节数。 如果中的设置不兼容的标志`dwFlags`，此成员函数将返回`E_INVALIDARG`。  
  
### <a name="remarks"></a>备注  
 `GetTextLengthEx`提供了确定文本的长度的其他方式。 它支持 Rich Edit 2.0 功能。 请参阅[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="gettextmode"></a>CRichEditCtrl::GetTextMode  
 检索 rich edit 控件的当前文本模式和撤消级别。  
  
```  
UINT GetTextMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 中的位标志的一组[TEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774364)枚举类型，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 标志指示当前的文本模式和撤消的控制级别。  
  
##  <a name="gettextrange"></a>CRichEditCtrl::GetTextRange  
 获取指定的范围的字符。  
  
```  
int GetTextRange(
    int nFirst,  
    int nLast,  
    CString& refString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFirst`  
 在范围中前面，则第一个字符的字符位置的索引。  
  
 `nLast`  
 紧跟在范围内的最后一个字符的字符位置。  
  
 `refString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将收到文本的对象。  
  
### <a name="return-value"></a>返回值  
 复制的字符数，不包括终止 null 字符。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETTEXTRANGE](http://msdn.microsoft.com/library/windows/desktop/bb774199)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `GetTextRange`支持 Rich Edit 2.0 功能。 请参阅[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="getundoname"></a>CRichEditCtrl::GetUndoName  
 如果有的话，请检索撤消队列中的下一个可用操作的类型。  
  
```  
UNDONAMEID GetUndoName() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果已在控件的撤消队列，一个撤消操作`GetUndoName`返回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)枚举类型，该值指示在队列中的下一步操作的类型。 如果撤消队列为空，或如果队列中的撤消操作是未知类型，`GetUndoName`返回 0。  
  
### <a name="remarks"></a>备注  
 操作可撤消或重做的类型包括键入、 删除、 拖放、 剪切、 和粘贴操作。 此信息可用于提供撤消和重做操作，如下拉列表框可用于撤消的操作的扩展的用户界面的应用程序。  
  
##  <a name="getwordwrapmode"></a>CRichEditCtrl::GetWordWrapMode  
 检索当前的自动换行和 rich edit 控件的 word 换行选项。  
  
```  
UINT GetWordWrapMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的自动换行和断字选项中。 介绍了这些选项[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数是操作系统的仅适用于亚洲语言版本。  
  
##  <a name="hideselection"></a>CRichEditCtrl::HideSelection  
 更改所选内容的可见性。  
  
```  
void HideSelection(
    BOOL bHide,  
    BOOL bPerm);
```  
  
### <a name="parameters"></a>参数  
 `bHide`  
 指示应显示或隐藏，是否所选内容**TRUE**隐藏所选内容。  
  
 `bPerm`  
 指示是否应永久这一更改所选内容的可见性。  
  
### <a name="remarks"></a>备注  
 当`bPerm`是**TRUE**，它将更改`ECO_NOHIDESEL`此选项`CRichEditCtrl`对象。 此选项的简短说明，请参阅[SetOptions](#setoptions)。 你可以使用此函数来设置此的所有选项`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_HIDESELECTION](http://msdn.microsoft.com/library/windows/desktop/bb774210)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 18](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_18.cpp)]  
  
##  <a name="limittext"></a>CRichEditCtrl::LimitText  
 限制用户可以输入在编辑控件的文本的长度。  
  
```  
void LimitText(long nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nChars`  
 指定用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0 （默认值），则会将文本长度设置为 64k 字节。  
  
### <a name="remarks"></a>备注  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数将更多的文本放入比对的调用中指定的编辑控件`LimitText`，用户可以删除任何编辑控件中的文本。 但是，文本限制将阻止用户将现有的文本替换为新的文本，除非删除当前所选内容会导致将文本低于文本限制。  
  
> [!NOTE]
>  对于文本限制，每个 OLE 项算作单个字符。  
  
 有关详细信息，请参阅[EM_EXLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788003)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 19](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_19.cpp)]  
  
##  <a name="linefromchar"></a>CRichEditCtrl::LineFromChar  
 检索包含指定的字符索引的行的行号。  
  
```  
long LineFromChar(long nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含所需的字符的文本编辑控件中的从零开始的索引值或包含为-1。 如果`nIndex`为-1，它指定的当前行，即包含脱字号的行。  
  
### <a name="return-value"></a>返回值  
 包含指定的字符索引的行的从零开始的行号`nIndex`。 如果`nIndex`为-1，返回的包含所选内容的第一个字符的行数。 如果没有选择任何内容，则返回当前的行号。  
  
### <a name="remarks"></a>备注  
 字符索引是从开始处 rich edit 控件的字符数。 适用于字符计数，OLE 项被计为单个字符。  
  
 有关详细信息，请参阅[EM_EXLINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb788005)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 20](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_20.cpp)]  
  
##  <a name="lineindex"></a>CRichEditCtrl::LineIndex  
 检索在此行的字符索引`CRichEditCtrl`对象。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 包含所需的行的文本编辑控件中的索引值或包含为-1。 如果`nLine`为-1，它指定的当前行，即包含脱字号的行。  
  
### <a name="return-value"></a>返回值  
 在指定的行的字符索引`nLine`或-1，如果指定的行号大于然后编辑控件中的行数。  
  
### <a name="remarks"></a>备注  
 字符索引是从 rich edit 控件的开头到指定的行的字符数。  
  
 有关详细信息，请参阅[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 21](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_21.cpp)]  
  
##  <a name="linelength"></a>CRichEditCtrl::LineLength  
 检索 rich edit 控件中的行的长度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 指定其长度是要检索的行中的一个字符的字符索引。 如果此参数为-1，返回当前行 （包含脱字号的行） 的长度，不包括任何的长度在所选的行中的文本。 当`LineLength`称为对于单行编辑控件，则忽略此参数。  
  
### <a name="return-value"></a>返回值  
 当`LineLength`称为对于多行编辑控件，返回值是由指定的行的长度 （以字节为单位） `nLine`。 当`LineLength`称为对于单行编辑控件，返回值是编辑控件中的文本的长度 （以字节为单位）。  
  
### <a name="remarks"></a>备注  
 使用[LineIndex](#lineindex)成员函数以检索在此给定的行数量的字符索引`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LineIndex](#lineindex)。  
  
##  <a name="linescroll"></a>CRichEditCtrl::LineScroll  
 滚动的多行编辑控件的文本。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nLines`  
 指定垂直滚动的行的数。  
  
 `nChars`  
 指定水平滚动的字符位置的数。 如果 rich edit 控件已忽略此值**ES_RIGHT**或**ES_CENTER**样式。 [编辑样式](../../mfc/reference/edit-styles.md)中指定[创建](#create)。  
  
### <a name="remarks"></a>备注  
 编辑控件不垂直滚动过的文本编辑控件中的最后一行。 如果当前行加上指定的行数`nLines`超过了总的编辑控件中的行数，以便编辑控件的最后一行滚动到编辑控件窗口的顶部，将调整值。  
  
 `LineScroll`可以使用水平滚动过去的任意行的最后一个字符。  
  
 有关详细信息，请参阅[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="paste"></a>CRichEditCtrl::Paste  
 将数据从剪贴板粘贴到`CRichEditCtrl`中插入点，插入符号的位置。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含用识别的格式中的数据插入数据。  
  
 有关详细信息，请参阅[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 22](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_22.cpp)]  
  
##  <a name="pastespecial"></a>CRichEditCtrl::PasteSpecial  
 将在特定剪贴板格式的数据粘贴到此`CRichEditCtrl`对象。  
  
```  
void PasteSpecial(
    UINT nClipFormat,  
    DWORD dvAspect = 0,  
    HMETAFILE hMF = 0);
```  
  
### <a name="parameters"></a>参数  
 *nClipFormat*  
 剪贴板格式，将粘贴到此`CRichEditCtrl`对象。  
  
 *dvAspect*  
 要从剪贴板检索的数据的设备方面。  
  
 *hMF*  
 包含要粘贴的对象的图标化视图的图元文件的句柄。  
  
### <a name="remarks"></a>备注  
 在插入点，脱字号位置插入新材料。  
  
 有关详细信息，请参阅[EM_PASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/bb774214)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 23](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_23.cpp)]  
  
##  <a name="posfromchar"></a>CRichEditCtrl::PosFromChar  
 检索指定的字符的编辑控件中的客户端区域坐标。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 字符的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 字符、 （x，y） 的位置。 对于单行编辑控件，y 坐标值始终为零。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="redo"></a>CRichEditCtrl::Redo  
 重做控件的重做队列中的下一步操作。  
  
```  
BOOL Redo();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_REDO](http://msdn.microsoft.com/library/windows/desktop/bb774218)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="replacesel"></a>CRichEditCtrl::ReplaceSel  
 替换当前选定内容中这`CRichEditCtrl`具有指定文本的对象。  
  
```  
void ReplaceSel(
    LPCTSTR lpszNewText,  
    BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `lpszNewText`  
 指向以 null 结尾的字符串，包含替换文本指针。  
  
 `bCanUndo`  
 若要指定此函数可用于撤消，设置到此参数的值**TRUE**。 默认值是**FALSE**。  
  
### <a name="remarks"></a>备注  
 若要替换中的所有文本`CRichEditCtrl`对象，请使用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 如果没有当前没有选定内容，在插入点，即，当前脱字号位置插入替换文本。  
  
 此函数将设置插入的文本的格式与现有字符格式设置。 替换文本的整个范围时 (通过调用`SetSel`（0，-1） 之前调用`ReplaceSel`)，则会保留上一个段落格式设置，这在继承的新插入的文本的段落字符的结尾。  
  
 有关详细信息，请参阅[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LineIndex](#lineindex)。  
  
##  <a name="requestresize"></a>CRichEditCtrl::RequestResize  
 强制将此`CRichEditCtrl`对象发送**EN_REQUESTRESIZE**到其父窗口的通知消息。  
  
```  
void RequestResize();
```  
  
### <a name="remarks"></a>备注  
 此函数很有用期间[CWnd::OnSize](../../mfc/reference/cwnd-class.md#onsize)处理无界限`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb774220)消息和**无界限 Rich Edit 控件**部分[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setautourldetect"></a>CRichEditCtrl::SetAutoURLDetect  
 设置 rich edit 控件，若要自动检测 URL。  
  
```  
BOOL SetAutoURLDetect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否将控件设置为自动检测 URL。 如果**TRUE**，启用它。 如果**FALSE**，它处于禁用状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为非零的零。 例如，消息可能会由于内存不足导致失败。  
  
### <a name="remarks"></a>备注  
 如果启用，rich edit 控件将扫描以确定其是否符合标准的 URL 格式的文本。 有关这些 URL 格式的列表，请参阅[EM_AUTOURLDETECT](http://msdn.microsoft.com/library/windows/desktop/bb787991)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  未设置`SetAutoURLDetect`到**TRUE**如果编辑控件使用**CFE_LINK**文本而不是 Url 的效果。 `SetAutoURLDetect`url 中启用此效果并禁用所有其他文本。 请参阅[EN_LINK](http://msdn.microsoft.com/library/windows/desktop/bb787970)有关详细信息**CFE_LINK**效果。  
  
##  <a name="setbackgroundcolor"></a>CRichEditCtrl::SetBackgroundColor  
 此设置的背景色`CRichEditCtrl`对象。  
  
```  
COLORREF SetBackgroundColor(
    BOOL bSysColor,  
    COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `bSysColor`  
 指示是否应为系统值设置的背景色。 如果此值为**TRUE**，`cr`将被忽略。  
  
 `cr`  
 请求的背景色。 使用仅当`bSysColor`是**FALSE**。  
  
### <a name="return-value"></a>返回值  
 此以前的背景色`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 可以设置的背景色，到的系统值或指定[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。  
  
 有关详细信息，请参阅[EM_SETBKGNDCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774228)消息和[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 24](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_24.cpp)]  
  
##  <a name="setdefaultcharformat"></a>CRichEditCtrl::SetDefaultCharFormat  
 设置字符格式设置特性在此新文本`CRichEditCtrl`对象。  
  
```  
BOOL SetDefaultCharFormat(CHARFORMAT& cf);  
BOOL SetDefaultCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，它包含格式设置特性的新默认字符。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是 Rich Edit 2.0 扩展到**CHARFORMAT**结构，包含格式设置特性的默认字符。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和**CHARFORMAT**和**CHARFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 25](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_25.cpp)]  
  
##  <a name="seteventmask"></a>CRichEditCtrl::SetEventMask  
 设置此事件掩码`CRichEditCtrl`对象。  
  
```  
DWORD SetEventMask(DWORD dwEventMask);
```  
  
### <a name="parameters"></a>参数  
 *dwEventMask*  
 此新的事件掩码`CRichEditCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 以前的事件掩码。  
  
### <a name="remarks"></a>备注  
 事件掩码指定对哪些通知邮件`CRichEditCtrl`对象发送到其父窗口。  
  
 有关详细信息，请参阅[EM_SETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb774238)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 26](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_26.cpp)]  
  
##  <a name="setmodify"></a>CRichEditCtrl::SetModify  
 设置或清除编辑控件的已修改的标志。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 值为**TRUE**指出文本已修改，值为**FALSE**指示它未被修改。 默认情况下，设置已修改的标志。  
  
### <a name="remarks"></a>备注  
 修改的标志指示编辑控件中的文本已被修改。 它会自动设置的每当用户更改的文本。 可以使用检索其值[GetModify](#getmodify)成员函数。  
  
 有关详细信息，请参阅[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetModify](#getmodify)。  
  
##  <a name="setolecallback"></a>CRichEditCtrl::SetOLECallback  
 提供此`CRichEditCtrl`对象**IRichEditOleCallback**对象，用于访问 OLE 相关资源和信息。  
  
```  
BOOL SetOLECallback(IRichEditOleCallback* pCallback);
```  
  
### <a name="parameters"></a>参数  
 `pCallback`  
 指向[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)对象此`CRichEditCtrl`对象将用于获取 OLE 相关资源和信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 这`CRichEditCtrl`对象将调用[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)递增指定的 COM 对象的使用计数`pCallback`。  
  
 有关详细信息，请参阅[EM_SETOLECALLBACK](http://msdn.microsoft.com/library/windows/desktop/bb774252)消息和[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)接口中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setoptions"></a>CRichEditCtrl::SetOptions  
 设置此选项`CRichEditCtrl`对象。  
  
```  
void SetOptions(
    WORD wOp,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 *wOp*  
 指示操作的类型。 以下值之一：  
  
- `ECOOP_SET`将选项设置为所指定的`dwFlags`。  
  
- `ECOOP_OR`将当前的选项与所指定的结合起来`dwFlags`。  
  
- `ECOOP_AND`保留只有这些还由指定的当前选项`dwFlags`。  
  
- `ECOOP_XOR`保留仅将这些当前选项*不*指定的`dwFlags`。  
  
 `dwFlags`  
 格式文本编辑选项。 在备注部分中列出的标志值。  
  
### <a name="remarks"></a>备注  
 选项可将以下值的组合︰  
  
- `ECO_AUTOWORDSELECTION`自动选择字词上的双击。  
  
- `ECO_AUTOVSCROLL`自动将文本右 10 个字符滚动，当用户在行尾键入字符位置。 当用户按 ENTER 键时，则控件滚动回位置零的所有文本。  
  
- `ECO_AUTOHSCROLL`在用户的最后一行中按 ENTER 键时，自动滚动到上一页的文本。  
  
- `ECO_NOHIDESEL`对求反编辑控件的默认行为。 当控件失去输入的焦点并显示所选内容，当控件接收输入的焦点时，默认行为将隐藏所选内容。 如果指定`ECO_NOHIDESEL`，反转所选的文本，即使该控件没有焦点。  
  
- `ECO_READONLY`可以阻止用户键入或在编辑控件中编辑文本。  
  
- `ECO_WANTRETURN`指定在对话框中的多个行 rich edit 控件中输入文本时，在用户按 ENTER 键时的情况下插入一个回车。 如果未指定此样式，按 ENTER 键将命令发送到 rich edit 控件的父窗口，这将模拟单击父窗口的默认按钮 （例如，在对话框中确定按钮）。 此样式不起的单行编辑控件。  
  
- `ECO_SAVESEL`在控件失去焦点时，请保留所选内容。 默认情况下，当它重新获得焦点时选择控件的整个内容。  
  
- `ECO_VERTICAL`在垂直方向绘制文本和对象。 可用于仅亚洲语言。  
  
 有关详细信息，请参阅[EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 27](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_27.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditCtrl::SetParaFormat  
 设置的段落格式设置特性在此当前所选内容`CRichEditCtrl`对象。  
  
```  
BOOL SetParaFormat(PARAFORMAT& pf);  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>参数  
 `pf`  
 在第一个版本中，指向的指针[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)结构，它包含新的默认段落格式设置的属性。  
  
 在第二个版本中，指向的指针[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，它是 Rich Edit 2.0 扩展到**PARAFORMAT**存放格式设置特性的默认字符的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`pf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)消息和**PARAFORMAT**和**PARAFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 28](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_28.cpp)]  
  
##  <a name="setpunctuation"></a>CRichEditCtrl::SetPunctuation  
 Rich edit 控件中设置标点。  
  
```  
BOOL SetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc);
```  
  
### <a name="parameters"></a>参数  
 `fType`  
 标点标志中。 有关可能的值的列表，请参阅`fType`参数[EM_SETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774278)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 指向的指针[标点](http://msdn.microsoft.com/library/windows/desktop/bb787944)结构中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为非 0 否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是适用于仅亚洲语言版本的操作系统。  
  
##  <a name="setreadonly"></a>CRichEditCtrl::SetReadOnly  
 更改`ECO_READONLY`此选项`CRichEditCtrl`对象。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bReadOnly`  
 指示如果此`CRichEditCtrl`对象应为只读。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 此选项的简短说明，请参阅[SetOptions](#setoptions)。 你可以使用此函数来设置此的所有选项`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 29](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_29.cpp)]  
  
##  <a name="setrect"></a>CRichEditCtrl::SetRect  
 此设置的格式设置的矩形`CRichEditCtrl`对象。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指向[RECT](../../mfc/reference/rect-structure1.md) ，该值指示格式设置的矩形的新边界。  
  
### <a name="remarks"></a>备注  
 格式设置的矩形是文本的限制矩形。 限制矩形格式文本编辑控件窗口的大小无关。 当这`CRichEditCtrl`首次创建对象，格式设置的矩形是与窗口的工作区的大小相同。 使用`SetRect`大于或小于丰富的编辑窗口进行格式设置的矩形。  
  
 有关详细信息，请参阅[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 30](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_30.cpp)]  
  
##  <a name="setsel"></a>CRichEditCtrl::SetSel  
 设置在此选择`CRichEditCtrl`对象。  
  
```  
void SetSel(
    long nStartChar,  
    long nEndChar);  
  
void SetSel(CHARRANGE& cr);
```  
  
### <a name="parameters"></a>参数  
 `nStartChar`  
 所选内容的第一个字符的从零开始索引。  
  
 `nEndChar`  
 所选内容的最后一个字符的从零开始索引。  
  
 `cr`  
 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，其中包含当前所选内容的边界。  
  
### <a name="remarks"></a>备注  
 此函数的两种形式提供了备用方法设置所选内容的边界。 请按照这些窗体的简要说明操作︰  
  
- **SetSel (** `cr` **)**此窗体使用**CHARRANGE**结构，其**cpMin**和**cpMax**若要设置的成员。  
  
- **SetSel (** `nStartChar` **，** `nEndChar` **)**此窗体使用的参数`nStartChar`和`nEndChar`若要设置。  
  
 脱字号位于指示通过更高版本的启动所选内容的末尾 ( **cpMin**或`nStartChar`) 和结束 ( **cpMax**或`nEndChar`) 索引。 此函数的内容滚动`CRichEditCtrl`以便脱字号位于可见。  
  
 若要在此选择所有文本`CRichEditCtrl`对象，请调用`SetSel`开始索引为 0 和的结束索引为-1。  
  
 有关详细信息，请参阅[EM_EXSETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788007)消息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetSel](#getsel)。  
  
##  <a name="setselectioncharformat"></a>CRichEditCtrl::SetSelectionCharFormat  
 设置格式设置特性中这中的当前选定文本的字符`CRichEditCtrl`对象。  
  
```  
BOOL SetSelectionCharFormat(CHARFORMAT& cf);  
BOOL SetSelectionCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，它包含的字符格式设置属性的当前所选内容。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是 Rich Edit 2.0 扩展到**CHARFORMAT**结构，包含新的字符格式设置为当前所选内容的属性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)和**CHARFORMAT**和**CHARFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 31](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_31.cpp)]  
  
##  <a name="settargetdevice"></a>CRichEditCtrl::SetTargetDevice  
 设置用于所见即所得的目标设备和线条宽度 （所见即所得） 在此格式设置`CRichEditCtrl`对象。  
  
```  
BOOL SetTargetDevice(
    HDC hDC,  
    long lLineWidth);

 
BOOL SetTargetDevice(
    CDC& dc,  
    long lLineWidth);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 新的目标设备的设备上下文的句柄。  
  
 *lLineWidth*  
 要用于设置格式的线条宽度。  
  
 `dc`  
 [CDC](../../mfc/reference/cdc-class.md)的新的目标设备。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 如果此函数成功，rich edit 控件拥有设备上下文作为参数传递。 在这种情况下，调用的函数不应销毁设备上下文。  
  
 有关详细信息，请参阅[EM_SETTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/bb774282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 32](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_32.cpp)]  
  
##  <a name="settextmode"></a>CRichEditCtrl::SetTextMode  
 设置 rich edit 控件的文本模式或撤消和重做级别。  
  
```  
BOOL SetTextMode(UINT fMode);
```  
  
### <a name="parameters"></a>参数  
 *fMode*  
 指定控件的文本模式和撤消级别参数的新设置。 有关可能的值的列表，请参阅的模式参数[EM_SETTEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774286)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为非零的零。  
  
### <a name="remarks"></a>备注  
 文本模式的说明，请参阅**EM_SETTEXTMODE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果控件包含文本，此成员函数将失败。 若要确保控件为空，将发送[WM_SETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632644)使用空字符串的消息。  
  
##  <a name="setundolimit"></a>CRichEditCtrl::SetUndoLimit  
 设置可以存储在撤消队列中的操作的最大数量。  
  
```  
UINT SetUndoLimit(UINT nLimit);
```  
  
### <a name="parameters"></a>参数  
 *nLimit*  
 指定可以存储在撤消队列中的操作的最大数量。 设置为 0 以禁用撤消。  
  
### <a name="return-value"></a>返回值  
 新的丰富的撤消操作的最大数目的编辑控件。  
  
### <a name="remarks"></a>备注  
 默认情况下，撤消队列中的操作的最大数目为 100。 如果你提高此数字时，必须有内存不足以容纳新数。 为了提高性能，将限制设置为最小可能值。  
  
##  <a name="setwordcharformat"></a>CRichEditCtrl::SetWordCharFormat  
 设置字符格式设置属性的当前所选字`CRichEditCtrl`对象。  
  
```  
BOOL SetWordCharFormat(CHARFORMAT& cf);  
BOOL SetWordCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，它包含的字符格式设置属性的当前所选的单词。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是 Rich Edit 2.0 扩展到**CHARFORMAT**结构，包含新字符格式设置为当前所选的单词的特性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和**CHARFORMAT**和**CHARFORMAT2**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 33](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_33.cpp)]  
  
##  <a name="setwordwrapmode"></a>CRichEditCtrl::SetWordWrapMode  
 集丰富的自动换行和断字选项编辑控件。  
  
```  
UINT SetWordWrapMode(UINT uFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 `uFlags`  
 要设置为自动换行和断字的选项。 有关可能的选项的列表，请参阅[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 当前的自动换行和断字选项。  
  
### <a name="remarks"></a>备注  
 此消息是操作系统的仅在亚洲语言版本中可用。  
  
##  <a name="stopgrouptyping"></a>CRichEditCtrl::StopGroupTyping  
 停止其他当前的撤消操作中键入操作从收集控件。  
  
```  
void StopGroupTyping();
```  
  
### <a name="remarks"></a>备注  
 如果有的话，到撤消队列中的新操作，该控件将存储的下一步的键入操作。  
  
 有关详细信息，请参阅[EM_STOPGROUPTYPING](http://msdn.microsoft.com/library/windows/desktop/bb774300)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="streamin"></a>CRichEditCtrl::StreamIn  
 替换文本中这`CRichEditCtrl`对象中指定的输入流的文本。  
  
```  
long StreamIn(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>参数  
 `nFormat`  
 指定的输入的数据格式的标志。 有关详细信息，请参阅备注部分。  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构，它指定输入的流。 有关详细信息，请参阅备注部分。  
  
### <a name="return-value"></a>返回值  
 从输入流读取的字符数。  
  
### <a name="remarks"></a>备注  
 值`nFormat`必须是以下之一︰  
  
- `SF_TEXT`指示仅读取文本。  
  
- `SF_RTF`指示读取文本和格式设置。  
  
 上述任一值可以与组合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，则`StreamIn`替换当前选定内容的输入流的内容。 如果未指定，`StreamIn`的整个内容替换`CRichEditCtrl`对象。  
  
 在**EDITSTREAM**参数`es`，你指定的回调函数，用文本填充缓冲区。 直到用完输入的流时，将重复，调用此回调函数。  
  
 有关详细信息，请参阅[EM_STREAMIN](http://msdn.microsoft.com/library/windows/desktop/bb774302)消息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 34](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_34.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 35](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_35.cpp)]  
  
##  <a name="streamout"></a>CRichEditCtrl::StreamOut  
 此内容写出`CRichEditCtrl`到指定的输出流的对象。  
  
```  
long StreamOut(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>参数  
 `nFormat`  
 指定的输出数据格式的标志。 有关详细信息，请参阅备注部分。  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构，它指定输出流。 有关详细信息，请参阅备注部分。  
  
### <a name="return-value"></a>返回值  
 写入到输出流的字符数。  
  
### <a name="remarks"></a>备注  
 值`nFormat`必须是以下之一︰  
  
- `SF_TEXT`指示仅写入文本。  
  
- `SF_RTF`指示写入文本和格式设置。  
  
- `SF_RTFNOOBJS`指示写入文本和格式设置，将替换为空格的 OLE 项。  
  
- `SF_TEXTIZED`指示写入文本和格式设置，与 OLE 项的文本表示形式。  
  
 任何这些值可以与组合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，则`StreamOut`写出到输出流的当前选择。 如果未指定，`StreamOut`这整个内容写出`CRichEditCtrl`对象。  
  
 在**EDITSTREAM**参数`es`，指定一个回调函数，用文本填充缓冲区。 直到用完的输出流时，将重复，调用此回调函数。  
  
 有关详细信息，请参阅[EM_STREAMOUT](http://msdn.microsoft.com/library/windows/desktop/bb774304)消息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 36](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_36.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl # 37](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_37.cpp)]  
  
##  <a name="undo"></a>CRichEditCtrl::Undo  
 撤消 rich edit 控件中的最后一个操作。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>返回值  
 撤消操作是否成功; 如果非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 撤消操作也可以撤消。 例如，可以还原已删除的文本与首次调用**撤消**。 只要没有任何干预的编辑操作，你可以删除再次通过第二个调用的文本**撤消**。  
  
 有关详细信息，请参阅[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CanUndo](#canundo)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CRichEditView 类](../../mfc/reference/cricheditview-class.md)

