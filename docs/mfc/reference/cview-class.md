---
title: "CView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- views [C++], view classes
- multiple views
- CView class
- document/view architecture
- input, and view class
- MDI [C++], view windows
- print preview, view windows
- windows [C++], views
- child windows, views
- frame windows [C++], views
- user input [C++], interpreting through view class
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
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
ms.openlocfilehash: ce5100a9ee4a1c20df04f79f0c8cd645ae3afce7
ms.lasthandoff: 02/24/2017

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
|[CView::CView](#cview)|构造 `CView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CView::DoPreparePrinting](#doprepareprinting)|显示打印对话框并创建打印机设备上下文;当重写时，调用`OnPreparePrinting`成员函数。|  
|[CView::GetDocument](#getdocument)|返回与视图关联的文档。|  
|[CView::IsSelected](#isselected)|测试是否选择了文档项目。 对于 OLE 支持必需。|  
|[CView::OnDragEnter](#ondragenter)|当某一项第一次拖动到拖放区域的视图时调用。|  
|[CView::OnDragLeave](#ondragleave)|将拖动的项离开视图的拖放区域时调用。|  
|[CView::OnDragOver](#ondragover)|当某项拖动到视图的拖放区域上方时调用。|  
|[CView::OnDragScroll](#ondragscroll)|调用以确定是否将光标拖到窗口中滚动区域。|  
|[CView::OnDrop](#ondrop)|当某项已放入视图中，在默认处理程序的拖放区域时调用。|  
|[CView::OnDropEx](#ondropex)|当某项已放入视图中，主处理程序的拖放区域时调用。|  
|[Cview:: Oninitialupdate](#oninitialupdate)|在查看第一次附加到文档之后调用。|  
|[CView::OnPrepareDC](#onpreparedc)|之前调用`OnDraw`成员函数调用以进行屏幕显示或`OnPrint`针对打印或打印预览调用成员函数。|  
|[CView::OnScroll](#onscroll)|当超出了该视图的边框将 OLE 项时调用。|  
|[CView::OnScrollBy](#onscrollby)|滚动包含活动中现有 OLE 项的视图时调用。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|当激活或停用包含该视图的框架窗口时调用。|  
|[CView::OnActivateView](#onactivateview)|当激活视图时调用。|  
|[CView::OnBeginPrinting](#onbeginprinting)|当打印作业将会开始; 时，调用重写以分配图形设备接口 (GDI) 资源。|  
|[类库](#ondraw)|调用以呈现用于屏幕显示、 打印或打印预览的文档图像。 所需的实现。|  
|[CView::OnEndPrinting](#onendprinting)|打印作业结束; 时调用释放 GDI 资源的替代。|  
|[CView::OnEndPrintPreview](#onendprintpreview)|当退出预览模式时调用。|  
|[CView::OnPreparePrinting](#onprepareprinting)|在打印或预览; 文档之前调用重写以初始化打印对话框。|  
|[CView::OnPrint](#onprint)|调用以打印或预览文档的页。|  
|[CView::OnUpdate](#onupdate)|调用以通知一个视图，其文档已被修改。|  
  
## <a name="remarks"></a>备注  
 查看附加到文档，并且可作为文档和用户之间的媒介︰ 视图呈现在屏幕或打印机上文档的图像，并将用户输入解释为对文档的操作。  
  
 视图是框架窗口的子级。 多个视图可以共享框架窗口，如下所示的拆分器窗口的大小写。 视图类、 一个框架窗口类和文档类之间关系的建立方式`CDocTemplate`对象。 当用户打开一个新窗口或拆分现有一个框架构造一个新的视图，并将其附加到文档。  
  
 视图可以附加到只能有一个文档，但一个文档只能有一次附加到它的多个视图 — 例如，如果在拆分器窗口中或在多文档界面 (MDI) 应用程序中的多个子窗口中显示的文档。 您的应用程序可以为给定的文档类型; 支持不同类型的视图例如，字处理程序可能会提供文档的完整文本视图以及用于显示仅的节标题的大纲视图。 这些不同类型的视图可以放置在单独的框架窗口或在单独的单个框架窗口的窗格中如果您使用拆分器窗口中。  
  
 视图可能负责处理多种不同类型的输入，如键盘输入、 鼠标输入或从菜单、 工具栏或滚动条通过拖放，以及命令的输入。 视图接收转发的其框架窗口的命令。 如果该视图不处理给定的命令，它将转发到其关联文档的命令。 像所有的命令目标视图处理消息通过消息映射。  
  
 视图负责显示和修改文档的数据，而无需将其存储。 本文档提供有关其数据具有必要的详细信息视图。 您可以让直接，文档的数据成员也可以提供要调用的视图类的文档类中的成员函数的视图访问权限。  
  
 当文档的数据更改时，视图负责所做的更改通常会调用[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函数文档，并通过调用通知所有其他视图`OnUpdate`为每个成员函数。 默认实现`OnUpdate`使该视图的整个客户端区域无效。 您可以重写它要使之无效只有这些区域的工作区映射到文档的修改后的部分。  
  
 若要使用`CView`、 从其派生一个类和实现`OnDraw`成员函数以执行屏幕显示。 您还可以使用`OnDraw`来执行打印和打印预览。 该框架将处理用于打印和文档预览打印循环。  
  
 视图处理具有滚动条邮件[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成员函数。 您可以实现滚动条中的消息处理这些函数中，也可以使用`CView`派生类[CScrollView](../../mfc/reference/cscrollview-class.md)来为您处理滚动。  
  
 除了`CScrollView`，Microsoft 基础类库提供了九个派生自其他类`CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允许使用的文档-体系结构与树、 列表和 rich edit 控件的视图的视图。  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，显示对话框中控件中数据库记录的视图。  
  
- [CEditView](../../mfc/reference/ceditview-class.md)，提供了一个简单的多行文本编辑器的视图。 您可以使用`CEditView`为控件在对话框中，以及对文档的视图的对象。  
  
- [CFormView](../../mfc/reference/cformview-class.md)，包含对话框控件和基于对话框模板资源的可滚动视图。  
  
- [CListView](../../mfc/reference/clistview-class.md)，允许使用文档的视图体系结构与列表控件的视图。  
  
- [CRecordView](../../mfc/reference/crecordview-class.md)，显示对话框中控件中数据库记录的视图。  
  
- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允许使用的文档-体系结构与 rich edit 控件的视图的视图。  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md)，自动提供滚动支持的视图。  
  
- [Ctreeview 类](../../mfc/reference/ctreeview-class.md)，允许使用文档的视图体系结构与树控件的视图。  
  
 `CView`类还具有一个名为派生的实现类**CPreviewView**，框架使用它来执行打印预览。 此类支持打印预览窗口工具栏上，单页或双预览版中，如独有的功能并提供缩放的，扩大预览的图像。 无需调用或重写任何**CPreviewView**的成员函数，除非您想要实现您自己的打印预览的界面 （例如，如果你想要支持在打印预览模式中编辑）。 有关详细信息使用`CView`，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)和[打印](../../mfc/printing.md)。 此外，请参阅[技术注意 30](../../mfc/tn030-customizing-printing-and-print-preview.md)有关自定义打印预览的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cview"></a>CView::CView  
 构造 `CView` 对象。  
  
```  
CView();
```  
  
### <a name="remarks"></a>备注  
 创建新的框架窗口或拆分窗口时，框架将调用构造函数。 重写[OnInitialUpdate](#oninitialupdate)成员函数以初始化后附加文档的视图。  
  
##  <a name="doprepareprinting"></a>CView::DoPreparePrinting  
 调用此函数的重写从[OnPreparePrinting](#onprepareprinting)来调用打印对话框中，并创建打印机设备上下文。  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构描述当前的打印作业。  
  
### <a name="return-value"></a>返回值  
 非零，如果打印或打印预览才能开始实施。如果取消该操作，则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的行为取决于是否正在调用它的打印或打印预览 (由指定**m_bPreview**的成员`pInfo`参数)。 如果在打印一个文件，此函数将调用打印对话框中，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的`pInfo`指向; 用户已关闭对话框中后，该函数将创建基于用户在对话框中指定，并返回到此设备上下文设置是打印机设备上下文`pInfo`参数。 此设备上下文用于打印文档。  
  
 如果正在预览文件，此函数将创建使用当前的打印机设置; 是打印机设备上下文此设备上下文用于在预览期间模拟打印机。  
  
##  <a name="getdocument"></a>CView::GetDocument  
 调用此函数可获取指向该视图的文档的指针。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CDocument](../../mfc/reference/cdocument-class.md)与视图关联的对象。 **NULL**如果视图无法附加到文档。  
  
### <a name="remarks"></a>备注  
 这样您就可以调用文档的成员函数。  
  
##  <a name="isselected"></a>CView::IsSelected  
 由框架来检查是否选择了指定的文档项调用。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>参数  
 `pDocItem`  
 指向所测试的文档项目。  
  
### <a name="return-value"></a>返回值  
 如果指定的文档项处于选中状态，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现返回**FALSE**。 重写此函数，如果您要实现选择使用[CDocItem](../../mfc/reference/cdocitem-class.md)对象。 如果您的视图包含 OLE 项，必须重写此函数。  
  
##  <a name="onactivateframe"></a>CView::OnActivateFrame  
 激活或停用包含该视图的框架窗口时由框架调用。  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>参数  
 `nState`  
 指定是否在框架窗口正在激活或停用。 它可以是下列值之一︰  
  
- **WA_INACTIVE**框架窗口正在停用。  
  
- **WA_ACTIVE**以外 （例如，通过使用的键盘界面来选择该窗口），鼠标单击的框架窗口已激活通过一些方法。  
  
- **WA_CLICKACTIVE**框架窗口正在激活通过单击鼠标  
  
 `pFrameWnd`  
 指向要激活的框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 如果你想要激活或停用与视图关联的框架窗口时执行特殊处理，重写该成员函数。 例如， [CFormView](../../mfc/reference/cformview-class.md)执行此重写时它将保存并还原具有焦点的控件。  
  
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
 指示是否视图处于激活还是停用状态。  
  
 `pActivateView`  
 指向正在激活的视图对象。  
  
 `pDeactiveView`  
 指向正在停用的视图对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将焦点设置为正在激活视图。 如果你想要激活或停用视图时执行特殊处理，重写此函数。 例如，如果您想要提供特殊可视提示，可从非活动视图区分活动视图，您会检查`bActivate`参数并相应地更新视图的外观。  
  
 `pActivateView`和`pDeactiveView`参数指向在同一个视图，如果应用程序的主框架窗口激活并在活动视图中的任何更改，例如，如果正在时焦点转移到这台的其他应用程序中而不是从一个视图到另一个应用程序中或在 MDI 子窗口间切换。 如果需要这会使视图来重新实现其调色板。  
  
 这些参数与不同，当[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)称为具有的视图的不同于什么[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)将返回。 发生这种情况最常与拆分器窗口。  
  
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
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构描述当前的打印作业。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数以分配专用于打印的任何 GDI 资源，例如笔或字体。 选择到设备上下文中的 GDI 对象[OnPrint](#onprint)成员函数，每个使用这些页。 如果要使用相同的视图对象执行屏幕显示和打印，请为每个显示所需的 GDI 资源使用单独的变量；这样做可以在打印期间更新屏幕。  
  
 你也可以使用此函数根据打印机设备上下文的属性执行初始化。 例如，打印文档所需的页面数可能取决于用户在“打印”对话框中指定的设置（例如页面长度）。 在这种情况下，不能指定文档长度以[OnPreparePrinting](#onprepareprinting)成员函数，其中您通常这样做; 你必须等待，直到具有基于对话框中的设置创建打印机设备上下文。 [OnBeginPrinting](#onbeginprinting)是第一个可重写函数，使您可以访问到[CDC](../../mfc/reference/cdc-class.md)表示打印机设备上下文，因此你可以设置文档长度，从该函数对象。 请注意，如果此时还不指定文档长度，打印预览期间将不会显示滚动条。  
  
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
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)拖入视图拖放区域。  
  
 `dwKeyState`  
 包含修改键的状态。 这是以下任意数量的组合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 当前鼠标位置相对于工作区的视图。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，它指示如果用户在此位置删除该对象，将出现的拖放的类型。 拖放类型通常取决于所指示的当前密钥状态`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是︰  
  
- `DROPEFFECT_NONE`不能在此窗口中删除此数据对象。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL |MK_SHIFT**创建对象和它的服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**会创建一份拖放的对象。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**会创建一份拖放的对象，则删除原始对象。 这通常是默认的拖放效果，何时该视图可以接受此数据对象。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回`DROPEFFECT_NONE`。  
  
 重写此函数准备未来调用[OnDragOver](#ondragover)成员函数。 需要此数据对象中的所有数据应在这次是为了在以后用于都检索`OnDragOver`成员函数。 该视图还应以提供用户的可视反馈这次更新。 有关详细信息，请参阅文章[将拖放︰ 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragleave"></a>CView::OnDragLeave  
 由框架调用在拖动操作期间时为该窗口将鼠标移出了有效的放置区域。  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>备注  
 如果当前视图需要清理期间所执行任何操作来重写此函数[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)调用，如同时拖动并删除了对象中删除任何可视用户反馈。  
  
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
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖动到放置目标。  
  
 `dwKeyState`  
 包含修改键的状态。 这是以下任意数量的组合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 当前的视图工作区相对的鼠标位置。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，它指示如果用户在此位置删除该对象，将出现的拖放的类型。 拖放的类型通常取决于当前密钥状态如中所示`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是︰  
  
- `DROPEFFECT_NONE`不能在此窗口中删除此数据对象。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL |MK_SHIFT**创建对象和它的服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**会创建一份拖放的对象。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**会创建一份拖放的对象，则删除原始对象。 这通常是默认的拖放效果，何时该视图可以接受的数据对象。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回`DROPEFFECT_NONE`。  
  
 重写此函数可在拖动操作期间提供的用户的可视反馈。 由于连续调用此函数时，它所包含的任何代码应优化尽可能多地。 有关详细信息，请参阅文章[将拖放︰ 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragscroll"></a>CView::OnDragScroll  
 由之前调用框架调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)来确定的点是否在滚动区域内。  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `dwKeyState`  
 包含修改键的状态。 这是以下任意数量的组合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含以像素为单位，相对于屏幕光标的位置。  
  
### <a name="return-value"></a>返回值  
 取值范围为`DROPEFFECT`枚举类型，它指示如果用户在此位置删除该对象，将出现的拖放的类型。 拖放类型通常取决于所指示的当前密钥状态`dwKeyState`。 到 keystates 的标准映射`DROPEFFECT`值是︰  
  
- `DROPEFFECT_NONE`不能在此窗口中删除此数据对象。  
  
- `DROPEFFECT_LINK`有关**MK_CONTROL |MK_SHIFT**创建对象和它的服务器之间的链接。  
  
- `DROPEFFECT_COPY`有关**MK_CONTROL**会创建一份拖放的对象。  
  
- `DROPEFFECT_MOVE`有关**MK_ALT**会创建一份拖放的对象，则删除原始对象。  
  
- `DROPEFFECT_SCROLL`指示拖动滚动操作将要发生，或在目标视图中进行。  
  
 有关详细信息，请参阅 MFC 高级概念示例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>备注  
 当您想要为此事件提供特殊行为时，重写此函数。 默认实现将自动滚动 windows 光标拖到每个窗口的边框内的默认滚动区域中时。有关详细信息，请参阅文章[将拖放︰ 实现放置目标](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondraw"></a>类库  
 由要呈现的文档图像的框架调用。  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文中以用于呈现文档的图像。  
  
### <a name="remarks"></a>备注  
 框架将调用此函数以执行屏幕显示、 打印和打印预览中，并且在每个用例中传递不同的设备上下文。 没有默认实现。  
  
 必须重写此函数可显示文档的视图。 您可以使用图形设备接口 (GDI) 调用[CDC](../../mfc/reference/cdc-class.md)指向对象`pDC`参数。 可以选择 GDI 资源，如钢笔或字体，到之前绘制的设备上下文，然后之后取消选择它们。 通常绘制代码可以是独立于设备;也就是说，它不需要的设备类型已显示的图像的信息。  
  
 若要优化绘图，请调用[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)的设备上下文中以找出是否绘制给定的矩形将成员函数。 如果您需要区分普通屏幕显示和打印，调用[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)设备上下文的成员函数。  
  
##  <a name="ondrop"></a>CView::OnDrop  
 当用户的有效放置目标上释放数据对象由框架调用。  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)放入拖放目标。  
  
 `dropEffect`  
 用户已请求拖放效果。  
  
- `DROPEFFECT_COPY`创建要删除的数据对象的副本。  
  
- `DROPEFFECT_MOVE`将数据对象移动到当前的鼠标位置。  
  
- `DROPEFFECT_LINK`创建数据对象和它的服务器之间的链接。  
  
 `point`  
 当前的视图工作区相对的鼠标位置。  
  
### <a name="return-value"></a>返回值  
 如果删除成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作并返回**FALSE**。  
  
 重写此函数可在视图的工作区中实施的 OLE 拖放效果。 数据对象可以通过检查`pDataObject`对于剪贴板数据格式和数据删除的指定点处。  
  
> [!NOTE]
>  框架不调用此函数的重写是否[OnDropEx](#ondropex)在此视图类中。  
  
##  <a name="ondropex"></a>CView::OnDropEx  
 当用户的有效放置目标上释放数据对象由框架调用。  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)放入拖放目标。  
  
 `dropDefault`  
 用户选择了基于当前的关键状态的默认拖放操作效果。 它可能`DROPEFFECT_NONE`。 在备注部分中讨论了放置效果。  
  
 `dropList`  
 拖放源支持拖放效果的列表。 可以使用按位 OR 组合放置效果值 ( **|**) 操作。 在备注部分中讨论了放置效果。  
  
 `point`  
 当前的视图工作区相对的鼠标位置。  
  
### <a name="return-value"></a>返回值  
 通过指定的位置处的删除尝试而导致的放置效果`point`。 这必须是所指示的值之一*dropEffectList*。 在备注部分中讨论了放置效果。  
  
### <a name="remarks"></a>备注  
 默认实现是不执行任何操作并返回一个虚拟的值 (-1) 调用以指示应调用框架[OnDrop](#ondrop)处理程序。  
  
 重写此函数可实现适当的鼠标按钮拖放效果。 右侧的鼠标按钮拖放通常会在释放鼠标右键时显示选项的菜单。  
  
 重写`OnDropEx`右侧鼠标按钮应该查询。 您可以调用[GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301)存储从右侧的鼠标按钮状态，或您[OnDragEnter](#ondragenter)处理程序。  
  
-   如果鼠标右键已关闭，重写应显示一个弹出式菜单，它提供了通过拖放源支持拖放效果。  
  
    -   检查`dropList`若要确定支持的拖放源的拖放效果。 启用弹出菜单上的这些操作。  
  
    -   使用[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)若要设置的默认操作基于`dropDefault`。  
  
    -   最后，采取的操作由用户选择从弹出菜单。  
  
-   如果未按下鼠标右键，重写应处理此作为标准的删除请求。 使用拖放效果中指定`dropDefault`。 或者，您的重写可返回虚值 (-1) 以指示`OnDrop`将处理此拖放操作。  
  
 使用`pDataObject`检查`COleDataObject`对于剪贴板数据格式和数据删除的指定点处。  
  
 拖放效果描述与拖放操作相关联的操作。 请参阅下面放置效果的列表︰  
  
- `DROPEFFECT_NONE`将不允许放置。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立到原始数据放置的数据的链接。  
  
- `DROPEFFECT_SCROLL`指示拖动滚动操作将要发生或出现在目标中。  
  
 有关设置默认菜单命令的详细信息，请参阅[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]和[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此卷中。  
  
##  <a name="onendprinting"></a>CView::OnEndPrinting  
 由框架调用后打印或预览文档。  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构描述当前的打印作业。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数可释放任何中分配的 GDI 资源[OnBeginPrinting](#onbeginprinting)成员函数。  
  
##  <a name="onendprintpreview"></a>CView::OnEndPrintPreview  
 在用户退出打印预览模式时，由框架调用。  
  
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
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构描述当前的打印作业。  
  
 `point`  
 上次在预览模式下显示的页面上指定的点。  
  
 `pView`  
 指向以用于预览的视图对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[OnEndPrinting](#onendprinting)成员函数和还原主框架窗口到打印预览之前的状态开始。 重写此函数可终止预览模式时执行特殊处理。 例如，如果您想要维护文档中的用户的位置，从预览模式切换到普通显示模式时，您可以滚动到所描述的位置`point`参数和`m_nCurPage`的成员`CPrintInfo`结构的`pInfo`参数指向。  
  
 始终调用基类版本的`OnEndPrintPreview`通过重写，通常在该函数的末尾。  
  
##  <a name="oninitialupdate"></a>Cview:: Oninitialupdate  
 查看第一次附加到文档之后, 但在最初显示的视图之前，由框架调用。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[OnUpdate](#onupdate)而不提示信息的成员函数 (即，使用默认值为 0 表示`lHint`参数和**NULL**为`pHint`参数)。 重写此函数以执行任何需要与文档有关的信息的一次性初始化。 例如，如果您的应用程序具有固定大小的文档，您可以使用此函数来初始化视图的滚动限制基于文档的大小。 如果您的应用程序支持大小可变的文档，使用[OnUpdate](#onupdate)用于滚动更新的限制每次文档发生更改。  
  
##  <a name="onpreparedc"></a>CView::OnPrepareDC  
 由框架之前调用[OnDraw](#ondraw)屏幕显示和之前调用成员函数[OnPrint](#onprint)打印或打印预览期间的每个页调用成员函数。  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文中以用于呈现文档的图像。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构，描述当前的打印作业，如果`OnPrepareDC`打印或打印预览，则为调用`m_nCurPage`成员指定要打印的页。 此参数是**NULL**如果`OnPrepareDC`正在调用以进行屏幕显示。  
  
### <a name="remarks"></a>备注  
 如果是为了屏幕显示调用该函数时，此函数的默认实现将没有任何效果。 但是，此函数中重写派生类中，如[CScrollView](../../mfc/reference/cscrollview-class.md)、 调整设备上下文中; 特性因此，您应始终调用基类实现重写的开头。  
  
 如果针对打印调用该函数，则默认实现将检查中存储的页信息`pInfo`参数。 如果尚未指定文档的长度，`OnPrepareDC`假定要长度只有一页的文档，并会在一页打印完后停止打印循环。 函数通过设置停止打印循环`m_bContinuePrinting`到结构中的成员**FALSE**。  
  
 重写`OnPrepareDC`任何下列原因之一︰  
  
-   若要根据需要为指定的页调整设备上下文的属性。 例如，如果您需要设置映射模式或其他特性的设备上下文，这样做在此函数。  
  
-   若要执行打印时分页。 通常情况下指定文档的长度，当打印开始时，使用[OnPreparePrinting](#onprepareprinting)成员函数。 但是，如果您不知道提前时间文档程序 （例如，当从数据库中打印的记录不确定的数），重写`OnPrepareDC`正在打印的同时测试文档的末尾。 如果有没有更多的文档要打印，设置`m_bContinuePrinting`的成员`CPrintInfo`结构**FALSE**。  
  
-   若要将转义代码发送到每页的页上的打印机。 若要发送中的转义码`OnPrepareDC`，调用**转义**成员函数`pDC`参数。  
  
 调用基类版本的`OnPrepareDC`重写的开头。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&183;](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>CView::OnPreparePrinting  
 打印或预览文档之前，由框架调用。  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构描述当前的打印作业。  
  
### <a name="return-value"></a>返回值  
 开始打印，则非零值如果取消打印作业，则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。  
  
 必须重写此函数可启用打印和打印预览。 调用[DoPreparePrinting](#doprepareprinting)成员函数，并向其传递`pInfo`参数，然后返回其返回值;`DoPreparePrinting`显示打印对话框中，并创建打印机设备上下文。 如果您想要初始化默认值以外的值与打印对话框中，将值分配给的成员`pInfo`。 例如，如果您知道文档的长度，将值传递给[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成员函数`pInfo`之前调用`DoPreparePrinting`。 此值显示在收件人︰ 框中的打印对话框中的范围部分。  
  
 `DoPreparePrinting`不显示预览作业打印对话框。 如果你要绕过打印作业打印对话框中，检查**m_bPreview**的成员`pInfo`是**FALSE**然后将它设置为**TRUE**之前将其传递给`DoPreparePrinting`; 重置到**FALSE**之后。  
  
 如果您需要执行初始化，则需要访问`CDC`对象，表示打印机设备上下文 （例如，如果您需要之前需要了解的页大小指定文档的长度），重写`OnBeginPrinting`成员函数。  
  
 如果您想要设置的值**m_nNumPreviewPages**或**m_strPageDesc**成员`pInfo`参数，这样做之后调用`DoPreparePrinting`。 `DoPreparePrinting`成员函数集**m_nNumPreviewPages**到该应用程序中找到的值。INI 文件，并设置**m_strPageDesc**为其默认值。  
  
### <a name="example"></a>示例  
  重写`OnPreparePrinting`并调用`DoPreparePrinting`重写，因此框架将显示一个打印对话框中，并为您创建一个打印机 DC。  
  
 [!code-cpp[NVC_MFCDocView #&184;](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 如果您知道文档中包含多少个页面，在设置最大页数`OnPreparePrinting`之前调用`DoPreparePrinting`。 框架将在"收件人"框中的打印对话框中显示的最大的页码。  
  
 [!code-cpp[NVC_MFCDocView #&185;](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>CView::OnPrint  
 由框架以打印或预览文档的页调用。  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文。  
  
 `pInfo`  
 指向`CPrintInfo`结构描述当前的打印作业。  
  
### <a name="remarks"></a>备注  
 对于正在打印每一页，框架将调用此函数在调用后立即[OnPrepareDC](#onpreparedc)成员函数。 指定要打印的页`m_nCurPage`的成员[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)结构的`pInfo`指向。 默认实现调用[OnDraw](#ondraw)成员函数并将其传递打印机设备上下文。  
  
 以下原因之一，重写此函数︰  
  
-   若要允许多页文档的打印。 呈现只有对应于当前正在打印的页的文档的部分。 如果您使用`OnDraw`以进行呈现，可以调整视区原点，以使打印的文档相应部分。  
  
-   若要使打印的图像看起来不同于屏幕图像 （即，如果您的应用程序不是所见即所得）。 而不是传递到的设备上下文的打印机`OnDraw`，设备上下文用于呈现的图像使用不会显示在屏幕上的属性。  
  
     如果需要将 GDI 资源的不是为了屏幕显示使用的打印设置，请选择这些到之前绘制的设备上下文，然后取消选择它们之后。 应将这些 GDI 资源分配中[OnBeginPrinting](#onbeginprinting)和发布在[OnEndPrinting](#onendprinting)。  
  
-   若要实现的页眉或页脚。 您仍然可以使用`OnDraw`以通过限制可以在打印的区域进行渲染。  
  
 请注意， **m_rectDraw**的成员`pInfo`参数描述中的逻辑单元的页的可打印区域。  
  
 不要调用`OnPrepareDC`的重写中`OnPrint`; 框架将调用`OnPrepareDC`自动之前调用`OnPrint`。  
  
### <a name="example"></a>示例  
 下面是被重写的主干`OnPrint`函数︰  
  
 [!code-cpp[NVC_MFCDocView #&186;](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 另一个示例，请参阅[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。  
  
##  <a name="onscroll"></a>CView::OnScroll  
 由框架调用以确定是否滚动是可能的。  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nScrollCode`  
 指示用户的滚动条代码的滚动请求。 此参数由两个部分组成︰ 低位字节，它确定滚动正在进行水平的类型和一个高序位字节，它确定滚动正在进行垂直的类型︰  
  
- **SB_BOTTOM**滚动到下的顺序。  
  
- **SB_LINEDOWN**向下滚动一行。  
  
- **SB_LINEUP**向上滚动一行。  
  
- **SB_PAGEDOWN**向下滚动一页。  
  
- **SB_PAGEUP**向上滚动一页。  
  
- **SB_THUMBTRACK**拖动滚动框移到指定位置。 中指定当前位置`nPos`。  
  
- **SB_TOP**滚动到顶部。  
  
 `nPos`  
 滚动条代码是否包含滚动框的当前位置**SB_THUMBTRACK**; 否则不使用。 具体取决于初始滚动范围，`nPos`可以是负数，并且应强制转换为`int`如有必要。  
  
 `bDoScroll`  
 确定是否应实际指定的滚动操作。 如果**为 TRUE，**滚动时应采取的位置; 然后**FALSE**，则不应该发生滚动。  
  
### <a name="return-value"></a>返回值  
 如果`bDoScroll`是**TRUE**并且实际上滚动视图，然后返回非零; 否则为 0。 如果`bDoScroll`是**FALSE**，然后返回值，则返回如果`bDoScroll`已**TRUE**，即使您实际上不执行滚动。  
  
### <a name="remarks"></a>备注  
 该框架中一种情况下调用此函数`bDoScroll`设置为**TRUE**视图时收到的滚动条消息。 在这种情况下，您实际上滚动视图。 在其他情况下调用此函数与`bDoScroll`设置为**FALSE**时 OLE 项最初拖到拖放目标的自动滚动区域之前滚动实际的发生。 在这种情况下，您应该不实际滚动视图。  
  
##  <a name="onscrollby"></a>CView::OnScrollBy  
 当用户查看文档，通过拖动将 OLE 项针对视图的当前边框或通过操纵垂直或水平滚动条的存在视图之外的区域，由框架调用。  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `sizeScroll`  
 水平和垂直滚动区中的像素数。  
  
 `bDoScroll`  
 确定是否滚动视图的执行。 如果**为 TRUE，**然后滚动发生; 如果**FALSE**，则不会发生滚动。  
  
### <a name="return-value"></a>返回值  
 非零，如果视图能够滚动;否则为 0。  
  
### <a name="remarks"></a>备注  
 在派生类中此方法检查以确定是否可在用户请求，然后更新新区域，如有必要的方向滚动视图。 将自动调用此函数[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)才能执行实际的滚动请求。  
  
 此方法的默认实现不会更改视图中，但如果未调用，该视图不会发生滚动中`CScrollView`的派生类。  
  
 如果文档的宽度或高度超过 32767 像素，过去的 32767 滚动将失败，因为`OnScrollBy`调用使用了无效`sizeScroll`参数。  
  
##  <a name="onupdate"></a>CView::OnUpdate  
 后已修改该视图的文档，则由框架调用调用此函数[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) ，并允许视图以更新其显示效果以反映这些修改。  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>参数  
 `pSender`  
 指向修改了文档的视图或**NULL**如果要更新的所有视图都数。  
  
 `lHint`  
 包含有关所做的修改信息。  
  
 `pHint`  
 指向以存储信息所做的修改的对象。  
  
### <a name="remarks"></a>备注  
 它还由的默认实现调用[OnInitialUpdate](#oninitialupdate)。 默认实现将使整个客户端区域中，将它标记为对于绘制何时失效的下一步`WM_PAINT`接收消息。 如果你想要更新仅将映射到文档中的已修改部分这些区域，重写此函数。 若要这样做，您必须通过使用所提示参数修改的信息。  
  
 若要使用`lHint`，定义特殊的提示值、 通常是一个位掩码或枚举的类型，并拥有此文档将传递两个值之一。 若要使用`pHint`，提示从派生类[CObject](../../mfc/reference/cobject-class.md)并且具有在重写时，将指针传递给提示的对象; 该文档`OnUpdate`，使用[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成员函数可确定提示对象的运行时类型。  
  
 通常您不应执行任何绘图直接从`OnUpdate`。 而是确定设备坐标描述要求的更新; 的区域的矩形传递到此矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 这将导致绘制下一次时[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)接收消息。  
  
 如果`lHint`为 0 和`pHint`是**NULL**，文档已发送泛型更新通知。 如果视图收到泛型更新通知，或者如果它不能对提示进行解码，它应使其整个客户端区域。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)

