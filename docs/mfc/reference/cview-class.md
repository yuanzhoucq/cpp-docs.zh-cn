---
title: "CView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 843417508fc43f99b0027873988746d03a7863cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CView::OnDragEnter](#ondragenter)|当某一项第一次拖动到拖放区域的视图时调用。|  
|[CView::OnDragLeave](#ondragleave)|拖动的项离开视图的拖放区域时调用。|  
|[CView::OnDragOver](#ondragover)|当某项拖动到视图的拖放区域上方时调用。|  
|[CView::OnDragScroll](#ondragscroll)|调用以确定是否将光标拖到窗口的滚动区域。|  
|[CView::OnDrop](#ondrop)|当项具有已放入视图，默认处理程序的拖放区域时调用。|  
|[CView::OnDropEx](#ondropex)|当项具有已放入视图中，主处理程序的拖放区域时调用。|  
|[Cview:: Oninitialupdate](#oninitialupdate)|视图首先附加到文档之后调用。|  
|[CView::OnPrepareDC](#onpreparedc)|之前调用`OnDraw`是用于屏幕显示调用成员函数或`OnPrint`为打印或打印预览调用成员函数。|  
|[CView::OnScroll](#onscroll)|当超出视图的边框将 OLE 项时调用。|  
|[CView::OnScrollBy](#onscrollby)|当滚动包含活动的就地 OLE 项的视图时调用。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|当激活或停用包含视图的框架窗口时调用。|  
|[CView::OnActivateView](#onactivateview)|激活视图时调用。|  
|[CView::OnBeginPrinting](#onbeginprinting)|当打印作业开始; 时调用重写以分配图形设备接口 (GDI) 资源。|  
|[类库](#ondraw)|调用以呈现屏幕显示、 打印或打印预览的文档的映像。 所需的实现。|  
|[CView::OnEndPrinting](#onendprinting)|当打印作业结束; 时，调用释放 GDI 资源的替代。|  
|[CView::OnEndPrintPreview](#onendprintpreview)|当退出预览模式时调用。|  
|[CView::OnPreparePrinting](#onprepareprinting)|在打印或预览; 文档之前调用重写以初始化打印对话框。|  
|[CView::OnPrint](#onprint)|调用以打印或预览文档的一页。|  
|[CView::OnUpdate](#onupdate)|调用以通知视图其文档已被修改。|  
  
## <a name="remarks"></a>备注  
 查看附加到文档和充当文档和用户之间的中介： 视图呈现屏幕或打印机上的文档的映像，并将用户输入解释为对文档的操作。  
  
 视图是框架窗口的子级。 多个视图可以共享框架窗口，如下所示拆分窗口的大小写。 视图类，框架窗口类，并文档类之间的关系由`CDocTemplate`对象。 当用户打开一个新窗口或将拆分现有框架的一个构造的新视图，并将其附加到文档。  
  
 视图可以附加到只有一个文档，但一个文档只能有一次附加到它的多个视图 — 例如，如果在拆分窗口中或在多文档界面 (MDI) 应用程序中的多个子窗口中显示的文档。 你的应用程序可以为给定的文档类型; 支持不同类型的视图例如，字处理程序可能会提供文档的完整文本视图和显示仅部分标题的大纲视图。 如果使用拆分器窗口，在单独的框架窗口中或在单独的单个框架窗口的窗格中可以被放置这些不同类型的视图。  
  
 视图可能负责处理多种不同类型的输入，如键盘输入、 鼠标输入或通过拖放，以及命令从菜单、 工具栏或滚动条的输入。 视图接收转发其框架窗口的命令。 如果视图不能处理给定的命令，它会将转发到其关联文档命令。 所有的命令目标，如视图处理消息通过消息映射。  
  
 该视图负责为显示和修改文档的数据而不是将其存储。 本文档提供有关其数据具有必要的详细信息视图。 你可以让直接，文档的数据成员也可以提供要调用的视图类的文档类中的成员函数的视图访问权限。  
  
 当文档的数据更改时，通常调用负责所做的更改视图[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函数文档，这将告知所有其他视图，通过调用`OnUpdate`成员函数每个。 默认实现`OnUpdate`使视图的整个工作区无效。 你可以重写它要使其无效仅这些区域的工作区映射到文档的修改后的部分。  
  
 若要使用`CView`、 从其派生一个类和实现`OnDraw`成员函数以执行屏幕显示。 你还可以使用`OnDraw`执行打印和打印预览。 该框架将处理有关打印和文档预览打印循环。  
  
 视图处理具有滚动条邮件[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 您可以实现滚动条消息处理在这些函数中，也可以使用`CView`派生类[CScrollView](../../mfc/reference/cscrollview-class.md)来为您处理滚动。  
  
 除了`CScrollView`，Microsoft 基础类库提供了九个派生自其他类`CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允许使用文档的体系结构与树、 列表和 rich edit 控件的视图的视图。  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，显示对话框控件中数据库记录的视图。  
  
- [CEditView](../../mfc/reference/ceditview-class.md)，提供了简单的多行文本编辑器的视图。 你可以使用`CEditView`对象作为一个对话框，以及在文档上的视图中的控件。  
  
- [CFormView](../../mfc/reference/cformview-class.md)，包含对话框控件和基于对话框模板资源的可滚动视图。  
  
- [CListView](../../mfc/reference/clistview-class.md)，允许使用文档的视图体系结构与列表控件的视图。  
  
- [CRecordView](../../mfc/reference/crecordview-class.md)，显示对话框控件中数据库记录的视图。  
  
- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允许使用文档的体系结构与 rich edit 控件的视图的视图。  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md)，自动提供滚动支持的视图。  
  
- [CTreeView](../../mfc/reference/ctreeview-class.md)，允许使用文档的视图体系结构与树控件的视图。  
  
 `CView`类还具有一个名为的派生的实现类**CPreviewView**，用于由框架执行打印预览。 此类为唯一的打印预览窗口中，例如一个工具栏，单或双页面预览功能提供支持和缩放的，增大预览的图像。 无需调用或重写任何**CPreviewView**的成员函数，除非你想要实现您自己的打印预览的界面 （例如，如果你想要支持在打印预览模式中编辑）。 有关详细信息使用`CView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[打印](../../mfc/printing.md)。 此外，请参阅[技术注意 30](../../mfc/tn030-customizing-printing-and-print-preview.md)有关自定义打印预览的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="cview"></a>CView::CView  
 构造 `CView` 对象。  
  
```  
CView();
```  
  
### <a name="remarks"></a>备注  
 创建新的框架窗口或拆分窗口时，框架将调用构造函数。 重写[OnInitialUpdate](#oninitialupdate)成员函数以初始化视图，在附加文档之后。  
  
##  <a name="doprepareprinting"></a>CView::DoPreparePrinting  
 调用此函数的重写从[OnPreparePrinting](#onprepareprinting)以调用打印对话框并创建打印机设备上下文。  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。  
  
### <a name="return-value"></a>返回值  
 如果可以开始打印或打印预览; 则为非 0如果操作已取消，则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的行为取决于是否正在出于打印或打印预览调用 (通过指定**m_bPreview**的成员`pInfo`参数)。 如果打印文件时，此函数将调用打印对话框中，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的`pInfo`指向; 用户已关闭该对话框后，该函数将创建打印机设备上下文基于在对话框中指定的用户设置并返回通过此设备上下文`pInfo`参数。 此设备上下文用于打印文档。  
  
 如果正在预览一个文件，此函数将创建使用当前的打印机设置; 是打印机设备上下文此设备上下文用于在预览期间模拟打印机。  
  
##  <a name="getdocument"></a>CView::GetDocument  
 调用此函数可获取指向视图的文档的指针。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CDocument](../../mfc/reference/cdocument-class.md)与视图关联的对象。 **NULL**如果视图未附加到文档。  
  
### <a name="remarks"></a>备注  
 这样，您才能调用文档的成员函数。  
  
##  <a name="isselected"></a>CView::IsSelected  
 由框架调用以检查是否指定的文档项被选中。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pDocItem`  
 指向所测试的文档项的链接。  
  
### <a name="return-value"></a>返回值  
 如果选定了指定的文档项; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现返回**FALSE**。 重写此函数，如果你要实现选择使用[CDocItem](../../mfc/reference/cdocitem-class.md)对象。 如果你的视图包含 OLE 项，必须重写此函数。  
  
##  <a name="onactivateframe"></a>CView::OnActivateFrame  
 当激活或停用包含视图的框架窗口时，由框架调用。  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>参数  
 `nState`  
 指定是否框架窗口正在激活或停用。 它可以是以下值之一：  
  
- **WA_INACTIVE**框架窗口正在停用。  
  
- **WA_ACTIVE**框架窗口正在激活通过某些方法是之外 （例如，通过使用要选择的窗口的键盘接口），鼠标单击。  
  
- **WA_CLICKACTIVE**鼠标单击激活框架窗口  
  
 `pFrameWnd`  
 指向要激活的框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 如果你想要执行特殊处理，在激活或停用与视图关联的框架窗口时，重写该成员函数。 例如， [CFormView](../../mfc/reference/cformview-class.md)执行此重写时它将保存并还原具有焦点的控件。  
  
##  <a name="onactivateview"></a>CView::OnActivateView  
 当激活或停用视图时，由框架调用。  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>参数  
 `bActivate`  
 指示是否视图处于激活或停用。  
  
 `pActivateView`  
 指向正在激活的视图对象。  
  
 `pDeactiveView`  
 指向正在停用的视图对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将焦点设置到正在激活的视图。 如果你想要执行特殊处理，在激活或停用视图时，重写此函数。 例如，如果你想要提供特殊可视提示，从非活动视图区分活动视图，你会检查`bActivate`参数并相应地更新视图的外观。  
  
 `pActivateView`和`pDeactiveView`参数指向在同一个视图，如果应用程序的主框架窗口激活与活动视图不会更改 — 例如，如果从另一个应用程序到这台，而不是从一个传输焦点查看到另一个应用程序中或在 MDI 子窗口之间切换时。 如果需要这样，要重新实现其调色板的视图。  
  
 与不同，这些参数时[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)称为与不同于什么视图[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)将返回。 发生这种情况最常与拆分窗口。  
  
##  <a name="onbeginprinting"></a>CView::OnBeginPrinting  
 在调用 `OnPreparePrinting` 之后，由框架在打印或打印预览作业开始时调用。  
  
```  
virtual void OnBeginPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数以分配专用于打印的任何 GDI 资源，例如笔或字体。 选择到设备上下文中的 GDI 对象[OnPrint](#onprint)使用它们的每一页的成员函数。 如果要使用相同的视图对象执行屏幕显示和打印，请为每个显示所需的 GDI 资源使用单独的变量；这样做可以在打印期间更新屏幕。  
  
 你也可以使用此函数根据打印机设备上下文的属性执行初始化。 例如，打印文档所需的页面数可能取决于用户在“打印”对话框中指定的设置（例如页面长度）。 在这种情况下，不能指定文档长度以[OnPreparePrinting](#onprepareprinting)成员函数，其中你平常; 你必须等待，直到已根据对话框设置创建打印机设备上下文。 [OnBeginPrinting](#onbeginprinting)是第一个可重写函数，使您可以访问到[CDC](../../mfc/reference/cdc-class.md)表示打印机设备上下文，因此你可以从该函数设置文档长度的对象。 请注意，如果此时还不指定文档长度，打印预览期间将不会显示滚动条。  
  
##  <a name="ondragenter"></a>CView::OnDragEnter  
 当鼠标首次进入放置目标窗口的非滚动区域，由框架调用。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖放到视图的拖放区域。  
  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 当前鼠标位置相对于客户端区域的视图。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，该值指示如果用户在此位置删除对象，将出现的下拉的类型。 拖放的类型通常依赖于当前的密钥状态由指示`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是：  
  
- `DROPEFFECT_NONE`无法删除该数据对象，该窗口中。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL &#124;MK_SHIFT**创建对象和其服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**创建已删除的对象的副本。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**创建已删除的对象的副本，则删除原始对象。 这通常是默认放置效果，当该视图可以接受此数据对象。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回`DROPEFFECT_NONE`。  
  
 重写此函数可准备以便将来调用[OnDragOver](#ondragover)成员函数。 此数据对象中所需的任何数据应检索以便以后用于在此时`OnDragOver`成员函数。 该视图还应能够在用户的视觉反馈这次会更新。 有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragleave"></a>CView::OnDragLeave  
 由框架调用在拖动操作期间时鼠标退出该窗口的有效拖放区域。  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>备注  
 重写此函数，如果当前视图需要清理期间执行任何操作[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)调用，删除任何可视用户反馈时拖动并删除了对象等.  
  
##  <a name="ondragover"></a>CView::OnDragOver  
 由框架调用在拖动操作期间当鼠标移到放置目标窗口。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖动到放置目标上。  
  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 相对于视图客户端区域的当前鼠标位置。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，该值指示如果用户在此位置删除对象，将出现的下拉的类型。 拖放的类型通常取决于当前项的状态由`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是：  
  
- `DROPEFFECT_NONE`无法删除该数据对象，该窗口中。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL &#124;MK_SHIFT**创建对象和其服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**创建已删除的对象的副本。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**创建已删除的对象的副本，则删除原始对象。 这通常是默认放置效果，当该视图可以接受的数据对象。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回`DROPEFFECT_NONE`。  
  
 重写此函数可在拖动操作期间提供的用户的可视反馈。 由于连续调用此函数，其中包含的任何代码应优化尽可能多地。 有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragscroll"></a>CView::OnDragScroll  
 由框架在调用之前调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)以确定该点是否位于滚动区域。  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含光标，以像素为单位，相对于屏幕的位置。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，该值指示如果用户在此位置删除对象，将出现的下拉的类型。 拖放的类型通常依赖于当前的密钥状态由指示`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是：  
  
- `DROPEFFECT_NONE`无法删除该数据对象，该窗口中。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL &#124;MK_SHIFT**创建对象和其服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**创建已删除的对象的副本。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**创建已删除的对象的副本，则删除原始对象。  
  
- `DROPEFFECT_SCROLL`指示，拖动滚动操作即将发生或者问题发生在目标视图。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 如果你想要为此事件提供特殊行为，重写此函数。 默认实现自动滚动 windows 时光标拖放到每个窗口的边框内的默认滚动区域。有关详细信息，请参阅文章[拖放： 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondraw"></a>类库  
 由框架调用以呈现文档的图像。  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文以用于呈现文档的映像。  
  
### <a name="remarks"></a>备注  
 框架调用此函数可执行屏幕显示、 打印和打印预览中，并且每个用例中传递不同的设备上下文。 没有默认实现。  
  
 你必须重写此函数来显示文档的视图。 你可以使用图形设备接口 (GDI) 调用[CDC](../../mfc/reference/cdc-class.md)指向对象`pDC`参数。 可以选择到设备上下文中绘制之前的 GDI 资源，例如笔或字体，然后之后取消选择它们。 绘制代码通常可以是独立于设备;也就是说，它不需要哪种类型的设备已显示的图像的信息。  
  
 若要优化绘制，调用[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)的设备上下文以了解是否将绘制给定的矩形的成员函数。 如果你需要区分普通屏幕显示和打印，调用[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)的设备上下文的成员函数。  
  
##  <a name="ondrop"></a>CView::OnDrop  
 当用户释放数据对象有效放置目标之上时，由框架调用。  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)删除到放置目标。  
  
 `dropEffect`  
 用户已请求放置效果。  
  
- `DROPEFFECT_COPY`创建一份丢弃的数据对象。  
  
- `DROPEFFECT_MOVE`将数据对象移到当前的鼠标位置。  
  
- `DROPEFFECT_LINK`创建数据对象和其服务器之间的链接。  
  
 `point`  
 相对于视图客户端区域的当前鼠标位置。  
  
### <a name="return-value"></a>返回值  
 如果下拉成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作并返回**FALSE**。  
  
 重写此函数在视图的工作区中实现的 OLE 拖放效果。 可以通过检查数据对象`pDataObject`剪贴板数据格式和数据删除在指定的点。  
  
> [!NOTE]
>  框架不调用此函数的重写是否[OnDropEx](#ondropex)此视图类中。  
  
##  <a name="ondropex"></a>CView::OnDropEx  
 当用户释放数据对象有效放置目标之上时，由框架调用。  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)删除到放置目标。  
  
 `dropDefault`  
 用户选择基于当前的关键状态的默认拖放操作效果。 它可能是`DROPEFFECT_NONE`。 在备注部分中讨论了放置效果。  
  
 `dropList`  
 放置源支持拖放效果的列表。 可以使用按位 OR 组合放置效果值 ( **&#124;**) 操作。 在备注部分中讨论了放置效果。  
  
 `point`  
 相对于视图客户端区域的当前鼠标位置。  
  
### <a name="return-value"></a>返回值  
 从指定位置处删除尝试导致的放置效果`point`。 这必须是一个由值*dropEffectList*。 在备注部分中讨论了放置效果。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回一个虚拟值 (-1) 以指示应调用 framework [OnDrop](#ondrop)处理程序。  
  
 重写此函数可实现右侧的鼠标按钮拖放的效果。 右侧的鼠标按钮拖放通常会在释放鼠标右键时显示选择的菜单。  
  
 重写`OnDropEx`应该查询右侧的鼠标按钮。 你可以调用[GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301)或存储中的右侧的鼠标按钮状态你[OnDragEnter](#ondragenter)处理程序。  
  
-   如果右侧的鼠标按钮已关闭，则重写应显示弹出菜单，它提供了放置源支持放置效果。  
  
    -   检查`dropList`以确定支持的放置源放置效果。 启用弹出菜单上的这些操作。  
  
    -   使用[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)设置基于的默认操作`dropDefault`。  
  
    -   最后，需要由用户选择从弹出菜单中的操作。  
  
-   如果未按下鼠标右键，则重写应处理此作为标准放请求。 使用中指定的放置效果`dropDefault`。 或者，重写可返回虚拟值 (-1)，则指示`OnDrop`将处理此拖放操作。  
  
 使用`pDataObject`检查`COleDataObject`剪贴板数据格式和数据删除在指定的点。  
  
 放置效果描述与拖放操作相关联的操作。 请参阅以下放置效果的列表：  
  
- `DROPEFFECT_NONE`不允许删除。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL`指示，拖动滚动操作即将发生或者问题发生在目标中。  
  
 设置默认菜单命令的详细信息，请参阅[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) Windows SDK 中和[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此卷中。  
  
##  <a name="onendprinting"></a>CView::OnEndPrinting  
 在打印文档或将其预览后，由框架调用。  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数可释放中分配任何 GDI 资源[OnBeginPrinting](#onbeginprinting)成员函数。  
  
##  <a name="onendprintpreview"></a>CView::OnEndPrintPreview  
 当用户退出打印预览模式时，由框架调用。  
  
```  
virtual void OnEndPrintPreview(
    CDC* pDC,  
    CPrintInfo* pInfo,  
    POINT point,  
    CPreviewView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。  
  
 `point`  
 上次在预览模式下显示的页面上指定的点。  
  
 `pView`  
 指向以用于预览的视图对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[OnEndPrinting](#onendprinting)成员函数，并还原主框架窗口到在打印预览之前的状态开始。 重写此函数以执行特殊处理，预览模式而终止时。 例如，如果你想要维护了文档中的用户的位置，从预览模式切换到普通显示模式时，你可以向下滚动到所描述的位置`point`参数和`m_nCurPage`的成员`CPrintInfo`结构`pInfo`参数指向。  
  
 始终调用基类版本的`OnEndPrintPreview`从你重写时，通常在该函数的末尾。  
  
##  <a name="oninitialupdate"></a>Cview:: Oninitialupdate  
 视图首先附加到文档中之后, 但在最初显示的视图之前，由框架调用。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[OnUpdate](#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示`lHint`参数和**NULL**为`pHint`参数)。 重写此函数以执行任何需要有关文档的信息的一次性初始化。 例如，如果你的应用程序具有固定大小的文档，你可以使用此函数来初始化视图的滚动限制基于的文档大小。 如果你的应用程序支持大小可变的文档，使用[OnUpdate](#onupdate)更新滚动限制每次文档发生更改。  
  
##  <a name="onpreparedc"></a>CView::OnPrepareDC  
 由框架在之前调用[OnDraw](#ondraw)为屏幕显示和之前调用成员函数[OnPrint](#onprint)在打印或打印预览过程的每个页面调用成员函数。  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文以用于呈现文档的映像。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构，描述当前打印作业，如果`OnPrepareDC`正在为打印或打印预览，则为调用`m_nCurPage`成员指定要打印的页。 此参数是**NULL**如果`OnPrepareDC`调用是用于屏幕显示。  
  
### <a name="remarks"></a>备注  
 如果为屏幕显示调用函数，则此函数的默认实现没有任何效果。 但是，此函数被重写在派生类中，如[CScrollView](../../mfc/reference/cscrollview-class.md)，调整属性的设备上下文中; 因此，你始终应开头的重写调用基类实现。  
  
 如果打印调用函数时，默认实现将检查中存储的页信息`pInfo`参数。 如果尚未指定文档的长度，`OnPrepareDC`假定要长的一页的文档，并且会在已打印一页后停止打印循环。 函数通过设置来停止打印循环`m_bContinuePrinting`到结构中的成员**FALSE**。  
  
 重写`OnPrepareDC`任何由于以下原因之一：  
  
-   若要根据需要为指定的页调整设备上下文的属性。 例如，如果你需要设置的映射模式或的设备上下文的其他特征，这样在此函数。  
  
-   若要执行打印时分页。 通常指定文档的长度，开始打印时，使用[OnPreparePrinting](#onprepareprinting)成员函数。 但是，如果你不知道提前多长时间文档程序 （例如，当从数据库中打印的记录不确定的数），重写`OnPrepareDC`来测试而在打印文档的结尾。 当没有更多的要打印的文档时，设置`m_bContinuePrinting`的成员`CPrintInfo`结构**FALSE**。  
  
-   若要将转义码发送到按页基于打印机。 若要发送中的转义码`OnPrepareDC`，调用**转义**成员函数`pDC`参数。  
  
 调用基类版本的`OnPrepareDC`重写的开头。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>CView::OnPreparePrinting  
 打印或预览文档之前，由框架调用。  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述当前打印作业的结构。  
  
### <a name="return-value"></a>返回值  
 非零值，开始打印;如果打印作业已被取消，则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。  
  
 你必须重写此函数可启用打印和打印预览。 调用[DoPreparePrinting](#doprepareprinting)成员函数，将其传递`pInfo`参数，然后返回其返回值;`DoPreparePrinting`显示打印对话框中，并创建打印机设备上下文。 如果你想要初始化使用默认值以外的值打印对话框中，将值分配给的成员`pInfo`。 例如，如果你知道文档的长度，将值传递给[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成员函数`pInfo`之前调用`DoPreparePrinting`。 此值显示在收件人： 框中的打印对话框中的范围部分。  
  
 `DoPreparePrinting`不显示预览作业的打印对话框。 如果你想要绕过打印作业的打印对话框，请检查**m_bPreview**的成员`pInfo`是**FALSE**然后将它设置为**TRUE**之前将其传递给`DoPreparePrinting`; 重置到**FALSE**之后。  
  
 如果你需要执行需要访问的初始化`CDC`表示打印机设备上下文 （例如，如果你之前需要知道的页大小指定文档的长度），对象重写`OnBeginPrinting`成员函数。  
  
 如果你想要设置的值**m_nNumPreviewPages**或**m_strPageDesc**的成员`pInfo`参数，这样做之后调用`DoPreparePrinting`。 `DoPreparePrinting`成员函数集**m_nNumPreviewPages**到应用程序的中找到的值。INI 文件和设置**m_strPageDesc**为其默认值。  
  
### <a name="example"></a>示例  
  重写`OnPreparePrinting`并调用`DoPreparePrinting`重写，以便框架将显示一个打印对话框并为你创建是打印机设备。  
  
 [!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 如果你知道该文档包含多少个页面，在中设置最大页数`OnPreparePrinting`之前调用`DoPreparePrinting`。 框架将显示在"收件人"框中的打印对话框中的最大的页码。  
  
 [!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>CView::OnPrint  
 由框架调用以打印或预览文档的一页。  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向`CPrintInfo`描述当前打印作业的结构。  
  
### <a name="remarks"></a>备注  
 对于每个打印的页，框架会调用此函数在调用后立即[OnPrepareDC](#onpreparedc)成员函数。 通过指定打印页`m_nCurPage`的成员[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的`pInfo`指向。 默认实现调用[OnDraw](#ondraw)成员函数并将其传递打印机设备上下文。  
  
 由于以下原因导致重写此函数：  
  
-   若要允许打印多页文档。 呈现仅的文档的对应于当前打印页的部分。 如果你使用`OnDraw`要执行呈现，你可以调整视区原点以便打印仅文档的相应部分。  
  
-   要打印的图像看起来不同于屏幕图像 （即，如果你的应用程序不是所见即所得）。 而不是传递到的设备上下文的打印机`OnDraw`，使用的设备上下文来呈现使用属性未显示在屏幕上的映像。  
  
     如果你需要在未使用进行屏幕显示打印的 GDI 资源，它们选入设备上下文在绘制之前和之后取消选择它们。 应以分配这些 GDI 资源[OnBeginPrinting](#onbeginprinting)和发布[OnEndPrinting](#onendprinting)。  
  
-   若要实现页眉或页脚。 你仍然可以使用`OnDraw`如何呈现通过限制可以打印的区域。  
  
 请注意， **m_rectDraw**的成员`pInfo`参数描述中逻辑单元的页可打印区域。  
  
 不要调用`OnPrepareDC`的重写中`OnPrint`; 框架调用`OnPrepareDC`自动之前调用`OnPrint`。  
  
### <a name="example"></a>示例  
 以下是被重写主干`OnPrint`函数：  
  
 [!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 另一个示例，请参阅[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。  
  
##  <a name="onscroll"></a>CView::OnScroll  
 由框架可以确定是否滚动一点。  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nScrollCode`  
 指示的用户的滚动条代码的滚动请求。 此参数由两个部分组成： 低序位字节，用于确定滚动正在进行水平的类型，并确定的一种滚动发生垂直高序位字节：  
  
- **SB_BOTTOM**滚动到下的顺序。  
  
- **SB_LINEDOWN**向下滚动一行。  
  
- **SB_LINEUP**向上滚动一行。  
  
- **SB_PAGEDOWN**向下滚动一页。  
  
- **SB_PAGEUP**向上滚动一页。  
  
- **SB_THUMBTRACK**拖动到指定位置的滚动框。 在指定当前位置`nPos`。  
  
- **SB_TOP**滚动到顶部。  
  
 `nPos`  
 滚动条代码是否包含滚动框的当前位置**SB_THUMBTRACK**; 否则为未使用。 具体取决于初始滚动范围，`nPos`可以是负数，并且应强制转换为`int`如有必要。  
  
 `bDoScroll`  
 确定是否应实际完成指定滚动操作。 如果**为 TRUE，**然后滚动应发生; 如果**FALSE**，然后滚动应不会发生。  
  
### <a name="return-value"></a>返回值  
 如果`bDoScroll`是**TRUE**和实际滚动视图，然后返回非零; 否则为 0。 如果`bDoScroll`是**FALSE**，然后返回值，将返回如果`bDoScroll`已**TRUE**，即使您不实际执行滚动。  
  
### <a name="remarks"></a>备注  
 框架使用一种情况下在调用此函数`bDoScroll`设置为**TRUE**视图当收到滚动条消息。 在这种情况下，你应实际滚动视图。 使用在其他情况下调用此函数`bDoScroll`设置为**FALSE**时 OLE 项最初拖放到放置目标的自动滚动区域滚动实际的发生之前。 在这种情况下，你应实际滚动视图。  
  
##  <a name="onscrollby"></a>CView::OnScrollBy  
 当用户查看文档，通过拖动针对视图的当前边框的 OLE 项或操作的垂直或水平滚动条的存在视图之外的区域，由框架调用。  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `sizeScroll`  
 水平和垂直，滚动的像素数。  
  
 `bDoScroll`  
 确定是否滚动视图的执行。 如果**为 TRUE，**然后滚动发生; 如果**FALSE**，然后滚动不会发生。  
  
### <a name="return-value"></a>返回值  
 如果视图能够滚动; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 在派生类中此方法检查以确定是否在用户请求，然后更新新的区域，如有必要的方向可滚动视图。 将自动调用此函数[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)执行实际的滚动请求。  
  
 此方法的默认实现不会更改视图，但如果未调用，该视图将在不滚动`CScrollView`-派生类。  
  
 如果文档宽度或高度超过 32767 的像素为单位，过去的 32767 滚动将失败，因为`OnScrollBy`称为无效`sizeScroll`自变量。  
  
##  <a name="onupdate"></a>CView::OnUpdate  
 修改视图的文档; 后，由框架调用调用此函数[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) ，并允许更新以反映这些修改显示的视图。  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>参数  
 `pSender`  
 指向修改文档，该视图或**NULL**如果所有视图进行更新。  
  
 `lHint`  
 包含有关修改信息。  
  
 `pHint`  
 指向以存储有关修改信息的对象。  
  
### <a name="remarks"></a>备注  
 它还由的默认实现[OnInitialUpdate](#oninitialupdate)。 默认实现将使失效整个客户端区域中，将它标记为对于绘制时的下一步`WM_PAINT`接收消息。 如果你想要更新映射到文档的修改后的部分的区域，重写此函数。 若要执行此操作必须传递有关使用提示参数的修改的信息。  
  
 若要使用`lHint`，定义特殊的提示值、 通常是一个位屏蔽或枚举的类型，并且必须传递这些值之一的文档。 若要使用`pHint`，提示从派生类[CObject](../../mfc/reference/cobject-class.md)和拥有在重写时，将指针传递给提示的对象; 此文档`OnUpdate`，使用[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)到成员函数确定提示对象的运行时类型。  
  
 通常，则应不执行任何直接从绘制`OnUpdate`。 相反，确定描述，在设备坐标中，则需要更新; 的区域的矩形传递到此矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 这将导致绘制下一次时[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)接收消息。  
  
 如果`lHint`为 0 和`pHint`是**NULL**，文档已发送泛型更新通知。 如果视图收到一个泛型更新通知，或者如果它不能进行解码提示，它应使其整个工作区。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)
