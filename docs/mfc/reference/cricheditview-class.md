---
title: 克里希编辑视图类
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
ms.openlocfilehash: b72daac576411b45908d1e91bd86bbd9aeacf738
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754454"
---
# <a name="cricheditview-class"></a>克里希编辑视图类

通过[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRichEditCntrItem，](../../mfc/reference/cricheditcntritem-class.md)在 MFC 的文档视图体系结构上下文中提供了丰富的编辑控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[克里希编辑视图：克里希编辑视图](#cricheditview)|构造 `CRichEditView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[克里希编辑视图：：调整对话位置](#adjustdialogposition)|移动对话框，使其不会遮挡当前选择。|
|[克里希编辑视图：：可以粘贴](#canpaste)|告知剪贴板是否包含可粘贴到富编辑视图中的数据。|
|[克里希编辑视图：:DoPaste](#dopaste)|将 OLE 项粘贴到此丰富的编辑视图中。|
|[克里希编辑视图：查找文本](#findtext)|查找指定的文本，调用等待光标。|
|[克里希编辑视图：查找文本简单](#findtextsimple)|查找指定的文本。|
|[克里希编辑视图：获取字符格式选择](#getcharformatselection)|检索当前选择的字符格式属性。|
|[克里希编辑视图：获取文档](#getdocument)|检索指向相关[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的指针。|
|[克里希编辑视图：获取位置活动项目](#getinplaceactiveitem)|检索当前在富编辑视图中处于活动状态的 OLE 项。|
|[克里希编辑视图：获取边缘](#getmargins)|检索此富编辑视图的边距。|
|[克里希编辑视图：获取页面Rect](#getpagerect)|检索此富编辑视图的页面矩形。|
|[克里希编辑视图：获取纸张大小](#getpapersize)|检索此富编辑视图的纸张大小。|
|[克里希编辑视图：获取帕拉格式选择](#getparaformatselection)|检索当前选择的段落格式属性。|
|[克里希编辑视图：获取打印重新](#getprintrect)|检索此富编辑视图的打印矩形。|
|[克里希编辑视图：获取打印宽度](#getprintwidth)|检索此富编辑视图的打印宽度。|
|[克里希编辑视图：获取里希编辑Ctrl](#getricheditctrl)|检索丰富的编辑控件。|
|[克里希编辑视图：获取选定项目](#getselecteditem)|从富编辑视图中检索所选项目。|
|[克里希编辑视图：获取文本长度](#gettextlength)|检索富编辑视图中的文本长度。|
|[克里希编辑视图：获取文本长度Ex](#gettextlengthex)|检索富编辑视图中的字符或字节数。 用于确定长度的方法的展开标志列表。|
|[克里希编辑视图：：插入文件对象](#insertfileasobject)|将文件插入为 OLE 项。|
|[克里希编辑视图：插入项目](#insertitem)|将新项目插入为 OLE 项。|
|[克里希编辑视图：：是里希编辑格式](#isricheditformat)|告知剪贴板是否包含丰富的编辑或文本格式的数据。|
|[克里希编辑视图：：在字符效果](#onchareffect)|切换当前选择的字符格式。|
|[克里希编辑视图：在帕拉维莱](#onparaalign)|更改段落的对齐方式。|
|[克里希编辑视图：上更新字符效果](#onupdatechareffect)|更新字符公共成员函数的命令 UI。|
|[克里希编辑视图：更新帕拉对齐](#onupdateparaalign)|更新段落公共成员函数的命令 UI。|
|[克里希编辑视图：:P林特内卡雷茨](#printinsiderect)|在给定矩形中设置指定文本的格式。|
|[克里希编辑视图：:PrintPage](#printpage)|在给定页面中设置指定文本的格式。|
|[克里希编辑视图：设置字符格式](#setcharformat)|设置当前选择的字符格式属性。|
|[克里希编辑视图：：设置边距](#setmargins)|设置此富编辑视图的边距。|
|[克里希编辑视图：：设置纸张大小](#setpapersize)|设置此富编辑视图的纸张大小。|
|[克里希编辑视图：：设置帕拉格式](#setparaformat)|设置当前选择的段落格式属性。|
|[克里希编辑视图：：未找到文本](#textnotfound)|重置控件的内部搜索状态。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[克里希编辑视图：获取剪贴板数据](#getclipboarddata)|检索此丰富编辑视图中范围的剪贴板对象。|
|[克里希编辑视图：获取上下文菜单](#getcontextmenu)|检索要在鼠标右键下使用的上下文菜单。|
|[克里希编辑视图：已选定](#isselected)|指示是否选择了给定的 OLE 项。|
|[克里希编辑视图：：在查找下一个](#onfindnext)|查找子字符串的下一个匹配项。|
|[克里希编辑视图：初始更新](#oninitialupdate)|首次将视图附加到文档时刷新视图。|
|[克里希编辑视图：：粘贴本机对象](#onpastenativeobject)|从 OLE 项检索本机数据。|
|[克里希编辑视图：打开打印机已更改](#onprinterchanged)|将打印特征设置到给定设备。|
|[克里希编辑视图：：全部替换](#onreplaceall)|将给定字符串的所有匹配项替换为新字符串。|
|[克里希编辑视图：打开替换塞尔](#onreplacesel)|替换当前选择。|
|[克里希编辑视图：：未找到文本](#ontextnotfound)|处理用户通知，通知未找到请求的文本。|
|[克里希编辑视图：：查询接受数据](#queryacceptdata)|查询以查看 上的数据`IDataObject`。|
|[克里希编辑视图：包装](#wrapchanged)|根据 的值调整此富编辑视图的目标输出设备`m_nWordWrap`。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[克里希编辑视图：m_nBulletIndent](#m_nbulletindent)|指示项目符号列表的缩进量。|
|[克里希编辑视图：：m_nWordWrap](#m_nwordwrap)|指示换行约束。|

## <a name="remarks"></a>备注

"富编辑控件"是用户可以在其中输入和编辑文本的窗口。 文本可以分配字符和段落格式，并可以包括嵌入的 OLE 对象。 丰富的编辑控件为文本格式设置提供了编程界面。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`维护视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 通用控件（因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用富编辑视图的示例，请参阅[WORDPAD](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>要求

**标题：** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>克里希编辑视图：：调整对话位置

调用此函数以移动给定的对话框，以便它不会遮盖当前选择。

```cpp
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>参数

*pDlg*<br/>
指向 `CDialog` 对象的指针。

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>克里希编辑视图：：可以粘贴

调用此函数以确定剪贴板是否包含可粘贴到此丰富编辑视图中的信息。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>返回值

如果剪贴板以此丰富的编辑视图可以接受的格式包含数据，则非零;否则，0。

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>克里希编辑视图：克里希编辑视图

调用此函数以创建对象`CRichEditView`。

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>克里希编辑视图：:DoPaste

调用此函数以将*dataobj*中的 OLE 项粘贴到此丰富的编辑文档/视图中。

```cpp
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>参数

*达多布吉*<br/>
包含要粘贴的数据的[COleData 对象](../../mfc/reference/coledataobject-class.md)。

*Cf*<br/>
所需的剪贴板格式。

*哈梅塔皮克特*<br/>
表示要粘贴的项的元文件。

### <a name="remarks"></a>备注

该框架调用此函数作为[查询接受数据](#queryacceptdata)默认实现的一部分。

此函数根据粘贴特殊处理程序的结果确定粘贴类型。 如果*cf*是 0，则新项目使用当前标志性表示形式。 如果*cf*是非零且*hMetaPict*不是 NULL，则新项目将使用*hMetaPict*进行表示。

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>克里希编辑视图：查找文本

调用此函数以查找指定的文本并将其设置为当前选择。

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
指示搜索是否应仅匹配整个单词，而不是单词的某些部分。

*b下一个*<br/>
指示搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果 FALSE，则搜索方向朝向缓冲区的开头。

### <a name="return-value"></a>返回值

如果找到*lpsz 查找*文本，则非零;否则 0。

### <a name="remarks"></a>备注

此函数在查找操作期间显示等待光标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>克里希编辑视图：查找文本简单

调用此函数以查找指定的文本并将其设置为当前选择。

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
指示搜索是否应仅匹配整个单词，而不是单词的某些部分。

*b下一个*<br/>
指示搜索的方向。 如果为 TRUE，则搜索方向朝向缓冲区的末尾。 如果 FALSE，则搜索方向朝向缓冲区的开头。

### <a name="return-value"></a>返回值

如果找到*lpsz 查找*文本，则非零;否则 0。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：：查找文本](#findtext)。

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>克里希编辑视图：获取字符格式选择

调用此函数获取当前选择的字符格式属性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>返回值

包含当前选择的字符格式属性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat)消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>克里希编辑视图：获取剪贴板数据

该框架调用此函数作为[IRichEditOle 回调处理的一部分：getClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>参数

*lpchrg*<br/>
指向[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)结构的指针，指定要复制到*lplpdataobj*指定的数据对象的字符范围（和 OLE 项）。

*德德雷科*<br/>
剪贴板操作标志。 可以是这些值之一。

- RECO_COPY复制到剪贴板。

- RECO_CUT剪切到剪贴板。

- RECO_DRAG拖动操作（拖放）。

- RECO_DROP拖放操作（拖放）。

- RECO_PASTE从剪贴板粘贴。

*lpRichDataObj*<br/>
指向包含来自丰富编辑控件的剪贴板数据的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)对象指针[（IRichEditOle：：getClipboard 数据](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)）。

*lpdataobj*<br/>
指向接收表示*lpchrg*参数中指定范围`IDataObject`的对象地址的指针变量。 如果返回错误，则忽略*lpdataobj*的值。

### <a name="return-value"></a>返回值

报告操作成功的 HRESULT 值。 有关 HRESULT 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="remarks"></a>备注

如果返回值指示成功，则`IRichEditOleCallback::GetClipboardData`返回`IDataObject`*lplpdataobj*访问的 。否则，它返回由*lpRichDataObj*访问的一个 。 重写此函数以提供您自己的剪贴板数据。 此函数的默认实现返回E_NOTIMPL。

这是一个高级的可重写。

有关详细信息，请参阅[IRichEditOle：：获取剪贴板数据](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)[、IRichEditOle 回拨：：获取剪辑板数据](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)，并在 Windows SDK 中查看[IDataObject。](/windows/win32/api/objidl/nn-objidl-idataobject) [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>克里希编辑视图：获取上下文菜单

该框架调用此函数作为[IRichEditOleCallback](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)处理的一部分：获取ContextMenu 。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>参数

*塞尔蒂普*<br/>
选择类型。 选择类型值在"备注"部分中描述。

*利波洛比*<br/>
如果所选内容`OLEOBJECT`包含一个或多个 OLE 项，则指向指定第一个选定 OLE 对象的结构的指针。 如果所选内容不包含任何项目，*则 lpoleobj*为 NULL。 结构`OLEOBJECT`包含指向 OLE 对象 v 表的指针。

*lpchrg*<br/>
指向包含当前选择的[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)结构的指针。

### <a name="return-value"></a>返回值

处理上下文菜单。

### <a name="remarks"></a>备注

此功能是鼠标右下处理的典型部分。

选择类型可以是以下标志的任意组合：

- SEL_EMPTY 表示没有当前选择。

- SEL_TEXT 指示当前所选内容包含文本。

- SEL_OBJECT 指示当前所选内容至少包含一个 OLE 项。

- SEL_MULTICHAR 指示当前所选内容包含多个文本字符。

- SEL_MULTIOBJECT 指示当前选择包含多个 OLE 对象。

默认实现返回 NULL。 这是一个高级的可重写。

有关详细信息，请参阅[IRichEditOle 回拨：：获取 Windows](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) SDK 中的上下文菜单和[CHARRANGE。](/windows/win32/api/richedit/ns-richedit-charrange)

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>克里希编辑视图：获取文档

调用此函数以获取指向与此视图`CRichEditDoc`关联的指针。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向与`CRichEditView`对象关联的[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)对象。

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>克里希编辑视图：获取位置活动项目

调用此函数以获取当前在此`CRichEditView`对象中激活的 OLE 项。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>返回值

指向此富编辑视图中的单个、就地活动[CRichEditCntrItem 对象的](../../mfc/reference/cricheditcntritem-class.md)指针;如果当前没有 OLE 项处于就地活动状态，则为 NULL。

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>克里希编辑视图：获取边缘

调用此函数以检索打印中使用的当前边距。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>返回值

打印中使用的边距，以MM_TWIPS为单位。

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>克里希编辑视图：获取页面Rect

调用此函数以获取打印中使用的页面的尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>返回值

打印中使用的页面边界，以MM_TWIPS为单位。

### <a name="remarks"></a>备注

此值基于纸张大小。

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>克里希编辑视图：获取纸张大小

调用此函数以检索当前纸张大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>返回值

印刷用的纸张大小，以MM_TWIPS为单位。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>克里希编辑视图：获取帕拉格式选择

调用此函数获取当前选择的段落格式属性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>返回值

包含当前选择的段落格式属性的[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

### <a name="remarks"></a>备注

有关详细信息，请参阅[EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Windows SDK 中的消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>克里希编辑视图：获取打印重新

调用此函数以检索页面矩形内打印区域的边界。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>返回值

打印中使用的图像区域的边界，以MM_TWIPS为单位进行测量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>克里希编辑视图：获取打印宽度

调用此函数以确定打印区域的宽度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>返回值

打印区域的宽度，以MM_TWIPS为单位。

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>克里希编辑视图：获取里希编辑Ctrl

调用此函数以检索与`CRichEditView`该对象关联的[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)对象。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>返回值

此`CRichEditCtrl`视图的对象。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：：查找文本](#findtext)。

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>克里希编辑视图：获取选定项目

调用此函数以检索当前在此`CRichEditCntrItem``CRichEditView`对象中选择的 OLE 项（对象）。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>返回值

指向在对象中选择的[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) `CRichEditView`对象;如果在此视图中未选择任何项目，则为 NULL。

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>克里希编辑视图：获取文本长度

调用此函数以检索此`CRichEditView`对象中文本的长度。

```
long GetTextLength() const;
```

### <a name="return-value"></a>返回值

此`CRichEditView`对象中的文本长度。

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>克里希编辑视图：获取文本长度Ex

调用此成员函数以计算此`CRichEditView`对象中文本的长度。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>参数

dwFlags**<br/>
指定用于确定文本长度的方法的值。 此成员可以是 Windows SDK 中描述的[GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex)标志成员中列出的一个或多个值。

*u代码页*<br/>
用于转换的代码页（CP_ACP用于 ANSI 代码页，Unicode 为 1200）。

### <a name="return-value"></a>返回值

编辑控件中的字符或字节数。 如果在*dwFlags*中设置了不兼容标志，则此成员函数将返回E_INVALIDARG。

### <a name="remarks"></a>备注

`GetTextLengthEx`提供了确定文本长度的其他方法。 它支持富编辑 2.0 功能。 有关详细信息，请参阅有关 Windows SDK 中的[丰富编辑控件](/windows/win32/Controls/about-rich-edit-controls)。

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>克里希编辑视图：：插入文件对象

调用此函数以将指定的文件（作为[CRichEditCntrItem 对象](../../mfc/reference/cricheditcntritem-class.md)）插入到丰富的编辑视图中。

```cpp
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
包含要插入的文件的名称的字符串。

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>克里希编辑视图：插入项目

调用此函数以将[CRichEditCntrItem 对象](../../mfc/reference/cricheditcntritem-class.md)插入到富编辑视图中。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要插入的项的指针。

### <a name="return-value"></a>返回值

指示插入成功的 HRESULT 值。

### <a name="remarks"></a>备注

有关 HRESULT 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>克里希编辑视图：：是里希编辑格式

调用此函数以确定*cf*是带有 OLE 项的文本、富文本或富文本的剪贴板格式。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>参数

*Cf*<br/>
感兴趣的剪贴板格式。

### <a name="return-value"></a>返回值

如果*cf*是丰富的编辑或文本剪贴板格式，则非零。

## <a name="cricheditviewisselected"></a><a name="isselected"></a>克里希编辑视图：已选定

调用此函数以确定当前是否在此视图中选择了指定的 OLE 项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>参数

*pDocItem*<br/>
指向视图中的对象。

### <a name="return-value"></a>返回值

如果选择对象，则非零;否则 0。

### <a name="remarks"></a>备注

如果派生视图类具有处理 OLE 项选择的不同方法，请重写此函数。

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>克里希编辑视图：m_nBulletIndent

列表中项目符号项的缩进;默认情况下，720 个单位，即 1/2 英寸。

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>克里希编辑视图：：m_nWordWrap

指示此富编辑视图的换行类型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>备注

以下值之一：

- `WrapNone`指示没有自动换字。

- `WrapToWindow`指示基于窗口宽度的换行符。

- `WrapToTargetDevice`指示基于目标设备特征的换字。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：：换行](#wrapchanged)。

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>克里希编辑视图：：在字符效果

调用此函数以切换当前选择的字符格式效果。

```cpp
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>参数

*dwMask*<br/>
要在当前选择中修改的字符格式效果。

*dwEffect*<br/>
要切换的字符格式效果所需的列表。

### <a name="remarks"></a>备注

对此函数的每个调用都会切换当前选择的指定格式效果。

有关*dwMask*和*dwEffect*参数及其潜在值的详细信息，请参阅 Windows SDK 中的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的相应数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>克里希编辑视图：：在查找下一个

在处理"查找/替换"对话框中的命令时，框架调用。

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

*b下一个*<br/>
搜索方向：TRUE 向下指示;FALSE，向上。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索是否仅匹配整个单词。

### <a name="remarks"></a>备注

调用此函数以查找 中`CRichEditView`的文本。 重写此函数可更改派生视图类的搜索特征。

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>克里希编辑视图：初始更新

视图首次附加到文档后由框架调用，但在最初显示视图之前。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现调用[CView：：OnUpdate](../../mfc/reference/cview-class.md#onupdate)成员函数，没有提示信息（即，使用*lHint*参数的默认值 0，对于*pHint*参数使用 NULL）。 重写此函数以执行任何需要有关文档信息的一次性初始化。 例如，如果应用程序具有固定大小的文档，则可以使用此函数根据文档大小初始化视图的滚动限制。 如果应用程序支持可变大小的文档，请使用`OnUpdate`在每次文档更改时更新滚动限制。

### <a name="example"></a>示例

  请参阅[CRichEditView 示例：：m_nWordWrap](#m_nwordwrap)。

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>克里希编辑视图：：粘贴本机对象

使用此函数从嵌入项加载本机数据。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>参数

*lpStg*<br/>
指向[IStorage](/windows/win32/api/objidl/nn-objidl-istorage)对象的指针。

### <a name="return-value"></a>返回值

如果成功，则非零;否则，0;

### <a name="remarks"></a>备注

通常，您可以通过在 中创建[COleStreamFile](../../mfc/reference/colestreamfile-class.md)来执行此操作`IStorage`。 `COleStreamFile`可以附加到存档和[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)调用以加载数据。

这是一个高级的可重写。

有关详细信息，请参阅 Windows SDK 中的[IStorage。](/windows/win32/api/objidl/nn-objidl-istorage)

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>克里希编辑视图：在帕拉维莱

调用此函数以更改所选段落的段落对齐方式。

```cpp
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>参数

*w对齐*<br/>
所需的段落对齐方式。 以下值之一：

- PFA_LEFT 将段落与左边距对齐。

- PFA_RIGHT 将段落与右边距对齐。

- PFA_CENTER 将段落居中边缘。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>克里希编辑视图：打开打印机已更改

覆盖此功能以在打印机更改时更改此富编辑视图的特征。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>参数

*直流打印机*<br/>
新打印机的[CDC](../../mfc/reference/cdc-class.md)对象。

### <a name="remarks"></a>备注

默认实现将纸张大小设置为输出设备（打印机）的物理高度和宽度。 如果没有与*dcPrinter*关联的设备上下文，则默认实现将纸张大小设置为 8.5 x 11 英寸。

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>克里希编辑视图：：全部替换

在处理"替换"对话框中替换所有命令时，框架调用该命令。

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

*lpsz替换*<br/>
替换文本。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索是否必须选择整个单词。

### <a name="remarks"></a>备注

调用此函数以将某些给定文本的所有匹配项替换为另一个字符串。 重写此函数以更改此视图的搜索特征。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：：查找文本](#findtext)。

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>克里希编辑视图：打开替换塞尔

在处理"替换"对话框中的替换命令时，框架调用。

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

*b下一个*<br/>
指示搜索的方向：TRUE 已关闭;FALSE，向上。

*bCase*<br/>
指示搜索是否区分大小写。

*bWord*<br/>
指示搜索是否必须选择整个单词。

*lpsz替换*<br/>
替换文本。

### <a name="remarks"></a>备注

调用此函数以将某些给定文本的一个匹配项替换为另一个字符串。 重写此函数以更改此视图的搜索特征。

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>克里希编辑视图：：未找到文本

每当搜索失败时，由框架调用。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
未找到的文本。

### <a name="remarks"></a>备注

重写此函数以更改[来自消息蜂比的](/windows/win32/api/winuser/nf-winuser-messagebeep)输出通知。

有关详细信息，请参阅 Windows SDK 中的[MessageBeep。](/windows/win32/api/winuser/nf-winuser-messagebeep)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>克里希编辑视图：上更新字符效果

框架调用此函数以更新字符效果命令的命令 UI。

```cpp
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。

*dwMask*<br/>
指示字符格式蒙版。

*dwEffect*<br/>
指示字符格式效果。

### <a name="remarks"></a>备注

掩*码 dwMask*指定要检查的字符格式属性。 标志*dwEffect*列出要设置/清除的字符格式属性。

有关*dwMask*和*dwEffect*参数及其潜在值的详细信息，请参阅 Windows SDK 中的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的相应数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>克里希编辑视图：更新帕拉对齐

框架调用此函数以更新段落效果命令的命令 UI。

```cpp
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。

*w对齐*<br/>
要检查的段落对齐方式。 以下值之一：

- PFA_LEFT 将段落与左边距对齐。

- PFA_RIGHT 将段落与右边距对齐。

- PFA_CENTER 将段落居中边缘。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>克里希编辑视图：:P林特内卡雷茨

调用此函数以在丰富的编辑控件中格式化文本范围，以适应*pDC*指定的设备的*rectLayout。*

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
指向输出区域的设备上下文。

*重新布局*<br/>
定义输出区域的[RECT](/windows/win32/api/windef/ns-windef-rect)或[CRect。](../../atl-mfc-shared/reference/crect-class.md)

*nIndex 开始*<br/>
要格式化的第一个字符的基于零的索引。

*nIndexStop*<br/>
要格式化的最后一个字符的零基索引。

*b输出*<br/>
指示是否应呈现文本。 如果 FALSE，则仅测量文本。

### <a name="return-value"></a>返回值

最后一个字符的索引，适合输出区域加上 1。

### <a name="remarks"></a>备注

通常，此调用之后是调用生成输出的[CRichEditCtrl：:DisplayBand。](../../mfc/reference/cricheditctrl-class.md#displayband)

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：获取纸张大小](#getpapersize)。

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>克里希编辑视图：:PrintPage

调用此函数，在*pDC*指定的输出设备的富编辑控件中格式化文本范围。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向设备上下文以进行页面输出。

*nIndex 开始*<br/>
要格式化的第一个字符的基于零的索引。

*nIndexStop*<br/>
要格式化的最后一个字符的零基索引。

### <a name="return-value"></a>返回值

上一个字符的索引，位于页面上，外加一个字符。

### <a name="remarks"></a>备注

每个页面的布局由[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)控制。 通常，此调用之后是调用生成输出的[CRichEditCtrl：:DisplayBand。](../../mfc/reference/cricheditctrl-class.md#displayband)

请注意，边距相对于物理页，而不是逻辑页。 因此，零边距通常会剪辑文本，因为许多打印机在页面上具有不可打印的区域。 为了避免剪切文本，应在打印之前调用[SetMargins](#setmargins)并设置合理的边距。

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>克里希编辑视图：：查询接受数据

由框架调用，将对象粘贴到富编辑中。

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

*lpcf格式*<br/>
指向可接受的数据格式的指针。

*德德雷科*<br/>
未使用。

*b真的*<br/>
指示粘贴操作是否应继续。

*hMetaFile*<br/>
用于绘制项目图标的元文件的句柄。

### <a name="return-value"></a>返回值

报告操作成功的 HRESULT 值。

### <a name="remarks"></a>备注

重写此函数以处理派生文档类中不同的 COM 项组织。 这是一个高级的可重写。

有关 HRESULT 和`IDataObject`的详细信息，请参阅在 Windows SDK 中分别看到 COM[错误代码](/windows/win32/com/structure-of-com-error-codes)和[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>克里希编辑视图：设置字符格式

调用此函数可为此`CRichEditView`对象中的新文本设置字符格式属性。

```cpp
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>参数

*Cf*<br/>
包含新的默认字符格式属性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="remarks"></a>备注

只有`dwMask`*cf*成员指定的属性由此函数更改。

有关详细信息，请参阅[EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Windows SDK 中的消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>克里希编辑视图：：设置边距

调用此函数可设置此富编辑视图的打印边距。

```cpp
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>参数

*rectMargin*<br/>
打印的新边距值，以MM_TWIPS为单位。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)为`WrapToTargetDevice`，则应在使用此函数调整打印特征后调用[Wrap"更改](#wrapchanged)"。

请注意[，PrintPage](#printpage)使用的边距与物理页无关，而不是逻辑页。 因此，零边距通常会剪辑文本，因为许多打印机在页面上具有不可打印的区域。 为了避免剪切文本，应在打印之前调用 使用`SetMargins`设置合理的打印机边距。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：获取纸张大小](#getpapersize)。

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>克里希编辑视图：：设置纸张大小

调用此函数以设置纸张大小以打印此丰富的编辑视图。

```cpp
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>参数

*大小纸*<br/>
打印的新纸张大小值，以MM_TWIPS为单位。

### <a name="remarks"></a>备注

如果[m_nWordWrap](#m_nwordwrap)为`WrapToTargetDevice`，则应在使用此函数调整打印特征后调用[Wrap"更改](#wrapchanged)"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>克里希编辑视图：：设置帕拉格式

调用此函数可为此`CRichEditView`对象中的当前选择设置段落格式属性。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>参数

*普夫*<br/>
包含新的默认段落格式属性的[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

### <a name="return-value"></a>返回值

如果成功，则非零;否则，0。

### <a name="remarks"></a>备注

只有`dwMask`*pf*成员指定的属性由此函数更改。

有关详细信息，请参阅[EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Windows SDK 中的消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>克里希编辑视图：：未找到文本

调用此函数以重置对[FindText](#findtext)的呼叫失败后[CRichEditView](../../mfc/reference/cricheditview-class.md)控件的内部搜索状态。

```cpp
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>参数

*lpszFind*<br/>
包含未找到的文本字符串。

### <a name="remarks"></a>备注

建议在调用[FindText](#findtext)失败后立即调用此方法，以便正确重置控件的内部搜索状态。

*lpszFind*参数应包含与提供给[FindText](#findtext)的字符串相同的内容。 重置内部搜索状态后，此方法将使用提供的搜索字符串调用[OnTextNotFound](#ontextnotfound)方法。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：：查找文本](#findtext)。

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>克里希编辑视图：包装

当打印特征发生更改时调用此功能（[设置边距](#setmargins)或[SetPaperSize）。](#setpapersize)

```
virtual void WrapChanged();
```

### <a name="remarks"></a>备注

重写此函数以修改富编辑视图响应[m_nWordWrap](#m_nwordwrap)或打印特征[（OnPrinterEdit）](#onprinterchanged)更改的方式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 类](../../mfc/reference/cctrlview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)
