---
title: CView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ccb638669712222cac2dee522bf729766a4bc93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402260"
---
# <a name="cview-class"></a>CView 类

提供用户定义视图类的基本功能。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CView::CView](#cview)|构造 `CView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|显示打印对话框并创建打印机设备上下文;当重写时，调用`OnPreparePrinting`成员函数。|
|[CView::GetDocument](#getdocument)|返回与视图关联的文档。|
|[CView::IsSelected](#isselected)|测试是否选择了文档项。 对于 OLE 支持必需。|
|[CView::OnDragEnter](#ondragenter)|当第一次到视图的拖放区域拖动项时调用。|
|[CView::OnDragLeave](#ondragleave)|拖动的项离开视图的拖放区域时调用。|
|[CView::OnDragOver](#ondragover)|当视图拖放区域上拖动项时调用。|
|[CView::OnDragScroll](#ondragscroll)|调用以确定是否将光标拖到窗口的滚动区域。|
|[CView::OnDrop](#ondrop)|当某项已放入视图，默认处理程序的拖放区域时调用。|
|[CView::OnDropEx](#ondropex)|当某项已放入视图中，主要处理程序的拖放区域时调用。|
|[Cview:: Oninitialupdate](#oninitialupdate)|视图首次附加到文档后调用。|
|[CView::OnPrepareDC](#onpreparedc)|之前调用`OnDraw`是用于屏幕显示调用成员函数或`OnPrint`个打印或打印预览调用成员函数。|
|[CView::OnScroll](#onscroll)|当不在视图的边框将 OLE 项时调用。|
|[CView::OnScrollBy](#onscrollby)|包含活动的就地 OLE 项的视图滚动时调用。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|当激活或停用包含视图的框架窗口时调用。|
|[CView::OnActivateView](#onactivateview)|当激活视图时调用。|
|[CView::OnBeginPrinting](#onbeginprinting)|打印作业开始; 时调用重写以分配图形设备接口 (GDI) 资源。|
|[Cview:: Ondraw](#ondraw)|调用以呈现用于屏幕显示、 打印或打印预览的文档图像。 所需的实现。|
|[CView::OnEndPrinting](#onendprinting)|打印作业结束; 时调用若要解除分配 GDI 资源的重写。|
|[CView::OnEndPrintPreview](#onendprintpreview)|当退出预览模式时调用。|
|[CView::OnPreparePrinting](#onprepareprinting)|在打印或预览; 文档之前调用重写以初始化打印对话框。|
|[CView::OnPrint](#onprint)|调用以打印或预览文档的页。|
|[CView::OnUpdate](#onupdate)|调用以通知视图，其文档已被修改。|

## <a name="remarks"></a>备注

一个视图附加到文档，并且可作为文档和用户之间的媒介： 视图呈现屏幕或打印机上的文档的图像，并将用户输入解释为文档的操作。

视图是框架窗口的子级。 多个视图可以共享框架窗口，如下所示的拆分器窗口大小写。 视图类、 框架窗口类与文档类之间的关系通过建立`CDocTemplate`对象。 当用户打开一个新窗口或将拆分的现有一个框架构造一个新的视图，并将其附加到文档。

视图可以附加到一个文档，但的文档可以包含多个视图在一次附加到它 — 例如，如果拆分器窗口中或在多文档界面 (MDI) 应用程序中的多个子窗口中显示的文档。 应用程序可以为给定的文档类型; 支持不同类型的视图例如，字处理程序可能会提供一个文档的完整文本视图和大纲视图，显示了仅的节标题。 这些不同类型的视图可以放置在单独的框架窗口或独立的单个框架窗口的窗格中如果使用拆分器窗口。

视图可能需要负责处理多种不同类型的输入，如键盘输入、 鼠标输入或从菜单、 工具栏或滚动条通过拖放，以及命令的输入。 视图接收转发的其框架窗口的命令。 如果视图不会处理给定的命令，它会转发到其关联文档命令。 所有命令目标，如视图处理消息映射中的消息。

视图负责显示和修改文档的数据而不是将其存储。 此文档提供了有关其数据具有必要的详细信息视图。 可以让直接，文档的数据成员也可以提供要调用的视图类的文档类中的成员函数的视图访问权限。

文档的数据更改时，视图负责所做的更改通常会调用[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)文档，这将告知所有其他视图通过调用函数`OnUpdate`成员函数每个。 默认实现`OnUpdate`使该视图的整个客户端区域无效。 可以重写它要使之无效仅这些区域的工作区映射到文档的修改后的部分。

若要使用`CView`、 从其派生一个类和实现`OnDraw`成员函数以执行屏幕显示。 此外可以使用`OnDraw`执行打印和打印预览。 该框架将处理用于打印和文档预览打印循环。

视图处理滚动条的消息[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)并[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 您可以实现滚动条消息处理在这些函数中，也可以使用`CView`派生的类[CScrollView](../../mfc/reference/cscrollview-class.md)来为您处理滚动。

除了`CScrollView`，Microsoft 基础类库提供了九个派生自其他类`CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允许使用的文档-视图体系结构与树、 列表和 rich edit 控件的视图。

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，在对话框控件中显示数据库记录的视图。

- [CEditView](../../mfc/reference/ceditview-class.md)，提供了一个简单的多行文本编辑器的视图。 可以使用`CEditView`对象作为一个对话框，以及上一个文档的视图中的控件。

- [CFormView](../../mfc/reference/cformview-class.md)，包含对话框控件和基于对话框模板资源的可滚动视图。

- [CListView](../../mfc/reference/clistview-class.md)，允许使用的文档-视图体系结构与列表控件的视图。

- [CRecordView](../../mfc/reference/crecordview-class.md)，在对话框控件中显示数据库记录的视图。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允许使用的文档-视图体系结构使用丰富的编辑控件的视图。

- [CScrollView](../../mfc/reference/cscrollview-class.md)，自动提供滚动支持一个视图。

- [CTreeView](../../mfc/reference/ctreeview-class.md)，允许使用的文档-视图体系结构与树控件的视图。

`CView`类还具有一个名为派生的实现类`CPreviewView`，用于框架执行打印预览。 此类为唯一的打印预览窗口中，如工具栏、 单或双页面预览功能提供支持和缩放的，扩大预览的图像。 无需调用或重写任何`CPreviewView`的成员函数，除非你想要实现您自己的界面为打印预览 （例如，如果您想要支持在打印预览模式下编辑）。 有关使用的详细信息`CView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)并[打印](../../mfc/printing.md)。 此外，请参阅[技术注意 30](../../mfc/tn030-customizing-printing-and-print-preview.md)有关自定义打印预览的详细信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cview"></a>  CView::CView

构造 `CView` 对象。

```
CView();
```

### <a name="remarks"></a>备注

创建新的框架窗口或拆分窗口时，框架将调用构造函数。 重写[OnInitialUpdate](#oninitialupdate)成员函数以初始化视图后附加文档。

##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting

调用此函数的重写从[OnPreparePrinting](#onprepareprinting)调用打印对话框并创建打印机设备上下文。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。

### <a name="return-value"></a>返回值

如果可以开始打印或打印预览; 非零值如果操作已取消，则为 0。

### <a name="remarks"></a>备注

此函数的行为取决于是否正在调用它的打印或打印预览 (由指定`m_bPreview`的成员*pInfo*参数)。 如果打印文件时，此函数将调用打印对话框中，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的*pInfo*指向; 用户已关闭对话框的后，该函数将创建打印机设备上下文上设置基于在对话框中指定的用户，并返回通过此设备上下文*pInfo*参数。 此设备上下文用于打印文档。

如果文件正处于预览状态，此函数将创建使用当前的打印机设置; 是打印机设备上下文此设备上下文用于在预览期间模拟打印机。

##  <a name="getdocument"></a>  CView::GetDocument

调用此函数可获得到视图的文档的指针。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>返回值

一个指向[CDocument](../../mfc/reference/cdocument-class.md)与视图关联的对象。 如果该视图未附加到文档为 NULL。

### <a name="remarks"></a>备注

这样，您可以调用文档的成员函数。

##  <a name="isselected"></a>  CView::IsSelected

由框架调用以检查是否选择了指定的文档项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>参数

*pDocItem*<br/>
指向所测试的文档项目。

### <a name="return-value"></a>返回值

如果指定的文档项处于选中状态，非零值否则为 0。

### <a name="remarks"></a>备注

此函数的默认实现返回 FALSE。 如果要实现选择使用重写此函数[CDocItem](../../mfc/reference/cdocitem-class.md)对象。 如果您的视图包含 OLE 项，必须重写此函数。

##  <a name="onactivateframe"></a>  CView::OnActivateFrame

包含视图的框架窗口被激活或停用时由框架调用。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>参数

*nState*<br/>
指定是否在框架窗口正在激活或停用。 它可以是下列值之一：

- 正在停用 WA_INACTIVE 框架窗口。

- WA_ACTIVE 框架窗口正在激活通过某种方法不是鼠标单击 （例如，通过选择窗口的键盘界面使用）。

- 通过单击鼠标激活的 WA_CLICKACTIVE 框架窗口

*pFrameWnd*<br/>
指向要激活的框架窗口的指针。

### <a name="remarks"></a>备注

如果你想要执行特殊处理激活或停用与视图关联的框架窗口时，重写此成员函数。 例如， [CFormView](../../mfc/reference/cformview-class.md)执行此重写时它将保存并还原具有焦点的控件。

##  <a name="onactivateview"></a>  CView::OnActivateView

激活或停用视图时，由框架调用。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>参数

*bActivate*<br/>
指示是否视图处于激活或停用。

*pActivateView*<br/>
指向正在激活的视图对象。

*pDeactiveView*<br/>
指向正在停用的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现将焦点设置到正在激活的视图。 如果你想要执行特殊处理激活或停用视图时，重写此函数。 例如，如果你想要提供特殊的非活动视图区分开来的活动视图的可视提示，则会检查*bActivate*参数并相应地更新视图的外观。

*PActivateView*并*pDeactiveView*参数指向在同一个视图，如果应用程序的主框架窗口激活活动视图中进行任何更改 — 例如，如果要将焦点传输从另一个应用程序，而不是从一个视图到另一个应用程序中或在 MDI 子窗口之间切换时。 如果需要这允许视图来重新实现其调色板。

这些参数存在差异时[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)称为具有的视图的不同于什么[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)将返回。 发生这种情况最常使用拆分窗口。

##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting

在调用 `OnPreparePrinting` 之后，由框架在打印或打印预览作业开始时调用。

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以分配专用于打印的任何 GDI 资源，例如笔或字体。 选择到设备上下文中的 GDI 对象[OnPrint](#onprint)每个页面的使用它们的成员函数。 如果要使用相同的视图对象执行屏幕显示和打印，请为每个显示所需的 GDI 资源使用单独的变量；这样做可以在打印期间更新屏幕。

你也可以使用此函数根据打印机设备上下文的属性执行初始化。 例如，打印文档所需的页面数可能取决于用户在“打印”对话框中指定的设置（例如页面长度）。 在这种情况下，不能指定文档长度，以[OnPreparePrinting](#onprepareprinting)成员函数，其中您平常; 你必须等待，直到已根据对话框设置创建了打印机设备上下文。 [OnBeginPrinting](#onbeginprinting)是第一个可重写函数，可提供访问权限[CDC](../../mfc/reference/cdc-class.md)表示打印机设备上下文，因此你可以从此函数设置文档长度的对象。 请注意，如果此时还不指定文档长度，打印预览期间将不会显示滚动条。

##  <a name="ondragenter"></a>  CView::OnDragEnter

当鼠标首次进入放置目标窗口的非滚动区域，由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)拖入该视图的拖放区域。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*点*<br/>
当前鼠标相对于客户端区域视图的位置。

### <a name="return-value"></a>返回值

从 DROPEFFECT 值的枚举类型，指示如果用户在此位置删除该对象会发生的拖放的类型。 拖放类型通常取决于所指示的当前密钥状态*dwKeyState*。 Keystates DROPEFFECT 值的标准映射为：

- 在此窗口中，不能删除 DROPEFFECT_NONE 数据对象。

- 有关 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 创建对象和其服务器之间的链接。

- 有关 MK_CONTROL DROPEFFECT_COPY 创建已删除对象的副本。

- 有关 MK_ALT DROPEFFECT_MOVE 创建已删除的对象和删除原始对象的副本。 这通常是默认放置效果，在该视图可以接受此数据对象。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回 DROPEFFECT_NONE。

重写此函数可用于未来调用准备[OnDragOver](#ondragover)成员函数。 应在这一次以便以后用于检索此数据对象中所需的任何数据`OnDragOver`成员函数。 此外应在此时间为提供用户可视反馈更新视图。 有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondragleave"></a>  CView::OnDragLeave

由框架在拖动操作过程时调用该窗口的鼠标移出有效放置区域。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>备注

如果当前视图需要清理过程中所执行任何操作来重写此函数[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)调用，例如虽然拖动并删除了对象中删除任何视觉用户反馈.

##  <a name="ondragover"></a>  CView::OnDragOver

由框架调用拖动操作期间当鼠标移到放置目标窗口上。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖放目标上方。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*点*<br/>
当前的鼠标位置相对于视图的客户端区域。

### <a name="return-value"></a>返回值

从 DROPEFFECT 值的枚举类型，指示如果用户在此位置删除该对象会发生的拖放的类型。 拖放类型通常取决于当前密钥状态所示*dwKeyState*。 Keystates DROPEFFECT 值的标准映射为：

- 在此窗口中，不能删除 DROPEFFECT_NONE 数据对象。

- 有关 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 创建对象和其服务器之间的链接。

- 有关 MK_CONTROL DROPEFFECT_COPY 创建已删除对象的副本。

- 有关 MK_ALT DROPEFFECT_MOVE 创建已删除的对象和删除原始对象的副本。 这通常是默认放置效果，在该视图可以接受的数据对象。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回 DROPEFFECT_NONE。

重写此函数可拖动操作过程中为提供用户可视反馈。 由于连续调用此函数时，它所包含的任何代码应优化尽可能多地。 有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondragscroll"></a>  CView::OnDragScroll

由框架调用之前调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)来确定点是否在滚动区域内。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*点*<br/>
包含以像素为单位，相对于屏幕光标的位置。

### <a name="return-value"></a>返回值

从 DROPEFFECT 值的枚举类型，指示如果用户在此位置删除该对象会发生的拖放的类型。 拖放类型通常取决于所指示的当前密钥状态*dwKeyState*。 Keystates DROPEFFECT 值的标准映射为：

- 在此窗口中，不能删除 DROPEFFECT_NONE 数据对象。

- 有关 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 创建对象和其服务器之间的链接。

- 有关 MK_CONTROL DROPEFFECT_COPY 创建已删除对象的副本。

- 有关 MK_ALT DROPEFFECT_MOVE 创建已删除的对象和删除原始对象的副本。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或目标视图中不存在。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>备注

当你想要为此事件提供特殊行为时，重写此函数。 将光标拖到默认滚动区域内的每个窗口的边框时，默认实现自动滚动 windows。有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondraw"></a>  Cview:: Ondraw

由框架调用以呈现文档的图像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向设备上下文以用于呈现文档的图像。

### <a name="remarks"></a>备注

框架调用此函数以执行屏幕显示、 打印和打印预览中，并且每种情况下传递不同的设备上下文。 没有默认实现。

必须重写此函数可显示文档的视图。 您可以使用图形设备接口 (GDI) 调用[CDC](../../mfc/reference/cdc-class.md)指向对象*pDC*参数。 可以选择 GDI 资源，例如笔或字体，设备上下文中绘制之前和之后然后取消选择它们。 通常绘制代码可以是独立于设备;也就是说，它不需要什么样的设备已显示的图像的信息。

若要优化绘图，请调用[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)要找出是否将绘制给定的矩形的设备上下文的成员函数。 如果你需要区分普通屏幕显示和打印，则调用[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)设备上下文的成员函数。

##  <a name="ondrop"></a>  CView::OnDrop

当用户的有效放置目标上释放的数据对象时由框架调用。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>参数

pDataObject * 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)放入拖放目标。

*dropEffect*<br/>
用户已请求放置效果。

- DROPEFFECT_COPY 创建要删除的数据对象的副本。

- DROPEFFECT_MOVE 移动到当前的鼠标位置的数据对象。

- DROPEFFECT_LINK 创建数据对象和其服务器之间的链接。

*点*<br/>
当前的鼠标位置相对于视图的客户端区域。

### <a name="return-value"></a>返回值

如果删除成功，则非零值否则为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作，并返回 FALSE。

重写此函数可实现到视图的工作区的 OLE 拖放效果。 可以通过检查数据对象*pDataObject*对于剪贴板数据格式和数据删除在指定的点。

> [!NOTE]
>  框架不调用此函数的重写是否[OnDropEx](#ondropex)此视图类中。

##  <a name="ondropex"></a>  CView::OnDropEx

当用户的有效放置目标上释放的数据对象时由框架调用。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)放入拖放目标。

*dropDefault*<br/>
用户选择基于当前的关键状态的默认拖放操作效果。 它可能是 DROPEFFECT_NONE。 放置效果备注部分所述。

*下拉列表*<br/>
放置源支持拖放效果的列表。 可以使用的按位 OR 组合放置效果值 ( **&#124;**) 操作。 放置效果备注部分所述。

*点*<br/>
当前的鼠标位置相对于视图的客户端区域。

### <a name="return-value"></a>返回值

由于在指定的位置删除尝试而导致的放效果*点*。 这必须是所指示的值之一*dropEffectList*。 放置效果备注部分所述。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回虚拟值 (-1) 以指示应调用框架[OnDrop](#ondrop)处理程序。

重写此函数可实现的鼠标右键拖放效果。 右侧的鼠标按钮拖放功能通常会释放鼠标右键时显示选择菜单。

重写`OnDropEx`应该查询右侧的鼠标按钮。 您可以调用[GetKeyState](https://msdn.microsoft.com/library/windows/desktop/ms646301)或将从右侧的鼠标按钮状态存储在[OnDragEnter](#ondragenter)处理程序。

- 如果鼠标右键已关闭，重写应显示一个弹出菜单，其中提供了通过拖放源支持放置效果。

   - 检查*下拉列表*来确定支持的拖放源放置效果。 使弹出菜单上的这些操作。

   - 使用[SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem)若要设置的默认操作基于*dropDefault*。

   - 最后，需要从弹出菜单的用户选择所指示的操作。

- 如果正确的鼠标左键未按下，重写应处理这与标准的删除请求。 使用中指定的放效果*dropDefault*。 或者，重写可返回虚拟值 (-1) 若要指示`OnDrop`将处理此删除操作。

使用*pDataObject*检查`COleDataObject`对于剪贴板数据格式和数据删除在指定的点。

放置效果描述与拖放操作相关联的操作。 请参阅下面放置效果的列表：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或目标中不存在。

设置默认菜单命令的详细信息，请参阅[SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) Windows SDK 中并[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此卷中。

##  <a name="onendprinting"></a>  CView::OnEndPrinting

打印或预览文档后，由框架调用。

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数可释放分配的任何 GDI 资源[OnBeginPrinting](#onbeginprinting)成员函数。

##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview

在用户退出打印预览模式时，由框架调用。

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。

*点*<br/>
上次在预览模式下显示的页面上指定的点。

*pView*<br/>
指向用于预览的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现调用[OnEndPrinting](#onendprinting)成员函数，并还原到之前打印预览状态的主框架窗口开始。 重写此函数以执行特殊处理终止预览模式时。 例如，如果你想要保留文档中的用户的位置，从预览模式切换到正常的显示模式时，您可以滚动到所描述的位置*点*参数和`m_nCurPage`成员`CPrintInfo`结构的*pInfo*参数指向。

始终调用基类版本的`OnEndPrintPreview`通过重写，通常在该函数的末尾。

##  <a name="oninitialupdate"></a>  Cview:: Oninitialupdate

该视图首次附加到文档中之后, 但在最初显示的视图之前由框架调用。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现调用[OnUpdate](#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示*lHint*参数，NULL 表示*pHint*参数)。 重写此函数以执行任何需要有关文档的信息的一次性初始化。 例如，如果你的应用程序具有固定大小的文档，您可以使用此函数来初始化视图的滚动限制基于文档大小。 如果你的应用程序支持大小可变的文档，请使用[OnUpdate](#onupdate)更新滚动限制每次文档发生更改。

##  <a name="onpreparedc"></a>  CView::OnPrepareDC

由框架之前调用[OnDraw](#ondraw)调用成员函数是用于屏幕显示和之前[OnPrint](#onprint)打印或打印预览期间的每个页调用成员函数。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向设备上下文以用于呈现文档的图像。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构，描述当前打印作业，如果`OnPrepareDC`打印或打印预览，则为调用`m_nCurPage`成员指定要打印的页。 此参数为 NULL，如果`OnPrepareDC`正在调用是用于屏幕显示。

### <a name="remarks"></a>备注

如果是用于屏幕显示调用该函数时，此函数的默认实现将没有任何影响。 但是，此函数中重写派生类，如[CScrollView](../../mfc/reference/cscrollview-class.md)，以调整属性的设备上下文中; 因此，您应始终调用基类实现重写的开头。

如果针对打印调用该函数，则默认实现将检查中存储的页信息*pInfo*参数。 如果尚未指定文档的长度，`OnPrepareDC`假定要长的一页的文档和打印一页后停止打印循环。 该函数通过设置停止打印循环`m_bContinuePrinting`为 FALSE 的结构的成员。

重写`OnPrepareDC`任何原因如下：

- 若要根据指定的页调整设备上下文的特性。 例如，如果您需要设置映射模式或设备上下文的其他特征，这样做此函数中。

- 若要执行打印时分页。 通常情况下开始打印，使用时指定文档的长度[OnPreparePrinting](#onprepareprinting)成员函数。 但是，如果您不知道提前时间文档 （例如，当从数据库中打印未知的记录数目），重写`OnPrepareDC`要测试时要打印文档的结尾。 如果没有更多要打印的文档，设置`m_bContinuePrinting`的成员`CPrintInfo`结构为 FALSE。

- 若要将转义码发送到的页的基础上的打印机。 若要发送从转义码`OnPrepareDC`，调用`Escape`成员函数*pDC*参数。

调用基类版本的`OnPrepareDC`重写的开头。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting

打印或预览文档之前由框架调用。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。

### <a name="return-value"></a>返回值

非零值，开始打印;如果打印作业已取消，则为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。

必须重写此函数可启用打印和打印预览。 调用[DoPreparePrinting](#doprepareprinting)成员函数，并向其传递*pInfo*参数，然后返回其返回值;`DoPreparePrinting`显示打印对话框中，并创建打印机设备上下文。 如果你想要初始化的默认值以外的值与打印对话框中，将值分配到的成员*pInfo*。 例如，如果您知道文档的长度，将值传递给[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成员函数*pInfo*之前调用`DoPreparePrinting`。 此值显示在收件人： 框中的打印对话框中的范围部分。

`DoPreparePrinting` 不显示预览作业的打印对话框。 如果你想要绕过打印作业的打印对话框，检查`m_bPreview`的成员*pInfo*是 FALSE，然后将其设置为 TRUE 之前将其传递给`DoPreparePrinting`; 将它重置为 FALSE 之后。

如果您需要执行初始化，则需要访问`CDC`对象，表示打印机设备上下文 （例如，如果需要之前需要了解的页大小指定文档的长度），重写`OnBeginPrinting`成员函数。

如果你想要设置的值`m_nNumPreviewPages`或`m_strPageDesc`的成员*pInfo*参数，执行此操作之后调用`DoPreparePrinting`。 `DoPreparePrinting`成员函数集`m_nNumPreviewPages`到应用程序中找到的值。INI 文件，并设置`m_strPageDesc`为其默认值。

### <a name="example"></a>示例

  重写`OnPreparePrinting`，并调用`DoPreparePrinting`重写，因此该框架将显示打印对话框并为你创建打印机 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果您知道该文档包含多少页，在中设置最大页`OnPreparePrinting`之前调用`DoPreparePrinting`。 框架将显示在"收件人"框中的打印对话框中的最大页面数。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>  CView::OnPrint

由框架调用以打印或预览文档的页。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向`CPrintInfo`描述当前打印作业的结构。

### <a name="remarks"></a>备注

对于每个正在打印的页，框架将调用此函数调用后立即[OnPrepareDC](#onpreparedc)成员函数。 指定要打印的页面`m_nCurPage`的成员[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的*pInfo*指向。 默认实现调用[OnDraw](#ondraw)成员函数并将其传递打印机设备上下文。

由于以下原因，重写此函数：

- 若要允许打印多页文档。 呈现只有对应于当前正在打印的页的文档的部分。 如果您使用的`OnDraw`用于执行呈现，可以调整视区原点，这样就可以打印的文档相应部分。

- 要打印的图像看起来与屏幕图像不同 （即，如果你的应用程序不是所见即所得）。 而不是传递到设备上下文的打印机`OnDraw`，使用设备上下文来呈现使用属性不会在屏幕上显示的图像。

     如果你需要有关不是用于屏幕显示使用的打印的 GDI 资源，它们选入设备上下文在绘制之前和之后取消选择它们。 应在分配这些 GDI 资源[OnBeginPrinting](#onbeginprinting)且已在发布[OnEndPrinting](#onendprinting)。

- 若要实现页眉或页脚。 您仍然可以使用`OnDraw`就可完成呈现的限制可以在打印的区域。

请注意，`m_rectDraw`的成员*pInfo*参数描述中的逻辑单元的页的可打印区域。

不要调用`OnPrepareDC`中的重写`OnPrint`; 框架将调用`OnPrepareDC`自动之前调用`OnPrint`。

### <a name="example"></a>示例

下面是一个重写框架`OnPrint`函数：

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

有关其他示例，请参阅[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

##  <a name="onscroll"></a>  CView::OnScroll

由框架调用以确定是否滚动可能。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*nScrollCode*<br/>
指示用户的滚动条代码的滚动请求。 此参数由两个部分组成： 确定的水平滚动发生的类型，低序位字节和高位字节，用于确定的垂直滚动发生类型：

- SB_BOTTOM 滚动到底部。

- SB_LINEDOWN 滚动行下移一行。

- SB_LINEUP 滚动行上移一行。

- 向下 SB_PAGEDOWN 滚动一页。

- 向上 SB_PAGEUP 滚动一页。

- SB_THUMBTRACK 拖动滚动框指定位置。 在指定当前位置*nPos*。

- SB_TOP 滚动到顶部。

*nPos*<br/>
如果滚动条代码 SB_THUMBTRACK;，包含滚动框的当前位置否则不使用它。 具体取决于初始滚动范围*nPos*可以是负数，并且应强制转换为**int**如有必要。

*bDoScroll*<br/>
确定是否应实际执行操作的指定滚动操作。 如果为 TRUE，然后滚动应发生;如果为 FALSE，不应发生滚动。

### <a name="return-value"></a>返回值

如果*bDoScroll*为 TRUE 并且实际上滚动视图，然后返回非零值; 否则为 0。 如果*bDoScroll*为 FALSE，则返回值，则返回如果*bDoScroll*是 TRUE，即使实际上不执行操作的滚动。

### <a name="remarks"></a>备注

在一种情况下由框架调用此函数*bDoScroll*视图收到滚动条消息时设置为 TRUE。 在这种情况下，你应实际滚动视图。 在其他情况下调用此函数与*bDoScroll*时滚动实际的发生之前，OLE 项最初拖到拖放目标的自动滚动区域设置为 FALSE。 在这种情况下，你应实际滚动视图。

##  <a name="onscrollby"></a>  CView::OnScrollBy

当用户查看该文档，既可以在其中通过将 OLE 项针对视图的当前边框操作垂直或水平滚动条的存在视图的区域时由框架调用。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*sizeScroll*<br/>
水平和垂直方向上滚动的像素数。

*bDoScroll*<br/>
确定是否滚动视图的执行。 如果为 TRUE，然后滚动发生;如果为 FALSE，然后滚动不会发生。

### <a name="return-value"></a>返回值

如果视图能够滚动; 非零值否则为 0。

### <a name="remarks"></a>备注

在派生类中此方法检查以确定视图是否为可在用户请求，然后更新新区域，如有必要的方向滚动。 自动调用此函数[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)并[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)来执行实际的滚动请求。

此方法的默认实现不会更改视图，但如果未调用，该视图将滚动中`CScrollView`-派生的类。

如果文档的宽度或高度超过 32767 像素，过去的 32767 滚动将失败，因为`OnScrollBy`调用使用了无效*sizeScroll*参数。

##  <a name="onupdate"></a>  CView::OnUpdate

后已修改，视图的文档，则由框架调用调用此函数[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) ，并允许视图以更新其显示效果以反映这些修改。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指向的视图，修改文档，则所有视图都将更新为 null。

*lHint*<br/>
包含有关所做的修改信息。

*pHint*<br/>
指的对象存储有关所做的修改的信息。

### <a name="remarks"></a>备注

它还会调用的默认实现[OnInitialUpdate](#oninitialupdate)。 使整个客户端区域，接收到的下一个 WM_PAINT 消息时将其标记为绘制无效，默认实现。 如果你想要更新将映射到文档的修改后的部分的区域，重写此函数。 若要执行此操作必须通过使用提示参数的修改有关的信息。

若要使用*lHint*，定义特殊的提示值、 通常是一个位掩码或枚举的类型，并且具有传递这些值之一的文档。 若要使用*pHint*，提示从派生类[CObject](../../mfc/reference/cobject-class.md)并且具有重写时，将指针传递到提示的对象; 该文档`OnUpdate`，使用[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)若要确定提示对象的运行时类型的成员函数。

通常不应执行任何直接从绘制`OnUpdate`。 相反，确定设备坐标，描述需要更新; 的区域的矩形传递到此矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 这将导致绘制下一次时[WM_PAINT](/windows/desktop/gdi/wm-paint)接收消息。

如果*lHint*为 0 并*pHint*为 NULL，该文档已发送泛型更新通知。 如果视图接收用于执行常规更新通知，或者如果它不能对提示进行解码，它应使其整个工作区。

## <a name="see-also"></a>请参阅

[MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)
