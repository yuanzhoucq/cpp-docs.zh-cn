---
title: CView 类
ms.date: 11/04/2016
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
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855436"
---
# <a name="cview-class"></a>CView 类

提供用户定义视图类的基本功能。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CView：： CView](#cview)|构造 `CView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CView：:D oPreparePrinting](#doprepareprinting)|显示 "打印" 对话框并创建打印机设备上下文;重写 `OnPreparePrinting` 成员函数时调用。|
|[CView：： GetDocument](#getdocument)|返回与视图关联的文档。|
|[CView：： IsSelected](#isselected)|测试是否选择了文档项。 OLE 支持需要。|
|[CView：： System.windows.uielement.ondragenter](#ondragenter)|当首次将项拖动到视图的拖放区域时调用。|
|[CView：： System.windows.uielement.ondragleave](#ondragleave)|在拖动项离开视图的拖放区域时调用。|
|[CView：： System.windows.uielement.ondragover](#ondragover)|当将某个项拖动到视图的拖放区域上时调用。|
|[CView：： OnDragScroll](#ondragscroll)|调用以确定光标是否拖到窗口的滚动区域。|
|[CView：： System.windows.uielement.ondrop](#ondrop)|在将项拖放到视图的拖放区域（默认处理程序）时调用。|
|[CView：： OnDropEx](#ondropex)|在将项拖放到视图的拖放区域（主处理程序）时调用。|
|[CView：： OnInitialUpdate](#oninitialupdate)|在第一次将视图附加到文档后调用。|
|[CView：： OnPrepareDC](#onpreparedc)|在为屏幕显示调用 `OnDraw` 成员函数之前调用，或为打印或打印预览调用 `OnPrint` 成员函数。|
|[CView：： OnScroll](#onscroll)|在将 OLE 项拖至视图边框之外时调用。|
|[CView：： OnScrollBy](#onscrollby)|当滚动包含活动的就地 OLE 项的视图时调用。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CView：： OnActivateFrame](#onactivateframe)|当激活或停用包含视图的框架窗口时调用。|
|[CView：： OnActivateView](#onactivateview)|当激活视图时调用。|
|[CView：： OnBeginPrinting](#onbeginprinting)|当打印作业开始时调用;重写以分配图形设备接口（GDI）资源。|
|[CView：： OnDraw](#ondraw)|调用以呈现文档的图像以进行屏幕显示、打印或打印预览。 需要实现。|
|[CView：： OnEndPrinting](#onendprinting)|当打印作业结束时调用;重写以释放 GDI 资源。|
|[CView：： OnEndPrintPreview](#onendprintpreview)|在退出预览模式时调用。|
|[CView：： OnPreparePrinting](#onprepareprinting)|在打印或预览文档之前调用。重写以初始化 "打印" 对话框。|
|[CView：： OnPrint](#onprint)|调用以打印或预览文档页。|
|[CView：： OnUpdate](#onupdate)|调用以通知视图其文档已修改。|

## <a name="remarks"></a>备注

视图附加到文档并充当文档和用户之间的中介：视图在屏幕或打印机上呈现文档的图像，并将用户输入解释为文档上的操作。

视图是框架窗口的子级。 与拆分窗口的情况一样，多个视图可以共享框架窗口。 视图类、框架窗口类和文档类之间的关系由 `CDocTemplate` 对象建立。 当用户打开一个新窗口或拆分现有窗口时，框架将构造一个新视图，并将其附加到文档。

一个视图只能附加到一个文档，但一个文档可以同时附加到它的多个视图，例如，如果文档显示在拆分窗口中或多个文档界面（MDI）应用程序的多个子窗口中。 您的应用程序可以支持给定文档类型的不同类型的视图;例如，字处理程序可能同时提供文档的完整文本视图和只显示节标题的大纲视图。 如果使用拆分窗口，这些不同类型的视图可以放置在单独的框架窗口中，也可以放在单个框架窗口的单独窗格中。

视图可能负责处理多种不同类型的输入，例如键盘输入、通过拖放的鼠标输入或输入，以及来自菜单、工具栏或滚动条的命令。 视图接收其框架窗口转发的命令。 如果视图未处理给定的命令，则会将命令转发到其关联文档。 与所有命令目标一样，视图通过消息映射来处理消息。

视图负责显示和修改文档的数据，但不负责存储文档。 文档向视图提供有关其数据的必要详细信息。 您可以让视图直接访问文档的数据成员，或者可以在 document 类中提供成员函数以供视图类调用。

当文档的数据更改时，负责更改的视图通常会调用文档的[CDocument：： UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函数，该函数通过为每个视图调用 `OnUpdate` 成员函数来通知所有其他视图。 `OnUpdate` 的默认实现将使视图的整个工作区失效。 您可以将其重写为仅使那些映射到文档的已修改部分的工作区区域无效。

若要使用 `CView`，请从中派生一个类，并实现 `OnDraw` 成员函数以执行屏幕显示。 你还可以使用 `OnDraw` 来执行打印和打印预览。 框架处理打印循环来打印和预览文档。

视图使用[cwnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[Cwnd：： OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数处理滚动条消息。 可以在这些函数中实现滚动条消息处理，也可以使用 `CView` 派生类[CScrollView](../../mfc/reference/cscrollview-class.md)来处理滚动。

除了 `CScrollView`之外，Microsoft 基础类库还提供从 `CView`派生的九个其他类：

- [CCtrlView](../../mfc/reference/cctrlview-class.md)，一种允许将文档视图结构与树、列表和丰富的编辑控件一起使用的视图。

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，在对话框控件中显示数据库记录的视图。

- [CEditView](../../mfc/reference/ceditview-class.md)，提供简单多行文本编辑器的视图。 您可以使用 `CEditView` 对象作为对话框中的控件以及文档上的视图。

- [CFormView](../../mfc/reference/cformview-class.md)：包含对话框控件并基于对话框模板资源的可滚动视图。

- [CListView](../../mfc/reference/clistview-class.md)：允许将文档视图结构与列表控件一起使用的视图。

- [CRecordView](../../mfc/reference/crecordview-class.md)，在对话框控件中显示数据库记录的视图。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)，一种视图，允许使用具有丰富编辑控件的文档视图结构。

- [CScrollView](../../mfc/reference/cscrollview-class.md)，此视图自动提供滚动支持。

- [CTreeView](../../mfc/reference/ctreeview-class.md)，一种允许将文档视图结构与树控件一起使用的视图。

`CView` 类还具有一个名为 `CPreviewView`的派生实现类，框架使用此类来执行打印预览。 此类提供了对打印预览窗口独有功能的支持，如工具栏、单页或双页预览以及缩放，即放大预览的图像。 不需要调用或重写 `CPreviewView`的任何成员函数，除非你想要实现自己的打印预览界面（例如，如果你想要支持在 "打印预览" 模式下编辑）。 有关使用 `CView`的详细信息，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[打印](../../mfc/printing.md)。 此外，请参阅[技术说明 30](../../mfc/tn030-customizing-printing-and-print-preview.md) ，详细了解自定义打印预览。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cview"></a>CView：： CView

构造 `CView` 对象。

```
CView();
```

### <a name="remarks"></a>备注

创建新的框架窗口或拆分窗口时，框架会调用构造函数。 重写[OnInitialUpdate](#oninitialupdate)成员函数以在附加文档后初始化视图。

##  <a name="doprepareprinting"></a>CView：:D oPreparePrinting

从[OnPreparePrinting](#onprepareprinting)的重写调用此函数以调用 "打印" 对话框，并创建打印机设备上下文。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>parameters

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="return-value"></a>返回值

如果可以开始打印或打印预览，则为非零值;如果操作已取消，则为0。

### <a name="remarks"></a>备注

此函数的行为取决于是否要为打印或打印预览调用它（由*pInfo*参数的 `m_bPreview` 成员指定）。 如果正在打印文件，此函数将使用*pInfo*指向的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构中的值调用 "打印" 对话框;用户关闭对话框后，该函数将根据用户在对话框中指定的设置创建打印机设备上下文，并通过*pInfo*参数返回此设备上下文。 此设备上下文用于打印文档。

如果正在预览文件，此函数将使用当前打印机设置创建打印机设备上下文;此设备上下文用于在预览期间模拟打印机。

##  <a name="getdocument"></a>CView：： GetDocument

调用此函数可获取指向视图文档的指针。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向与视图关联的[CDocument](../../mfc/reference/cdocument-class.md)对象的指针。 如果视图未附加到文档，则为 NULL。

### <a name="remarks"></a>备注

这使你可以调用文档的成员函数。

##  <a name="isselected"></a>CView：： IsSelected

由框架调用，用于检查是否选择了指定的文档项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>parameters

*pDocItem*<br/>
指向要测试的文档项。

### <a name="return-value"></a>返回值

如果选定了指定的文档项，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数的默认实现返回 FALSE。 如果使用[CDocItem](../../mfc/reference/cdocitem-class.md)对象实现选择，则重写此函数。 如果视图包含 OLE 项，则必须重写此函数。

##  <a name="onactivateframe"></a>CView：： OnActivateFrame

当激活或停用包含视图的框架窗口时由框架调用。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>parameters

*nState*<br/>
指定是否正在激活或停用框架窗口。 可以为下列值之一：

- WA_INACTIVE 框架窗口处于停用状态。

- WA_ACTIVE 通过鼠标单击之外的某种方法激活框架窗口（例如，通过使用键盘界面选择窗口）。

- WA_CLICKACTIVE 通过鼠标单击激活框架窗口

*pFrameWnd*<br/>
指向要激活的框架窗口的指针。

### <a name="remarks"></a>备注

如果要在激活或停用视图关联的框架窗口时执行特殊处理，请重写此成员函数。 例如， [CFormView](../../mfc/reference/cformview-class.md)在保存和还原具有焦点的控件时执行此重写。

##  <a name="onactivateview"></a>CView：： OnActivateView

当激活或停用视图时由框架调用。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>parameters

*bActivate*<br/>
指示是否正在激活或停用视图。

*pActivateView*<br/>
指向正在激活的视图对象。

*pDeactiveView*<br/>
指向要停用的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现将焦点设置为要激活的视图。 如果要在激活或停用视图时执行特殊处理，请重写此函数。 例如，如果想要提供从非活动视图中区分活动视图的特殊视觉提示，可以检查*bActivate*参数并相应地更新视图的外观。

如果在活动视图中激活应用程序的主框架窗口，而不更改活动视图，则*pActivateView*和*pDeactiveView*参数指向同一视图，例如，如果将焦点从另一个应用程序传输到此应用程序，而不是从应用程序中的一个视图切换到另一个视图，则在切换到 MDI 子窗口时。 这允许视图根据需要重新实现其调色板。

当使用与[CFrameWnd：： GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)返回的视图不同的视图调用[CFrameWnd：： SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)时，这些参数是不同的。 最常见的情况是拆分窗口。

##  <a name="onbeginprinting"></a>CView：： OnBeginPrinting

在调用 `OnPreparePrinting` 之后，由框架在打印或打印预览作业开始时调用。

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以分配专用于打印的任何 GDI 资源，例如笔或字体。 在设备上下文中从 [OnPrint](#onprint) 成员函数内为每个使用 GDI 对象的页面选择这些对象。 如果要使用相同的视图对象执行屏幕显示和打印，请为每个显示所需的 GDI 资源使用单独的变量；这样做可以在打印期间更新屏幕。

你也可以使用此函数根据打印机设备上下文的属性执行初始化。 例如，打印文档所需的页面数可能取决于用户在“打印”对话框中指定的设置（例如页面长度）。 在这种情况下，你不能在 [OnPreparePrinting](#onprepareprinting) 成员函数中指定文档长度（这是一般情况下的做法）；你必须等待片刻，直到根据对话框设置创建了打印机设备上下文为止。 [OnBeginPrinting](#onbeginprinting) 是第一个允许你访问 [CDC](../../mfc/reference/cdc-class.md) 对象（表示打印机设备上下文）的可重写函数，因此，你可以从此函数设置文档长度。 请注意，如果此时还不指定文档长度，打印预览期间将不会显示滚动条。

##  <a name="ondragenter"></a>CView：： System.windows.uielement.ondragenter

当鼠标第一次进入拖放目标窗口的非滚动区域时由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>parameters

*pDataObject*<br/>
指向要拖动到视图拖放区域中的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： "MK_CONTROL"、"MK_SHIFT"、"MK_ALT"、"MK_LBUTTON"、"MK_MBUTTON" 和 "MK_RBUTTON"。

*情况*<br/>
相对于视图的工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的一个值，指示当用户在此位置删除对象时将发生的放置类型。 删除的类型通常取决于*dwKeyState*指示的当前密钥状态。 Keystates 到 DROPEFFECT 值的标准映射为：

- DROPEFFECT_NONE 无法在此窗口中删除数据对象。

- MK_CONTROL &#124;的 DROPEFFECT_LINK MK_SHIFT 会在对象与其服务器之间创建链接。

- MK_CONTROL 的 DROPEFFECT_COPY 创建已删除对象的副本。

- MK_ALT 的 DROPEFFECT_MOVE 创建已删除对象的副本，并删除原始对象。 当视图可以接受此数据对象时，这通常是默认的放置效果。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回 DROPEFFECT_NONE。

重写此函数以准备将来调用[system.windows.uielement.ondragover](#ondragover)成员函数。 此时应检索数据对象所需的任何数据，以便以后在 `OnDragOver` 成员函数中使用。 此时还应更新该视图以向用户提供视觉反馈。 有关详细信息，请参阅[OLE 拖放：实现放置目标一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondragleave"></a>CView：： System.windows.uielement.ondragleave

在拖动操作过程中，当鼠标移出该窗口的有效放置区域时由框架调用。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>备注

如果当前视图需要清理在[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)调用期间执行的任何操作（例如，在拖动和删除对象时删除任何视觉对象），则重写此函数。

##  <a name="ondragover"></a>CView：： System.windows.uielement.ondragover

在拖动操作过程中，当鼠标移到拖放目标窗口上时由框架调用。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>parameters

*pDataObject*<br/>
指向要拖动到拖放目标上的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： "MK_CONTROL"、"MK_SHIFT"、"MK_ALT"、"MK_LBUTTON"、"MK_MBUTTON" 和 "MK_RBUTTON"。

*情况*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的一个值，指示当用户在此位置删除对象时将发生的放置类型。 删除的类型通常取决于当前的键状态，如*dwKeyState*所示。 Keystates 到 DROPEFFECT 值的标准映射为：

- DROPEFFECT_NONE 无法在此窗口中删除数据对象。

- MK_CONTROL &#124;的 DROPEFFECT_LINK MK_SHIFT 会在对象与其服务器之间创建链接。

- MK_CONTROL 的 DROPEFFECT_COPY 创建已删除对象的副本。

- MK_ALT 的 DROPEFFECT_MOVE 创建已删除对象的副本，并删除原始对象。 当视图可以接受数据对象时，这通常是默认的放置效果。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回 DROPEFFECT_NONE。

重写此函数以在拖动操作过程中为用户提供视觉反馈。 由于此函数是连续调用的，因此，其中包含的任何代码应尽可能优化。 有关详细信息，请参阅[OLE 拖放：实现放置目标一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondragscroll"></a>CView：： OnDragScroll

在调用[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)之前由框架调用，以确定点是否在滚动区域中。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>parameters

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合： "MK_CONTROL"、"MK_SHIFT"、"MK_ALT"、"MK_LBUTTON"、"MK_MBUTTON" 和 "MK_RBUTTON"。

*情况*<br/>
包含光标相对于屏幕的位置（以像素为单位）。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的一个值，指示当用户在此位置删除对象时将发生的放置类型。 删除的类型通常取决于*dwKeyState*指示的当前密钥状态。 Keystates 到 DROPEFFECT 值的标准映射为：

- DROPEFFECT_NONE 无法在此窗口中删除数据对象。

- MK_CONTROL &#124;的 DROPEFFECT_LINK MK_SHIFT 会在对象与其服务器之间创建链接。

- MK_CONTROL 的 DROPEFFECT_COPY 创建已删除对象的副本。

- MK_ALT 的 DROPEFFECT_MOVE 创建已删除对象的副本，并删除原始对象。

- DROPEFFECT_SCROLL 指示将发生拖动滚动操作，或者在目标视图中发生拖动滚动操作。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

如果要为此事件提供特殊行为，请重写此函数。 当光标拖入每个窗口边框内的默认滚动区域时，默认实现会自动滚动窗口。 有关详细信息，请参阅[OLE 拖放：实现放置目标一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondraw"></a>CView：： OnDraw

由框架调用以呈现文档的图像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向要用于呈现文档图像的设备上下文。

### <a name="remarks"></a>备注

框架调用此函数以执行屏幕显示、打印和打印预览，并在每种情况下传递不同的设备上下文。 没有默认实现。

必须重写此函数才能显示文档视图。 您可以使用*pDC*参数指向的[CDC](../../mfc/reference/cdc-class.md)对象进行图形设备接口（GDI）调用。 在绘制之前，可以在设备上下文中选择 GDI 资源，例如笔或字体，然后取消选择它们。 您的绘图代码通常可以与设备无关;也就是说，它不需要有关显示图像的设备类型的信息。

若要优化绘图，请调用设备上下文的[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)成员函数，以确定是否绘制给定的矩形。 如果需要区分普通屏幕显示和打印，请调用设备上下文的[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)成员函数。

##  <a name="ondrop"></a>CView：： System.windows.uielement.ondrop

当用户通过有效的拖放目标释放数据对象时，由框架调用。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>parameters

' pDataObject * 指向拖放到拖放目标的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dropEffect*<br/>
用户已请求的放置效果。

- DROPEFFECT_COPY 创建要删除的数据对象的副本。

- DROPEFFECT_MOVE 将数据对象移动到当前鼠标位置。

- DROPEFFECT_LINK 在数据对象与其服务器之间创建链接。

*情况*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

如果删除成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

默认实现不执行任何操作并返回 FALSE。

重写此函数以实现 OLE 拖放到视图的工作区中的效果。 数据对象可以通过*pDataObject*检查剪贴板数据格式，并在指定点处丢弃数据。

> [!NOTE]
>  如果此视图类中存在对[OnDropEx](#ondropex)的重写，则框架不会调用此函数。

##  <a name="ondropex"></a>CView：： OnDropEx

当用户通过有效的拖放目标释放数据对象时，由框架调用。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>parameters

*pDataObject*<br/>
指向拖放到拖放目标的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dropDefault*<br/>
用户根据当前键状态选择的默认删除操作的效果。 可能 DROPEFFECT_NONE。 "备注" 部分讨论了 Drop 效果。

*dropList*<br/>
放置源所支持的放置效果的列表。 可以使用按位 "或" （ **&#124;** ）运算组合删除效果值。 "备注" 部分讨论了 Drop 效果。

*情况*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

由于放置尝试在*点*指定的位置导致的放置效果。 此值必须是*dropEffectList*指示的值之一。 "备注" 部分讨论了 Drop 效果。

### <a name="remarks"></a>备注

默认实现是不执行任何操作，并返回一个虚拟值（-1），以指示框架应调用[system.windows.uielement.ondrop](#ondrop)处理程序。

重写此函数以实现鼠标右键拖放的效果。 鼠标右键拖放通常会在释放鼠标右键时显示选项的菜单。

您的 `OnDropEx` 重写应查询鼠标右键。 可以从[system.windows.uielement.ondragenter](#ondragenter)处理程序调用[GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate)或存储鼠标右键的鼠标按钮状态。

- 如果鼠标右键处于关闭状态，则重写应显示一个弹出菜单，该菜单提供放置源所支持的放置效果。

   - 检查*dropList*以确定放置源支持的放置效果。 仅在弹出菜单中启用这些操作。

   - 使用[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)基于*dropDefault*设置默认操作。

   - 最后，执行用户从弹出菜单中选择所指示的操作。

- 如果鼠标右键未关闭，则重写应将其处理为标准放置请求。 使用*dropDefault*中指定的投影效果。 或者，重写可以返回虚值（-1），以指示 `OnDrop` 将处理此删除操作。

使用*pDataObject*检查剪贴板数据格式的 `COleDataObject`，并将数据放在指定点上。

Drop 效果描述与删除操作相关联的操作。 请参阅下面的删除效果列表：

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 执行移动操作。

- DROPEFFECT_LINK 将建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示将要发生或在目标中发生拖动滚动操作。

有关设置默认菜单命令的详细信息，请参阅此卷中 Windows SDK 和[CMenu：： GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)中的[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) 。

##  <a name="onendprinting"></a>CView：： OnEndPrinting

在打印或预览文档后由框架调用。

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以释放在[OnBeginPrinting](#onbeginprinting)成员函数中分配的任何 GDI 资源。

##  <a name="onendprintpreview"></a>CView：： OnEndPrintPreview

当用户退出打印预览模式时由框架调用。

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

*情况*<br/>
指定页面上最后以预览模式显示的点。

*pView*<br/>
指向用于预览的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现将调用[OnEndPrinting](#onendprinting)成员函数，并将主框架窗口还原到打印预览开始之前的状态。 当终止预览模式时，重写此函数以执行特殊处理。 例如，如果想要在从预览模式切换到正常显示模式时保持用户在文档中的位置，则可以滚动到*point*参数所描述的位置以及*pInfo*参数指向的 `CPrintInfo` 结构的 `m_nCurPage` 成员。

始终从重写调用 `OnEndPrintPreview` 的基类版本，通常是在函数的末尾。

##  <a name="oninitialupdate"></a>CView：： OnInitialUpdate

在视图第一次附加到文档之后但最初显示视图之前由框架调用。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现调用[OnUpdate](#onupdate)成员函数，该函数不包含提示信息（也就是说，对于*lHint*参数使用默认值0，对*pHint*参数使用 NULL）。 重写此函数以执行需要文档相关信息的任何一次性初始化。 例如，如果应用程序具有固定大小的文档，则可以使用此函数根据文档大小初始化视图的滚动限制。 如果你的应用程序支持可变大小的文档，请使用[OnUpdate](#onupdate)每次更改文档时更新滚动限制。

##  <a name="onpreparedc"></a>CView：： OnPrepareDC

在为屏幕显示调用[OnDraw](#ondraw)成员函数之前和在打印或打印预览过程中为每个页面调用[OnPrint](#onprint)成员函数之前，由框架调用。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向要用于呈现文档图像的设备上下文。

*pInfo*<br/>
指向描述当前打印作业的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构（如果正在为打印或打印预览调用 `OnPrepareDC`）;`m_nCurPage` 成员指定要打印的页面。 如果为屏幕显示调用 `OnPrepareDC`，则此参数为 NULL。

### <a name="remarks"></a>备注

如果调用此函数以进行屏幕显示，则此函数的默认实现不执行任何操作。 但是，在派生类（如[CScrollView](../../mfc/reference/cscrollview-class.md)）中将重写此函数以调整设备上下文的特性;因此，应始终在重写开始时调用基类实现。

如果调用函数进行打印，则默认实现将检查存储在*pInfo*参数中的页信息。 如果尚未指定文档的长度，`OnPrepareDC` 会将文档的长度指定为一页，并在打印一页后停止打印循环。 此函数通过将结构的 `m_bContinuePrinting` 成员设置为 FALSE 来停止打印循环。

出于以下任一原因重写 `OnPrepareDC`：

- 根据需要调整指定页的设备上下文特性。 例如，如果需要设置映射模式或设备上下文的其他特征，请在此函数中执行此操作。

- 执行打印时分页。 通常，使用[OnPreparePrinting](#onprepareprinting)成员函数在打印开始时指定文档的长度。 但是，如果事先不知道文档的时间长度（例如，从数据库打印不确定数量的记录），请在打印文档时重写 `OnPrepareDC` 以测试文档的结尾。 如果没有更多的文档要打印，请将 `CPrintInfo` 结构的 `m_bContinuePrinting` 成员设置为 FALSE。

- 逐页地将转义码发送到打印机。 若要从 `OnPrepareDC`发送转义码，请调用*pDC*参数的 `Escape` 成员函数。

在重写开始时调用 `OnPrepareDC` 的基类版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView：： OnPreparePrinting

在打印或预览文档之前由框架调用。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>parameters

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="return-value"></a>返回值

若要开始打印，则为非零值;如果已取消打印作业，则为0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。

必须重写此函数以启用打印和打印预览。 调用[DoPreparePrinting](#doprepareprinting)成员函数，将*pInfo*参数传递给它，然后返回其返回值;`DoPreparePrinting` 显示 "打印" 对话框，并创建打印机设备上下文。 如果要用除默认值以外的值初始化 "打印" 对话框，请将值分配给*pInfo*的成员。 例如，如果知道文档的长度，请在调用 `DoPreparePrinting`之前将值传递给*pInfo*的[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成员函数。 此值显示在 "打印" 对话框范围部分的 "到：" 框中。

`DoPreparePrinting` 不显示预览作业的 "打印" 对话框。 如果要跳过打印作业的 "打印" 对话框，请检查*pInfo*的 `m_bPreview` 成员是否为 FALSE，然后将其设置为 TRUE，然后将其传递给 `DoPreparePrinting`;以后将其重置为 FALSE。

如果需要执行需要访问表示打印机设备上下文的 `CDC` 对象的初始化（例如，如果在指定文档长度之前需要知道页面大小），请重写 `OnBeginPrinting` 成员函数。

如果要设置*pInfo*参数的 `m_nNumPreviewPages` 或 `m_strPageDesc` 成员的值，请在调用 `DoPreparePrinting`后执行此操作。 `DoPreparePrinting` 成员函数将 `m_nNumPreviewPages` 设置为在应用程序中找到的值。INI 文件，并将 `m_strPageDesc` 设置为其默认值。

### <a name="example"></a>示例

  重写 `OnPreparePrinting` 并从该重写调用 `DoPreparePrinting`，以便框架将显示 "打印" 对话框并为您创建一个打印机 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果知道文档包含多少页，请在调用 `DoPreparePrinting`之前，在 `OnPreparePrinting` 中设置最大页。 框架将在 "打印" 对话框的 "到" 框中显示最大页码。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView：： OnPrint

由框架调用以打印或预览文档页。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前打印作业的 `CPrintInfo` 结构。

### <a name="remarks"></a>备注

对于要打印的每一页，框架将在调用[OnPrepareDC](#onpreparedc)成员函数后立即调用此函数。 要打印的页面由*pInfo*指向的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的 `m_nCurPage` 成员指定。 默认实现调用[OnDraw](#ondraw)成员函数并向其传递打印机设备上下文。

出于以下任一原因重写此函数：

- 允许打印多页文档。 只呈现与当前正在打印的页相对应的文档部分。 如果使用 `OnDraw` 执行呈现，则可以调整视区原点，以便仅打印文档的相应部分。

- 使打印的图像与屏幕图像不同（即，如果应用程序不是 WYSIWYG）。 不要将打印机设备上下文传递到 `OnDraw`，而是使用设备上下文来呈现使用屏幕上未显示的属性的映像。

   如果需要 GDI 资源进行打印，而不是将其用于屏幕显示，请在绘制之前将它们选择到设备上下文中，然后再取消选中它们。 这些 GDI 资源应该在[OnBeginPrinting](#onbeginprinting)中分配并在[OnEndPrinting](#onendprinting)中发布。

- 实现页眉或页脚。 你仍可以使用 `OnDraw` 通过限制其打印区域来进行呈现。

请注意， *pInfo*参数的 `m_rectDraw` 成员以逻辑单元描述页面的可打印区域。

不要在 `OnPrint`的重写中调用 `OnPrepareDC`;在调用 `OnPrint`之前，框架会自动调用 `OnPrepareDC`。

### <a name="example"></a>示例

下面是重写的 `OnPrint` 函数的骨架：

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

有关其他示例，请参阅[CRichEditView：:P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

##  <a name="onscroll"></a>CView：： OnScroll

由框架调用，以确定是否可以进行滚动。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>parameters

*nScrollCode*<br/>
指示用户滚动请求的滚动条代码。 此参数由两部分组成：一个低序位字节，用于确定水平滚动的类型和一个高序位字节，该字节确定垂直发生的滚动类型：

- SB_BOTTOM 向下滚动。

- SB_LINEDOWN 向下滚动一行。

- SB_LINEUP 向上滚动一行。

- SB_PAGEDOWN 向下滚动一页。

- SB_PAGEUP 向上滚动一页。

- SB_THUMBTRACK 将滚动框拖动到指定位置。 当前位置在*nPos*中指定。

- SB_TOP 滚动到顶部。

*nPos*<br/>
如果滚动条代码是 SB_THUMBTRACK，则包含当前滚动框位置;否则，不使用。 根据初始滚动范围， *nPos*可能为负数，并且应在必要时强制转换为**int** 。

*bDoScroll*<br/>
确定是否应实际执行指定的滚动操作。 如果为 TRUE，则应进行滚动;如果为 FALSE，则不会发生滚动。

### <a name="return-value"></a>返回值

如果*bDoScroll*为 TRUE，并且实际滚动视图，则返回非零值;否则为0。 如果*bDoScroll*为 FALSE，则返回在*bDoScroll*为 TRUE 时要返回的值，即使您实际上并不执行滚动操作也是如此。

### <a name="remarks"></a>备注

在一种情况下，此函数由框架调用，在视图收到滚动条消息时， *bDoScroll*设置为 TRUE。 在这种情况下，您应实际滚动视图。 在另一种情况下，当在实际发生滚动之前，OLE 项最初拖动到拖放目标的自动滚动区域中时，将使用*bDoScroll*设置为 FALSE。 在这种情况下，不应实际滚动视图。

##  <a name="onscrollby"></a>CView：： OnScrollBy

当用户通过将 OLE 项拖至视图的当前边框或通过操作垂直或水平滚动条来查看文档当前视图之外的区域时，由框架调用。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>parameters

*sizeScroll*<br/>
水平和垂直滚动的像素数。

*bDoScroll*<br/>
确定是否发生了视图滚动。 如果为 TRUE，则发生滚动;如果为 FALSE，则不发生滚动。

### <a name="return-value"></a>返回值

如果可以滚动视图，则为非零值;否则为0。

### <a name="remarks"></a>备注

在派生类中，此方法检查视图是否可在用户请求的方向上滚动，并在必要时更新新区域。 [CWnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[Cwnd：： OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)会自动调用此函数以执行实际滚动请求。

此方法的默认实现不会更改视图，但如果不调用视图，则视图不会滚动到 `CScrollView`派生的类中。

如果文档宽度或高度超过32767像素，则滚动超过32767将失败，因为使用无效的*sizeScroll*参数调用 `OnScrollBy`。

##  <a name="onupdate"></a>CView：： OnUpdate

在视图的文档已修改后由框架调用;此函数由[CDocument：： UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)调用，并允许视图更新其显示以反映这些修改。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>parameters

*pSender*<br/>
指向修改文档的视图，如果要更新所有视图，则为 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储修改信息的对象。

### <a name="remarks"></a>备注

它也通过[OnInitialUpdate](#oninitialupdate)的默认实现来调用。 默认实现会使整个工作区无效，并将其标记为在收到下一 WM_PAINT 消息时进行绘制。 如果只想更新映射到文档修改部分的区域，请重写此函数。 为此，必须使用提示参数传递有关修改的信息。

若要使用*lHint*，请定义特殊提示值（通常为位掩码或枚举类型），并让文档传递其中一个值。 若要使用*pHint*，请从[CObject](../../mfc/reference/cobject-class.md)派生提示类，并使文档将指针传递到提示对象;重写 `OnUpdate`时，请使用[CObject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数确定提示对象的运行时类型。

通常不应直接从 `OnUpdate`执行任何绘制。 相反，确定在设备坐标中描述需要更新的区域的矩形;将此矩形传递给[CWnd：： InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 这会导致在下次接收到[WM_PAINT](/windows/win32/gdi/wm-paint)消息时进行绘制。

如果*lHint*为0， *pHint*为 NULL，则文档已发送一般更新通知。 如果视图收到一般更新通知，或者无法对提示进行解码，则它应使其整个工作区无效。

## <a name="see-also"></a>另请参阅

[MFC 示例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)
