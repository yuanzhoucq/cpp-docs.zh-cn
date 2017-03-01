---
title: "CRichEditView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditView
dev_langs:
- C++
helpviewer_keywords:
- document/view architecture, rich edit controls
- OLE containers, rich edit
- rich edit controls, OLE container
- CRichEditView class
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: 25
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
ms.openlocfilehash: 9f54ec0c8aae58828607b01973a263e458c30ddb
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditview-class"></a>CRichEditView 类
与[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移动一个对话框，以便它不会掩盖当前所选内容。|  
|[CRichEditView::CanPaste](#canpaste)|告知剪贴板中是否包含可以粘贴到格式文本编辑视图中的数据。|  
|[CRichEditView::DoPaste](#dopaste)|将一个 OLE 项粘贴到此格式文本编辑视图。|  
|[CRichEditView::FindText](#findtext)|查找指定的文本，调用将等待光标。|  
|[CRichEditView::FindTextSimple](#findtextsimple)|查找指定的文本。|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|检索字符格式设置为当前所选内容的属性。|  
|[CRichEditView::GetDocument](#getdocument)|检索指向相关[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|检索为当前处于就地活动状态丰富的编辑视图中的 OLE 项。|  
|[CRichEditView::GetMargins](#getmargins)|检索此格式文本编辑视图的边距。|  
|[CRichEditView::GetPageRect](#getpagerect)|检索此格式文本编辑视图页矩形。|  
|[CRichEditView::GetPaperSize](#getpapersize)|检索此格式文本编辑视图的纸张大小。|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|检索段落格式设置为当前所选内容的属性。|  
|[CRichEditView::GetPrintRect](#getprintrect)|检索此格式文本编辑视图的打印矩形。|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|检索此格式文本编辑视图的打印宽度。|  
|[Cricheditview:: Getricheditctrl](#getricheditctrl)|检索 rich edit 控件。|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|从丰富的编辑视图中检索所选的项目。|  
|[CRichEditView::GetTextLength](#gettextlength)|检索丰富的编辑视图中的文本的长度。|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|检索字符或格式文本编辑视图中的字节的数。 用于确定长度的方法扩展的标志列表。|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|作为 OLE 项插入文件。|  
|[CRichEditView::InsertItem](#insertitem)|作为 OLE 项插入一个新项。|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|告知剪贴板中是否包含带格式文本或文本格式中的数据。|  
|[CRichEditView::OnCharEffect](#onchareffect)|切换当前所选内容的格式的字符。|  
|[CRichEditView::OnParaAlign](#onparaalign)|更改段落的对齐方式。|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新字符公共成员函数的命令 UI。|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新段落公共成员函数的命令 UI。|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|设置给定的矩形范围内的指定的文本的格式。|  
|[CRichEditView::PrintPage](#printpage)|设置给定页面内的指定的文本的格式。|  
|[CRichEditView::SetCharFormat](#setcharformat)|设置字符格式设置为当前所选内容的属性。|  
|[CRichEditView::SetMargins](#setmargins)|设置此丰富的边距编辑视图。|  
|[CRichEditView::SetPaperSize](#setpapersize)|设置此格式文本编辑视图的纸张大小。|  
|[CRichEditView::SetParaFormat](#setparaformat)|设置段落格式设置为当前所选内容的属性。|  
|[CRichEditView::TextNotFound](#textnotfound)|重置控件的内部搜索状态。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|检索此格式文本编辑视图中的范围的剪贴板对象。|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|检索一个上下文菜单上右鼠标左键按下使用。|  
|[CRichEditView::IsSelected](#isselected)|指示给定的 OLE 项选择的与否。|  
|[CRichEditView::OnFindNext](#onfindnext)|查找子字符串的下一个匹配项。|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|刷新视图时首次附加到文档。|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|从 OLE 项检索本机数据。|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|将打印特性设置为给定设备。|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|使用新的字符串来替换给定字符串的所有匹配项。|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|找不到请求的文本的句柄用户通知。|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|若要查看有关数据上的查询`IDataObject`。|  
|[CRichEditView::WrapChanged](#wrapchanged)|调整目标输出设备，此 rich edit 视图中，根据值`m_nWordWrap`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|指示项目符号列表的缩进量。|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|指示 word 自动换行约束。|  
  
## <a name="remarks"></a>备注  
 "格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本可以为分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`保留视图中的 OLE 客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。  
  
 此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 是仅供程序在运行 Windows 95/98 和 Windows NT 版本 3.51 及更高版本。  
  
 在 MFC 应用程序中使用格式文本编辑视图的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrich.h  
  
##  <a name="a-nameadjustdialogpositiona--cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition  
 调用此函数可将给定对话框中移动，以便使当前所选内容不清楚。  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>参数  
 *pDlg*  
 指向 `CDialog` 对象的指针。  
  
##  <a name="a-namecanpastea--cricheditviewcanpaste"></a><a name="canpaste"></a>CRichEditView::CanPaste  
 调用此函数可确定剪贴板是否包含可以粘贴到此格式文本编辑视图的信息。  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果剪贴板中包含可接受此格式文本编辑视图; 的格式的数据否则为 0。  
  
##  <a name="a-namecricheditviewa--cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CRichEditView  
 调用此函数可创建`CRichEditView`对象。  
  
```  
CRichEditView();
```  
  
##  <a name="a-namedopastea--cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste  
 调用此函数可将中的 OLE 项粘贴`dataobj`到此格式文本编辑文档/视图。  
  
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
 框架将调用此函数的默认实现的一部分[QueryAcceptData](#queryacceptdata)。  
  
 此函数将确定粘贴基于 for 选择性粘贴处理程序的结果的类型。 如果`cf`为 0，则新的项使用了当前的图标表示形式。 如果`cf`为非零值和`hMetaPict`不是**NULL**，新项使用`hMetaPict`为它的表示形式。  
  
##  <a name="a-namefindtexta--cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText  
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
 指示搜索应匹配整个单词，而非单词的一部分。  
  
 `bNext`  
 指示搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区的末尾。 如果**FALSE**，搜索方向将是朝向该缓冲区的开头。  
  
### <a name="return-value"></a>返回值  
 如果非零`lpszFind`找到文本; 否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数在查找操作过程中显示等待光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView 收益分析](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="a-namefindtextsimplea--cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple  
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
 指示搜索应匹配整个单词，而非单词的一部分。  
  
 `bNext`  
 指示搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区的末尾。 如果**FALSE**，搜索方向将是朝向该缓冲区的开头。  
  
### <a name="return-value"></a>返回值  
 如果非零`lpszFind`找到文本; 否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="a-namegetcharformatselectiona--cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection  
 调用此函数可获取字符格式设置的当前所选内容的属性。  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>返回值  
 一个[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构其中包含的字符格式的当前所选内容的属性。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026)消息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&152;](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="a-namegetclipboarddataa--cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData  
 框架将调用此函数的处理过程中[IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)。  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>参数  
 `lpchrg`  
 指向[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，它指定的字符 （和 OLE 项），将复制到指定的数据对象的范围`lplpdataobj`。  
  
 `dwReco`  
 剪贴板操作标志。 可以是下列值之一。  
  
- **RECO_COPY**复制到剪贴板。  
  
- **RECO_CUT**剪切到剪贴板。  
  
- **RECO_DRAG**拖动操作 （拖放）。  
  
- **RECO_DROP**放 （拖放） 的操作。  
  
- **RECO_PASTE**从剪贴板粘贴时。  
  
 `lpRichDataObj`  
 指向[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)包含从丰富的剪贴板数据对象编辑控件 ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341))。  
  
 `lplpdataobj`  
 指向接收的地址的指针变量`IDataObject`对象，表示中指定的范围`lpchrg`参数。 值`lplpdataobj`如果返回错误将被忽略。  
  
### <a name="return-value"></a>返回值  
 `HRESULT`报告操作的成功的值。 有关详细信息`HRESULT`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果返回值表示成功， **IRichEditOleCallback::GetClipboardData**返回`IDataObject`访问`lplpdataobj`; 否则为它将返回一个由访问`lpRichDataObj`。 重写此函数可提供您自己的剪贴板数据。 此函数的默认实现返回**E_NOTIMPL**。  
  
 这是一个高级可重写。  
  
 有关详细信息，请参阅[IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)， [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315)，和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]并查看[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
##  <a name="a-namegetcontextmenua--cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu  
 框架将调用此函数的处理过程中[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)。  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>参数  
 *seltyp*  
 所选内容类型。 所选内容类型值备注部分所述。  
  
 `lpoleobj`  
 指向**OLEOBJECT**结构，它指定所选的第一个 OLE 对象，如果所选内容包含一个或多个 OLE 项。 如果所选内容不包含任何项`lpoleobj`是**NULL**。 **OLEOBJECT**结构保存到一个 OLE 对象 v-表指针。  
  
 `lpchrg`  
 指向[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)结构，它包含当前所选内容。  
  
### <a name="return-value"></a>返回值  
 上下文菜单上的句柄。  
  
### <a name="remarks"></a>备注  
 此函数是处理下的右侧鼠标按钮的主要组成部分。  
  
 所选内容类型可以是下列标志的任意组合︰  
  
- `SEL_EMPTY`指示当前没有选定内容。  
  
- `SEL_TEXT`指示当前所选内容包含文本。  
  
- `SEL_OBJECT`指示当前所选内容包含至少一个 OLE 项。  
  
- `SEL_MULTICHAR`指示当前所选内容包含多个字符的文本。  
  
- `SEL_MULTIOBJECT`指示当前所选内容包含多个 OLE 对象。  
  
 默认实现返回**NULL**。 这是一个高级可重写。  
  
 有关详细信息，请参阅[IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317)和[CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息**OLEOBJECT**类型，请参阅中的 OLE 数据结构和结构分配项目*OLE 醚畐 ゅ*。  
  
##  <a name="a-namegetdocumenta--cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument  
 调用此函数可获取一个指向`CRichEditDoc`与此视图关联。  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)与您`CRichEditView`对象。  
  
##  <a name="a-namegetinplaceactiveitema--cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem  
 调用此函数可获取 OLE 项在此中就地对目前处于激活状态`CRichEditView`对象。  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 为单一的、 处于就地活动状态的指针[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)此格式文本编辑视图; 中的对象**NULL**如果目前没有 OLE 项处于就地活动状态。  
  
##  <a name="a-namegetmarginsa--cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::GetMargins  
 调用此函数可检索当前边距打印时使用。  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>返回值  
 边距打印，使用的单位`MM_TWIPS`。  
  
##  <a name="a-namegetpagerecta--cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect  
 调用此函数可获取在打印中使用的页的尺寸。  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 在印刷中，使用的页边界单位`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 此值取决于纸张大小。  
  
##  <a name="a-namegetpapersizea--cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize  
 调用此函数可检索当前的纸张大小。  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在打印中使用的纸张大小单位`MM_TWIPS`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&153;](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="a-namegetparaformatselectiona--cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection  
 调用此函数可获取的段落格式设置的当前所选内容的属性。  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>返回值  
 一个[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构其中包含的段落格式设置的当前所选内容的属性。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182)消息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetprintrecta--cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect  
 调用此函数可检索页面矩形内的打印区域的边界。  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 在打印中使用的图像区域的边界单位`MM_TWIPS`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&154;](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="a-namegetprintwidtha--cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth  
 调用此函数可确定的打印区域的宽度。  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 打印区域的宽度以`MM_TWIPS`。  
  
##  <a name="a-namegetricheditctrla--cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>Cricheditview:: Getricheditctrl  
 调用此函数可检索[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)与关联对象`CRichEditView`对象。  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `CRichEditCtrl`此视图的对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="a-namegetselecteditema--cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem  
 调用此函数可检索 OLE 项 (`CRichEditCntrItem`对象) 中这当前选定`CRichEditView`对象。  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)中所选对象`CRichEditView`对象;**NULL**如果在此视图中不选定任何项。  
  
##  <a name="a-namegettextlengtha--cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength  
 调用此函数可检索此中文本的长度`CRichEditView`对象。  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 在此文本的长度`CRichEditView`对象。  
  
##  <a name="a-namegettextlengthexa--cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx  
 调用此成员函数来计算此中文本的长度`CRichEditView`对象。  
  
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
 `GetTextLengthEx`提供了其他方法，来确定文本的长度。 它支持丰富的编辑 2.0 的功能。 有关详细信息，请参阅[有关格式文本编辑控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertfileasobjecta--cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject  
 调用此函数可插入指定的文件 (作为[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象) 读入格式文本编辑视图。  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 包含要插入的文件的名称的字符串。  
  
##  <a name="a-nameinsertitema--cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem  
 调用此函数可插入[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)到格式文本编辑视图的对象。  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 要插入的项的指针。  
  
### <a name="return-value"></a>返回值  
 `HRESULT`值，该值指示成功的插入。  
  
### <a name="remarks"></a>备注  
 有关详细信息`HRESULT`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisricheditformata--cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CRichEditView::IsRichEditFormat  
 调用此函数可确定是否`cf`是一种剪贴板格式，这是文本、 格式文本或格式文本与 OLE 项。  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 感兴趣的剪贴板格式。  
  
### <a name="return-value"></a>返回值  
 如果非零`cf`是丰富的编辑或文本剪贴板格式。  
  
##  <a name="a-nameisselecteda--cricheditviewisselected"></a><a name="isselected"></a>CRichEditView::IsSelected  
 调用此函数可确定在此视图中当前是否选定了指定的 OLE 项。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pDocItem`  
 在视图中的对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果该对象处于选中状态，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果您的派生的视图类具有用于处理 OLE 项的选择不同的方法，重写此函数。  
  
##  <a name="a-namemnbulletindenta--cricheditviewmnbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent  
 项目符号列表中的项目; 缩进默认情况下，720 单位，即 1/2 英寸。  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="a-namemnwordwrapa--cricheditviewmnwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap  
 指示为此格式文本编辑视图的自动换行的类型。  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>备注  
 以下值之一：  
  
- `WrapNone`指示没有自动自动换行。  
  
- `WrapToWindow`指示根据窗口宽度自动换行。  
  
- `WrapToTargetDevice`指示根据目标设备的特性的自动换行。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::WrapChanged](#wrapchanged)。  
  
##  <a name="a-nameonchareffecta--cricheditviewonchareffect"></a><a name="onchareffect"></a>CRichEditView::OnCharEffect  
 调用此函数可切换的字符格式设置当前所选内容的效果。  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>参数  
 `dwMask`  
 字符格式设置来修改中当前所选内容的效果。  
  
 `dwEffect`  
 字符格式效果来切换所需的列表。  
  
### <a name="remarks"></a>备注  
 每次调用此函数用于切换当前所选内容的指定格式设置的效果。  
  
 有关详细信息`dwMask`和`dwEffect`参数和它们的潜在值，请参阅的对应数据成员[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&155;](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="a-nameonfindnexta--cricheditviewonfindnext"></a><a name="onfindnext"></a>CRichEditView::OnFindNext  
 在处理来自查找/替换对话框中的命令时，由框架调用。  
  
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
 要搜索的方向︰ **TRUE**指示关闭;**FALSE**, up.  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 指示是否仅或不全字匹配搜索。  
  
### <a name="remarks"></a>备注  
 调用此函数可查找中的文本`CRichEditView`。 重写此函数可更改您的派生的视图类的搜索特征。  
  
##  <a name="a-nameoninitialupdatea--cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate  
 查看第一次附加到文档之后, 但在最初显示的视图之前，由框架调用。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示`lHint`参数和**NULL**为`pHint`参数)。 重写此函数以执行任何需要与文档有关的信息的一次性初始化。 例如，如果您的应用程序具有固定大小的文档，您可以使用此函数来初始化视图的滚动限制基于文档的大小。 如果您的应用程序支持大小可变的文档，使用`OnUpdate`用于滚动更新的限制每次文档发生更改。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::m_nWordWrap](#m_nwordwrap)。  
  
##  <a name="a-nameonpastenativeobjecta--cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject  
 使用此函数加载嵌入项从本机数据。  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>参数  
 *lpStg*  
 指向[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0;  
  
### <a name="remarks"></a>备注  
 通常情况下，您即可完成此操作创建[COleStreamFile](../../mfc/reference/colestreamfile-class.md)周围`IStorage`。 `COleStreamFile`可以附加到存档和[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)调用以将数据加载。  
  
 这是一个高级可重写。  
  
 有关详细信息，请参阅[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonparaaligna--cricheditviewonparaalign"></a><a name="onparaalign"></a>CRichEditView::OnParaAlign  
 调用此函数可更改所选段落的段落对齐方式。  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>参数  
 `wAlign`  
 所需的段落对齐方式。 以下值之一：  
  
- `PFA_LEFT`对齐与左边距的段落。  
  
- `PFA_RIGHT`对齐与右边距的段落。  
  
- `PFA_CENTER`中心之间的边距的段落。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&156;](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="a-nameonprinterchangeda--cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged  
 重写此函数可打印机发生更改时更改此格式文本编辑视图的特征。  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>参数  
 `dcPrinter`  
 一个[CDC](../../mfc/reference/cdc-class.md)新打印机的对象。  
  
### <a name="remarks"></a>备注  
 默认实现将纸张大小设置为的实际高度和宽度输出设备 （打印机）。 如果没有与相关联无设备上下文`dcPrinter`，默认实现将纸张大小设置为 8.5 × 11 英寸。  
  
##  <a name="a-nameonreplacealla--cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CRichEditView::OnReplaceAll  
 在处理来自替换对话框中的全部替换命令时，由框架调用。  
  
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
 替换文字。  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 表示是否搜索是否必须选择整个单词。  
  
### <a name="remarks"></a>备注  
 调用此函数可将某些给定文本的所有实例替换为另一个字符串。 重写此函数可更改此视图的搜索特征。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="a-nameonreplacesela--cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CRichEditView::OnReplaceSel  
 在处理来自替换对话框中的替换命令时，由框架调用。  
  
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
 指示搜索方向︰ **TRUE**已关闭;**FALSE**, up.  
  
 `bCase`  
 指示搜索是否区分大小写。  
  
 `bWord`  
 表示是否搜索是否必须选择整个单词。  
  
 `lpszReplace`  
 替换文字。  
  
### <a name="remarks"></a>备注  
 调用此函数可将某些给定文本的一个匹配项替换为另一个字符串。 重写此函数可更改此视图的搜索特征。  
  
##  <a name="a-nameontextnotfounda--cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CRichEditView::OnTextNotFound  
 由框架调用时的搜索失败。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 找不到文本。  
  
### <a name="remarks"></a>备注  
 重写此函数可更改从输出通知[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356)。  
  
 有关详细信息，请参阅[MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&157;](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="a-nameonupdatechareffecta--cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect  
 框架调用此函数以更新命令 UI 字符效果命令。  
  
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
 指示格式掩码的字符。  
  
 `dwEffect`  
 指示字符格式设置的效果。  
  
### <a name="remarks"></a>备注  
 掩码`dwMask`指定的字符格式设置属性来检查。 标志`dwEffect`列表的字符格式设置属性组/清除。  
  
 有关详细信息`dwMask`和`dwEffect`参数和它们的潜在值，请参阅的对应数据成员[CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&158;](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="a-nameonupdateparaaligna--cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign  
 框架调用此函数以更新命令 UI 段落效果命令。  
  
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
  
- `PFA_LEFT`对齐与左边距的段落。  
  
- `PFA_RIGHT`对齐与右边距的段落。  
  
- `PFA_CENTER`中心之间的边距的段落。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&159;](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="a-nameprintinsiderecta--cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect  
 调用此函数可设置区域的中 rich edit 控件以适合文本格式*rectLayout*由指定的设备`pDC`。  
  
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
 向输出区域的设备上下文的指针。  
  
 *rectLayout*  
 [RECT](../../mfc/reference/rect-structure1.md)或[CRect](../../atl-mfc-shared/reference/crect-class.md)定义的输出区域。  
  
 `nIndexStart`  
 要设置格式的第一个字符的从零开始索引。  
  
 `nIndexStop`  
 要设置格式的最后一个字符的从零开始索引。  
  
 *bOutput*  
 指示是否应呈现的文本。 如果**FALSE**，只是测量的文本。  
  
### <a name="return-value"></a>返回值  
 适合在输出区域加&1; 中的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 通常情况下，此调用后跟调用[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成输出。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="a-nameprintpagea--cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage  
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
 适合在页上加&1; 的最后一个字符的索引。  
  
### <a name="remarks"></a>备注  
 每个页的布局受[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)。 通常情况下，此调用后跟调用[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成输出。  
  
 请注意，边距相对于物理页面，而不是逻辑的页面。 因此，为零的边距通常将剪切文本，由于许多打印机页上的不可打印区域。 若要避免剪切文本，应调用[SetMargins](#setmargins)并设置在打印之前的合理边距。  
  
##  <a name="a-namequeryacceptdataa--cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CRichEditView::QueryAcceptData  
 由框架将对象粘贴到格式文本编辑调用。  
  
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
 指示粘贴操作是否应继续与否。  
  
 `hMetaFile`  
 用于绘制项的图标的图元文件句柄。  
  
### <a name="return-value"></a>返回值  
 `HRESULT`报告操作的成功的值。  
  
### <a name="remarks"></a>备注  
 重写此函数来处理 COM 中的项派生的文档类的其他组织。 这是一个高级可重写。  
  
 有关详细信息`HRESULT`和`IDataObject`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)和[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)，分别在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&160;](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="a-namesetcharformata--cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat  
 调用此函数可设置字符格式设置特性在此新文本`CRichEditView`对象。  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构，其中包含新的默认字符格式的属性。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`cf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230)消息和[CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&152;](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="a-namesetmarginsa--cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins  
 调用此函数可将此格式文本编辑视图的打印边距设置。  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>参数  
 *rectMargin*  
 新的边距值，用于打印，以衡量`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，应调用[WrapChanged](#wrapchanged)之后使用此功能可以调整打印特征。  
  
 请注意，使用边距[PrintPage](#printpage)相对于物理页上，而不是逻辑的页面。 因此，为零的边距通常将剪切文本，由于许多打印机页上的不可打印区域。 若要避免剪切文本，应调用使用`SetMargins`将在打印之前的合理打印机边距设置。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::GetPaperSize](#getpapersize)。  
  
##  <a name="a-namesetpapersizea--cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize  
 调用此函数可设置打印该格式文本编辑视图的纸张大小。  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>参数  
 *sizePaper*  
 用于打印，新的纸张大小值以衡量`MM_TWIPS`。  
  
### <a name="remarks"></a>备注  
 如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，应调用[WrapChanged](#wrapchanged)之后使用此功能可以调整打印特征。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&161;](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="a-namesetparaformata--cricheditviewsetparaformat"></a><a name="setparaformat"></a>CRichEditView::SetParaFormat  
 调用此函数可设置的段落格式设置特性在此当前所选内容`CRichEditView`对象。  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>参数  
 `pf`  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构，其中包含新的默认段落格式设置属性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 指定特性**dwMask**的成员`pf`更改此函数。  
  
 有关详细信息，请参阅[EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276)消息和[PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&162;](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="a-nametextnotfounda--cricheditviewtextnotfound"></a><a name="textnotfound"></a>CRichEditView::TextNotFound  
 调用此函数可重置的内部搜索状态[CRichEditView](../../mfc/reference/cricheditview-class.md)后的失败调用控件[FindText](#findtext)。  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 包含找不到的文本字符串。  
  
### <a name="remarks"></a>备注  
 建议在对失败的调用后立即调用此方法[FindText](#findtext) ，以便正确地重置控件的内部搜索状态。  
  
 `lpszFind`参数应留到提供的字符串相同的内容[FindText](#findtext)。 重置内部搜索状态，则此方法将调用[OnTextNotFound](#ontextnotfound)使用提供的搜索字符串的方法。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::FindText](#findtext)。  
  
##  <a name="a-namewrapchangeda--cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapChanged  
 打印特性的更改时调用该函数 ( [SetMargins](#setmargins)或[SetPaperSize](#setpapersize))。  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>备注  
 重写此函数可修改丰富的编辑视图的方式响应更改[m_nWordWrap](#m_nwordwrap)或打印的特征 ( [OnPrinterChanged](#onprinterchanged))。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&163;](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)

