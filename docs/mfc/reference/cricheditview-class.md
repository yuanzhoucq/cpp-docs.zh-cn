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
ms.openlocfilehash: b32578cc3c9ad4f7a89b8ee76449259c0fa0b43b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741514"
---
# <a name="cricheditview-class"></a>CRichEditView 类

对于[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRICHEDITCNTRITEM](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构上下文中 rich edit 控件的功能。

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
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移动对话框，使其不会遮盖当前选定内容。|
|[CRichEditView::CanPaste](#canpaste)|指示剪贴板是否包含可粘贴到富编辑视图中的数据。|
|[CRichEditView::DoPaste](#dopaste)|在此 rich edit 视图中粘贴 OLE 项。|
|[CRichEditView::FindText](#findtext)|查找指定的文本，并调用等待光标。|
|[CRichEditView::FindTextSimple](#findtextsimple)|查找指定的文本。|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|检索当前所选内容的字符格式特性。|
|[CRichEditView::GetDocument](#getdocument)|检索指向相关[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的指针。|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|检索在 rich edit 视图中当前就地活动的 OLE 项。|
|[CRichEditView::GetMargins](#getmargins)|检索此富编辑视图的边距。|
|[CRichEditView::GetPageRect](#getpagerect)|检索此富编辑视图的页面矩形。|
|[CRichEditView::GetPaperSize](#getpapersize)|检索此富编辑视图的纸张大小。|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|检索当前所选内容的段落格式特性。|
|[CRichEditView::GetPrintRect](#getprintrect)|检索此富编辑视图的打印矩形。|
|[CRichEditView::GetPrintWidth](#getprintwidth)|检索此富编辑视图的打印宽度。|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|检索 rich edit 控件。|
|[CRichEditView::GetSelectedItem](#getselecteditem)|从 rich edit 视图中检索选定项。|
|[CRichEditView::GetTextLength](#gettextlength)|检索 rich edit 视图中的文本长度。|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|检索 rich edit 视图中的字符数或字节数。 用于确定长度的方法的扩展标志列表。|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|将文件作为 OLE 项插入。|
|[CRichEditView::InsertItem](#insertitem)|将新项作为 OLE 项插入。|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|说明剪贴板是否包含以丰富的编辑格式或文本格式显示的数据。|
|[CRichEditView::OnCharEffect](#onchareffect)|为当前所选内容切换字符格式设置。|
|[CRichEditView::OnParaAlign](#onparaalign)|更改段落的对齐方式。|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新字符公共成员函数的命令用户界面。|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新段落公共成员函数的命令 UI。|
|[CRichEditView::PrintInsideRect](#printinsiderect)|设置给定矩形内的指定文本格式。|
|[CRichEditView::PrintPage](#printpage)|设置给定页面内的指定文本格式。|
|[CRichEditView::SetCharFormat](#setcharformat)|为当前所选内容设置字符格式特性。|
|[CRichEditView::SetMargins](#setmargins)|设置此 rich edit 视图的边距。|
|[CRichEditView::SetPaperSize](#setpapersize)|设置此富编辑视图的纸张大小。|
|[CRichEditView::SetParaFormat](#setparaformat)|为当前所选内容设置段落格式特性。|
|[CRichEditView::TextNotFound](#textnotfound)|重置控件的内部搜索状态。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|为此富编辑视图中的范围检索剪贴板对象。|
|[CRichEditView::GetContextMenu](#getcontextmenu)|检索要在鼠标右键下使用的上下文菜单。|
|[CRichEditView::IsSelected](#isselected)|指示是否选择了给定的 OLE 项。|
|[CRichEditView::OnFindNext](#onfindnext)|查找子字符串的下一个匹配项。|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|当视图第一次附加到文档时，刷新视图。|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|从 OLE 项检索本机数据。|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|将打印特性设置到给定的设备。|
|[CRichEditView::OnReplaceAll](#onreplaceall)|将出现的所有给定字符串替换为新字符串。|
|[CRichEditView::OnReplaceSel](#onreplacesel)|替换当前选定内容。|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|处理找不到请求的文本的用户通知。|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|查询查看上`IDataObject`的数据。|
|[CRichEditView::WrapChanged](#wrapchanged)|基于的值`m_nWordWrap`调整此 rich edit 视图的目标输出设备。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|指示项目符号列表的缩进量。|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|指示换行约束。|

## <a name="remarks"></a>备注

"Rich edit 控件" 是用户可在其中输入和编辑文本的窗口。 可以为文本分配字符和段落格式，还可以包括嵌入的 OLE 对象。 Rich edit 控件提供了用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`维护视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 公共控件（以及[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类）仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用 rich edit 视图的示例，请参阅[写字板](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>要求

**标头：** afxrich

##  <a name="adjustdialogposition"></a>CRichEditView：： AdjustDialogPosition

调用此函数可移动给定对话框，使其不会掩盖当前选定内容。

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>参数

*pDlg*<br/>
指向 `CDialog` 对象的指针。

##  <a name="canpaste"></a>CRichEditView：： CanPaste

调用此函数可确定剪贴板是否包含可粘贴到此富编辑视图中的信息。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>返回值

如果剪贴板包含的数据格式是此富编辑视图可以接受的格式，则为非零值;否则为0。

##  <a name="cricheditview"></a>CRichEditView：： CRichEditView

调用此函数可创建`CRichEditView`对象。

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView：:D oPaste

调用此函数可将*dataobj*中的 OLE 项粘贴到此丰富的编辑文档/视图中。

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>参数

*dataobj*<br/>
包含要粘贴的数据的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*cf*<br/>
所需的剪贴板格式。

*hMetaPict*<br/>
表示要粘贴的项的图元文件。

### <a name="remarks"></a>备注

框架将此函数作为[QueryAcceptData](#queryacceptdata)的默认实现的一部分进行调用。

此函数根据选择性粘贴的处理程序结果来确定粘贴类型。 如果*cf*为0，则新项使用当前的图标表示形式。 如果*cf*为非零值并且*hMetaPict*不为 NULL，则新项使用*hMetaPict*作为其表示形式。

##  <a name="findtext"></a>CRichEditView：： FindText

调用此函数可查找指定的文本，并将其设置为当前选择。

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
指示搜索是否应仅匹配全字，而不匹配单词的部分。

*bNext*<br/>
指示搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果为 FALSE，则搜索方向朝向缓冲区的开头。

### <a name="return-value"></a>返回值

如果找到*lpszFind*文本，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数在查找操作过程中显示等待光标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView：： FindTextSimple

调用此函数可查找指定的文本，并将其设置为当前选择。

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
指示搜索是否应仅匹配全字，而不匹配单词的部分。

*bNext*<br/>
指示搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果为 FALSE，则搜索方向朝向缓冲区的开头。

### <a name="return-value"></a>返回值

如果找到*lpszFind*文本，则为非零值;否则为0。

### <a name="example"></a>示例

  请参阅[CRichEditView：： FindText](#findtext)的示例。

##  <a name="getcharformatselection"></a>CRichEditView：： GetCharFormatSelection

调用此函数可获取当前所选内容的字符格式设置特性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>返回值

一个[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构，其中包含当前选定内容的字符格式设置特性。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat)消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView：： GetClipboardData

在处理[IRichEditOleCallback：： GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)时，框架会调用此函数。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>参数

*lpchrg*<br/>
指向[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)结构的指针，该结构指定要复制到*lplpdataobj*指定的数据对象的字符（和 OLE 项）范围。

*dwReco*<br/>
剪贴板操作标志。 可以是下列值之一。

- RECO_COPY 复制到剪贴板。

- RECO_CUT 剪切到剪贴板。

- RECO_DRAG 拖动操作（拖放）。

- RECO_DROP Drop operation （拖放）。

- 从剪贴板中粘贴 RECO_PASTE。

*lpRichDataObj*<br/>
指向包含富编辑控件（ [IRichEditOle：： GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)）中剪贴板数据的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)对象的指针。

*lplpdataobj*<br/>
一个指针，指向用于接收`IDataObject`对象地址的指针变量，该对象表示在*lpchrg*参数中指定的范围。 如果返回错误，则忽略*lplpdataobj*的值。

### <a name="return-value"></a>返回值

报告操作成功的 HRESULT 值。 有关 HRESULT 的详细信息，请参阅 Windows SDK 中[COM 错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="remarks"></a>备注

如果返回`IRichEditOleCallback::GetClipboardData`值指示 success，则返回由`IDataObject` *lplpdataobj*访问的; 否则，它将返回*lpRichDataObj*访问的值。 重写此函数以提供您自己的剪贴板数据。 此函数的默认实现将返回 E_NOTIMPL。

这是一种高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[IRichEditOle：： GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)、 [IRichEditOleCallback：： GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)和[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) ，并在 Windows SDK 中查看[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 。

##  <a name="getcontextmenu"></a>CRichEditView：： GetContextMenu

在处理[IRichEditOleCallback：： GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)时，框架会调用此函数。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>参数

*seltyp*<br/>
选择类型。 "备注" 部分中介绍了选择类型值。

*lpoleobj*<br/>
指向`OLEOBJECT`结构的指针，该结构指定选定的第一个 ole 对象（如果选定内容包含一个或多个 ole 项）。 如果所选内容不包含任何项，则*lpoleobj*为 NULL。 `OLEOBJECT`结构保存指向 OLE 对象 v 表的指针。

*lpchrg*<br/>
指向包含当前所选内容的[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)结构的指针。

### <a name="return-value"></a>返回值

上下文菜单的句柄。

### <a name="remarks"></a>备注

此函数是鼠标右键按下鼠标按钮的典型部分。

选择类型可以是以下标志的任意组合：

- SEL_EMPTY 指示当前没有选定内容。

- SEL_TEXT 指示当前所选内容包含文本。

- SEL_OBJECT 指示当前所选内容至少包含一个 OLE 项。

- SEL_MULTICHAR 指示当前所选内容包含多个文本字符。

- SEL_MULTIOBJECT 指示当前所选内容包含多个 OLE 对象。

默认实现返回 NULL。 这是一种高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[IRichEditOleCallback：： GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)和[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) 。

##  <a name="getdocument"></a>CRichEditView：： GetDocument

调用此函数可获取一个指针，该`CRichEditDoc`指针指向与此视图关联的。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向与您 `CRichEditView`的对象相关联的 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 对象的指针。

##  <a name="getinplaceactiveitem"></a>CRichEditView：： GetInPlaceActiveItem

调用此函数可获取此`CRichEditView`对象中当前就地激活的 OLE 项。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>返回值

指向此富编辑视图中单一的就地活动[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象的指针;如果当前没有 OLE 项处于就地活动状态，则为 NULL。

##  <a name="getmargins"></a>CRichEditView：： GetMargins

调用此函数可检索打印中使用的当前边距。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>返回值

打印时使用的边距，以 MM_TWIPS 度量。

##  <a name="getpagerect"></a>CRichEditView：： GetPageRect

调用此函数可获取打印中使用的页的尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>返回值

用于打印的页面的边界，以 MM_TWIPS 度量。

### <a name="remarks"></a>备注

此值基于纸张大小。

##  <a name="getpapersize"></a>CRichEditView：： GetPaperSize

调用此函数可检索当前纸张大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

打印时使用的纸张大小，以 MM_TWIPS 度量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView：： GetParaFormatSelection

调用此函数可获取当前所选内容的段落格式特性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>返回值

一个[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构，其中包含当前选定内容的段落格式特性。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat)消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

##  <a name="getprintrect"></a>CRichEditView：： GetPrintRect

调用此函数可在页矩形内检索打印区域的边界。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>返回值

用于打印的图像区域的边界，以 MM_TWIPS 度量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView：： GetPrintWidth

调用此函数可确定打印区域的宽度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>返回值

打印区域的宽度，以 MM_TWIPS 度量。

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

调用此函数可检索与 `CRichEditView`对象关联的 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 对象。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>返回值

此`CRichEditCtrl`视图的对象。

### <a name="example"></a>示例

  请参阅[CRichEditView：： FindText](#findtext)的示例。

##  <a name="getselecteditem"></a>CRichEditView：： GetSelectedItem

调用此函数可检索此`CRichEditCntrItem` `CRichEditView`对象中当前选定的 OLE 项（对象）。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>返回值

指向`CRichEditView`对象中选定的[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象的指针;如果未在此视图中选择任何项，则为 NULL。

##  <a name="gettextlength"></a>CRichEditView：： GetTextLength

调用此函数可检索此对象中文本`CRichEditView`的长度。

```
long GetTextLength() const;
```

### <a name="return-value"></a>返回值

此对象中文本`CRichEditView`的长度。

##  <a name="gettextlengthex"></a>CRichEditView：： GetTextLengthEx

调用此成员函数以计算此对象中文本`CRichEditView`的长度。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
值，用于指定确定文本长度时使用的方法。 此成员可以是 Windows SDK 中所述的[GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) flags 成员中列出的一个或多个值。

*uCodePage*<br/>
用于转换的代码页（对于 ANSI 代码页为 CP_ACP，对于 Unicode 为1200）。

### <a name="return-value"></a>返回值

编辑控件中的字符数或字节数。 如果*dwFlags*中设置了不兼容的标志，此成员函数将返回 E_INVALIDARG。

### <a name="remarks"></a>备注

`GetTextLengthEx`提供确定文本长度的其他方法。 它支持丰富的编辑2.0 功能。 有关详细信息，请参阅关于 Windows SDK 中的[丰富编辑控件](/windows/win32/Controls/about-rich-edit-controls)。

##  <a name="insertfileasobject"></a>CRichEditView：： InsertFileAsObject

调用此函数可将指定的文件（作为[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象）插入到丰富的编辑视图中。

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
包含要插入的文件的名称的字符串。

##  <a name="insertitem"></a>CRichEditView：： InsertItem

调用此函数可将[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象插入到丰富的编辑视图中。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要插入的项的指针。

### <a name="return-value"></a>返回值

HRESULT 值，指示插入是否成功。

### <a name="remarks"></a>备注

有关 HRESULT 的详细信息，请参阅 Windows SDK 中[COM 错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

##  <a name="isricheditformat"></a>CRichEditView：： IsRichEditFormat

调用此函数可确定*cf*是否为文本、格式文本或带有 OLE 项的多格式文本的剪贴板格式。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
所需的剪贴板格式。

### <a name="return-value"></a>返回值

如果*cf*是丰富的编辑或文本剪贴板格式，则为非零值。

##  <a name="isselected"></a>CRichEditView：： IsSelected

调用此函数可确定当前是否在此视图中选择了指定的 OLE 项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>参数

*pDocItem*<br/>
指向视图中的对象的指针。

### <a name="return-value"></a>返回值

如果选择对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果派生视图类有不同的方法来处理 OLE 项的选择，则重写此函数。

##  <a name="m_nbulletindent"></a>CRichEditView：： m_nBulletIndent

列表中项目符号项的缩进;默认值为720个单位，即1/2 英寸。

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>CRichEditView：： m_nWordWrap

指示此富编辑视图的自动换行类型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>备注

以下值之一：

- `WrapNone`指示不自动换行。

- `WrapToWindow`指示基于窗口宽度的自动换行。

- `WrapToTargetDevice`指示基于目标设备特性的自动换行。

### <a name="example"></a>示例

  请参阅[CRichEditView：： WrapChanged](#wrapchanged)的示例。

##  <a name="onchareffect"></a>CRichEditView：： OnCharEffect

调用此函数可为当前所选内容切换字符格式设置效果。

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>参数

*dwMask*<br/>
要在当前选定内容中修改的字符格式设置效果。

*dwEffect*<br/>
要切换的字符格式设置效果的所需列表。

### <a name="remarks"></a>备注

对此函数的每个调用都将为当前选择切换指定的格式设置效果。

有关*dwMask*和*dwEffect*参数及其潜在值的详细信息，请参阅 Windows SDK 中[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的对应数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView：： OnFindNext

当处理 "查找/替换" 对话框中的命令时由框架调用。

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
搜索方向：TRUE 表示向下;FALSE。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索是否全字匹配。

### <a name="remarks"></a>备注

调用此函数可在中`CRichEditView`查找文本。 重写此函数以更改派生视图类的搜索特性。

##  <a name="oninitialupdate"></a>CRichEditView：： OnInitialUpdate

在视图第一次附加到文档之后但最初显示视图之前由框架调用。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现将调用[CView：： OnUpdate](../../mfc/reference/cview-class.md#onupdate)成员函数，该函数不包含提示信息（也就是说，对于*lHint*参数使用默认值0，对*pHint*参数使用 NULL）。 重写此函数以执行需要文档相关信息的任何一次性初始化。 例如，如果应用程序具有固定大小的文档，则可以使用此函数根据文档大小初始化视图的滚动限制。 如果你的应用程序支持可变大小的文档`OnUpdate` ，请使用在每次更改文档时更新滚动限制。

### <a name="example"></a>示例

  请参阅[CRichEditView：： m_nWordWrap](#m_nwordwrap)的示例。

##  <a name="onpastenativeobject"></a>CRichEditView：： OnPasteNativeObject

使用此函数加载嵌入项中的本机数据。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>参数

*lpStg*<br/>
指向[IStorage](/windows/win32/api/objidl/nn-objidl-istorage)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则为非零值;否则为 0;

### <a name="remarks"></a>备注

通常，可以通过创建[COleStreamFile](../../mfc/reference/colestreamfile-class.md) `IStorage`来实现此目的。 可以附加到存档和[CObject：：串行化](../../mfc/reference/cobject-class.md#serialize)以加载数据。 `COleStreamFile`

这是一种高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 。

##  <a name="onparaalign"></a>CRichEditView：： OnParaAlign

调用此函数可更改所选段落的段落对齐方式。

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>参数

*wAlign*<br/>
所需段落对齐方式。 以下值之一：

- PFA_LEFT 将段落与左边距对齐。

- PFA_RIGHT 对齐段落和右边距。

- PFA_CENTER 使边距之间的段落居中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView：： OnPrinterChanged

重写此函数以在打印机更改时更改此富编辑视图的特征。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>参数

*dcPrinter*<br/>
新打印机的[CDC](../../mfc/reference/cdc-class.md)对象。

### <a name="remarks"></a>备注

默认实现将纸张大小设置为输出设备（打印机）的物理高度和宽度。 如果没有与*dcPrinter*关联的设备上下文，则默认实现会将纸张大小设置为 8.5 x 11 英寸。

##  <a name="onreplaceall"></a>CRichEditView：： OnReplaceAll

当处理 "替换" 对话框中的 "替换所有命令" 时由框架调用。

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
指示搜索是否必须选择整个单词。

### <a name="remarks"></a>备注

调用此函数可将出现的所有给定文本替换为其他字符串。 重写此函数以更改此视图的搜索特性。

### <a name="example"></a>示例

  请参阅[CRichEditView：： FindText](#findtext)的示例。

##  <a name="onreplacesel"></a>CRichEditView：： OnReplaceSel

在处理替换对话框中的替换命令时由框架调用。

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
指示搜索方向：如果为 TRUE，则为 TRUE;FALSE。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索是否必须选择整个单词。

*lpszReplace*<br/>
替换文本。

### <a name="remarks"></a>备注

调用此函数可将某个给定文本的一个匹配项替换为其他字符串。 重写此函数以更改此视图的搜索特性。

##  <a name="ontextnotfound"></a>CRichEditView：： OnTextNotFound

在搜索失败时由框架调用。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
找不到的文本。

### <a name="remarks"></a>备注

重写此函数以更改[MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep)的输出通知。

有关详细信息，请参阅 Windows SDK 中的[MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>CRichEditView：： OnUpdateCharEffect

框架调用此函数来更新字符效果命令的命令用户界面。

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。

*dwMask*<br/>
指示字符格式掩码。

*dwEffect*<br/>
指示字符格式设置效果。

### <a name="remarks"></a>备注

掩码*dwMask*指定要检查的字符格式设置特性。 Flags *dwEffect*列出要设置/清除的字符格式设置属性。

有关*dwMask*和*dwEffect*参数及其潜在值的详细信息，请参阅 Windows SDK 中[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的对应数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView：： OnUpdateParaAlign

框架调用此函数来更新段落效果命令的命令 UI。

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。

*wAlign*<br/>
要检查的段落对齐方式。 以下值之一：

- PFA_LEFT 将段落与左边距对齐。

- PFA_RIGHT 对齐段落和右边距。

- PFA_CENTER 使边距之间的段落居中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView：:P rintInsideRect

调用此函数可在 rich edit 控件中设置文本范围的格式，使其适合*pDC*指定的设备的*rectLayout* 。

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
指向输出区域的设备上下文的指针。

*rectLayout*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)或[CRect](../../atl-mfc-shared/reference/crect-class.md) ，定义输出区域。

*nIndexStart*<br/>
要设置格式的第一个字符的从零开始的索引。

*nIndexStop*<br/>
要进行格式设置的最后一个字符的从零开始的索引。

*bOutput*<br/>
指示是否应呈现文本。 如果为 FALSE，则仅度量文本。

### <a name="return-value"></a>返回值

输出区域中的最后一个字符的索引加一。

### <a name="remarks"></a>备注

通常，此调用后跟对[CRichEditCtrl：:D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband)的调用，该调用生成输出。

### <a name="example"></a>示例

  请参阅[CRichEditView：： GetPaperSize](#getpapersize)的示例。

##  <a name="printpage"></a>CRichEditView：:P rintPage

调用此函数可为*pDC*指定的输出设备设置超文本编辑控件中的文本范围。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向页面输出的设备上下文的指针。

*nIndexStart*<br/>
要设置格式的第一个字符的从零开始的索引。

*nIndexStop*<br/>
要进行格式设置的最后一个字符的从零开始的索引。

### <a name="return-value"></a>返回值

在页面上容纳的最后一个字符的索引。

### <a name="remarks"></a>备注

每页的布局由[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)控制。 通常，此调用后跟对[CRichEditCtrl：:D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband)的调用，该调用生成输出。

请注意，边距相对于物理页面，而不是逻辑页面。 因此，零的边距经常会剪裁文本，因为许多打印机在页面上都有不可打印的区域。 若要避免剪裁文本，应在打印之前调用[SetMargins](#setmargins)并设置合理的边距。

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

由框架调用以将对象粘贴到丰富的编辑中。

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
指向要查询的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的指针。

*lpcfFormat*<br/>
指向可接受的数据格式的指针。

*dwReco*<br/>
未使用。

*bReally*<br/>
指示粘贴操作是否应继续。

*hMetaFile*<br/>
用于绘制项的图标的图元文件的句柄。

### <a name="return-value"></a>返回值

报告操作成功的 HRESULT 值。

### <a name="remarks"></a>备注

重写此函数可处理派生文档类中的不同 COM 项的组织。 这是一种高级的可重写。

有关 HRESULT 和`IDataObject`的详细信息，请参阅 Windows SDK 中的[COM 错误代码](/windows/win32/com/structure-of-com-error-codes)和[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView：： SetCharFormat

调用此函数可设置此`CRichEditView`对象中新文本的字符格式设置特性。

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
包含新的默认字符格式设置属性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="remarks"></a>备注

此函数只更改`dwMask` *cf*成员指定的属性。

有关详细信息，请参阅 Windows SDK 中的[EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat)消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView：： SetMargins

调用此函数可设置此 rich edit 视图的打印边距。

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>参数

*rectMargin*<br/>
用于打印的新边距值，以 MM_TWIPS 度量。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)为`WrapToTargetDevice`，则在使用此函数调整打印特征后，应调用[WrapChanged](#wrapchanged) 。

请注意， [system.drawing.printing.printdocument.printpage>](#printpage)使用的边距相对于物理页，而不是逻辑页。 因此，零的边距经常会剪裁文本，因为许多打印机在页面上都有不可打印的区域。 若要避免剪裁文本，应在打印之前`SetMargins`调用 "使用设置合理的打印机边距"。

### <a name="example"></a>示例

  请参阅[CRichEditView：： GetPaperSize](#getpapersize)的示例。

##  <a name="setpapersize"></a>CRichEditView：： SetPaperSize

调用此函数可设置打印此富编辑视图的纸张大小。

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>参数

*sizePaper*<br/>
用于打印的新纸张大小值，以 MM_TWIPS 度量。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)为`WrapToTargetDevice`，则在使用此函数调整打印特征后，应调用[WrapChanged](#wrapchanged) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView：： SetParaFormat

调用此函数可设置此`CRichEditView`对象中当前选定内容的段落格式特性。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>参数

*pf*<br/>
[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构，其中包含新的默认段落格式特性。

### <a name="return-value"></a>返回值

如果成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数只更改由`dwMask` *pf*的成员指定的属性。

有关详细信息，请参阅 Windows SDK 中的[EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat)消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView：： TextNotFound

调用此函数可在调用[FindText](#findtext)后重置[CRichEditView](../../mfc/reference/cricheditview-class.md)控件的内部搜索状态。

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
包含未找到的文本字符串。

### <a name="remarks"></a>备注

建议在调用[FindText](#findtext)之后立即调用此方法，以便正确重置控件的内部搜索状态。

*LpszFind*参数应包含与提供给[FindText](#findtext)的字符串相同的内容。 重置内部搜索状态后，此方法将调用具有所提供的搜索字符串的[OnTextNotFound](#ontextnotfound)方法。

### <a name="example"></a>示例

  请参阅[CRichEditView：： FindText](#findtext)的示例。

##  <a name="wrapchanged"></a>CRichEditView：： WrapChanged

当打印特征发生更改时调用此函数（ [SetMargins](#setmargins)或[SetPaperSize](#setpapersize)）。

```
virtual void WrapChanged();
```

### <a name="remarks"></a>备注

重写此函数以修改 rich edit 视图响应[m_nWordWrap](#m_nwordwrap)或打印特征（ [OnPrinterChanged](#onprinterchanged)）的更改的方式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)
