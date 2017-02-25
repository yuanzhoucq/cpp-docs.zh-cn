---
title: "多页文档 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintInfo 结构, 多页文档"
  - "文档页与打印机页"
  - "文档, 分页"
  - "文档, 打印"
  - "DoPreparePrinting 方法和分页"
  - "多页文档"
  - "OnBeginPrinting 方法"
  - "OnDraw 方法, 打印"
  - "OnEndPrinting 方法"
  - "OnPrepareDC 方法"
  - "OnPreparePrinting 方法"
  - "OnPrint 方法"
  - "重写, 查看用于打印的类函数"
  - "pages, 打印"
  - "分页"
  - "分页, 打印多页文档"
  - "打印机模式"
  - "打印机, 打印机模式"
  - "打印 [MFC], 多页文档"
  - "打印 [MFC], 分页"
  - "打印 [MFC], 协议"
  - "protocols, 打印协议"
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 多页文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述窗口打印协议并阐释了如何打印包含多页的文档。  本文涵盖以下主题：  
  
-   [打印协议](#_core_the_printing_protocol)  
  
-   [重写视图类函数](#_core_overriding_view_class_functions)  
  
-   [分页](#_core_pagination)  
  
-   [打印机页与文档页](#_core_printer_pages_vs.._document_pages)  
  
-   [打印时分页](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> 打印协议  
 打印多页文档，框架和视图按下列方式交互。  框架首先演示 **打印** 对话框，创建打印机的设备上下文，并且调用 [CDC](../mfc/reference/cdc-class.md) [StartDoc](../Topic/CDC::StartDoc.md) 对象的成员函数。  然后，文档的每页框架，需要 `CDC` 对象的函数 [为 StartPage](../Topic/CDC::StartPage.md) 成员，指示视图对象打印页，然后调用 [EndPage](../Topic/CDC::EndPage.md) 成员函数。  如果必须在启动某个特定页之前更改打印机模式，视图称为 [ResetDC](../Topic/CDC::ResetDC.md)，更新包含新打印机模式信息的结构。[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) 在整个文档打印时，框架调用[EndDoc](../Topic/CDC::EndDoc.md)成员函数。  
  
##  <a name="_core_overriding_view_class_functions"></a> 重写视图类函数  
 [CView](../mfc/reference/cview-class.md) 类定义在打印期间，由框架调用的成员函数。  通过在重写视图类的这些函数，则提供框架的打印逻辑和视图类的打印逻辑之间建立连接。  下表列出这些成员函数。  
  
### 打印的 CView 的可重写的函数  
  
|Name|重写的原因|  
|----------|-----------|  
|[OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|到打印对话框插入值，尤其是文档的长度|  
|[OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|分配字体 GDI 或其他资源|  
|[OnPrepareDC](../Topic/CView::OnPrepareDC.md)|为给定的页上下文的时间打印设备调整特性，或者执行分页|  
|[OnPrint](../Topic/CView::OnPrint.md)|打印某一特定页|  
|[OnEndPrinting](../Topic/CView::OnEndPrinting.md)|释放 GDI 资源|  
  
 可以在其他函数中执行与打印相关的处理，但这些函数是驱动打印过程的文件。  
  
 下图演示晒印方法涉及的步骤并显示每一个 `CView` 打印成员函数的位置调用。  本文的其余部分将更详细地说明这些步骤的大部分。  晒印方法的附加部分，文章 [GDI 资源分配](../mfc/allocating-gdi-resources.md)中描述。  
  
 ![打印循环过程](../Image/vc37C71.gif "vc37C71")  
打印循环  
  
##  <a name="_core_pagination"></a> 分页  
 框架存储许多位于 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 结构中的有关打印作业的信息。  `CPrintInfo` 中的值与分页；这些值可以被访问，如下表所示。  
  
### 在 CPrintInfo 存储的页数信息  
  
|成员变量或。<br /><br /> 函数名|引用的页面|  
|--------------------|-----------|  
|`GetMinPage`\/`SetMinPage`|文档第一页|  
|`GetMaxPage`\/`SetMaxPage`|文档之前页|  
|`GetFromPage`|要打印的第一页|  
|`GetToPage`|要打印的最后一页|  
|`m_nCurPage`|当前打印的页|  
  
 页码开始显示 1，即，第一页的第 1，而不是 0。  有关这些和 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)的其他成员的更多信息，请参见 *MFC 参考*。  
  
 在晒印方法开头，则框架调用视图的 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 成员函数传递，指向 `CPrintInfo` 结构。  应用程序向导提供调用 [DoPreparePrinting](../Topic/CView::DoPreparePrinting.md)`OnPreparePrinting` 的实现，`CView`的其他成员函数。  `DoPreparePrinting` 是显示打印对话框并且创建打印机设备上下文的函数。  
  
 此时应用程序无法知道文档中有多少页。  为文档的第一个和最后一个页使用文档的默认值 1 和 0xFFFF。  如果您知道页面文档具有多少，在将其发送给 `DoPreparePrinting`之前，请重写 `OnPreparePrinting` 并调用 [SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md) `CPrintInfo` 结构。  这可以指定文档的长度。  
  
 `DoPreparePrinting`然后显示打印的对话框。  当返回时，`CPrintInfo` 结构包含用户指定的值。  如果仅打印选定范围的用户希望页，即或她在打印对话框可以指定开始日期和数字。端页  使用 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)的 `GetFromPage` 和 `GetToPage` 函数检索框架，这些值。  如果用户未指定页范围，框架调用 `GetMinPage` 和 `GetMaxPage` 并使用返回的值打印整个文档。  
  
 对于要打印文档的每页，框架调用在类视图和[OnPrepareDC](../Topic/CView::OnPrepareDC.md) [OnPrint](../Topic/CView::OnPrint.md)的两个成员函数，并将函数每两个参数：到 [CDC](../mfc/reference/cdc-class.md) 对象的指针以及指向 `CPrintInfo` 结构。  每次框架调用 `OnPrepareDC` 和 `OnPrint`，它将 `CPrintInfo` 结构的 `m_nCurPage` 成员的值不同。  此框架调用应打印的页的视图。  
  
 [OnPrepareDC](../Topic/CView::OnPrepareDC.md) 成员函数用于屏幕显示。  在绘制前，它所做调整到设备上下文。  `OnPrepareDC` 在打印中充当类似的效果，但两个差异：首先，`CDC` 对象表示一台打印机设备上下文 \(而不是屏幕设备上下文，并且，接下来，`CPrintInfo` 对象将作为第二个参数。\(此参数是 **NULL**，当 `OnPrepareDC` 为屏幕显示调用时。\)重写 `OnPrepareDC` 将调整到根据哪些设备上下文要打印的页。  例如，您可以移动视区原点和剪辑区域确保文档的相应部分印出。  
  
 [OnPrint](../Topic/CView::OnPrint.md) 成员函数执行页的实际打印。  文章 [默认打印如何完成](../mfc/how-default-printing-is-done.md) 演示框架如何用打印机打印设备上下文调用 [OnDraw](../Topic/CView::OnDraw.md) 来执行打印。  更确切地说，`CPrintInfo` 结构和设备上下文的框架调用 `OnPrint` 和 `OnPrint` 传递 `OnDraw`的设备上下文。  重写 `OnPrint` 实现应只完成在打印期间和不为屏幕显示的所有呈现。  例如，打印页眉或页脚 \(文章 [页眉和页脚](../mfc/headers-and-footers.md)。更多信息。\)  然后从要执行呈现的 `OnPrint` 重写中调用 `OnDraw` 共有屏幕显示和打印。  
  
 事实，`OnDraw` 执行屏幕显示和打印的呈现表示应用程序 WYSIWYG:“所见即所获取”。但是，假设不编写 WYSIWYG 应用程序。  例如，假设使用用粗体供打印，但显示控制代码可以将屏幕上的粗体文本的文本编辑器。  在这种情况下，可为屏幕显示强使用 `OnDraw`。  当重写 `OnPrint`时，请重写调用与调用 `OnDraw` 对绘制单独函数。  函数文档绘制方式显示它在纸张，使用屏幕上不显示的特性。  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> 打印机页与文档页  
 当引用页面时，页面区分打印机的概念和页之间建立文档的概念有时是必需的。  从打印机的角度，页是一幅的。  但是，一张纸文档的页不一定相同。  例如，在中，如果要打印新闻稿，将折叠一张表，进行可能包含两种文档的第一个和最后一个页，并行。  同样，如果打印电子表格，文档根本不包含页。  不过，一张在其上可能包含 1 至第 20 行，6 至 10 列。  
  
 在 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 结构的所有页面引用打印机页。  框架调用一次 `OnPrepareDC` 和 `OnPrint` 将通过打印机的每张进行的。  当您重写函数 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 指定文档的长度时，必须使用打印机页。  如果存在一个一对一的通信 \(即一台打印机页等于一文档页\)，则这非常容易。  如果，另一方面，文档页和打印机页不直接对应，您必须强制转换它们之间。  例如，考虑打印电子表格。  当重写 `OnPreparePrinting`时，必须计算需要多少个进行打印整个电子表格然后使用该值，当调用 `CPrintInfo`的 `SetMaxPage` 成员函数。  相似，当重写 `OnPrepareDC`时，必须将 `m_nCurPage` 变为显示在该特定表然后相应地对表进行调整视区的源范围的行和列。  
  
##  <a name="_core_print.2d.time_pagination"></a> 打印时分页  
 在某些情况下，类视图不能预先知道文档多长时间直到实际打印。  例如，假定应用程序不是WYSIWYG，这样，在屏幕的文档的长度不对应在打印时其长度。  
  
 在重写视图类时，[OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 这导致问题：，因为您不知道文档的长度，可以不传递值。[CPrintInfo](../mfc/reference/cprintinfo-structure.md) 结构中的 `SetMaxPage` 函数。  如果用户未指定页码在停止使用打印对话框，框架时不知道停止打印循环。  在结束时，唯一方式决定打印时将停止循环输出文档和发现。  视图类必须检查文档末尾，并在打印时，然后通知框架，在结束时到达。  
  
 框架时依赖视图类的函数 [OnPrepareDC](../Topic/CView::OnPrepareDC.md) 调用就会停止。  在对 `OnPrepareDC`的每次调用，则框架检查调用 `m_bContinuePrinting`后的 `CPrintInfo` 结构的成员。  默认值为**TRUE.**。只要保持，因此延续框架打印循环。  如果设置为 **FALSE**，框架已停止。  执行打印时分页、重写 `OnPrepareDC` 检查文档末尾是否已到达和 `m_bContinuePrinting` 设置为 **FALSE**，则具有。  
  
 如果当前页比 1.，大于 `OnPrepareDC` 的默认实现将 `m_bContinuePrinting` 设置为 **FALSE**。  这意味着，如果文档的长度不指定，则假定文档框架中早已一页。  这样的一个后果是必须注意，如果调用 `OnPrepareDC`的基类版本。  不要假设，`m_bContinuePrinting` 将为 **TRUE** 之后调用基类版本。  
  
### 您想进一步了解什么？  
  
-   [页眉和页脚](../mfc/headers-and-footers.md)  
  
-   [分配 GDI 资源](../mfc/allocating-gdi-resources.md)  
  
## 请参阅  
 [打印](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC 类](../mfc/reference/cdc-class.md)