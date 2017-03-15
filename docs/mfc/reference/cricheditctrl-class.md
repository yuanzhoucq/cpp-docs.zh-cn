---
title: "CRichEditCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCtrl
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 77b8dfb6011831f4e4300096a127f70b26bcc603
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditctrl-class"></a>CRichEditCtrl 类
提供 Rich Edit 控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](#cricheditctrl)|构造 `CRichEditCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](#canpaste)|确定是否可以将剪贴板内容粘贴到此 rich edit 控件。|  
|[CRichEditCtrl::CanRedo](#canredo)|确定是否在控件的重做队列中的任何操作。|  
|[CRichEditCtrl::CanUndo](#canundo)|确定是否编辑操作可用于撤消。|  
|[CRichEditCtrl::CharFromPos](#charfrompos)|检索有关与编辑控件的工作区中的指定点最接近的字符的信息。|  
|[CRichEditCtrl::Clear](#clear)|清除当前所选内容。|  
|[CRichEditCtrl::Copy](#copy)|将当前所选内容复制到剪贴板。|  
|[CRichEditCtrl::Create](#create)|创建 Windows rich edit 控件，并将其与此相关联`CRichEditCtrl`对象。|  
|[CRichEditCtrl::CreateEx](#createex)|创建 Windows rich edit 控件指定扩展窗口样式，并将其与此相关联`CRichEditCtrl`对象。|  
|[CRichEditCtrl::Cut](#cut)|剪切到剪贴板上当前所选内容。|  
|[CRichEditCtrl::DisplayBand](#displayband)|将显示此内容的一部分`CRichEditCtrl`对象。|  
|[CRichEditCtrl::EmptyUndoBuffer](#emptyundobuffer)|重置 （清除） 的撤消标志`CRichEditCtrl`对象。|  
|[CRichEditCtrl::FindText](#findtext)|查找在此文本`CRichEditCtrl`对象。|  
|[CRichEditCtrl::FindWordBreak](#findwordbreak)|查找下一个 word 断点之前或之后的指定的字符位置，或检索有关该位置处的字符的信息。|  
|[CRichEditCtrl::FormatRange](#formatrange)|设置的目标输出设备的文本范围的格式。|  
|[CRichEditCtrl::GetCharPos](#getcharpos)|确定给定字符在此位置`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetDefaultCharFormat](#getdefaultcharformat)|检索格式设置此属性的当前默认字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetEventMask](#geteventmask)|检索此事件掩码`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetFirstVisibleLine](#getfirstvisibleline)|确定在此最顶层的可见的行`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetIRichEditOle](#getiricheditole)|检索一个指向`IRichEditOle`接口此 rich edit 控件。|  
|[CRichEditCtrl::GetLimitText](#getlimittext)|获取可供用户输入到此文本的量的限制`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetLine](#getline)|检索文本行从此`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetLineCount](#getlinecount)|检索此中的行数`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetModify](#getmodify)|确定此内容`CRichEditCtrl`对象自上次保存后已更改。|  
|[CRichEditCtrl::GetOptions](#getoptions)|检索格式文本编辑控件选项。|  
|[CRichEditCtrl::GetParaFormat](#getparaformat)|检索段落格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetPunctuation](#getpunctuation)|检索 rich edit 控件的当前标点字符。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::GetRect](#getrect)|检索此格式化矩形`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetRedoName](#getredoname)|如果任何，在该控件的重做队列中检索下一个操作的类型。|  
|[CRichEditCtrl::GetSel](#getsel)|获取的起始和结束位置在此当前所选内容`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelectionCharFormat](#getselectioncharformat)|检索格式设置当前选定内容中此属性的字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelectionType](#getselectiontype)|检索当前选定内容中此内容的类型`CRichEditCtrl`对象。|  
|[CRichEditCtrl::GetSelText](#getseltext)|在此获取当前所选内容的文本`CRichEditCtrl`对象|  
|[CRichEditCtrl::GetTextLength](#gettextlength)|检索文本，以字符为单位，在此长度`CRichEditCtrl`对象。 不包括终止 null 字符。|  
|[CRichEditCtrl::GetTextLengthEx](#gettextlengthex)|检索字符或格式文本编辑视图中的字节的数。 接受标志，用于指示确定格式文本编辑控件中文本的长度的方法的列表|  
|[CRichEditCtrl::GetTextMode](#gettextmode)|检索 rich edit 控件的当前文本模式和撤消级别。|  
|[CRichEditCtrl::GetTextRange](#gettextrange)|检索指定的范围的文本。|  
|[CRichEditCtrl::GetUndoName](#getundoname)|如果有的话，则检索下一个撤消操作的类型。|  
|[CRichEditCtrl::GetWordWrapMode](#getwordwrapmode)|检索当前的自动换行和 rich edit 控件的 word 换行选项。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::HideSelection](#hideselection)|显示或隐藏当前所选内容。|  
|[CRichEditCtrl::LimitText](#limittext)|限制用户可键入的文本量`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineFromChar](#linefromchar)|确定哪一行包含给定的字符。|  
|[CRichEditCtrl::LineIndex](#lineindex)|检索给定行中的字符索引`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineLength](#linelength)|检索给定行中的长度`CRichEditCtrl`对象。|  
|[CRichEditCtrl::LineScroll](#linescroll)|将在此文本滚动`CRichEditCtrl`对象。|  
|[CRichEditCtrl::Paste](#paste)|将剪贴板的内容插入到此 rich edit 控件。|  
|[CRichEditCtrl::PasteSpecial](#pastespecial)|将剪贴板的内容插入到此 rich edit 控件中所指定的数据格式。|  
|[CRichEditCtrl::PosFromChar](#posfromchar)|检索客户端区域坐标的编辑控件中的指定字符。|  
|[CRichEditCtrl::Redo](#redo)|重复该控件的重做队列中的下一步操作。|  
|[CRichEditCtrl::ReplaceSel](#replacesel)|将替换当前选定内容在此`CRichEditCtrl`具有指定文本的对象。|  
|[CRichEditCtrl::RequestResize](#requestresize)|这将强制`CRichEditCtrl`要发送请求的大小调整通知对象。|  
|[CRichEditCtrl::SetAutoURLDetect](#setautourldetect)|指示自动 URL 检测是否在 rich edit 控件中处于活动状态。|  
|[CRichEditCtrl::SetBackgroundColor](#setbackgroundcolor)|在此设置的背景色`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetDefaultCharFormat](#setdefaultcharformat)|设置格式在此属性的当前默认字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetEventMask](#seteventmask)|设置此事件掩码`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetModify](#setmodify)|设置或清除此修改标志`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetOLECallback](#setolecallback)|集`IRichEditOleCallback`此 rich edit 控件的 COM 对象。|  
|[CRichEditCtrl::SetOptions](#setoptions)|设置此选项`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetParaFormat](#setparaformat)|设置段落格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetPunctuation](#setpunctuation)|设置 rich edit 控件的标点字符。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::SetReadOnly](#setreadonly)|设置此只读选项`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetRect](#setrect)|此设置的格式设置矩形`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetSel](#setsel)|在此设置的选择`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetSelectionCharFormat](#setselectioncharformat)|设置字符格式设置当前选定内容中此特性`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetTargetDevice](#settargetdevice)|设置此目标输出设备`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetTextMode](#settextmode)|设置 rich edit 控件的文本模式或撤消级别。 如果控件包含文本，消息将失败。|  
|[CRichEditCtrl::SetUndoLimit](#setundolimit)|设置可以存储在撤消队列的操作的最大数目。|  
|[CRichEditCtrl::SetWordCharFormat](#setwordcharformat)|设置格式属性当前在此单词中的字符`CRichEditCtrl`对象。|  
|[CRichEditCtrl::SetWordWrapMode](#setwordwrapmode)|丰富的自动换行和断字选项集编辑控件。 此消息是操作系统的仅在亚洲语言版本中可用。|  
|[CRichEditCtrl::StopGroupTyping](#stopgrouptyping)|停止该控件从收集其他键入到当前撤消操作的操作。 如果有的话，到撤消队列中的新操作，该控件将存储的下一步的键入操作。|  
|[CRichEditCtrl::StreamIn](#streamin)|将从输入流的文本插入到此`CRichEditCtrl`对象。|  
|[CRichEditCtrl::StreamOut](#streamout)|将从该文本存储`CRichEditCtrl`对象插入的输出流。|  
|[CRichEditCtrl::Undo](#undo)|反转最后一个编辑操作。|  
  
## <a name="remarks"></a>备注  
 "格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本可以为分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 此 Windows 公共控件 (并因此`CRichEditCtrl`类) 是仅供程序在运行 Windows 95/98 和 Windows NT 版本 3.51 及更高版本。 `CRichEditCtrl`类支持的版本 2.0 和 3.0 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] rich edit 控件。  
  
> [!CAUTION]
>  如果您使用 rich edit 控件在对话框中 (无论是否您的应用程序是 SDI、 MDI 还是基于对话框的)，则必须调用[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)一旦对话框框中显示之前。 调用此函数的一个典型位置位于程序的 `InitInstance` 成员函数中。 您无需在每次显示对话框时调用它，仅第一次需要。 如果您使用 `AfxInitRichEdit`，则不必调用 `CRichEditView`。  
  
 有关详细信息使用`CRichEditCtrl`，请参阅︰  
  
- [控件](../../mfc/controls-mfc.md)  
  
- [使用 CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   知识库文章 Q259949︰ 信息︰ SetCaretPos() 是不适合用 CEdit 或 CRichEditCtrl 控件  
  
 在 MFC 应用程序中使用 rich edit 控件的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-namecanpastea--cricheditctrlcanpaste"></a><a name="canpaste"></a>CRichEditCtrl::CanPaste  
 确定格式文本编辑控件可以粘贴指定的剪贴板格式。  
  
```  
BOOL CanPaste(UINT nFormat = 0) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFormat`  
 为查询剪贴板数据格式。 此参数可以是预定义的剪贴板格式或返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)。  
  
### <a name="return-value"></a>返回值  
 非零，如果可以粘贴剪贴板格式;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`nFormat`为 0，`CanPaste`会尝试将剪贴板中当前的任何格式。  
  
 有关详细信息，请参阅[EM_CANPASTE](http://msdn.microsoft.com/library/windows/desktop/bb787993)消息和[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&1;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_1.cpp)]  
  
##  <a name="a-namecanredoa--cricheditctrlcanredo"></a><a name="canredo"></a>CRichEditCtrl::CanRedo  
 确定是否重做队列包含的任何操作。  
  
```  
BOOL CanRedo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果重做队列中包含的操作，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 若要了解重做队列中的操作的名称，调用[CRichEditCtrl::GetRedoName](#getredoname)。 若要重做最新的撤消操作，调用[重做](#redo)。  
  
 有关详细信息，请参阅[EM_CANREDO](http://msdn.microsoft.com/library/windows/desktop/bb787995)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecanundoa--cricheditctrlcanundo"></a><a name="canundo"></a>CRichEditCtrl::CanUndo  
 确定是否可撤消的上一个编辑操作。  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果上一个编辑操作可以撤消的对的调用，则为非[撤消](#undo)成员函数; 如果不能撤消，将 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&2;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_2.cpp)]  
  
##  <a name="a-namecharfromposa--cricheditctrlcharfrompos"></a><a name="charfrompos"></a>CRichEditCtrl::CharFromPos  
 检索有关由参数指定点处的字符的信息`pt`。  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含指定点的坐标。  
  
### <a name="return-value"></a>返回值  
 最接近指定的点字符的从零开始的字符索引。 如果指定的点不在控件中的最后一个字符，则返回值指示在控件中的最后一个字符。  
  
### <a name="remarks"></a>备注  
 此成员函数适用于 rich edit 控件。 若要获取编辑控件的信息，请调用[CEdit::CharFromPos](../../mfc/reference/cedit-class.md#charfrompos)。  
  
 有关详细信息，请参阅[EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecleara--cricheditctrlclear"></a><a name="clear"></a>CRichEditCtrl::Clear  
 删除 （清除） 中的当前选定内容 （如果有） 格式文本编辑控件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 删除由执行**清除**会通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容并放置到剪贴板上已删除的内容，请调用[剪切](#cut)成员函数。  
  
 有关详细信息，请参阅[WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&3;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_3.cpp)]  
  
##  <a name="a-namecopya--cricheditctrlcopy"></a><a name="copy"></a>CRichEditCtrl::Copy  
 将当前所选内容 （如果有） 在 rich edit 控件到剪贴板。  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&4;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_4.cpp)]  
  
##  <a name="a-namecreatea--cricheditctrlcreate"></a><a name="create"></a>CRichEditCtrl::Create  
 创建 Windows rich edit 控件，并将其与此相关联`CRichEditCtrl`对象。  
  
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
 如果初始化成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CRichEditCtrl`两个步骤中的对象。 首先，调用[CRichEditCtrl](#cricheditctrl)构造函数中，然后调用**创建**，它创建 Windows 编辑控件并将其附加到`CRichEditCtrl`对象。  
  
 如果使用此函数创建 rich edit 控件，首先必须加载必要的公共控件库。 若要加载库，调用全局函数[AfxInitRichEdit](application-information-and-management.md#afxinitrichedit)，这反过来初始化公共控件库。 您需要调用`AfxInitRichEdit`在过程中的仅执行一次。  
  
 当**创建**执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)的编辑控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，从派生类`CRichEditCtrl`、 将消息映射添加到新的类，并重写上面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)向一个编辑控件。  
  
- **WS_CHILD**始终。  
  
- **WS_VISIBLE**通常。  
  
- **WS_DISABLED**很少。  
  
- **WS_GROUP**控件组合。  
  
- **WS_TABSTOP**按 tab 键顺序包括编辑控件。  
  
 窗口样式的详细信息，请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&5;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_5.cpp)]  
  
##  <a name="a-namecreateexa--cricheditctrlcreateex"></a><a name="createex"></a>CRichEditCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CRichEditCtrl`对象。  
  
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
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是**创建**应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="a-namecricheditctrla--cricheditctrlcricheditctrl"></a><a name="cricheditctrl"></a>CRichEditCtrl::CRichEditCtrl  
 构造 `CRichEditCtrl` 对象。  
  
```  
CRichEditCtrl();
```  
  
### <a name="remarks"></a>备注  
 使用[创建](#create)来构建 Windows rich edit 控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&6;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_6.cpp)]  
  
##  <a name="a-namecuta--cricheditctrlcut"></a><a name="cut"></a>CRichEditCtrl::Cut  
 删除 （剪切） 中的当前选定内容 （如果有） 格式文本编辑控件和将已删除的文本复制到剪贴板。  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>备注  
 删除由执行**剪切**会通过调用撤消[撤消](#undo)成员函数。  
  
 若要删除当前所选内容，而无需将已删除的文本放入剪贴板，调用[清除](#clear)成员函数。  
  
 有关详细信息，请参阅[WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&7;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_7.cpp)]  
  
##  <a name="a-namedisplaybanda--cricheditctrldisplayband"></a><a name="displayband"></a>CRichEditCtrl::DisplayBand  
 显示与先前设置格式的 rich edit 控件 （文本和 OLE 项） 的内容的部分[FormatRange](#formatrange)。  
  
```  
BOOL DisplayBand(LPRECT pDisplayRect);
```  
  
### <a name="parameters"></a>参数  
 `pDisplayRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定要显示的文本的设备的区域。  
  
### <a name="return-value"></a>返回值  
 如果带格式的文本的显示成功，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 文本和 OLE 项剪辑到指定的指针的区域`pDisplayRect`。  
  
 有关详细信息，请参阅[EM_DISPLAYBAND](http://msdn.microsoft.com/library/windows/desktop/bb787997)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::FormatRange](#formatrange)。  
  
##  <a name="a-nameemptyundobuffera--cricheditctrlemptyundobuffer"></a><a name="emptyundobuffer"></a>CRichEditCtrl::EmptyUndoBuffer  
 重置 (clear) 此 rich edit 控件的撤消标志。  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>备注  
 现在，该控件将无法撤消上一个编辑操作。 每当 rich edit 控件中的操作可用于撤消，则设置还原标志。  
  
 每次调用，会自动清除撤消标志[CWnd](../../mfc/reference/cwnd-class.md)成员函数[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 有关详细信息，请参阅[EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&8;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_8.cpp)]  
  
##  <a name="a-namefindtexta--cricheditctrlfindtext"></a><a name="findtext"></a>CRichEditCtrl::FindText  
 查找在 rich edit 控件中的文本。  
  
```  
long FindText(
    DWORD dwFlags,  
    FINDTEXTEX* pFindText) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 有关可能的值的列表，请参阅`wParam`中[EM_FINDTEXTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788011)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *pFindText*  
 指向[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)结构，从而为参数，搜索并返回已找到匹配项的范围。  
  
### <a name="return-value"></a>返回值  
 从零开始的字符位置的下一个匹配项;– 如果有没有更多的匹配项，则为 1。  
  
### <a name="remarks"></a>备注  
 您可以搜索其中之一向上或向下的设置中的适当范围参数[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构内**FINDTEXTEX**结构。  
  
 有关详细信息，请参阅[EM_FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb788011)消息和[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&9;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_9.cpp)]  
  
##  <a name="a-namefindwordbreaka--cricheditctrlfindwordbreak"></a><a name="findwordbreak"></a>CRichEditCtrl::FindWordBreak  
 查找下一个 word 断点之前或之后指定的位置`nStart`。  
  
```  
DWORD FindWordBreak(
    UINT nCode,  
    DWORD nStart) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCode`  
 指示要执行的操作。 有关可能的值的列表，请参阅有关参数说明`code`中**EM_FINDWORDBREAK**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nStart`  
 从其开始从零开始的字符位置。  
  
### <a name="return-value"></a>返回值  
 基于参数`nCode`。 有关详细信息，请参阅[EM_FINDWORDBREAK](http://msdn.microsoft.com/library/windows/desktop/bb788018)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数可用于检索给定位置处字符的信息。  
  
##  <a name="a-nameformatrangea--cricheditctrlformatrange"></a><a name="formatrange"></a>CRichEditCtrl::FormatRange  
 设置格式特定设备的 rich edit 控件中的文本的范围。  
  
```  
long FormatRange(
    FORMATRANGE* pfr,  
    BOOL bDisplay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pfr*  
 指向[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)结构其中包含有关输出设备的信息。 **NULL**指示 rich edit 控件中的缓存的信息可以被释放。  
  
 *bDisplay*  
 指示是否应呈现的文本。 如果**FALSE**，只是测量的文本。  
  
### <a name="return-value"></a>返回值  
 适合区域加一的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 通常情况下，此调用后跟调用[DisplayBand](#displayband)。  
  
 有关详细信息，请参阅[EM_FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb788020)消息和[FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&10;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_10.cpp)]  
  
##  <a name="a-namegetcharposa--cricheditctrlgetcharpos"></a><a name="getcharpos"></a>CRichEditCtrl::GetCharPos  
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
 通过为相应的从零开始的索引值指定的字符。 如果`lChar`大于最后一个字符在此索引`CRichEditCtrl`对象，则返回值在此指定的坐标刚好超出最后一个字符的字符位置的`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdefaultcharformata--cricheditctrlgetdefaultcharformat"></a><a name="getdefaultcharformat"></a>CRichEditCtrl::GetDefaultCharFormat  
 获取格式设置此属性的默认字符`CRichEditCtrl`对象。  
  
```  
DWORD GetDefaultCharFormat(CHARFORMAT& cf) const;  DWORD GetDefaultCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a **CHARFORMAT** structure holding the default character formatting attributes.  
  
 In the second version, a pointer to a **CHARFORMAT2** structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure, holding the default character formatting attributes.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specified the default character formatting attributes.  
  
### Remarks  
 For more information, see the **EM_GETCHARFORMAT** message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetDefaultCharFormat](#setdefaultcharformat).  
  
##  <a name="geteventmask"></a>  CRichEditCtrl::GetEventMask  
 Gets the event mask for this `CRichEditCtrl` object.  
  
```  
长 GetEventMask() const;  
```  
  
### Return Value  
 The event mask for this `CRichEditCtrl` object.  
  
### Remarks  
 The event mask specifies which notification messages the `CRichEditCtrl` object sends to its parent window.  
  
 For more information, see [EM_GETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb788032) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [CRichEditCtrl::SetEventMask](#seteventmask).  
  
##  <a name="getfirstvisibleline"></a>  CRichEditCtrl::GetFirstVisibleLine  
 Determines the topmost visible line in this `CRichEditCtrl` object.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### Return Value  
 Zero-based index of the uppermost visible line in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#11](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_11.cpp)]  
  
##  <a name="getiricheditole"></a>  CRichEditCtrl::GetIRichEditOle  
 Accesses the **IRichEditOle** interface for this `CRichEditCtrl` object.  
  
```  
IRichEditOle * GetIRichEditOle() const;  
```  
  
### Return Value  
 Pointer to the [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface that can be used to access this `CRichEditCtrl` object's OLE functionality; **NULL** if the interface is not accessible.  
  
### Remarks  
 Use this interface to access this `CRichEditCtrl` object's OLE functionality.  
  
 For more information, see [EM_GETOLEINTERFACE](http://msdn.microsoft.com/library/windows/desktop/bb788041) message and [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getlimittext"></a>  CRichEditCtrl::GetLimitText  
 Gets the text limit for this `CRichEditCtrl` object.  
  
```  
长 GetLimitText() const;  
```  
  
### Return Value  
 The current text limit, in bytes, for this `CRichEditCtrl` object.  
  
### Remarks  
 The text limit is the maximum amount of text, in bytes, the rich edit control can accept.  
  
 For more information, see [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#12](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_12.cpp)]  
  
##  <a name="getline"></a>  CRichEditCtrl::GetLine  
 Retrieves a line of text from this `CRichEditCtrl` object.  
  
```  
int GetLine (int nIndex，  
    LPTSTR lpszBuffer) const;  
  
int GetLine (int nIndex，  
    LPTSTR lpszBuffer  
    int nMaxLength) const;  
```  
  
### Parameters  
 `nIndex`  
 Zero-based index of the line to retrieve.  
  
 `lpszBuffer`  
 Points to the buffer to receive the text. The first word of the buffer must specify the maximum number of bytes that can be copied into the buffer.  
  
 `nMaxLength`  
 Maximum number of characters that can be copied into `lpszBuffer`. The second form of `GetLine` places this value into the first word of the buffer specified by `lpszBuffer`.  
  
### Return Value  
 The number of characters copied into `lpszBuffer`.  
  
### Remarks  
 The copied line does not contain a terminating null character.  
  
> [!NOTE]
>  Because the first word of the buffer stores the number of characters to be copied, make sure that your buffer is at least 4 bytes long.  
  
 For more information, see [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>  CRichEditCtrl::GetLineCount  
 Retrieves the number of lines in the `CRichEditCtrl` object.  
  
```  
int GetLineCount() const;  
```  
  
### Return Value  
 The number of lines in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#13](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_13.cpp)]  
  
##  <a name="getmodify"></a>  CRichEditCtrl::GetModify  
 Determines if the contents of this `CRichEditCtrl` object have been modified.  
  
```  
BOOL GetModify() const;  
```  
  
### Return Value  
 Nonzero if the text in this `CRichEditCtrl` object has been modified; otherwise 0.  
  
### Remarks  
 Windows maintains an internal flag indicating whether the contents of the rich edit control have been changed. This flag is cleared when the edit control is first created and can also be cleared by calling the [SetModify](#setmodify) member function.  
  
 For more information, see [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#14](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_14.cpp)]  
  
##  <a name="getoptions"></a>  CRichEditCtrl::GetOptions  
 Retrieves the options currently set for the rich edit control.  
  
```  
UINT GetOptions() const;  
```  
  
### Return Value  
 A combination of the current option flag values. For a list of these values, see the *fOptions* parameter in the [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) message, as described in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getparaformat"></a>  CRichEditCtrl::GetParaFormat  
 Gets the paragraph formatting attributes of the current selection.  
  
```  
DWORD GetParaFormat(PARAFORMAT& pf) const; DWORD GetParaFormat(PARAFORMAT2& pf) const; ```  
  
### <a name="parameters"></a>参数  
 `pf`  
 在第一个版本中，指向的指针[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)结构，用于保存的段落格式设置的当前所选内容的属性。  
  
 在第二个版本中，指向的指针[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，它是一个丰富的编辑 2.0 扩展到**PARAFORMAT**存放默认字符格式设置属性的结构。  
  
### <a name="return-value"></a>返回值  
 **DwMask**数据成员的`pf`。 它将指定的段落格式设置当前所选内容中一致的特性。  
  
### <a name="remarks"></a>备注  
 如果选择多个段落，`pf`接收第一所选段落的特性。 返回的值指定选择中一致的哪些属性。  
  
 有关详细信息，请参阅[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)消息和**PARAFORMAT**和**PARAFORMAT2**中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::SetParaFormat](#setparaformat)。  
  
##  <a name="a-namegetpunctuationa--cricheditctrlgetpunctuation"></a><a name="getpunctuation"></a>CRichEditCtrl::GetPunctuation  
 在 rich edit 控件中获取当前的标点字符。  
  
```  
BOOL GetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc) const;  
```  
  
### <a name="parameters"></a>参数  
 `fType`  
 标点类型标志，如中所述`fType`参数[EM_GETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774184)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 一个指向[标点](http://msdn.microsoft.com/library/windows/desktop/bb787944)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 此成员函数是适用于操作系统的亚洲语言版本。  
  
##  <a name="a-namegetrecta--cricheditctrlgetrect"></a><a name="getrect"></a>CRichEditCtrl::GetRect  
 检索此格式化矩形`CRichEditCtrl`对象。  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指针，指向[RECT](../../mfc/reference/rect-structure1.md)要接收的格式设置的矩形`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 格式设置矩形是文本的边框。 此值的大小无关`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LimitText](#limittext)。  
  
##  <a name="a-namegetredonamea--cricheditctrlgetredoname"></a><a name="getredoname"></a>CRichEditCtrl::GetRedoName  
 如果有的话，请检索重做队列中的下一个可用操作的类型。  
  
```  
UNDONAMEID GetRedoName() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，`GetRedoName`返回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)枚举类型，该值指示控件的重做队列中的下一步操作的类型。 如果重做队列为空，或在队列中的重做操作属于未知类型， `GetRedoName` ，则返回 0。  
  
### <a name="remarks"></a>备注  
 可以撤消或重做操作的类型包括键入、 删除、 拖放、 剪切和粘贴操作。 此信息可用于撤消和重做操作，如 redoable 操作下拉列表框提供扩展的用户界面的应用程序。  
  
##  <a name="a-namegetsela--cricheditctrlgetsel"></a><a name="getsel"></a>CRichEditCtrl::GetSel  
 检索在此当前所选内容的边界`CRichEditCtrl`对象。  
  
```  
void GetSel(CHARRANGE& cr) const;  
  
void GetSel(
    long& nStartChar,  
    long& nEndChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 引用[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构用于接收当前所选内容的边界。  
  
 `nStartChar`  
 在当前所选内容中的第一个字符的从零开始索引。  
  
 `nEndChar`  
 在当前所选内容中的最后一个字符的从零开始索引。  
  
### <a name="remarks"></a>备注  
 此函数的两种形式提供备用方式以获得所选内容的边界。 请按照这些窗体的简短说明︰  
  
- **GetSel (** `cr` **)**此窗体使用**CHARRANGE**结构与其**cpMin**和**cpMax**成员返回界限。  
  
- **GetSel (** `nStartChar` **，** `nEndChar` **)**此窗体在参数中返回的界限`nStartChar`和`nEndChar`。  
  
 如果所选内容都将包括所有内容开头 ( **cpMin**或`nStartChar`) 为 0 和末尾 ( **cpMax**或`nEndChar`) 为 – 1。  
  
 有关详细信息，请参阅[EM_EXGETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788001)消息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&15;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_15.cpp)]  
  
##  <a name="a-namegetselectioncharformata--cricheditctrlgetselectioncharformat"></a><a name="getselectioncharformat"></a>CRichEditCtrl::GetSelectionCharFormat  
 获取字符格式设置的当前所选内容的属性。  
  
```  
DWORD GetSelectionCharFormat(CHARFORMAT& cf) const;  DWORD GetSelectionCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) structure to receive the character formatting attributes of the current selection.  
  
 In the second version, a pointer to a [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure to receive the character formatting attributes of the current selection.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specifies the character formatting attributes that are consistent throughout the current selection.  
  
### Remarks  
 The `cf` parameter receives the attributes of the first character in the current selection. The return value specifies which attributes are consistent throughout the selection.  
  
 For more information, see the [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetSelectionCharFormat](#setselectioncharformat).  
  
##  <a name="getselectiontype"></a>  CRichEditCtrl::GetSelectionType  
 Determines the selection type in this `CRichEditCtrl` object.  
  
```  
WORD GetSelectionType() const;  
```  
  
### Return Value  
 Flags indicating the contents of the current selection. A combination of the following flags:  
  
- `SEL_EMPTY` Indicates that there is no current selection.  
  
- `SEL_TEXT` Indicates that the current selection contains text.  
  
- `SEL_OBJECT` Indicates that the current selection contains at least one OLE item.  
  
- `SEL_MULTICHAR` Indicates that the current selection contains more than one character of text.  
  
- `SEL_MULTIOBJECT` Indicates that the current selection contains more than one OLE object.  
  
### Remarks  
 For more information, see [EM_SELECTIONTYPE](http://msdn.microsoft.com/library/windows/desktop/bb774223) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#16](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_16.cpp)]  
  
##  <a name="getseltext"></a>  CRichEditCtrl::GetSelText  
 Retrieves the text from the current selection in this `CRichEditCtrl` object.  
  
```  
长 GetSelText(LPSTR lpBuf) const; CString GetSelText() const; ```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 要在当前所选内容中接收文本的缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 取决于该窗体︰  
  
- **GetSelText (** `lpBuf` **)**到复制的字符数`lpBuf`，不包括空终止。  
  
- **GetSelText （)**包含当前所选内容的字符串。  
  
### <a name="remarks"></a>备注  
 如果使用第一个窗体， **GetSelText (** `lpBuf` **)**，您必须确保缓冲区足够大，它将接收的文本。 调用[GetSel](#getsel)来确定当前所选内容中的字符数。  
  
 有关详细信息，请参阅[EM_GETSELTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774190)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditCtrl::GetSelectionType](#getselectiontype)。  
  
##  <a name="a-namegettextlengtha--cricheditctrlgettextlength"></a><a name="gettextlength"></a>CRichEditCtrl::GetTextLength  
 检索文本，以字符为单位，在此长度`CRichEditCtrl`对象，不包括终止 null 字符。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此文本的长度`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[WM_GETTEXTLENGTH](http://msdn.microsoft.com/library/windows/desktop/ms632628)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&17;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_17.cpp)]  
  
##  <a name="a-namegettextlengthexa--cricheditctrlgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditCtrl::GetTextLengthEx  
 计算 rich edit 控件中文本的长度。  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 值，该值指定该方法用于确定文本长度。 此成员可以是一个或多个值所列出的标志成员[GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `uCodePage`  
 翻译 (CP_ACP 的 ANSI 代码页，对 Unicode 1200) 的代码页。  
  
### <a name="return-value"></a>返回值  
 字符或编辑控件中的字节数。 如果中的设置不兼容的标志`dwFlags`，此成员函数将返回`E_INVALIDARG`。  
  
### <a name="remarks"></a>备注  
 `GetTextLengthEx`提供了其他方法，来确定文本的长度。 它支持丰富的编辑 2.0 的功能。 请参阅[有关格式文本编辑控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-namegettextmodea--cricheditctrlgettextmode"></a><a name="gettextmode"></a>CRichEditCtrl::GetTextMode  
 检索 rich edit 控件的当前文本模式和撤消级别。  
  
```  
UINT GetTextMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 一组位标志从[TEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774364)枚举类型，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 这些标志指示当前文本模式和撤消的控制级别。  
  
##  <a name="a-namegettextrangea--cricheditctrlgettextrange"></a><a name="gettextrange"></a>CRichEditCtrl::GetTextRange  
 获取指定的范围的字符。  
  
```  
int GetTextRange(
    int nFirst,  
    int nLast,  
    CString& refString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFirst`  
 在范围中前面，则第一个字符的字符位置索引。  
  
 `nLast`  
 紧跟在范围内的最后一个字符的字符位置。  
  
 `refString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将接收文本的对象。  
  
### <a name="return-value"></a>返回值  
 复制的字符数，不包括终止 null 字符。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETTEXTRANGE](http://msdn.microsoft.com/library/windows/desktop/bb774199)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `GetTextRange`支持丰富的编辑 2.0 的功能。 请参阅[有关格式文本编辑控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-namegetundonamea--cricheditctrlgetundoname"></a><a name="getundoname"></a>CRichEditCtrl::GetUndoName  
 如果有的话，请检索撤消队列中的下一个可用操作的类型。  
  
```  
UNDONAMEID GetUndoName() const;  
```  
  
### <a name="return-value"></a>返回值  
 撤消操作是否在控件的撤消队列`GetUndoName`返回[UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365)枚举类型，该值指示在队列中的下一个操作的类型。 如果撤消队列为空，或在队列中的撤消操作属于未知类型， `GetUndoName` ，则返回 0。  
  
### <a name="remarks"></a>备注  
 可以撤消或重做操作的类型包括键入、 删除、 拖放、 剪切和粘贴操作。 此信息可用于撤消和重做操作，如可用于撤消的操作下拉列表框提供扩展的用户界面的应用程序。  
  
##  <a name="a-namegetwordwrapmodea--cricheditctrlgetwordwrapmode"></a><a name="getwordwrapmode"></a>CRichEditCtrl::GetWordWrapMode  
 检索当前的自动换行和 rich edit 控件的 word 换行选项。  
  
```  
UINT GetWordWrapMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的自动换行和断字选项中。 中描述了这些选项[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数是操作系统的仅适用于亚洲语言版本。  
  
##  <a name="a-namehideselectiona--cricheditctrlhideselection"></a><a name="hideselection"></a>CRichEditCtrl::HideSelection  
 更改所选内容的可见性。  
  
```  
void HideSelection(
    BOOL bHide,  
    BOOL bPerm);
```  
  
### <a name="parameters"></a>参数  
 `bHide`  
 指示应显示或隐藏的是否所选内容**TRUE**隐藏所选内容。  
  
 `bPerm`  
 指示是否应永久这一更改所选内容的可见性。  
  
### <a name="remarks"></a>备注  
 当`bPerm`是**TRUE**，它将更改`ECO_NOHIDESEL`选项为此`CRichEditCtrl`对象。 此选项的简短说明，请参阅[SetOptions](#setoptions)。 可以使用此函数可设置为此的所有选项`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_HIDESELECTION](http://msdn.microsoft.com/library/windows/desktop/bb774210)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&18;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_18.cpp)]  
  
##  <a name="a-namelimittexta--cricheditctrllimittext"></a><a name="limittext"></a>CRichEditCtrl::LimitText  
 限制用户可以输入在编辑控件的文本的长度。  
  
```  
void LimitText(long nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nChars`  
 指定的用户可以输入的文本的长度 （以字节为单位）。 如果此参数为 0 （默认值），文本长度设置为 64k 字节。  
  
### <a name="remarks"></a>备注  
 更改文本限制将限制用户可以输入文本。 它不起任何文本已在编辑控件中，也不会影响复制到的编辑控件的文本的长度[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)成员函数在`CWnd`。 如果应用程序使用`SetWindowText`函数放到不是对的调用中指定的编辑控件的更多文本`LimitText`，用户可以删除任何内编辑控件的文本。 但是，文本限制将阻止用户使用新文本替换现有文本，除非删除当前所选内容，否则将导致要低于短限制的文本。  
  
> [!NOTE]
>  对于文本限制每个 OLE 项将作为单个字符计数。  
  
 有关详细信息，请参阅[EM_EXLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788003)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&19;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_19.cpp)]  
  
##  <a name="a-namelinefromchara--cricheditctrllinefromchar"></a><a name="linefromchar"></a>CRichEditCtrl::LineFromChar  
 检索包含指定的字符索引的行的行号。  
  
```  
long LineFromChar(long nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 包含的文本编辑控件中的所需字符的从零开始的索引值或包含为-1。 如果`nIndex`为 –&1;，它指定当前行，即包含光标的行。  
  
### <a name="return-value"></a>返回值  
 包含由指定的字符索引的行的从零开始的行号`nIndex`。 如果`nIndex`为 –&1;，返回包含所选内容的第一个字符的行数。 如果没有选定，则返回当前行号。  
  
### <a name="remarks"></a>备注  
 字符索引是从 rich edit 控件的开头的字符数。 对字符进行计数，将 OLE 项都计为单个字符。  
  
 有关详细信息，请参阅[EM_EXLINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb788005)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&20;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_20.cpp)]  
  
##  <a name="a-namelineindexa--cricheditctrllineindex"></a><a name="lineindex"></a>CRichEditCtrl::LineIndex  
 检索此内的行的字符索引`CRichEditCtrl`对象。  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 包含所需的行的文本编辑控件中的索引值或包含为-1。 如果`nLine`为 –&1;，它指定当前行，即包含光标的行。  
  
### <a name="return-value"></a>返回值  
 在指定的行的字符索引`nLine`或 – 如果指定的行号大于&1;，然后编辑控件中的行数。  
  
### <a name="remarks"></a>备注  
 字符索引是从 rich edit 控件的开头到指定的行的字符数。  
  
 有关详细信息，请参阅[EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&21;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_21.cpp)]  
  
##  <a name="a-namelinelengtha--cricheditctrllinelength"></a><a name="linelength"></a>CRichEditCtrl::LineLength  
 检索 rich edit 控件中的行的长度。  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `nLine`  
 指定其长度为要检索的行中的一个字符的字符索引。 如果此参数为 –&1;，则返回当前行 （包含插入符号的行） 的长度，不包括任何的长度在所选的行内的文本。 当`LineLength`称为对于单行编辑控件，则忽略此参数。  
  
### <a name="return-value"></a>返回值  
 当`LineLength`称为对于多行编辑控件，则返回值是由指定的行的长度 （以字节为单位） `nLine`。 当`LineLength`称为对于单行编辑控件，则返回值是编辑控件中的文本的长度 （以字节为单位）。  
  
### <a name="remarks"></a>备注  
 使用[LineIndex](#lineindex)成员函数以检索给定的行号在此的字符索引`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LineIndex](#lineindex)。  
  
##  <a name="a-namelinescrolla--cricheditctrllinescroll"></a><a name="linescroll"></a>CRichEditCtrl::LineScroll  
 执行滚动操作使得多行编辑控件的文本。  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>参数  
 `nLines`  
 指定要垂直滚动行的数。  
  
 `nChars`  
 指定要水平滚动字符位置的数。 如果已经进行了 rich edit 控件，则忽略此值**ES_RIGHT**或**ES_CENTER**样式。 [编辑样式](../../mfc/reference/edit-styles.md)中指定[创建](#create)。  
  
### <a name="remarks"></a>备注  
 编辑控件不垂直滚动过的文本编辑控件中的最后一行。 如果当前行加上由指定的行数`nLines`超过编辑控件中的行的总数，以便编辑控件的最后一行滚动到编辑控件窗口的顶部，将调整值。  
  
 `LineScroll`可以用于水平滚动条越过数据的任意行的最后一个字符。  
  
 有关详细信息，请参阅[EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetFirstVisibleLine](#getfirstvisibleline)。  
  
##  <a name="a-namepastea--cricheditctrlpaste"></a><a name="paste"></a>CRichEditCtrl::Paste  
 将数据插入从剪贴板粘贴到`CRichEditCtrl`中插入点，插入符号的位置。  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>备注  
 只有当剪贴板包含识别的格式中的数据插入数据。  
  
 有关详细信息，请参阅[WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&22;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_22.cpp)]  
  
##  <a name="a-namepastespeciala--cricheditctrlpastespecial"></a><a name="pastespecial"></a>CRichEditCtrl::PasteSpecial  
 将数据粘贴到此特定剪贴板格式`CRichEditCtrl`对象。  
  
```  
void PasteSpecial(
    UINT nClipFormat,  
    DWORD dvAspect = 0,  
    HMETAFILE hMF = 0);
```  
  
### <a name="parameters"></a>参数  
 *nClipFormat*  
 剪贴板格式将粘贴到此`CRichEditCtrl`对象。  
  
 *dvAspect*  
 要从剪贴板检索的数据的设备方面。  
  
 *hMF*  
 包含要粘贴的对象的图标视图的图元文件的句柄。  
  
### <a name="remarks"></a>备注  
 在插入点，插入符号的位置插入新材料。  
  
 有关详细信息，请参阅[EM_PASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/bb774214)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl 第&23;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_23.cpp)]  
  
##  <a name="a-nameposfromchara--cricheditctrlposfromchar"></a><a name="posfromchar"></a>CRichEditCtrl::PosFromChar  
 检索客户端区域坐标的编辑控件中的指定字符。  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 字符的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 字符，（x，y） 的位置。 对于单行编辑控件，y 坐标值始终为零。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameredoa--cricheditctrlredo"></a><a name="redo"></a>CRichEditCtrl::Redo  
 重复该控件的重做队列中的下一步操作。  
  
```  
BOOL Redo();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_REDO](http://msdn.microsoft.com/library/windows/desktop/bb774218)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereplacesela--cricheditctrlreplacesel"></a><a name="replacesel"></a>CRichEditCtrl::ReplaceSel  
 将替换当前选定内容在此`CRichEditCtrl`具有指定文本的对象。  
  
```  
void ReplaceSel(
    LPCTSTR lpszNewText,  
    BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `lpszNewText`  
 指向以 null 结尾的字符串，包含替换文本指针。  
  
 `bCanUndo`  
 若要指定此函数可用于撤消，将设置为此参数的值**TRUE**。 默认值是**FALSE**。  
  
### <a name="remarks"></a>备注  
 若要替换的文本的`CRichEditCtrl`对象，请使用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
 如果没有当前没有选定内容，在插入点，即，当前插入符号位置插入替换文本。  
  
 此函数将现有字符格式的格式化插入的文本。 替换文本的整个范围时 (通过调用`SetSel`（0，则为-1） 之前，先调用`ReplaceSel`)，则会保留上一个段落格式设置，在由新插入的文本的继承的段落字符结束。  
  
 有关详细信息，请参阅[EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[LineIndex](#lineindex)。  
  
##  <a name="a-namerequestresizea--cricheditctrlrequestresize"></a><a name="requestresize"></a>CRichEditCtrl::RequestResize  
 这将强制`CRichEditCtrl`对象以便将发送**EN_REQUESTRESIZE**到其父窗口的通知消息。  
  
```  
void RequestResize();
```  
  
### <a name="remarks"></a>备注  
 此函数可在[CWnd::OnSize](../../mfc/reference/cwnd-class.md#onsize)处理无界限`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb774220)消息和**无界限的格式文本编辑控件**部分[有关格式文本编辑控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetautourldetecta--cricheditctrlsetautourldetect"></a><a name="setautourldetect"></a>CRichEditCtrl::SetAutoURLDetect  
 设置为自动检测 URL rich edit 控件。  
  
```  
BOOL SetAutoURLDetect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否将控件设置为自动检测一个 URL。 如果**TRUE**，启用它。 如果**FALSE**，它处于禁用状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为，则为非，零。 例如，消息可能会由于内存不足而失败。  
  
### <a name="remarks"></a>备注  
 如果启用，rich edit 控件将扫描以确定其是否符合标准的 URL 格式的文本。 有关这些 URL 格式的列表，请参阅[EM_AUTOURLDETECT](http://msdn.microsoft.com/library/windows/desktop/bb787991)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  未设置`SetAutoURLDetect`到**TRUE**如果编辑控件使用**CFE_LINK**文本而不是 Url 的效果。 `SetAutoURLDetect`对 Url 启用此效果，并禁用所有其他文本。 请参阅[EN_LINK](http://msdn.microsoft.com/library/windows/desktop/bb787970)有关详细信息**CFE_LINK**效果。  
  
##  <a name="a-namesetbackgroundcolora--cricheditctrlsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CRichEditCtrl::SetBackgroundColor  
 此设置的背景色`CRichEditCtrl`对象。  
  
```  
COLORREF SetBackgroundColor(
    BOOL bSysColor,  
    COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `bSysColor`  
 指示是否应该为系统的值设置的背景色。 如果此值为**TRUE**，`cr`将被忽略。  
  
 `cr`  
 请求的背景色。 使用仅当`bSysColor`是**FALSE**。  
  
### <a name="return-value"></a>返回值  
 为此以前的背景颜色`CRichEditCtrl`对象。  
  
### <a name="remarks"></a>备注  
 可以设置的背景色，为系统的值或指定[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值。  
  
 有关详细信息，请参阅[EM_SETBKGNDCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774228)消息和[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&24;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_24.cpp)]  
  
##  <a name="a-namesetdefaultcharformata--cricheditctrlsetdefaultcharformat"></a><a name="setdefaultcharformat"></a>CRichEditCtrl::SetDefaultCharFormat  
 设置格式属性在此新的文本的字符`CRichEditCtrl`对象。  
  
```  
BOOL SetDefaultCharFormat(CHARFORMAT& cf);  
BOOL SetDefaultCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，其中包含新的默认字符格式的属性。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是一个丰富的编辑 2.0 扩展到**CHARFORMAT**包含默认字符格式设置属性的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和**CHARFORMAT**和**CHARFORMAT2**中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&25;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_25.cpp)]  
  
##  <a name="a-nameseteventmaska--cricheditctrlseteventmask"></a><a name="seteventmask"></a>CRichEditCtrl::SetEventMask  
 设置此事件掩码`CRichEditCtrl`对象。  
  
```  
DWORD SetEventMask(DWORD dwEventMask);
```  
  
### <a name="parameters"></a>参数  
 *dwEventMask*  
 为此新的事件掩码`CRichEditCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 以前的事件掩码。  
  
### <a name="remarks"></a>备注  
 事件掩码指定对哪些通知邮件`CRichEditCtrl`对象将发送到其父窗口。  
  
 有关详细信息，请参阅[EM_SETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb774238)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&26;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_26.cpp)]  
  
##  <a name="a-namesetmodifya--cricheditctrlsetmodify"></a><a name="setmodify"></a>CRichEditCtrl::SetModify  
 设置或清除编辑控件的已修改的标记。  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 值为**TRUE**指出文本已修改，值为**FALSE**指示它不会进行修改。 默认情况下，设置已修改的标志。  
  
### <a name="remarks"></a>备注  
 修改后的标志指示修改了在编辑控件中的文本。 它将自动设置的每当用户更改的文本。 可以通过检索其值[GetModify](#getmodify)成员函数。  
  
 有关详细信息，请参阅[EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetModify](#getmodify)。  
  
##  <a name="a-namesetolecallbacka--cricheditctrlsetolecallback"></a><a name="setolecallback"></a>CRichEditCtrl::SetOLECallback  
 为此提供了`CRichEditCtrl`对象**IRichEditOleCallback**对象，用于访问 OLE 相关资源和信息。  
  
```  
BOOL SetOLECallback(IRichEditOleCallback* pCallback);
```  
  
### <a name="parameters"></a>参数  
 `pCallback`  
 指向[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)对象此`CRichEditCtrl`对象将用来获取 OLE 相关资源和信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 这`CRichEditCtrl`对象将调用[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)来增加由指定的 COM 对象的使用情况计数`pCallback`。  
  
 有关详细信息，请参阅[EM_SETOLECALLBACK](http://msdn.microsoft.com/library/windows/desktop/bb774252)消息和[IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308)接口中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetoptionsa--cricheditctrlsetoptions"></a><a name="setoptions"></a>CRichEditCtrl::SetOptions  
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
  
- `ECOOP_AND`保留仅那些当前的选项，还指定通过`dwFlags`。  
  
- `ECOOP_XOR`保留只是那些当前选项*不*由指定`dwFlags`。  
  
 `dwFlags`  
 格式文本编辑选项。 在备注部分中列出的标志值。  
  
### <a name="remarks"></a>备注  
 选项可以是以下值的组合︰  
  
- `ECO_AUTOWORDSELECTION`自动选择字词上的双击。  
  
- `ECO_AUTOVSCROLL`会自动滚动到右侧的文本 10 个字符时在用户键入行结尾处的字符。 当用户按 ENTER 键时，控件将返回到位置零的所有文本都滚动。  
  
- `ECO_AUTOHSCROLL`当用户按 ENTER 键上的最后一行时，会自动滚动文本上移一页。  
  
- `ECO_NOHIDESEL`求反的编辑控件的默认行为。 当控件失去输入的焦点并显示所选内容，该控件接收到输入的焦点时，默认行为会隐藏所选内容。 如果指定`ECO_NOHIDESEL`，所选的文本发生了颠倒，即使该控件没有焦点。  
  
- `ECO_READONLY`可以阻止用户键入或编辑文本编辑控件中。  
  
- `ECO_WANTRETURN`指定当用户按 ENTER 键下插入多行 rich edit 控件在对话框中输入文本时插入回车符。 如果未指定此样式中，按 ENTER 键将命令发送到 rich edit 控件的父窗口，模拟单击父窗口的默认按钮 （例如，在对话框中的确定按钮）。 此样式不起作用的单行上编辑控件。  
  
- `ECO_SAVESEL`在控件失去焦点时，会保留所选内容。 默认情况下，当它重新获得焦点时选择该控件的全部内容。  
  
- `ECO_VERTICAL`在垂直方向绘制文本和对象。 适用于仅亚洲语言。  
  
 有关详细信息，请参阅[EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&27;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_27.cpp)]  
  
##  <a name="a-namesetparaformata--cricheditctrlsetparaformat"></a><a name="setparaformat"></a>CRichEditCtrl::SetParaFormat  
 设置段落格式设置特性在此当前所选内容`CRichEditCtrl`对象。  
  
```  
BOOL SetParaFormat(PARAFORMAT& pf);  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>参数  
 `pf`  
 在第一个版本中，指向的指针[PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)结构，其中包含新的默认段落格式设置属性。  
  
 在第二个版本中，指向的指针[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，它是一个丰富的编辑 2.0 扩展到**PARAFORMAT**存放默认字符格式设置属性的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`pf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)消息和**PARAFORMAT**和**PARAFORMAT2**中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&28;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_28.cpp)]  
  
##  <a name="a-namesetpunctuationa--cricheditctrlsetpunctuation"></a><a name="setpunctuation"></a>CRichEditCtrl::SetPunctuation  
 在 rich edit 控件中设置标点。  
  
```  
BOOL SetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc);
```  
  
### <a name="parameters"></a>参数  
 `fType`  
 表示标点的标志。 有关可能的值的列表，请参阅`fType`参数[EM_SETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774278)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpPunc`  
 一个指向[标点](http://msdn.microsoft.com/library/windows/desktop/bb787944)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数仅供只有亚洲语言版本的操作系统。  
  
##  <a name="a-namesetreadonlya--cricheditctrlsetreadonly"></a><a name="setreadonly"></a>CRichEditCtrl::SetReadOnly  
 更改`ECO_READONLY`选项为此`CRichEditCtrl`对象。  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bReadOnly`  
 指示如果此`CRichEditCtrl`对象应为只读。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此选项的简短说明，请参阅[SetOptions](#setoptions)。 可以使用此函数可设置为此的所有选项`CRichEditCtrl`对象。  
  
 有关详细信息，请参阅[EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&29;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_29.cpp)]  
  
##  <a name="a-namesetrecta--cricheditctrlsetrect"></a><a name="setrect"></a>CRichEditCtrl::SetRect  
 此设置的格式设置矩形`CRichEditCtrl`对象。  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md)或指针，指向[RECT](../../mfc/reference/rect-structure1.md) ，该值指示的格式设置的矩形的新边界。  
  
### <a name="remarks"></a>备注  
 格式设置矩形是文本的限制矩形。 限制矩形是大小的独立于格式文本编辑控件窗口。 当这`CRichEditCtrl`首次创建对象、 格式设置矩形是窗口中的工作区的大小相同。 使用`SetRect`大于或小于格式文本编辑窗口进行格式化的矩形。  
  
 有关详细信息，请参阅[EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&30;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_30.cpp)]  
  
##  <a name="a-namesetsela--cricheditctrlsetsel"></a><a name="setsel"></a>CRichEditCtrl::SetSel  
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
 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，它包含当前所选内容的边界。  
  
### <a name="remarks"></a>备注  
 此函数的两种形式提供备用方法来设置所选内容的边界。 请按照这些窗体的简短说明︰  
  
- **SetSel (** `cr` **)**此窗体使用**CHARRANGE**结构与其**cpMin**和**cpMax**成员来设置边界。  
  
- **SetSel (** `nStartChar` **，** `nEndChar` **)**此窗体使用的参数`nStartChar`和`nEndChar`来设置边界。  
  
 插入符号放置在由更高版本的启动所选内容的结尾 ( **cpMin**或`nStartChar`) 和结束 ( **cpMax**或`nEndChar`) 的索引。 此函数将的内容滚动`CRichEditCtrl`以使插入符号可见。  
  
 若要在此选择所有文本`CRichEditCtrl`对象，请调用`SetSel`起始索引为 0 和结束索引为 – 1。  
  
 有关详细信息，请参阅[EM_EXSETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788007)消息和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[GetSel](#getsel)。  
  
##  <a name="a-namesetselectioncharformata--cricheditctrlsetselectioncharformat"></a><a name="setselectioncharformat"></a>CRichEditCtrl::SetSelectionCharFormat  
 设置格式属性在此当前所选内容中的文本的字符`CRichEditCtrl`对象。  
  
```  
BOOL SetSelectionCharFormat(CHARFORMAT& cf);  
BOOL SetSelectionCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，它包含的字符格式设置属性的当前所选内容。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是一个丰富的编辑 2.0 扩展到**CHARFORMAT**包含新字符格式设置为当前所选内容的属性的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)和**CHARFORMAT**和**CHARFORMAT2**中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&31;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_31.cpp)]  
  
##  <a name="a-namesettargetdevicea--cricheditctrlsettargetdevice"></a><a name="settargetdevice"></a>CRichEditCtrl::SetTargetDevice  
 设置用于所见即所得的目标设备和线条宽度 （所见即所得） 在此格式`CRichEditCtrl`对象。  
  
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
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此函数成功，rich edit 控件拥有设备上下文作为参数传递。 在这种情况下，调用的函数不应销毁的设备上下文。  
  
 有关详细信息，请参阅[EM_SETTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/bb774282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&32;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_32.cpp)]  
  
##  <a name="a-namesettextmodea--cricheditctrlsettextmode"></a><a name="settextmode"></a>CRichEditCtrl::SetTextMode  
 设置 rich edit 控件的文本模式或撤消和重做级别。  
  
```  
BOOL SetTextMode(UINT fMode);
```  
  
### <a name="parameters"></a>参数  
 *fMode*  
 指定控件的文本模式和撤消级别的参数的新设置。 有关可能的值的列表，请参阅的模式参数[EM_SETTEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774286)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，否则为，则为非，零。  
  
### <a name="remarks"></a>备注  
 在文本模式的说明，请参阅**EM_SETTEXTMODE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果控件包含文本，该成员函数将失败。 若要确保控件为空，将发送[WM_SETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632644)消息为空字符串。  
  
##  <a name="a-namesetundolimita--cricheditctrlsetundolimit"></a><a name="setundolimit"></a>CRichEditCtrl::SetUndoLimit  
 设置可以存储在撤消队列的操作的最大数目。  
  
```  
UINT SetUndoLimit(UINT nLimit);
```  
  
### <a name="parameters"></a>参数  
 *nLimit*  
 指定可以撤消队列中存储的操作的最大数目。 设置为&0; 可以禁用撤消。  
  
### <a name="return-value"></a>返回值  
 新的丰富的撤消操作的最大数目的编辑控件。  
  
### <a name="remarks"></a>备注  
 默认情况下，撤消队列中的操作的最大数目为 100。 如果增大此数字时，必须有足够的可用内存来容纳新的数字。 为了提高性能，将限制设置最小可能值。  
  
##  <a name="a-namesetwordcharformata--cricheditctrlsetwordcharformat"></a><a name="setwordcharformat"></a>CRichEditCtrl::SetWordCharFormat  
 设置字符格式设置属性的当前所选字`CRichEditCtrl`对象。  
  
```  
BOOL SetWordCharFormat(CHARFORMAT& cf);  
BOOL SetWordCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 在第一个版本中，指向的指针[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)结构，它包含的字符格式设置属性的当前所选的单词。  
  
 在第二个版本中，指向的指针[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它是一个丰富的编辑 2.0 扩展到**CHARFORMAT**包含新的字符格式的当前所选的单词的属性的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和**CHARFORMAT**和**CHARFORMAT2**中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl 第&33;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_33.cpp)]  
  
##  <a name="a-namesetwordwrapmodea--cricheditctrlsetwordwrapmode"></a><a name="setwordwrapmode"></a>CRichEditCtrl::SetWordWrapMode  
 丰富的自动换行和断字选项集编辑控件。  
  
```  
UINT SetWordWrapMode(UINT uFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 `uFlags`  
 要设置自动换行和断字的选项。 有关可能的选项的列表，请参阅[EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 当前的自动换行和断字选项。  
  
### <a name="remarks"></a>备注  
 此消息是操作系统的仅在亚洲语言版本中可用。  
  
##  <a name="a-namestopgrouptypinga--cricheditctrlstopgrouptyping"></a><a name="stopgrouptyping"></a>CRichEditCtrl::StopGroupTyping  
 停止该控件从收集其他键入到当前撤消操作的操作。  
  
```  
void StopGroupTyping();
```  
  
### <a name="remarks"></a>备注  
 如果有的话，到撤消队列中的新操作，该控件将存储的下一步的键入操作。  
  
 有关详细信息，请参阅[EM_STOPGROUPTYPING](http://msdn.microsoft.com/library/windows/desktop/bb774300)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namestreamina--cricheditctrlstreamin"></a><a name="streamin"></a>CRichEditCtrl::StreamIn  
 替换此文本`CRichEditCtrl`对象与指定的输入流中的文本。  
  
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
 值`nFormat`必须是以下项之一︰  
  
- `SF_TEXT`指示仅读取文本。  
  
- `SF_RTF`指示读取文本和格式设置。  
  
 这些值可以与组合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，则`StreamIn`用了输入流的内容替换当前所选内容。 如果未指定，`StreamIn`替换的整个内容`CRichEditCtrl`对象。  
  
 在**EDITSTREAM**参数`es`，指定填充文本的缓冲区的回调函数。 直到用尽了输入的流，将重复，调用此回调函数。  
  
 有关详细信息，请参阅[EM_STREAMIN](http://msdn.microsoft.com/library/windows/desktop/bb774302)消息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&34;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_34.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&35;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_35.cpp)]  
  
##  <a name="a-namestreamouta--cricheditctrlstreamout"></a><a name="streamout"></a>CRichEditCtrl::StreamOut  
 此内容写出`CRichEditCtrl`对象传递给指定的输出流。  
  
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
 向输出流写入的字符数。  
  
### <a name="remarks"></a>备注  
 值`nFormat`必须是以下项之一︰  
  
- `SF_TEXT`指示仅编写文本。  
  
- `SF_RTF`指示写入文本和格式设置。  
  
- `SF_RTFNOOBJS`指示写入文本和格式设置，用空格替换 OLE 项。  
  
- `SF_TEXTIZED`指示写入文本和格式设置，以文本形式表示的 OLE 项。  
  
 任何这些值可以与组合`SFF_SELECTION`。 如果`SFF_SELECTION`指定，则`StreamOut`写出到输出流的当前选定内容。 如果未指定，`StreamOut`写出的全部内容`CRichEditCtrl`对象。  
  
 在**EDITSTREAM**参数`es`，指定在其中填入文本缓冲区的回调函数。 此回调函数调用重复，直到用完的输出流。  
  
 有关详细信息，请参阅[EM_STREAMOUT](http://msdn.microsoft.com/library/windows/desktop/bb774304)消息和[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&36;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_36.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl #&37;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_37.cpp)]  
  
##  <a name="a-nameundoa--cricheditctrlundo"></a><a name="undo"></a>CRichEditCtrl::Undo  
 撤消 rich edit 控件中的最后一个操作。  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>返回值  
 如果撤消操作成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 撤消操作还可用于撤消。 例如，将还原已删除的文本与首次调用**撤消**。 只要没有任何干预的编辑操作，您可以删除再次用到第二次调用的文本**撤消**。  
  
 有关详细信息，请参阅[EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CanUndo](#canundo)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CRichEditView 类](../../mfc/reference/cricheditview-class.md)

