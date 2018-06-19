---
title: CRichEditView 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
dev_langs:
- C++
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 353a45cad513e9c862b6ae6c15ab5383d3d65d48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378951"
---
# <a name="cricheditview-class"></a>CRichEditView 类
与[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构上下文中 rich edit 控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CRichEditView : public CCtrlView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditView::CRichEditView](#cricheditview)|构造 `CRichEditView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移动一个对话框，以便它不会掩盖当前所选内容。|  
|[CRichEditView::CanPaste](#canpaste)|通知剪贴板是否包含可以粘贴到丰富的编辑视图中的数据。|  
|[CRichEditView::DoPaste](#dopaste)|将一个 OLE 项粘贴到此丰富的编辑视图。|  
|[CRichEditView::FindText](#findtext)|查找指定的文本，调用将等待光标。|  
|[CRichEditView::FindTextSimple](#findtextsimple)|查找指定的文本。|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|检索的字符格式设置为当前所选内容的属性。|  
|[CRichEditView::GetDocument](#getdocument)|检索指向相关[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|检索当前处于就地活动状态的丰富的编辑视图中的 OLE 项。|  
|[CRichEditView::GetMargins](#getmargins)|检索此丰富的编辑视图的边距。|  
|[CRichEditView::GetPageRect](#getpagerect)|检索此丰富的编辑视图的页矩形。|  
|[CRichEditView::GetPaperSize](#getpapersize)|检索此丰富的编辑视图的纸张大小。|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|检索段落格式设置为当前所选内容的属性。|  
|[CRichEditView::GetPrintRect](#getprintrect)|检索此丰富的编辑视图的打印矩形。|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|检索此丰富的编辑视图的打印宽度。|  
|[Cricheditview:: Getricheditctrl](#getricheditctrl)|检索 rich edit 控件。|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|从丰富的编辑视图中检索所选的项。|  
|[CRichEditView::GetTextLength](#gettextlength)|检索丰富的编辑视图中的文本的长度。|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|检索字符或丰富的编辑视图中的字节的数。 用于确定长度方法扩展的标志列表。|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|将文件作为一个 OLE 项。|  
|[CRichEditView::InsertItem](#insertitem)|作为 OLE 项插入一个新项。|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|通知剪贴板是否包含带格式文本或文本格式中的数据。|  
|[CRichEditView::OnCharEffect](#onchareffect)|切换当前选择格式的字符。|  
|[CRichEditView::OnParaAlign](#onparaalign)|更改段落的对齐方式。|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新命令 UI 字符公共成员函数。|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新命令 UI 段落公共成员函数。|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|设置给定矩形中的指定的文本的格式。|  
|[CRichEditView::PrintPage](#printpage)|设置给定页中的指定的文本的格式。|  
|[CRichEditView::SetCharFormat](#setcharformat)|设置字符格式设置为当前所选内容的属性。|  
|[CRichEditView::SetMargins](#setmargins)|设置此丰富的边距编辑视图。|  
|[CRichEditView::SetPaperSize](#setpapersize)|设置此丰富的编辑视图的纸张大小。|  
|[CRichEditView::SetParaFormat](#setparaformat)|设置的段落格式设置为当前所选内容的属性。|  
|[CRichEditView::TextNotFound](#textnotfound)|重置控件的内部搜索状态。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|检索此丰富的编辑视图中的范围的剪贴板对象。|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|检索要使用右鼠标按钮按下的上下文菜单。|  
|[CRichEditView::IsSelected](#isselected)|指示是否是否选定了给定的 OLE 项。|  
|[CRichEditView::OnFindNext](#onfindnext)|查找子字符串的下一个匹配项。|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|刷新视图时第一个附加到文档。|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|从 OLE 项检索本机数据。|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|将打印特性设置为给定的设备。|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|使用新的字符串来替换给定字符串的所有匹配项。|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|找不到请求的文本的句柄用户通知。|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|若要查看有关数据上的查询`IDataObject`。|  
|[CRichEditView::WrapChanged](#wrapchanged)|为此格式文本编辑视图中，基于值调整目标输出设备`m_nWordWrap`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|指示项目符号列表的缩进量。|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|指示 word 换行约束。|  
  
## <a name="remarks"></a>备注  
 "Rich edit 控件"是一个窗口，用户可以输入和编辑文本。 文本可以分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件用于设置文本格式提供一个编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 维护视图中的 OLE 客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。  
  
 此 Windows 公共控件 (因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 MFC 应用程序中使用的丰富的编辑视图的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrich.h  
  
##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition  
 调用此函数可将给定的对话框中移动，以便它不会遮盖当前所选内容。  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>参数  
 *pDlg*  
 指向 `CDialog` 对象的指针。  
  
##  <a name="canpaste"></a>  CRichEditView::CanPaste  
 调用此函数可确定剪贴板是否包含可以粘贴到此丰富的编辑视图的信息。  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果剪贴板包含可以接受此丰富的编辑视图; 的格式的数据否则为为 0。  
  
##  <a name="cricheditview"></a>  CRichEditView::CRichEditView  
 调用此函数可创建`CRichEditView`对象。  
  
```  
CRichEditView();
```  
  
##  <a name="dopaste"></a>  CRichEditView::DoPaste  
 调用此函数可将中的 OLE 项粘贴`dataobj`到此丰富编辑文档/视图。  
  
```  
void DoPaste(
    COleDataObject& dataobj,  
    CLIPFORMAT cf,  
    HMETAFILEPICT hMetaPict);
```  
  
### <a name="parameters"></a>参数  
 `dataobj`  
 [COleDataObject](../../mfc/reference/coledataobject-class.md)包含要粘贴的数据。  
  
 `cf`  
 所需的剪贴板格式。  
  
 `hMetaPict`  
 表示要粘贴的项图元文件。  
  
### <a name="remarks"></a>备注  
 框架调用此函数的默认实现的一部分[QueryAcceptData](#queryacceptdata)。  
  
 此函数将确定粘贴基于适用于选择性粘贴该处理程序的结果的类型。 如果`cf`为 0，则新的项使用的当前的图标表示。 如果`cf`为非零值和`hMetaPict`不**NULL**，新项使用`hMetaPict`其表示形式。  
  
##  <a name="findtext"></a>  CRichEditView::FindText  
 调用此函数可查找指定的文本并将其设置为当前所选内容。  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 包含要搜索的字符串。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示如果搜索应全字匹配，非单词的一部分。  
  
 `bNext`  
 指示搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区末尾。 如果**FALSE**，搜索方向将是朝向缓冲区开头。  
  
### <a name="return-value"></a>返回值  
 非零如果`lpszFind`找到文本; 否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数在查找操作过程中显示等待光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple  
 调用此函数可查找指定的文本并将其设置为当前所选内容。  
  
```  
BOOL FindTextSimple(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 包含要搜索的字符串。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示如果搜索应全字匹配，非单词的一部分。  
  
 `bNext`  
 指示搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区末尾。 如果**FALSE**，搜索方向将是朝向缓冲区开头。  
  
### <a name="return-value"></a>返回值  
 非零如果`lpszFind`找到文本; 否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection  
 调用此函数可获取的字符格式设置的当前所选内容的属性。  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>返回值  
 A [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，其中包含的字符格式设置的当前所选内容的属性。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026)消息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) Windows SDK 中的结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData  
 框架调用此函数的处理过程中[IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)。  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>参数  
 `lpchrg`  
 指向[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，它指定字符 （和 OLE 项） 将复制到指定的数据对象的范围内`lplpdataobj`。  
  
 `dwReco`  
 剪贴板操作标志。 可以是下列值之一。  
  
- **RECO_COPY**复制到剪贴板。  
  
- **RECO_CUT**剪切到剪贴板。  
  
- **RECO_DRAG**拖动操作 （拖放）。  
  
- **RECO_DROP**删除操作 （拖放）。  
  
- **RECO_PASTE**从剪贴板粘贴时。  
  
 `lpRichDataObj`  
 指向[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)包含丰富从剪贴板数据对象编辑控件 ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341))。  
  
 `lplpdataobj`  
 指向接收的地址的指针变量`IDataObject`表示中指定的范围对象`lpchrg`参数。 值`lplpdataobj`如果返回错误，则忽略。  
  
### <a name="return-value"></a>返回值  
 `HRESULT` Reporting 操作的成功与否的值。 有关详细信息`HRESULT`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 如果返回值指示成功， **IRichEditOleCallback::GetClipboardData**返回`IDataObject`访问`lplpdataobj`; 否则为它将返回一个访问`lpRichDataObj`。 重写此函数可提供你自己的剪贴板数据。 此函数的默认实现返回**E_NOTIMPL**。  
  
 这是一个高级可重写。  
  
 有关详细信息，请参阅[IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)， [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)，和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)在 Windows SDK 并查看[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) Windows SDK 中。  
  
##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu  
 框架调用此函数的处理过程中[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)。  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>参数  
 *seltyp*  
 选择类型。 备注部分所述的所选内容类型值。  
  
 `lpoleobj`  
 指向**OLEOBJECT**结构，它指定所选的第一个 OLE 对象，如果所选内容包含一个或多个 OLE 项。 如果所选内容不包含任何项，`lpoleobj`是**NULL**。 **OLEOBJECT**结构保存到 OLE 对象 v-表指针。  
  
 `lpchrg`  
 指向[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，它包含当前所选内容。  
  
### <a name="return-value"></a>返回值  
 上下文菜单的句柄。  
  
### <a name="remarks"></a>备注  
 此函数是典型处理下的右鼠标按钮的一部分。  
  
 所选内容类型可以是以下标志的任意组合：  
  
- `SEL_EMPTY` 指示当前没有选定内容。  
  
- `SEL_TEXT` 指示当前所选内容包含文本。  
  
- `SEL_OBJECT` 指示当前所选内容包含至少一个 OLE 项。  
  
- `SEL_MULTICHAR` 指示当前所选内容包含多个字符的文本。  
  
- `SEL_MULTIOBJECT` 指示当前所选内容包含多个 OLE 对象。  
  
 默认实现返回**NULL**。 这是一个高级可重写。  
  
 有关详细信息，请参阅[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) Windows SDK 中。  
  
 有关详细信息**OLEOBJECT**类型，请参阅中的 OLE 数据结构和结构分配文章*OLE 知识文库*。  
  
##  <a name="getdocument"></a>  CRichEditView::GetDocument  
 调用此函数可获取指向的指针`CRichEditDoc`与此视图关联。  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)与关联的对象你`CRichEditView`对象。  
  
##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem  
 调用此函数可获取 OLE 项当前激活此就地`CRichEditView`对象。  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 为单个、 处于就地活动状态的指针[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)此丰富的编辑视图; 中的对象**NULL**如果目前没有 OLE 项处于就地活动状态。  
  
##  <a name="getmargins"></a>  CRichEditView::GetMargins  
 调用此函数可检索在打印中使用的当前边距。  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用在打印中的边距以`MM_TWIPS`。  
  
##  <a name="getpagerect"></a>  CRichEditView::GetPageRect  
 调用此函数可获取在打印中使用的页的尺寸。  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 在打印中, 使用的页的边界以`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 此值基于纸张大小。  
  
##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize  
 调用此函数可检索当前的纸张大小。  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 用于打印，纸张的大小以`MM_TWIPS`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection  
 调用此函数可获取的段落格式设置的当前所选内容的属性。  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>返回值  
 A [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，其中包含的段落格式设置的当前所选内容的属性。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)消息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) Windows SDK 中的结构。  
  
##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect  
 调用此函数可检索页矩形中的打印区域的边界。  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 在打印中使用的图像区域的边界以`MM_TWIPS`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth  
 调用此函数可确定的打印区域的宽度。  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 打印区域的宽度以`MM_TWIPS`。  
  
##  <a name="getricheditctrl"></a>  Cricheditview:: Getricheditctrl  
 调用此函数可检索[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)与关联的对象`CRichEditView`对象。  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `CRichEditCtrl`此视图的对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem  
 调用此函数可检索 OLE 项 (`CRichEditCntrItem`对象) 中这当前选定`CRichEditView`对象。  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)中所选对象`CRichEditView`对象;**NULL**如果在此视图中不选定任何项。  
  
##  <a name="gettextlength"></a>  CRichEditView::GetTextLength  
 调用此函数可检索此中文本的长度`CRichEditView`对象。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此文本的长度`CRichEditView`对象。  
  
##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx  
 调用此成员函数来计算此中文本的长度`CRichEditView`对象。  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 指定该方法用于确定文本长度的值。 此成员可以是一个或多个值中的标志成员列出[GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915) Windows SDK 中所述。  
  
 `uCodePage`  
 翻译 (CP_ACP ANSI 代码页，适用于 Unicode 的 1200年) 的代码页。  
  
### <a name="return-value"></a>返回值  
 字符或编辑控件中的字节数。 如果中的设置不兼容的标志`dwFlags`，此成员函数将返回`E_INVALIDARG`。  
  
### <a name="remarks"></a>备注  
 `GetTextLengthEx` 提供了确定文本的长度的其他方式。 它支持 Rich Edit 2.0 功能。 有关详细信息，请参阅[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)Windows SDK 中。  
  
##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject  
 调用此函数可插入指定的文件 (作为[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象) 读入格式文本编辑视图。  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 包含要插入的文件的名称的字符串。  
  
##  <a name="insertitem"></a>  CRichEditView::InsertItem  
 调用此函数可插入[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)到丰富的编辑视图的对象。  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要插入的项的指针。  
  
### <a name="return-value"></a>返回值  
 `HRESULT`值，该值指示成功的插入。  
  
### <a name="remarks"></a>备注  
 有关详细信息`HRESULT`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat  
 调用此函数可确定如果`cf`是一种剪贴板格式，这是文本、 多格式文本或与 OLE 项的多格式文本。  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 感兴趣的剪贴板格式。  
  
### <a name="return-value"></a>返回值  
 非零如果`cf`是丰富的编辑或文本剪贴板格式。  
  
##  <a name="isselected"></a>  CRichEditView::IsSelected  
 调用此函数可确定是否此视图中当前选定的指定的 OLE 项。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pDocItem`  
 指针指向在视图中的对象。  
  
### <a name="return-value"></a>返回值  
 如果该对象已选中; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果派生的视图类具有处理选定的 OLE 项的不同方法，重写此函数。  
  
##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent  
 项目符号列表中的项; 缩进默认情况下，720 单位，即 1/2 英寸。  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap  
 指示此丰富的编辑视图的自动换行的类型。  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>备注  
 以下值之一：  
  
- `WrapNone` 指示没有自动自动换行。  
  
- `WrapToWindow` 指示基于窗口的宽度的自动换行。  
  
- `WrapToTargetDevice` 指示根据目标设备的特征的自动换行。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::WrapChanged](#wrapchanged)。  
  
##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect  
 调用此函数可切换的字符格式设置当前所选内容的效果。  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>参数  
 `dwMask`  
 格式效果来修改当前所选内容中的字符。  
  
 `dwEffect`  
 字符格式设置效果切换所需的列表。  
  
### <a name="remarks"></a>备注  
 每次调用此函数切换当前所选内容的指定格式设置影响。  
  
 有关详细信息`dwMask`和`dwEffect`参数及其可能值，请参阅的对应数据成员[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="onfindnext"></a>  CRichEditView::OnFindNext  
 处理从查找/替换对话框中的命令时，由框架调用。  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要查找的字符串。  
  
 `bNext`  
 要搜索的方向： **TRUE**指示关闭;**FALSE**，最多。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示搜索是否仅或不全字匹配。  
  
### <a name="remarks"></a>备注  
 调用此函数可查找中的文本`CRichEditView`。 重写此函数可更改搜索派生的视图类的特征。  
  
##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate  
 视图首先附加到文档中之后, 但在最初显示的视图之前，由框架调用。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示`lHint`参数和**NULL**为`pHint`参数)。 重写此函数以执行任何需要有关文档的信息的一次性初始化。 例如，如果你的应用程序具有固定大小的文档，你可以使用此函数来初始化视图的滚动限制基于的文档大小。 如果你的应用程序支持大小可变的文档，使用`OnUpdate`更新滚动限制每次文档发生更改。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::m_nWordWrap](#m_nwordwrap)。  
  
##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject  
 使用此函数从嵌入项加载本机数据。  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>参数  
 *lpStg*  
 指向[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为 0;  
  
### <a name="remarks"></a>备注  
 通常情况下，你可以执行此操作通过创建[COleStreamFile](../../mfc/reference/colestreamfile-class.md)围绕`IStorage`。 `COleStreamFile`可以附加到存档和[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)调用可加载数据。  
  
 这是一个高级可重写。  
  
 有关详细信息，请参阅[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) Windows SDK 中。  
  
##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign  
 调用此函数可更改为所选的段落的段落对齐方式。  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>参数  
 `wAlign`  
 所需的段落对齐方式。 以下值之一：  
  
- `PFA_LEFT` 对齐带有左边距段落。  
  
- `PFA_RIGHT` 对齐带有右边距段落。  
  
- `PFA_CENTER` 中心之间的边距的段落。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged  
 重写此函数可打印机发生更改时更改此丰富的编辑视图的特征。  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>参数  
 `dcPrinter`  
 A [CDC](../../mfc/reference/cdc-class.md)新打印机的对象。  
  
### <a name="remarks"></a>备注  
 默认实现将纸张大小设置为的物理高度和宽度输出设备 （打印机）。 如果没有任何设备上下文与`dcPrinter`，默认实现将纸张大小设置为 8.5 × 11 英寸。  
  
##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll  
 处理从替换对话框中的全部替换命令时，由框架调用。  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要替换的文本。  
  
 `lpszReplace`  
 替换文本。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示是否搜索必须选择全字或不。  
  
### <a name="remarks"></a>备注  
 调用此函数可将某些给定文本的所有实例替换为另一个字符串。 重写此函数可更改此视图的搜索特征。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel  
 处理从替换对话框中的替换命令时，由框架调用。  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要替换的文本。  
  
 `bNext`  
 指示搜索方向： **TRUE**已关闭;**FALSE**，最多。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示是否搜索必须选择全字或不。  
  
 `lpszReplace`  
 替换文本。  
  
### <a name="remarks"></a>备注  
 调用此函数可将一个匹配项的某些给定的文本替换为另一个字符串。 重写此函数可更改此视图的搜索特征。  
  
##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound  
 搜索未通过时，由框架调用。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 找不到该文本。  
  
### <a name="remarks"></a>备注  
 重写此函数可更改从输出通知[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356)。  
  
 有关详细信息，请参阅[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect  
 框架调用此函数可更新命令 UI 字符效果命令。  
  
```  
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,  
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象。  
  
 `dwMask`  
 指示的字符格式设置掩码。  
  
 `dwEffect`  
 指示的字符格式设置生效。  
  
### <a name="remarks"></a>备注  
 掩码`dwMask`指定的字符要检查的格式设置属性。 标志`dwEffect`列表的字符格式设置属性集/清除。  
  
 有关详细信息`dwMask`和`dwEffect`参数及其可能值，请参阅的对应数据成员[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign  
 框架调用此函数可更新命令 UI 段落效果命令。  
  
```  
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,  
    WORD wAlign);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象。  
  
 `wAlign`  
 要检查的段落对齐方式。 以下值之一：  
  
- `PFA_LEFT` 对齐带有左边距段落。  
  
- `PFA_RIGHT` 对齐带有右边距段落。  
  
- `PFA_CENTER` 中心之间的边距的段落。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect  
 调用此函数可设置以适合 rich edit 控件中的文本范围的格式*rectLayout*由指定的设备`pDC`。  
  
```  
long PrintInsideRect(
    CDC* pDC,  
    RECT& rectLayout,  
    long nIndexStart,  
    long nIndexStop,  
    BOOL bOutput);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向输出区的设备上下文的指针。  
  
 *rectLayout*  
 [RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)定义输出区域。  
  
 `nIndexStart`  
 要设置格式的第一个字符的从零开始索引。  
  
 `nIndexStop`  
 要设置格式的最后一个字符的从零开始索引。  
  
 *bOutput*  
 指示是否应呈现的文本。 如果**FALSE**，只需测量的文本。  
  
### <a name="return-value"></a>返回值  
 适合在输出区域加 1 中的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 通常情况下，此调用后跟调用[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成的输出。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="printpage"></a>  CRichEditView::PrintPage  
 调用此函数可设置由指定的输出设备 rich edit 控件中的文本范围的格式`pDC`。  
  
```  
long PrintPage(
    CDC* pDC,  
    long nIndexStart,  
    long nIndexStop);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 页面输出的设备上下文的指针。  
  
 `nIndexStart`  
 要设置格式的第一个字符的从零开始索引。  
  
 `nIndexStop`  
 要设置格式的最后一个字符的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 可以容纳在页加一的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 由控制每个页的布局[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)。 通常情况下，此调用后跟调用[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成的输出。  
  
 请注意，边距相对于物理页上，而不是在逻辑页面。 因此，为零的边距通常将剪切的文本，由于许多打印机具有页上无法打印区域中。 若要避免剪辑你的文本，应调用[SetMargins](#setmargins)并设置合理边距再进行打印。  
  
##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData  
 由框架调用以将对象粘贴到格式文本编辑。  
  
```  
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,  
    CLIPFORMAT* lpcfFormat,  
    DWORD dwReco,  
    BOOL bReally,  
    HGLOBAL hMetaFile);
```  
  
### <a name="parameters"></a>参数  
 *lpdataobj*  
 指向[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)查询。  
  
 *lpcfFormat*  
 为可接受的数据格式的指针。  
  
 `dwReco`  
 未使用。  
  
 *bReally*  
 指示是否应继续粘贴操作，或不。  
  
 `hMetaFile`  
 用于绘制项的图标的图元文件句柄。  
  
### <a name="return-value"></a>返回值  
 `HRESULT` Reporting 操作的成功与否的值。  
  
### <a name="remarks"></a>备注  
 重写此函数来处理不同的组织的 COM 派生的文档类中的项。 这是一个高级可重写。  
  
 有关详细信息`HRESULT`和`IDataObject`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)和[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)分别在 Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat  
 调用此函数可设置字符格式设置特性在此新文本`CRichEditView`对象。  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，它包含格式设置特性的新默认字符。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) Windows SDK 中的结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="setmargins"></a>  CRichEditView::SetMargins  
 调用此函数可将此丰富的编辑视图的打印边距设置。  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>参数  
 *rectMargin*  
 用于打印，新的边距值以衡量`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，应调用[WrapChanged](#wrapchanged)后使用此函数调整打印特征。  
  
 请注意，使用边距[对 PrintPage](#printpage)相对于物理页上，而不是在逻辑页面。 因此，为零的边距通常将剪切的文本，由于许多打印机具有页上无法打印区域中。 若要避免剪辑你的文本，应调用使用`SetMargins`将再进行打印的合理打印机边距设置。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize  
 调用此函数可设置用于打印此丰富的编辑视图的纸张大小。  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>参数  
 *sizePaper*  
 用于打印，新的纸张大小值以衡量`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，应调用[WrapChanged](#wrapchanged)后使用此函数调整打印特征。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat  
 调用此函数可设置的段落格式设置特性在此当前所选内容`CRichEditView`对象。  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>参数  
 `pf`  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，它包含新的默认段落格式设置的属性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 仅由指定的属性**dwMask**的成员`pf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)消息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) Windows SDK 中的结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="textnotfound"></a>  CRichEditView::TextNotFound  
 调用此函数可重置的内部搜索状态[CRichEditView](../../mfc/reference/cricheditview-class.md)后的失败调用控件[FindText](#findtext)。  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 包含找不到的文本字符串。  
  
### <a name="remarks"></a>备注  
 建议对失败的调用后立即调用此方法[FindText](#findtext)以便内部搜索控件状态的正确重置。  
  
 `lpszFind`参数应留作为到提供的字符串的相同内容[FindText](#findtext)。 在重置内部搜索状态之后, 此方法将调用[OnTextNotFound](#ontextnotfound)方法以提供的搜索字符串。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged  
 调用此函数，当更改打印特征 ( [SetMargins](#setmargins)或[SetPaperSize](#setpapersize))。  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>备注  
 此函数可修改丰富的编辑视图的方式响应中的更改的替代[m_nWordWrap](#m_nwordwrap)或打印的特征 ( [OnPrinterChanged](#onprinterchanged))。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)
