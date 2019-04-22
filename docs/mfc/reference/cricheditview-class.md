---
title: CRichEditView 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 60eeaa2a37dd824ae418b25e95743c21c65ae7ce
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773718"
---
# <a name="cricheditview-class"></a>CRichEditView 类

与[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)并[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|构造 `CRichEditView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移动一个对话框，使它不会隐藏当前所选内容。|
|[CRichEditView::CanPaste](#canpaste)|指示剪贴板是否包含可以粘贴到 rich edit 视图的数据。|
|[CRichEditView::DoPaste](#dopaste)|将 OLE 项粘贴到此 rich edit 视图。|
|[CRichEditView::FindText](#findtext)|查找指定的文本，调用将等待光标。|
|[CRichEditView::FindTextSimple](#findtextsimple)|查找指定的文本。|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|检索格式设置特性的当前所选内容的字符。|
|[CRichEditView::GetDocument](#getdocument)|检索指向相关[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|检索当前处于就地活动状态在 rich edit 视图中的 OLE 项。|
|[CRichEditView::GetMargins](#getmargins)|检索此 rich edit 视图的边距。|
|[CRichEditView::GetPageRect](#getpagerect)|检索此 rich edit 视图页矩形。|
|[CRichEditView::GetPaperSize](#getpapersize)|检索此 rich edit 视图的纸张大小。|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|检索段落格式设置为当前所选内容的属性。|
|[CRichEditView::GetPrintRect](#getprintrect)|检索此 rich edit 视图的打印矩形。|
|[CRichEditView::GetPrintWidth](#getprintwidth)|检索此 rich edit 视图的打印宽度。|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|检索格式文本编辑控件。|
|[CRichEditView::GetSelectedItem](#getselecteditem)|从 rich edit 视图中检索所选的项。|
|[CRichEditView::GetTextLength](#gettextlength)|检索 rich edit 视图中的文本的长度。|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|检索字符或 rich edit 视图中的字节的数。 确定长度的方法的扩展的标志列表。|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|作为 OLE 项插入文件。|
|[CRichEditView::InsertItem](#insertitem)|将作为 OLE 项插入新项。|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|指示剪贴板是否包含带格式文本或文本格式中的数据。|
|[CRichEditView::OnCharEffect](#onchareffect)|切换当前所选内容的格式设置的字符。|
|[CRichEditView::OnParaAlign](#onparaalign)|更改段落对齐方式。|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新命令 UI 对于字符公共成员函数。|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新命令 UI 的段落公共成员函数。|
|[CRichEditView::PrintInsideRect](#printinsiderect)|设置给定矩形内的指定的文本的格式。|
|[CRichEditView::PrintPage](#printpage)|设置给定页中指定的文本的格式。|
|[CRichEditView::SetCharFormat](#setcharformat)|设置字符格式设置为当前所选内容的属性。|
|[CRichEditView::SetMargins](#setmargins)|设置此丰富的边距编辑视图。|
|[CRichEditView::SetPaperSize](#setpapersize)|设置此 rich edit 视图的纸张大小。|
|[CRichEditView::SetParaFormat](#setparaformat)|设置段落格式设置为当前所选内容的属性。|
|[CRichEditView::TextNotFound](#textnotfound)|重置控件的内部搜索状态。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|检索 Clipboard 对象以在此 rich edit 视图中的范围。|
|[CRichEditView::GetContextMenu](#getcontextmenu)|检索一个上下文菜单上右鼠标左键按下使用。|
|[CRichEditView::IsSelected](#isselected)|指示是否选择给定的 OLE 项。|
|[CRichEditView::OnFindNext](#onfindnext)|查找子字符串的下一个匹配项。|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|刷新视图首次附加到文档。|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|从 OLE 项检索本机数据。|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|将打印特性设置为给定的设备。|
|[CRichEditView::OnReplaceAll](#onreplaceall)|给定字符串的所有匹配项替换为新的字符串。|
|[CRichEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|找不到请求的文本的句柄用户通知。|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|若要查看有关将数据上的查询`IDataObject`。|
|[CRichEditView::WrapChanged](#wrapchanged)|调整此 rich edit 视图中，值的基础的目标输出设备`m_nWordWrap`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|指示项目符号列表的缩进量。|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|指示 word 自动换行约束。|

## <a name="remarks"></a>备注

"格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本字符和段落格式设置，可以分配，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 维护视图中的 OLE 客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

在 MFC 应用程序中使用 rich edit 视图的示例，请参阅[写字板](../../overview/visual-cpp-samples.md)示例应用程序。

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

调用此函数来移动给定的对话框，以便它不会遮盖当前所选内容。

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>参数

*pDlg*<br/>
指向 `CDialog` 对象的指针。

##  <a name="canpaste"></a>  CRichEditView::CanPaste

调用此函数可确定剪贴板是否包含可以粘贴到此 rich edit 视图的信息。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>返回值

如果剪贴板中包含了可接受此 rich edit 视图; 格式的数据，非零值否则为为 0。

##  <a name="cricheditview"></a>  CRichEditView::CRichEditView

调用此函数可创建`CRichEditView`对象。

```
CRichEditView();
```

##  <a name="dopaste"></a>  CRichEditView::DoPaste

调用此函数可将中的 OLE 项粘贴*dataobj*到此丰富编辑文档/视图。

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>参数

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md)包含要粘贴的数据。

*cf*<br/>
所需的剪贴板格式。

*hMetaPict*<br/>
表示要粘贴的项图元文件。

### <a name="remarks"></a>备注

框架调用此函数的默认实现的一部分[QueryAcceptData](#queryacceptdata)。

此函数确定粘贴为选择性粘贴基于处理程序的结果的类型。 如果*cf*为 0，则新项使用当前的图标表示形式。 如果*cf*为非零值和*hMetaPict*不为 NULL，新项使用*hMetaPict*为它的表示形式。

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

*lpszFind*<br/>
包含要搜索的字符串。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索应匹配整个单词，而非单词的一部分。

*bNext*<br/>
指示搜索方向。 如果为 TRUE，搜索方向为向缓冲区末尾的方向。 如果为 FALSE，则搜索方向是缓冲区的开头。

### <a name="return-value"></a>返回值

如果非零*lpszFind*找到文本; 否则为 0。

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

*lpszFind*<br/>
包含要搜索的字符串。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索应匹配整个单词，而非单词的一部分。

*bNext*<br/>
指示搜索方向。 如果为 TRUE，搜索方向为向缓冲区末尾的方向。 如果为 FALSE，则搜索方向是缓冲区的开头。

### <a name="return-value"></a>返回值

如果非零*lpszFind*找到文本; 否则为 0。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::FindText](#findtext)。

##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection

调用此函数可获取的字符格式设置的当前所选内容的属性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>返回值

一个[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a)结构，其中包含的字符格式设置的当前所选内容的属性。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_GETCHARFORMAT](/windows/desktop/Controls/em-getcharformat)消息并[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) Windows SDK 中的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData

框架调用此函数的处理的一部分[IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata)。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>参数

*lpchrg*<br/>
指向[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)结构，它指定范围的字符 （和 OLE 项） 复制到指定的数据对象*lplpdataobj*。

*dwReco*<br/>
剪贴板操作标志。 可以是下列值之一。

- RECO_COPY 复制到剪贴板。

- RECO_CUT 剪切到剪贴板。

- RECO_DRAG 拖动 （拖放） 的操作。

- RECO_DROP 删除 （拖放） 的操作。

- 从剪贴板粘贴时 RECO_PASTE。

*lpRichDataObj*<br/>
指向[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)对象，其中包含剪贴板数据从丰富的编辑控件 ( [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata))。

*lplpdataobj*<br/>
指向接收的地址的指针变量`IDataObject`对象，表示中指定的范围*lpchrg*参数。 值*lplpdataobj*如果返回错误，则忽略。

### <a name="return-value"></a>返回值

报告操作的成功的 HRESULT 值。 HRESULT 的详细信息，请参阅[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)Windows SDK 中。

### <a name="remarks"></a>备注

如果返回值表示成功，`IRichEditOleCallback::GetClipboardData`返回`IDataObject`访问*lplpdataobj*; 否则为它将返回一个由访问*lpRichDataObj*。 重写此函数可提供你自己的剪贴板数据。 此函数的默认实现返回 E_NOTIMPL。

这是一种高级可重写。

有关详细信息，请参阅[IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata)， [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata)，并[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)中的 Windows SDK 和，请参阅[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) Windows SDK 中。

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

框架调用此函数的处理的一部分[IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu)。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>参数

*seltyp*<br/>
所选内容类型。 备注部分所述的所选内容类型的值。

*lpoleobj*<br/>
指向`OLEOBJECT`结构，它指定所选的第一个 OLE 对象，如果所选内容包含一个或多个 OLE 项。 如果所选内容不包含任何项， *lpoleobj*为 NULL。 `OLEOBJECT`结构保存到 OLE 对象 v-表指针。

*lpchrg*<br/>
指向[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)结构，它包含当前所选内容。

### <a name="return-value"></a>返回值

上下文菜单的句柄。

### <a name="remarks"></a>备注

此函数是典型正确按下鼠标处理的一部分。

所选内容类型可以是下列标志的任意组合：

- SEL_EMPTY 指示当前没有选定内容。

- SEL_TEXT 指示当前所选内容包含文本。

- SEL_OBJECT 指示当前所选内容包含至少一个 OLE 项。

- SEL_MULTICHAR 指示当前所选内容包含多个字符的文本。

- SEL_MULTIOBJECT 指示当前所选内容包含多个 OLE 对象。

默认实现返回 NULL。 这是一种高级可重写。

有关详细信息，请参阅[IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu)并[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) Windows SDK 中。

##  <a name="getdocument"></a>  CRichEditView::GetDocument

调用此函数可获取一个指向`CRichEditDoc`与此视图关联。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)与关联的对象在`CRichEditView`对象。

##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem

调用此函数可获取 OLE 项当前在此就地激活`CRichEditView`对象。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>返回值

为单个、 就地活动状态的指针[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)此 rich edit 视图; 中的对象如果没有 OLE 项当前处于就地活动状态，则为 NULL。

##  <a name="getmargins"></a>  CRichEditView::GetMargins

调用此函数可检索当前边距打印时使用。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>返回值

在打印中使用的边距，以 MM_TWIPS 单位。

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

调用此函数可获取在打印中使用的页的尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>返回值

在打印中使用的页的边界，以 MM_TWIPS 单位。

### <a name="remarks"></a>备注

此值基于纸张大小。

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

调用此函数可检索当前的纸张大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

在打印中使用的纸张大小单位 MM_TWIPS。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection

调用此函数可获取的段落格式的当前所选内容的属性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>返回值

一个[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2)包含段落格式设置属性的当前所选内容的结构。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_GETPARAFORMAT](/windows/desktop/Controls/em-getparaformat)消息并[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) Windows SDK 中的结构。

##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect

调用此函数可检索页矩形内的打印区域的边界。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>返回值

在打印中使用的图像区域的边界，以 MM_TWIPS 单位。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

调用此函数可确定的打印区域的宽度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>返回值

以 MM_TWIPS 度量的打印区域的宽度。

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

调用此函数可检索[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)与关联的对象`CRichEditView`对象。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>返回值

`CRichEditCtrl`此视图的对象。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::FindText](#findtext)。

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

调用此函数可检索 OLE 项 (`CRichEditCntrItem`对象) 中这当前所选`CRichEditView`对象。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>返回值

指向[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)中所选对象`CRichEditView`对象;如果在此视图中不选择任何项，则为 NULL。

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

调用此函数可检索在此文本的长度`CRichEditView`对象。

```
long GetTextLength() const;
```

### <a name="return-value"></a>返回值

在此文本的长度`CRichEditView`对象。

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

调用此成员函数以计算在此文本的长度`CRichEditView`对象。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
值，该值指定要在确定文本长度时使用的方法。 此成员可以是一个或多个值中的标志成员列出[GETTEXTLENGTHEX](/windows/desktop/api/richedit/ns-richedit-_gettextlengthex) Windows SDK 中所述。

*uCodePage*<br/>
翻译 (CP_ACP ANSI 代码页，对 Unicode 的 1200年) 的代码页。

### <a name="return-value"></a>返回值

字符或编辑控件中的字节数。 如果中的设置不兼容的标志*dwFlags*，此成员函数将返回 E_INVALIDARG。

### <a name="remarks"></a>备注

`GetTextLengthEx` 提供了其他方法，来确定文本的长度。 它支持的 Rich Edit 2.0 功能。 有关详细信息，请参阅[有关 Rich Edit 控件](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中。

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

调用此函数可插入指定的文件 (作为[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象) 到丰富的编辑视图。

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
包含要插入的文件的名称的字符串。

##  <a name="insertitem"></a>  CRichEditView::InsertItem

调用此函数可插入[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)到 rich edit 视图的对象。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要插入的项。

### <a name="return-value"></a>返回值

HRESULT 值，该值指示成功插入。

### <a name="remarks"></a>备注

HRESULT 的详细信息，请参阅[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)Windows SDK 中。

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

调用此函数可确定是否*cf*是一种剪贴板格式，这是文本、 格式文本或与 OLE 项的多格式文本。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
感兴趣的剪贴板格式。

### <a name="return-value"></a>返回值

如果非零*cf*为丰富的编辑或文本剪贴板格式。

##  <a name="isselected"></a>  CRichEditView::IsSelected

调用此函数可确定当前未在此视图中选择是否指定的 OLE 项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>参数

*pDocItem*<br/>
指针指向在视图中的对象。

### <a name="return-value"></a>返回值

如果该对象处于选中状态，非零值否则为 0。

### <a name="remarks"></a>备注

如果您的派生的视图类具有用于处理 OLE 项的选择不同的方法，重写此函数。

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

项目符号列表中的项目; 缩进默认情况下，720 单位，即 1/2 英寸。

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

指示此 rich edit 视图的自动换行的类型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>备注

以下值之一：

- `WrapNone` 指示没有自动的自动换行。

- `WrapToWindow` 指示基于窗口的宽度的自动换行。

- `WrapToTargetDevice` 指示目标设备的特征的自动换行。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::WrapChanged](#wrapchanged)。

##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect

调用此函数可切换的字符格式设置为当前所选内容的效果。

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>参数

*dwMask*<br/>
字符格式设置要修改当前选定内容中的效果。

*dwEffect*<br/>
字符格式设置要切换的效果所需的列表。

### <a name="remarks"></a>备注

每次调用此函数切换当前所选内容指定格式设置的效果。

有关详细信息*dwMask*并*dwEffect*参数及其可能值，请参阅的相应数据成员[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>  CRichEditView::OnFindNext

处理查找/替换对话框中的命令时，由框架调用。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要查找的字符串。

*bNext*<br/>
要搜索的方向：TRUE 表示下;为 FALSE，最高。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示是否仅或不全字匹配搜索。

### <a name="remarks"></a>备注

调用此函数可查找中的文本`CRichEditView`。 重写此函数可更改搜索特征派生的视图类。

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

该视图首次附加到文档中之后, 但在最初显示的视图之前由框架调用。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现调用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示*lHint*参数，NULL 表示*pHint*参数)。 重写此函数以执行任何需要有关文档的信息的一次性初始化。 例如，如果你的应用程序具有固定大小的文档，您可以使用此函数来初始化视图的滚动限制基于文档大小。 如果你的应用程序支持大小可变的文档，使用`OnUpdate`更新滚动限制每次文档发生更改。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::m_nWordWrap](#m_nwordwrap)。

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

使用此函数中嵌入项的本机数据加载。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>参数

*lpStg*<br/>
指向[IStorage](/windows/desktop/api/objidl/nn-objidl-istorage)对象。

### <a name="return-value"></a>返回值

如果成功，则非零值否则为 0;

### <a name="remarks"></a>备注

通常情况下，您将执行此操作通过创建[COleStreamFile](../../mfc/reference/colestreamfile-class.md)围绕`IStorage`。 `COleStreamFile`可以附加到存档并[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)调用以将数据加载。

这是一种高级可重写。

有关详细信息，请参阅[IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) Windows SDK 中。

##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign

调用此函数可更改所选段落的段落对齐方式。

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>参数

*wAlign*<br/>
所需的段落对齐方式。 以下值之一：

- PFA_LEFT 对齐带有左边距段落。

- PFA_RIGHT 对齐带有右边距段落。

- PFA_CENTER 中心之间的边距的段落。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

重写此函数可打印机发生更改时更改此 rich edit 视图的特征。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>参数

*dcPrinter*<br/>
一个[CDC](../../mfc/reference/cdc-class.md)新打印机的对象。

### <a name="remarks"></a>备注

默认实现将纸张大小设置为物理高度和宽度为输出设备 （打印机）。 如果没有任何设备上下文与相关联*dcPrinter*的默认实现将纸张大小设置为 8.5 × 11 英寸。

##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll

处理全部替换替换对话框中的命令时，由框架调用。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要替换的文本。

*lpszReplace*<br/>
替换文本。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示是否搜索必须选择全字或不。

### <a name="remarks"></a>备注

调用此函数可使用其他字符串替换所有出现的一些给定的文本。 重写此函数可更改此视图的搜索特征。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::FindText](#findtext)。

##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel

处理替换对话框中的替换命令时，由框架调用。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
要替换的文本。

*bNext*<br/>
指示搜索方向：TRUE 已关闭;为 FALSE，最高。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示是否搜索必须选择全字或不。

*lpszReplace*<br/>
替换文本。

### <a name="remarks"></a>备注

调用此函数可使用其他字符串替换一些给定文本的一个匹配项。 重写此函数可更改此视图的搜索特征。

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

搜索失败时由框架调用。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
找不到的文本。

### <a name="remarks"></a>备注

重写此函数可更改从输出通知[MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep)。

有关详细信息，请参阅[MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep) Windows SDK 中。

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

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象。

*dwMask*<br/>
指示的字符格式设置掩码。

*dwEffect*<br/>
指示的字符格式设置的效果。

### <a name="remarks"></a>备注

掩码*dwMask*指定的字符要检查的格式设置属性。 标志*dwEffect*列出的字符格式设置属性组/清除。

有关详细信息*dwMask*并*dwEffect*参数及其可能值，请参阅的相应数据成员[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign

框架调用此函数可更新命令 UI 的段落效果命令。

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象。

*wAlign*<br/>
要检查的段落对齐方式。 以下值之一：

- PFA_LEFT 对齐带有左边距段落。

- PFA_RIGHT 对齐带有右边距段落。

- PFA_CENTER 中心之间的边距的段落。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect

调用此函数可设置一系列中 rich edit 控件以适合文本的格式*rectLayout*为指定的设备*pDC*。

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向输出区的设备上下文指针。

*rectLayout*<br/>
[RECT](/windows/desktop/api/windef/ns-windef-tagrect)或[CRect](../../atl-mfc-shared/reference/crect-class.md)定义输出区域。

*nIndexStart*<br/>
要设置格式的第一个字符的从零开始索引。

*nIndexStop*<br/>
要设置格式的最后一个字符的从零开始索引。

*bOutput*<br/>
指示是否应呈现的文本。 如果为 FALSE，则只需度量文本。

### <a name="return-value"></a>返回值

适合在输出区域加 1 中的最后一个字符的索引。

### <a name="remarks"></a>备注

通常情况下，此调用对的调用后面[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成的输出。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::GetPaperSize](#getpapersize)。

##  <a name="printpage"></a>  CRichEditView::PrintPage

调用此函数可设置为指定的输出设备 rich edit 控件中的文本范围的格式*pDC*。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>参数

*pDC*<br/>
页面输出的设备上下文的指针。

*nIndexStart*<br/>
要设置格式的第一个字符的从零开始索引。

*nIndexStop*<br/>
要设置格式的最后一个字符的从零开始索引。

### <a name="return-value"></a>返回值

页面以及一个可以容纳的最后一个字符的索引。

### <a name="remarks"></a>备注

由控制每个页的布局[GetPageRect](#getpagerect)并[GetPrintRect](#getprintrect)。 通常情况下，此调用对的调用后面[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)这将生成的输出。

请注意，边距相对于物理页，而不是在逻辑页面。 因此，为零的边距通常将剪辑文本，因为许多打印机有不可打印的页上的区域。 若要避免剪辑文本，应调用[SetMargins](#setmargins)和设置合理再进行打印边距。

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

由框架调用以将对象粘贴到文本编辑。

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>参数

*lpdataobj*<br/>
指向[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)查询。

*lpcfFormat*<br/>
为可接受的数据格式的指针。

*dwReco*<br/>
未使用。

*bReally*<br/>
指示是否应继续粘贴操作，或不。

*hMetaFile*<br/>
用于绘制项的图标的图元文件句柄。

### <a name="return-value"></a>返回值

报告操作的成功的 HRESULT 值。

### <a name="remarks"></a>备注

重写此函数来处理 COM 中的项派生的文档类不同的组织。 这是一种高级可重写。

有关详细信息的 HRESULT 和`IDataObject`，请参阅[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)并[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)分别，Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat

调用此函数可设置的字符格式设置在此新文本的特性`CRichEditView`对象。

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a)结构，它包含新的默认字符格式设置属性。

### <a name="remarks"></a>备注

指定的属性`dwMask`的成员*cf*更改此函数。

有关详细信息，请参阅[EM_SETCHARFORMAT](/windows/desktop/Controls/em-setcharformat)消息并[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) Windows SDK 中的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>  CRichEditView::SetMargins

调用此函数可将此 rich edit 视图的打印边距设置。

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>参数

*rectMargin*<br/>
用于打印，新的边距值，以 MM_TWIPS 单位。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，则应调用[WrapChanged](#wrapchanged)后使用此函数调整打印特性。

请注意，通过使用边距[PrintPage](#printpage)相对于物理页上，而不是在逻辑页面。 因此，为零的边距通常将剪辑文本，因为许多打印机有不可打印的页上的区域。 若要避免剪辑文本，应调用使用`SetMargins`设置合理的打印机在打印前的边距。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::GetPaperSize](#getpapersize)。

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

调用此函数可设置纸张大小的打印此 rich edit 视图。

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>参数

*sizePaper*<br/>
用于打印，新的纸张大小值，以 MM_TWIPS 单位。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，则应调用[WrapChanged](#wrapchanged)后使用此函数调整打印特性。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat

调用此函数可设置段落格式设置当前选定内容中此特性`CRichEditView`对象。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>参数

*pf*<br/>
[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2)结构，它包含新的默认段落格式设置属性。

### <a name="return-value"></a>返回值

如果成功，则非零值否则为为 0。

### <a name="remarks"></a>备注

指定的属性`dwMask`的成员*pf*更改此函数。

有关详细信息，请参阅[EM_SETPARAFORMAT](/windows/desktop/Controls/em-setparaformat)消息并[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) Windows SDK 中的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

调用此函数的内部搜索状态重置[CRichEditView](../../mfc/reference/cricheditview-class.md)后的失败调用控制[FindText](#findtext)。

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
包含找不到的文本字符串。

### <a name="remarks"></a>备注

建议的失败调用后立即调用此方法[FindText](#findtext) ，以便正确重置控件的内部搜索状态。

*LpszFind*参数应包含相同的内容作为字符串提供给[FindText](#findtext)。 重置后内部搜索状态，此方法将调用[OnTextNotFound](#ontextnotfound)方法使用提供的搜索字符串。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::FindText](#findtext)。

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

打印特性已更改时调用此函数 ( [SetMargins](#setmargins)或[SetPaperSize](#setpapersize))。

```
virtual void WrapChanged();
```

### <a name="remarks"></a>备注

重写此函数可修改丰富的编辑视图的方式响应变化[m_nWordWrap](#m_nwordwrap)或打印的特征 ( [OnPrinterChanged](#onprinterchanged))。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)
