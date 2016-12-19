---
title: "在视图中绘制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "设备上下文, 屏幕绘图"
  - "绘图, 在视图中"
  - "视图类中的绘制消息"
  - "打印 [MFC], 视图"
  - "打印视图"
  - "视图, 打印"
  - "视图, 呈现"
  - "视图, 更新"
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在视图中绘制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

几乎在应用程序中的任何绘图在视图的 `OnDraw` 成员函数时，在视图类必须重写。\(例外是鼠标绘制，讨论\)。[通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)重写 `OnDraw` :  
  
1.  通过调用提供的文档成员函数获取数据。  
  
2.  通过调用设备上下文对象的成员函数来显示数据该框架将为 `OnDraw`。  
  
 在文档数据的某种方式更改时，必须重绘视图反映更改。  通常，通过视图，当用户进行更改。文档，这发生。  在这种情况下，调用文档的成员函数 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 视图通知在同一文档的所有视图的更新。  `UpdateAllViews` 每调用视图的成员函数。[更新时](../Topic/CView::OnUpdate.md) `OnUpdate` 的默认实现无效视图的整个工作区。  可以重写其无效映射到文档中修改的部分工作区的这些区域。  
  
 类 **CDocument** 的 `UpdateAllViews` 成员函数和 `CView` 类的 `OnUpdate` 成员函数可传递信息描述已修改文档的内容部分。  此“提示”机制可以限制视图必须重绘的区域。  `OnUpdate` 采用两“提示”参数。  第一，`lHint`，**LPARAM**类型，可以将您喜欢的任何数据，即，而第二个终结点，`pHint`，类型 `CObject`\*，可以将指针从 `CObject`派生的任何对象。  
  
 在视图变为无效时，Windows 将其发送 `WM_PAINT` 消息。  视图中处理 [OnPaint](../Topic/CWnd::OnPaint.md) 函数响应消息通过创建类 [CPaintDC](../mfc/reference/cpaintdc-class.md) 设备上下文对象并调用视图的 `OnDraw` 成员函数。  通常不必编写的重写 `OnPaint` 处理程序函数。  
  
 [设备上下文](../mfc/device-contexts.md) 是包含有关一个设备绘图特性的信息如显示或打印机的 Windows 数据结构。  所有绘制调用通过设备上下文对象调用。  有关绘制屏幕上，`OnDraw` 将 `CPaintDC` 对象。  有关绘制在打印机，将向其传递对当前设置打印机的 [CDC](../mfc/reference/cdc-class.md) 对象。  
  
 绘制的代码视图中先检索指向文档，然后通过设备上下文进行的调用。  下面的简单示例声明 `OnDraw` 过程：  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/CPP/drawing-in-a-view_1.cpp)]  
  
 在此示例中，应定义 `GetData` 函数，则派生类的成员，因此的文档。  
  
 示例打印所有字符串将从文档中获取，在视图中居中  如果 `OnDraw` 调用是为屏幕绘制，在传递 `pDC` 的 `CDC` 对象在构造函数已经调用 `BeginPaint`的 `CPaintDC`。  绘制到函数的调用通过设备上下文指针调用。  有关设备上下文以及绘图调用的信息，请参见和" *MFC 参考*[与 Window 对象一起使用](../mfc/working-with-window-objects.md)[CDC](../mfc/reference/cdc-class.md) 的类。  
  
 有关更多有关如何编写 `OnDraw`，请参见 [MFC 示例](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [使用视图](../mfc/using-views.md)