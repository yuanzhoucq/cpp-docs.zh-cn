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
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373206"
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
|[C查看：CView](#cview)|构造 `CView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CView：:D准备打印](#doprepareprinting)|显示打印对话框并创建打印机设备上下文;重写`OnPreparePrinting`成员函数时调用。|
|[CView：获取文档](#getdocument)|返回与视图关联的文档。|
|[CView：已选定](#isselected)|测试是否选择了文档项。 OLE 支持是必需的。|
|[C查看：：OnDragEnter](#ondragenter)|首次将项目拖入视图的拖放区域时调用。|
|[C查看：：OnDragLeave](#ondragleave)|当拖动的项目离开视图的拖放区域时调用。|
|[C查看：：在德拉格弗](#ondragover)|当项目拖动到视图的拖放区域时调用。|
|[CView：：OnDragScroll](#ondragscroll)|调用 以确定光标是否拖入窗口的滚动区域。|
|[C查看：上投](#ondrop)|当项目已放入视图的拖放区域时调用，默认处理程序。|
|[C查看：：OnDropEx](#ondropex)|当项已放入视图的主处理程序的拖放区域时调用。|
|[CView：初始更新](#oninitialupdate)|视图首次附加到文档后调用。|
|[C查看：：在准备DC](#onpreparedc)|在要求`OnDraw`成员函数进行屏幕显示之前调用，或者在`OnPrint`打印或打印预览时调用成员函数。|
|[C查看：：打开](#onscroll)|当 OLE 项拖出视图边界时调用。|
|[CView：OnScrollby](#onscrollby)|滚动包含活动就地 OLE 项的视图时调用。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CView：打开激活帧](#onactivateframe)|当包含视图的框架窗口激活或停用时调用。|
|[C查看：打开激活视图](#onactivateview)|激活视图时调用。|
|[CView::OnBeginPrinting](#onbeginprinting)|打印作业开始时调用;重写以分配图形设备接口 （GDI） 资源。|
|[C查看：在画上](#ondraw)|调用 以呈现文档的图像以进行屏幕显示、打印或打印预览。 需要实施。|
|[C查看：：结束打印](#onendprinting)|打印作业结束时调用;重写以取消分配 GDI 资源。|
|[CView：：结束打印预览](#onendprintpreview)|退出预览模式时调用。|
|[C查看：：准备打印](#onprepareprinting)|在打印或预览文档之前调用;覆盖以初始化打印对话框。|
|[C查看：：在打印](#onprint)|已调用以打印或预览文档的页面。|
|[CView：打开更新](#onupdate)|已调用以通知视图其文档已被修改。|

## <a name="remarks"></a>备注

视图附加到文档，充当文档和用户之间的中介：视图在屏幕上或打印机上呈现文档的图像，并将用户输入解释为对文档的操作。

视图是框架窗口的子级。 多个视图可以共享帧窗口，例如拆分器窗口。 视图类、框架窗口类和文档类之间的关系由`CDocTemplate`对象建立。 当用户打开新窗口或拆分现有窗口时，框架将构造一个新视图并将其附加到文档。

视图只能附加到一个文档，但文档可以同时附加多个视图-例如，如果文档显示在拆分器窗口中或多个文档接口 （MDI） 应用程序中的多个子窗口中）。 您的应用程序可以支持给定文档类型的不同类型的视图;但是，您的应用程序可以支持指定文档类型的视图。例如，字处理程序可能同时提供文档的完整文本视图和仅显示节标题的大纲视图。 如果使用拆分器窗口，则可以将这些不同类型的视图放置在单独的框架窗口或单个框架窗口的单独窗格中。

视图可能负责处理几种不同类型的输入，例如键盘输入、鼠标输入或通过拖放输入，以及菜单、工具栏或滚动条中的命令。 视图接收由其框架窗口转发的命令。 如果视图不处理给定命令，它将该命令转发到其关联的文档。 与所有命令目标一样，视图通过消息映射处理消息。

视图负责显示和修改文档的数据，但不负责存储文档的数据。 本文档向视图提供有关其数据的必要详细信息。 您可以让视图直接访问文档的数据成员，也可以在文档类中提供要调用的视图类的成员函数。

当文档的数据发生更改时，负责更改的视图通常调用文档的[CDocument：updateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函数，该函数通过为每个视图调用`OnUpdate`成员函数来通知所有其他视图。 默认实现`OnUpdate`使视图的整个工作区无效。 您可以重写它，使其仅使映射到文档修改部分的工作区区域无效。

要使用`CView`，从派生类并实现`OnDraw`成员函数来执行屏幕显示。 您还可以使用`OnDraw`执行打印和打印预览。 框架处理用于打印和预览文档的打印循环。

视图处理具有[CWnd：：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd：：onVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数的滚动条消息。 您可以在这些函数中实现滚动条消息处理，也可以使用`CView`派生类[CScrollView](../../mfc/reference/cscrollview-class.md)为您处理滚动。

此外`CScrollView`，微软基础类库提供来自`CView`以下九个其他类：

- [CCtrlView](../../mfc/reference/cctrlview-class.md)，一个允许使用具有树、列表和丰富编辑控件的文档视图体系结构的视图.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，一个在对话框控件中显示数据库记录的视图。

- [CEditView](../../mfc/reference/ceditview-class.md)，一个提供简单多行文本编辑器的视图。 可以将`CEditView`对象用作对话框中的控件以及文档上的视图。

- [CFormView](../../mfc/reference/cformview-class.md)，一个可滚动的视图，其中包含对话框控件，并且基于对话框模板资源。

- [CListView](../../mfc/reference/clistview-class.md)，一种允许使用带有列表控件的文档视图体系结构的视图.

- [CRecordView](../../mfc/reference/crecordview-class.md)，一个在对话框控件中显示数据库记录的视图。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)，一个允许使用具有丰富编辑控件的文档视图体系结构的视图.

- [CScrollView](../../mfc/reference/cscrollview-class.md)，自动提供滚动支持的视图。

- [CTreeView](../../mfc/reference/ctreeview-class.md)，一个允许使用带有树控件的文档视图体系结构的视图.

该`CView`类还有一个名为 的`CPreviewView`派生实现类，该类由框架用于执行打印预览。 此类支持打印预览窗口独有的要素，例如工具栏、单页或双页预览和缩放，即放大预览图像。 除非要实现自己的界面以进行打印预览（例如`CPreviewView`，如果要支持在打印预览模式下进行编辑），否则无需调用或重写任何成员函数。 有关使用`CView`的详细信息，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[打印](../../mfc/printing.md)。 此外，有关自定义打印预览的更多详细信息[，请参阅技术说明 30。](../../mfc/tn030-customizing-printing-and-print-preview.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>C查看：CView

构造 `CView` 对象。

```
CView();
```

### <a name="remarks"></a>备注

创建新帧窗口或拆分窗口时，框架将调用构造函数。 覆盖[On初始更新](#oninitialupdate)成员函数，在文档附加后初始化视图。

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView：:D准备打印

从[OnPreparePrinting](#onprepareprinting)的重写中调用此函数以调用"打印"对话框并创建打印机设备上下文。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="return-value"></a>返回值

如果可以开始打印或打印预览，则非零;如果操作已取消，则为 0。

### <a name="remarks"></a>备注

此功能的行为取决于是调用它进行打印或打印预览（由`m_bPreview`*pInfo*参数的成员指定）。 如果正在打印文件，此函数将使用[cPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构中*pInfo*指向的值调用"打印"对话框;用户关闭对话框后，该函数根据用户在对话框中指定的设置创建打印机设备上下文，并通过*pInfo*参数返回此设备上下文。 此设备上下文用于打印文档。

如果正在预览文件，此函数将使用当前打印机设置创建打印机设备上下文;如果正在预览该文件，则使用当前打印机设置创建打印机设备上下文。此设备上下文用于在预览期间模拟打印机。

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView：获取文档

调用此函数以获取指向视图文档的指针。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向与视图关联的[CDocument](../../mfc/reference/cdocument-class.md)对象的指针。 如果视图未附加到文档，则为 NULL。

### <a name="remarks"></a>备注

这允许您调用文档的成员函数。

## <a name="cviewisselected"></a><a name="isselected"></a>CView：已选定

由框架调用以检查是否选择了指定的文档项。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>参数

*pDocItem*<br/>
指向要测试的文档项。

### <a name="return-value"></a>返回值

如果选择了指定的文档项，则非零;否则 0。

### <a name="remarks"></a>备注

此函数的默认实现返回 FALSE。 如果要使用[CDocItem](../../mfc/reference/cdocitem-class.md)对象实现选择，则重写此函数。 如果视图包含 OLE 项，则必须重写此函数。

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView：打开激活帧

当包含视图的框架窗口被激活或停用时，框架调用。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>参数

*n州*<br/>
指定帧窗口是激活还是停用。 可以为下列值之一：

- WA_INACTIVE框架窗口正在停用。

- WA_ACTIVE框架窗口正在通过单击鼠标以外的方法激活（例如，通过使用键盘界面选择窗口）。

- WA_CLICKACTIVE鼠标单击激活框架窗口

*pFramewnd*<br/>
指向要激活的帧窗口的指针。

### <a name="remarks"></a>备注

如果要在与视图关联的帧窗口激活或停用时执行特殊处理，则覆盖此成员函数。 例如[，CFormView](../../mfc/reference/cformview-class.md)在保存和恢复具有焦点的控件时执行此重写。

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>C查看：打开激活视图

当视图激活或停用时，由框架调用。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>参数

*b 激活*<br/>
指示视图是正在激活还是停用。

*p 激活视图*<br/>
指向正在激活的视图对象。

*p 主动视图*<br/>
指向正在停用的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现将焦点设置为要激活的视图。 如果要在激活或停用视图时执行特殊处理，则重写此函数。 例如，如果要提供特殊视觉提示，将活动视图和非活动视图区分开来，则检查*bActivate*参数并相应地更新视图的外观。

如果激活应用程序的主框架窗口且活动视图没有变化 *，pActivateView*和*pDeactiveView*参数指向同一视图，例如，如果焦点从另一个应用程序传输到此应用程序，而不是在应用程序中从一个视图传输到另一个视图或在 MDI 子窗口之间切换时。 这允许视图根据需要重新实现其调色板。

当[CFrameWnd：setActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)调用视图时，这些参数会有所不同，该视图与[CFrameWnd：：getActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)返回的视图不同。 这通常发生在拆分器窗口。

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>C查看：：开始打印

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
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以分配专用于打印的任何 GDI 资源，例如笔或字体。 在设备上下文中从 [OnPrint](#onprint) 成员函数内为每个使用 GDI 对象的页面选择这些对象。 如果要使用相同的视图对象执行屏幕显示和打印，请为每个显示所需的 GDI 资源使用单独的变量；这样做可以在打印期间更新屏幕。

你也可以使用此函数根据打印机设备上下文的属性执行初始化。 例如，打印文档所需的页面数可能取决于用户在“打印”对话框中指定的设置（例如页面长度）。 在这种情况下，你不能在 [OnPreparePrinting](#onprepareprinting) 成员函数中指定文档长度（这是一般情况下的做法）；你必须等待片刻，直到根据对话框设置创建了打印机设备上下文为止。 [OnBeginPrinting](#onbeginprinting) 是第一个允许你访问 [CDC](../../mfc/reference/cdc-class.md) 对象（表示打印机设备上下文）的可重写函数，因此，你可以从此函数设置文档长度。 请注意，如果此时还不指定文档长度，打印预览期间将不会显示滚动条。

## <a name="cviewondragenter"></a><a name="ondragenter"></a>C查看：：OnDragEnter

当鼠标首次进入放置目标窗口的非滚动区域时，由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向被拖入视图的放置区域的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
相对于视图的工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的值，指示用户在此位置放置对象时将发生的放置类型。 丢弃的类型通常取决于*dwKeyState*指示的当前密钥状态。 键状态到 DROPEFFECT 值的标准映射是：

- DROPEFFECT_NONE数据对象不能在此窗口中删除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在对象及其服务器之间创建链接。

- DROPEFFECT_COPYMK_CONTROL 创建已删除对象的副本。

- DROPEFFECT_MOVEMK_ALT 创建已删除对象的副本并删除原始对象。 当视图可以接受此数据对象时，这通常是默认放置效果。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回DROPEFFECT_NONE。

重写此函数，以便为将来对[OnDragOver](#ondragover)成员函数的调用做好准备。 此时应检索数据对象所需的任何数据，以便以后在成员函数中使用`OnDragOver`。 此时还应更新视图，以便向用户提供可视反馈。 有关详细信息，请参阅文章 OLE[拖放：实现放置目标](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondragleave"></a><a name="ondragleave"></a>C查看：：OnDragLeave

当鼠标移出该窗口的有效放置区域时，框架在拖动操作期间调用。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>备注

如果当前视图需要清理[在 OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)调用期间采取的任何操作，例如在拖动和删除对象时删除任何可视用户反馈，请覆盖此函数。

## <a name="cviewondragover"></a><a name="ondragover"></a>C查看：：在德拉格弗

当鼠标移到放置目标窗口时，框架在拖动操作期间调用。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向被拖动到放置目标上的[COleData 对象](../../mfc/reference/coledataobject-class.md)。

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的值，指示用户在此位置放置对象时将发生的放置类型。 丢弃的类型通常取决于*dwKeyState*指示的当前密钥状态。 键状态到 DROPEFFECT 值的标准映射是：

- DROPEFFECT_NONE数据对象不能在此窗口中删除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在对象及其服务器之间创建链接。

- DROPEFFECT_COPYMK_CONTROL 创建已删除对象的副本。

- DROPEFFECT_MOVEMK_ALT 创建已删除对象的副本并删除原始对象。 当视图可以接受数据对象时，这通常是默认放置效果。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回DROPEFFECT_NONE。

重写此函数，在拖动操作期间为用户提供视觉反馈。 由于此函数是连续调用的，因此应尽可能优化其中包含的任何代码。 有关详细信息，请参阅文章 OLE[拖放：实现放置目标](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView：：OnDragScroll

在调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)之前由框架调用，以确定该点是否位于滚动区域中。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*德基州*<br/>
包含修改器键的状态。 这是以下任意数量的组合：MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*点*<br/>
包含光标相对于屏幕的位置（以像素为单位）。

### <a name="return-value"></a>返回值

DROPEFFECT 枚举类型中的值，指示用户在此位置放置对象时将发生的放置类型。 丢弃的类型通常取决于*dwKeyState*指示的当前密钥状态。 键状态到 DROPEFFECT 值的标准映射是：

- DROPEFFECT_NONE数据对象不能在此窗口中删除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在对象及其服务器之间创建链接。

- DROPEFFECT_COPYMK_CONTROL 创建已删除对象的副本。

- DROPEFFECT_MOVEMK_ALT 创建已删除对象的副本并删除原始对象。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或发生在目标视图中。

有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>备注

如果要为此事件提供特殊行为，请重写此函数。 当光标拖动到每个窗口边框内的默认滚动区域时，默认实现会自动滚动窗口。 有关详细信息，请参阅文章 OLE[拖放：实现放置目标](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondraw"></a><a name="ondraw"></a>C查看：在画上

由框架调用以呈现文档的图像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现文档图像的设备上下文。

### <a name="remarks"></a>备注

框架调用此函数以执行屏幕显示、打印和打印预览，并在每种情况下传递不同的设备上下文。 没有默认实现。

必须重写此函数才能显示文档的视图。 您可以使用*pDC*参数指向的[CDC](../../mfc/reference/cdc-class.md)对象进行图形设备接口 （GDI） 调用。 在绘制之前，您可以在设备上下文中选择 GDI 资源（如笔或字体），然后在绘制后取消选择这些资源。 通常，您的绘图代码可以独立于设备;也就是说，它不需要有关显示映像的设备类型的信息。

要优化绘图，请致电设备上下文的[Rect可见](../../mfc/reference/cdc-class.md#rectvisible)成员函数，以找出是否将绘制给定矩形。 如果需要区分正常屏幕显示和打印，请致电设备上下文的[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)成员功能。

## <a name="cviewondrop"></a><a name="ondrop"></a>C查看：上投

当用户在有效的放置目标上释放数据对象时，由框架调用。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>参数

"pDataObject] 指向丢弃目标中的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*滴效果*<br/>
用户请求的放置效果。

- DROPEFFECT_COPY创建要删除的数据对象的副本。

- DROPEFFECT_MOVE将数据对象移动到当前鼠标位置。

- DROPEFFECT_LINK 在数据对象及其服务器之间创建链接。

*点*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

如果下降成功，则为非零;否则 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作，并返回 FALSE。

重写此函数以实现 OLE 丢弃到视图的工作区的效果。 数据对象可以通过*pDataObject*检查剪贴板数据格式和丢弃在指定点的数据。

> [!NOTE]
> 如果此视图类中存在对[OnDropEx](#ondropex)的重写，则框架不会调用此函数。

## <a name="cviewondropex"></a><a name="ondropex"></a>C查看：：OnDropEx

当用户在有效的放置目标上释放数据对象时，由框架调用。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

*pDataObject*<br/>
指向丢弃目标中的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*丢弃默认*<br/>
用户根据当前键状态为默认放置操作选择的效果。 它可能是DROPEFFECT_NONE。 "注释"部分将讨论放置效果。

*下拉列表*<br/>
放置源支持的放置效果的列表。 可以使用位或 （ **&#124;**） 操作组合放置效果值。 "注释"部分将讨论放置效果。

*点*<br/>
相对于视图工作区的当前鼠标位置。

### <a name="return-value"></a>返回值

从*点指定的位置*的放置尝试产生的放置效果。 这必须是*dropEffectList*指示的值之一。 "注释"部分将讨论放置效果。

### <a name="remarks"></a>备注

默认实现是不执行任何操作并返回虚拟值 （-1），以指示框架应调用[OnDrop](#ondrop)处理程序。

重写此函数以实现鼠标右键拖放的效果。 右鼠标按钮拖放通常在释放鼠标右键时显示选项菜单。

对鼠标右`OnDropEx`键的重写应查询。 您可以调用[GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate)或从[OnDragEnter](#ondragenter)处理程序存储鼠标右键状态。

- 如果鼠标右键已关闭，则覆盖应显示一个弹出菜单，该菜单提供放置源支持的放置效果。

  - 检查*放置列表*以确定放置源支持的放置效果。 在弹出式菜单上仅启用这些操作。

  - 使用[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)设置基于*删除默认*的默认操作。

  - 最后，从弹出式菜单中执行用户选择指示的操作。

- 如果鼠标右键未关闭，则重写应作为标准放置请求处理。 使用*在下拉默认*中指定的放置效果。 或者，重写可以返回虚拟值 （-1），以指示`OnDrop`将处理此放置操作。

使用*pDataObject*检查`COleDataObject`用于剪贴板的数据格式和在指定点丢弃的数据。

放置效果描述与放置操作关联的操作。 请参阅以下放置效果列表：

- DROPEFFECT_NONE不允许掉下。

- DROPEFFECT_COPY将执行复制操作。

- DROPEFFECT_MOVE将执行移动操作。

- DROPEFFECT_LINK将建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或发生在目标中。

有关设置默认菜单命令的详细信息，请参阅 Windows SDK 中的[SetMenu 默认项目](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)，以及[CMenu：获取此卷中的SafeHmenu。](../../mfc/reference/cmenu-class.md#getsafehmenu)

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>C查看：：结束打印

在打印或预览文档后由框架调用。

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数以释放您在[OnBeginPrinting](#onbeginprinting)成员函数中分配的任何 GDI 资源。

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView：：结束打印预览

当用户退出打印预览模式时由框架调用。

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
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

*点*<br/>
指定上次在预览模式下显示的页面上的点。

*pView*<br/>
指向用于预览的视图对象。

### <a name="remarks"></a>备注

此函数的默认实现调用[OnEndPrinting](#onendprinting)成员函数，并将主框架窗口还原到打印预览开始之前的状态。 覆盖此函数以在预览模式终止时执行特殊处理。 例如，如果要在从预览模式切换到正常显示模式时维护用户在文档中的位置，则可以滚动到*点*参数和`m_nCurPage`*pInfo*参数指向`CPrintInfo`的结构成员描述的位置。

始终从重写调用 的`OnEndPrintPreview`基类版本，通常在函数的末尾。

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView：初始更新

视图首次附加到文档后由框架调用，但在最初显示视图之前。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>备注

此函数的默认实现调用[OnUpdate](#onupdate)成员函数，没有提示信息（即，使用*lHint*参数的默认值 0，对于*pHint*参数使用 NULL）。 重写此函数以执行任何需要有关文档信息的一次性初始化。 例如，如果应用程序具有固定大小的文档，则可以使用此函数根据文档大小初始化视图的滚动限制。 如果应用程序支持可变大小的文档，请使用[OnUpdate](#onupdate)在每次文档更改时更新滚动限制。

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>C查看：：在准备DC

在要求[OnDraw](#ondraw)成员函数进行屏幕显示之前，在打印或打印预览期间为每个页面调用[OnPrint](#onprint)成员函数之前，由框架调用。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于呈现文档图像的设备上下文。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构，该结构描述当前打印作业`OnPrepareDC`（如果需要打印或打印预览）;成员`m_nCurPage`指定要打印的页面。 如果`OnPrepareDC`为屏幕显示调用，则此参数为 NULL。

### <a name="remarks"></a>备注

如果为屏幕显示调用该函数，则此函数的默认实现将不执行任何操作。 但是，在派生类（如[CScrollView）](../../mfc/reference/cscrollview-class.md)中重写此函数，以调整设备上下文的属性;因此，应始终在重写开始时调用基类实现。

如果调用函数进行打印，则默认实现将检查存储在*pInfo*参数中的页面信息。 如果未指定文档的长度，则`OnPrepareDC`假定文档为一页长，并在打印一页后停止打印循环。 该函数通过将结构`m_bContinuePrinting`的成员设置为 FALSE 来停止打印循环。

由于`OnPrepareDC`以下任何原因，重写：

- 根据需要调整指定页面的设备上下文的属性。 例如，如果需要设置映射模式或设备上下文的其他特征，则在此函数中执行此操作。

- 执行打印时分。 通常，使用[OnPreparePrinting](#onprepareprinting)成员功能指定打印开始时的文档长度。 但是，如果您事先不知道文档有多长（例如，从数据库中打印不确定数量的记录时），则重写`OnPrepareDC`以在打印文档时测试文档的末尾。 如果没有要打印的文档，则将`m_bContinuePrinting``CPrintInfo`结构的成员设置为 FALSE。

- 逐页向打印机发送转义代码。 要从`OnPrepareDC`发送转义代码，`Escape`请调用*pDC*参数的成员函数。

在重写开始时调用 的`OnPrepareDC`基类版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>C查看：：准备打印

在打印或预览文档之前由框架调用。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
指向描述当前打印作业的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 结构。

### <a name="return-value"></a>返回值

开始打印的非零;如果打印作业已取消，则为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。

您必须重写此函数才能启用打印和打印预览。 调用[DoPreparePrinting](#doprepareprinting)成员函数，传递*pInfo*参数，然后返回其返回值;`DoPreparePrinting`显示"打印"对话框并创建打印机设备上下文。 如果要使用默认值以外的值初始化"打印"对话框，请将值分配给*pInfo*的成员。 例如，如果您知道文档的长度，则在调用`DoPreparePrinting`之前将值传递给*pInfo*的[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成员函数。 此值显示在"打印"对话框的"范围"部分的"到："框中。

`DoPreparePrinting`不显示预览作业的"打印"对话框。 如果要绕过打印作业的"打印"对话框，请检查`m_bPreview`*pInfo*的成员是否为 FALSE，然后将其设置为 TRUE，然后再将其传递给`DoPreparePrinting`;之后将其重置为 FALSE。

如果需要执行需要访问表示打印机设备上下文`CDC`的对象的初始化（例如，如果需要在指定文档长度之前知道页面大小），则重写`OnBeginPrinting`成员函数。

如果要设置*pInfo*参数`DoPreparePrinting``m_nNumPreviewPages`或`m_strPageDesc`成员的值，请在调用 后执行此操作。 成员`DoPreparePrinting`函数将设置`m_nNumPreviewPages`到应用程序 中找到的值。INI 文件并`m_strPageDesc`设置为其默认值。

### <a name="example"></a>示例

  从`OnPreparePrinting`覆盖覆盖`DoPreparePrinting`和调用，以便框架将显示一个打印对话框，并为您创建打印机 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果知道文档包含多少页，则在调用`OnPreparePrinting``DoPreparePrinting`之前在 中设置最大页。 框架将在"打印"对话框的"to"框中显示最大页码。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>C查看：：在打印

由框架调用以打印或预览文档的页面。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向打印机设备上下文。

*pInfo*<br/>
指向描述当前`CPrintInfo`打印作业的结构。

### <a name="remarks"></a>备注

对于要打印的每个页面，框架在调用[OnPrepareDC](#onpreparedc)成员函数后立即调用此函数。 正在打印的页面由`m_nCurPage`*pInfo*指向的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的成员指定。 默认实现调用[OnDraw](#ondraw)成员函数并传递打印机设备上下文。

出于以下任何原因，重写此函数：

- 允许打印多页文档。 仅呈现与当前打印的页面对应的文档部分。 如果使用`OnDraw`执行渲染，则可以调整视口原点，以便只打印文档的适当部分。

- 使打印的图像看起来与屏幕图像不同（即，如果应用程序不是 WYSIWYG）。 而不是将打印机设备上下文传递给`OnDraw`，使用设备上下文使用屏幕上未显示的属性渲染图像。

   如果需要不使用的 GDI 资源进行打印，请在绘制之前将其选择到设备上下文中，然后取消选择它们。 这些 GDI 资源应在[OnBeginPrinting 中](#onbeginprinting)分配，并在[OnEndPrinting 中](#onendprinting)发布。

- 实现标题或页脚。 您仍可以通过`OnDraw`限制可以打印的区域来执行渲染。

请注意`m_rectDraw`*，pInfo*参数的成员以逻辑单位描述页面的可打印区域。

不要调用`OnPrepareDC`您的覆盖`OnPrint`。框架在调用`OnPrepareDC`之前会自动`OnPrint`调用 。

### <a name="example"></a>示例

以下是重写`OnPrint`函数的骨架：

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

有关另一个示例，请参阅[CRichEditView：:PintInsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

## <a name="cviewonscroll"></a><a name="onscroll"></a>C查看：：打开

由框架调用以确定是否可能滚动。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*nScrollCode*<br/>
指示用户滚动请求的滚动条代码。 此参数由两部分组成：一个低阶字节，它确定水平发生的滚动类型;高阶字节，确定垂直发生的滚动类型：

- SB_BOTTOM滚动到底部。

- SB_LINEDOWN向下滚动一行。

- SB_LINEUP向上滚动一行。

- SB_PAGEDOWN向下滚动一页。

- SB_PAGEUP向上滚动一页。

- SB_THUMBTRACK将滚动框拖动到指定位置。 当前位置在*nPos*中指定。

- SB_TOP滚动到顶部。

*nPos*<br/>
如果滚动条代码SB_THUMBTRACK，则包含当前滚动框位置;否则，它不使用。 根据初始滚动范围 *，nPos*可能是负的，如有必要，应强制转换为**int。**

*b多卷*<br/>
确定是否实际执行指定的滚动操作。 如果为 TRUE，则应进行滚动;如果 FALSE，则不应进行滚动。

### <a name="return-value"></a>返回值

如果*bDoScroll*为 TRUE，并且视图实际上已滚动，则返回非零;否则 0。 如果*bDoScroll*是 FALSE，则返回如果*bDoScroll*为 TRUE 时返回的值，即使您实际上没有进行滚动。

### <a name="remarks"></a>备注

在一种情况下，当视图收到滚动条消息时，框架将此函数调用 *，其中 bDoScroll*设置为 TRUE。 在这种情况下，您实际上应该滚动视图。 在其他情况下，当 OLE 项最初在实际滚动之前拖入放置目标的自动滚动区域时，使用*bDoScroll*将此函数设置为 FALSE 时调用此函数。 在这种情况下，您实际上不应滚动视图。

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView：OnScrollby

当用户查看文档当前视图以外的区域时，由框架调用，通过根据视图的当前边框拖动 OLE 项或操作垂直或水平滚动条。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*大小滚动*<br/>
水平和垂直滚动的像素数。

*b多卷*<br/>
确定是否进行视图滚动。 如果为 TRUE，则进行滚动;如果为 TRUE，则进行滚动。如果 FALSE，则不会发生滚动。

### <a name="return-value"></a>返回值

如果视图能够滚动，则非零;否则 0。

### <a name="remarks"></a>备注

在派生类中，此方法检查视图是否按用户请求的方向滚动，然后在必要时更新新区域。 [CWnd：：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd：onVScroll](../../mfc/reference/cwnd-class.md#onvscroll)自动调用此功能，以执行实际滚动请求。

此方法的默认实现不会更改视图，但如果不调用视图，视图将不会在`CScrollView`派生类中滚动。

如果文档宽度或高度超过 32767 像素，则滚动超过 32767 将`OnScrollBy`失败，因为调用的大小*滚动*参数无效。

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView：打开更新

修改视图文档后由框架调用;此函数由[CDocument：：UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)调用，并允许视图更新其显示以反映这些修改。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指向修改文档的视图，如果要更新所有视图，则指向 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储有关修改信息的对象。

### <a name="remarks"></a>备注

它也称为[On初始更新](#oninitialupdate)的默认实现。 默认实现使整个工作区无效，在收到下一WM_PAINT消息时将其标记为绘制。 如果只想更新映射到文档修改部分的区域，请覆盖此函数。 为此，您必须使用提示参数传递有关修改的信息。

要使用*lHint*，请定义特殊提示值（通常是位掩码或枚举类型），并让文档传递这些值之一。 要使用*pHint*，请从[CObject](../../mfc/reference/cobject-class.md)派生提示类，并让文档传递指向提示对象的指针;例如，请从 CObject 派生提示类。重写`OnUpdate`时，使用[CObject：isKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数来确定提示对象的运行时类型。

通常，不应直接从 执行任何绘图`OnUpdate`。 相反，确定在设备坐标中描述需要更新的区域的矩形;将此矩形传递给[CWnd：：无效重新 。](../../mfc/reference/cwnd-class.md#invalidaterect) 这将导致下次收到[WM_PAINT](/windows/win32/gdi/wm-paint)消息时发生绘制。

如果*lHint*为*0，pHint*为 NULL，则文档已发送通用更新通知。 如果视图收到泛型更新通知，或者无法解码提示，则应将其整个工作区无效。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)
