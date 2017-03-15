---
title: "打印预览结构 | Microsoft Docs"
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
  - "预览打印"
  - "打印预览, 体系结构"
  - "打印预览, 对 MFC 的修改"
  - "打印预览, 进程"
  - "打印 [MFC], 打印预览"
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 打印预览结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明 MFC 框架如何实现打印预览功能。  所涵盖的主题包括：  
  
-   [打印预览进程](#_core_the_print_preview_process)  
  
-   [修改打印预览](#_core_modifying_print_preview)  
  
 打印预览与屏幕显示和打印有所不同，因为它不是直接绘制图像在设备上，而是应用程序必须使用屏幕模拟打印机。  为此，Microsoft 基础类库定义了从派生自 [CDC 类](../mfc/reference/cdc-class.md)的特定 \(未证明的\)类，调用 **CPreviewDC**。  所有设备上下文包含两个 `CDC` 对象，但是，通常它们是相同的。  在 **CPreviewDC** 对象中它们是不同的：一个表示模拟的打印机，另一个表示输出实际显示的屏幕。  
  
##  <a name="_core_the_print_preview_process"></a> 打印预览进程  
 当用户选择从 **文件** 菜单中打印预览命令时，框架创建 **CPreviewDC** 对象。  只要应用程序运行设置打印机设备上下文特性的操作，则该框架在屏幕设备上下文中执行类似的操作。  例如，如果应用程序选择一种字体打印，框架选择模拟打印机字体显示在屏幕上。  每当应用程序将输出发送到打印机，框架发送输出到屏幕。  
  
 打印预览与每个绘图文档页顺序的打印也不同。  在打印期间，框架继续打印循环，直到某范围分页呈现。  在打印预览期间，两页随时显示，然后应用程序等待；进一步不显示新页，直至用户响应。  在打印预览期间，应用程序还必须响应 `WM_PAINT` 消息，类似于普通屏幕显示期间。  
  
 [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 函数调用，在预览模式调用时，与在打印作业的开始一样。  [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) 结构传递给函数包含的成员值，可以对其进行设置以调整打印预览操作的某些特性。  例如，可以设置 **m\_nNumPreviewPages** 成员，指定是否要一页或两页预览文档模式。  
  
##  <a name="_core_modifying_print_preview"></a> 修改打印预览  
 可以修改打印预览行为和外观，许多方法相当容易。  例如，除了别的之外你还可以：  
  
-   创建打印预览窗口，以显示便于访问文档所有页的滚动条。  
  
-   创建打印预览通过在当前页开始显示以保留在文档中的用户位置。  
  
-   由于打印预览和打印执行不同初始化。  
  
-   导致在你自己格式下打印预览以显示页码。  
  
 如果您了解文档持续多久并用适当的值调用 `SetMaxPage`，则在打印期间，框架可以在预览模式使用此信息。  框架一旦知道文档的长度，可以为预览窗口提供滚动条，允许用户在预览模式下滚动上下页。  如果尚未设置文档的长度，框架不能定位滚动框以指示当前位置，所以框架无法添加一个滚动条。  在这种情况下，必须使用在预览窗口控件条上的“下一页”和“上一页”按钮对文档翻页。  
  
 对于打印预览，您或许会发现赋值到 `CPrintInfo`的 `m_nCurPage` 成员非常有用，即使你在普通打印时不会那样做。  在普通打印期间，此成员将信息由框架传播到视图类。  这使得框架知道该打印哪个视图。  
  
 相比之下，当打印预览模式启动时，`m_nCurPage` 成员以相反方向从视图传播信息到框架。  框架使用该成员值确定应先预览哪个页面。  该成员默认值为 1，以便文档的第一页显示。  在打印预览命令调用后，您可以重写 `OnPreparePrinting` 以将此成员设置为将要显示的页码。  这样，当从普通显示模式切换到打印预览模式时，应用程序保留用户的当前位置。  
  
 有时您可能希望 `OnPreparePrinting` 执行不同初始化，这取决于它是否为打印作业或打印预览调用。  通过检查在 `CPrintInfo` 结构的 **m\_bPreview** 成员变量来确定这一点。  在打印预览调用时，该成员设置为 **TRUE**。  
  
 `CPrintInfo` 结构还包含一个名为 **m\_strPageDesc**的成员，单页和多页模式下在屏幕底部使用格式字符串。  默认情况下这些字符串是窗体“*N*页”和“*n*页   \-*m*”，但您可以修改 **m\_strPageDesc** 从 `OnPreparePrinting` 内以及设置字符串为一些更具体的操作。  有关详细信息，请参阅*MFC Reference* 中的[CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md)。  
  
## 请参阅  
 [打印和打印预览](../mfc/printing-and-print-preview.md)   
 [打印](../mfc/printing.md)   
 [CView Class](../mfc/reference/cview-class.md)   
 [CDC 类](../mfc/reference/cdc-class.md)