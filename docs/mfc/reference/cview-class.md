---
title: "CView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子窗口, 视图"
  - "CView class"
  - "document/view architecture"
  - "frame windows [C++], 视图"
  - "input, and view class"
  - "MDI [C++], view windows"
  - "多个视图"
  - "打印预览, view windows"
  - "user input [C++], interpreting through view class"
  - "视图 [C++], view classes"
  - "windows [C++], 视图"
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为用户定义的视图选件类提供了基本功能。  
  
## 语法  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CView::CView](../Topic/CView::CView.md)|构造 `CView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CView::DoPreparePrinting](../Topic/CView::DoPreparePrinting.md)|显示打印对话框并创建打印机上下文;，并重写 `OnPreparePrinting` 成员函数时，请调用。|  
|[CView::GetDocument](../Topic/CView::GetDocument.md)|返回文档与视图。|  
|[CView::IsSelected](../Topic/CView::IsSelected.md)|测试文档项目是否已选中。  对OLE支持。|  
|[CView::OnDragEnter](../Topic/CView::OnDragEnter.md)|调用时，项目首次拖动到视图的拖放区域。|  
|[CView::OnDragLeave](../Topic/CView::OnDragLeave.md)|调用，将一个拖动的项出视图的拖放区域。|  
|[CView::OnDragOver](../Topic/CView::OnDragOver.md)|调用，在将项拖动到视图中的拖放区域。|  
|[CView::OnDragScroll](../Topic/CView::OnDragScroll.md)|调用确定光标是否拖入窗口中滚动区域。|  
|[CView::OnDrop](../Topic/CView::OnDrop.md)|调用，该项目被丢弃到视图的拖放区域，默认处理程序。|  
|[CView::OnDropEx](../Topic/CView::OnDropEx.md)|调用，该项目被丢弃到视图的拖放区域，主要处理程序。|  
|[CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)|调用，视图首先附加到文档之后。|  
|[CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)|调用，在 `OnDraw` 成员函数用于屏幕显示或 `OnPrint` 成员函数之前先对打印或打印预览调用。|  
|[CView::OnScroll](../Topic/CView::OnScroll.md)|调用，当OLE项在视图的内容边框外部拖动。|  
|[CView::OnScrollBy](../Topic/CView::OnScrollBy.md)|调用，即包含有效的就地OLE项的视图移动。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CView::OnActivateFrame](../Topic/CView::OnActivateFrame.md)|调用激活时，包含视图的框架窗口或停用。|  
|[CView::OnActivateView](../Topic/CView::OnActivateView.md)|调用激活时，视图。|  
|[CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|调用，当打印作业开始;重写分配图形设备接口\(GDI\)资源。|  
|[CView::OnDraw](../Topic/CView::OnDraw.md)|调用呈现文档的图像屏幕显示、打印、打印预览的。  需要的实现。|  
|[CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)|调用，当打印作业关闭;重写释放GDI资源。|  
|[CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)|调用，则预览模式退出。|  
|[CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|调用，在文档打印或已预览前;初始化打印对话框的重写。|  
|[CView::OnPrint](../Topic/CView::OnPrint.md)|调用或打印预览文档的页。|  
|[CView::OnUpdate](../Topic/CView::OnUpdate.md)|调用其文档的视图修改了通知。|  
  
## 备注  
 视图附加到文档并为文档和用户之间的中间方:视图呈现文档的图像在屏幕或打印机的并解释为操作的用户输入文档中。  
  
 视图是框架窗口的子级。  多个视图可以共享框架窗口，在拆分窗口。  视图选件类、框架窗口选件类和文档选件类之间的关系由 `CDocTemplate` 对象生成。  当用户打开一个新窗口或拆分现有一个记录时，框架构造新视图并附加到文档。  
  
 视图只能附加到一个文档，例如，但文档可以具有多个视图立即附加到它\)，如果文档在拆分窗口显示或在多个线程的多个子窗口文档界面\(MDI\)应用程序。  应用程序可以支持视图的不同类型为的文件类型;例如，字处理程序可能提供文档的全文视图，以及轮廓查看仅显示节标题。  如果使用一个拆分窗口，视图的这些不同的类型可以放置在单独的框架窗口或在单个框架窗口的单独窗格。  
  
 视图可以负责处理输入了几种不同的类型，例如通过拖放输入的或从菜单、工具栏或滚动条的输入类型、鼠标，以及命令。  视图接收其框架窗口转发的命令。  如果该视图不处理特定的命令，为其命令关联的向前文档。  与所有命令目标，视图处理消息传递消息映射。  
  
 视图负责显示和修改文档中的数据，但不可保存。  本文档提供视图有关其数据的必要的详细信息。  可以直接允许视图访问文档中的数据成员，或者您可以为视图选件类提供在文档选件类的成员函数调用。  
  
 当文件中的数据更改时，视图负责更改通常调用文档的 [CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 功能，通过调用每个的 `OnUpdate` 成员函数通知任何其他视图。  `OnUpdate` 的默认实现无效视图的整个工作区。  您可以重写其无效映射到文档的修改后的部分工作区的这些区域。  
  
 若要使用 `CView`，从中派生选件类并实现 `OnDraw` 成员函数执行屏幕显示。  还可以使用 `OnDraw` 执行打印和打印预览。  结构处理打印和打印预览的循环将文档。  
  
 与 [CWnd::OnHScroll](../Topic/CWnd::OnHScroll.md) 和 [CWnd::OnVScroll](../Topic/CWnd::OnVScroll.md) 成员函数的视图处理滚动条消息。  可以实现滚动条消息处理这些函数，也可以使用 `CView` 派生类 [CScrollView](../../mfc/reference/cscrollview-class.md) 处理滚动为。  
  
 除了 `CScrollView`外，Microsoft基础选件类库提供 `CView`从派生的其他九选件类:  
  
-   [CCtrlView](../../mfc/reference/cctrlview-class.md)，允许使用的视图文档\)使用树视图结构，列表，并且，rich edit控件。  
  
-   [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，在对话框中显示数据库记录的视图控件。  
  
-   [CEditView](../../mfc/reference/ceditview-class.md)，提供简单的多行文本编辑器的视图。  可以使用 `CEditView` 对象作为控件在对话框以及在文档的视图。  
  
-   [CFormView](../../mfc/reference/cformview-class.md)，包含对话框的控件和基于对话框模板资源的一个滚动视图。  
  
-   [CListView](../../mfc/reference/clistview-class.md)，允许使用的视图文档\)查看体系结构与列表控件。  
  
-   [CRecordView](../../mfc/reference/crecordview-class.md)，在对话框中显示数据库记录的视图控件。  
  
-   [CRichEditView](../../mfc/reference/cricheditview-class.md)，允许使用的视图文档\)支持丰富查看体系结构编辑控件。  
  
-   [CScrollView](../../mfc/reference/cscrollview-class.md)，自动提供滚动的视图支持。  
  
-   [CTreeView](../../mfc/reference/ctreeview-class.md)，允许使用的视图文档\)使用树控件查看体系结构。  
  
 `CView` 选件类还具有派生的实现选件类继承 **CPreviewView**，框架用于执行打印预览。  此选件类提供功能支持唯一、打印预览窗口，如工具栏，单或双页预览和缩放，也就是说，扩展了预览的图像。  您不需要调用或重写任何一个CPreviewView的成员函数，除非要实现自己打印预览自己的接口\(例如，因此，如果要支持编辑在打印预览模式）。  有关使用 `CView`的更多信息，请参见 [文档\/视图结构](../../mfc/document-view-architecture.md) 和 [打印](../../mfc/printing.md)。  有关更多详细信息此外，请参见 [技术说明30](../../mfc/tn030-customizing-printing-and-print-preview.md) 在自定义打印预览。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDIDOCVW示例](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)