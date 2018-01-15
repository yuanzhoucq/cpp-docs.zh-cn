---
title: "在视图中绘制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3457597edce1b7ce36b132d1bdd16d286cb94d03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drawing-in-a-view"></a>在视图中绘制
在你的应用程序中的几乎所有绘制出现在视图的`OnDraw`成员函数，你必须在视图类中重写。 (例外情况是鼠标绘制中, 所述[通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)。)你`OnDraw`重写：  
  
1.  通过调用成员函数，你提供的文档获取数据。  
  
2.  通过调用成员函数的框架将传递到的设备上下文对象中显示的数据`OnDraw`。  
  
 当以某种方式更改文档的数据时，则必须重绘视图以反映所做的更改。 通常情况下，此情况在用户可以通过在文档视图的更改。 在这种情况下，视图调用文档的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成员函数来通知进行自我更新将同一文档上的所有视图。 `UpdateAllViews`调用每个视图[OnUpdate](../mfc/reference/cview-class.md#onupdate)成员函数。 默认实现`OnUpdate`使视图的整个工作区无效。 你可以重写它要使其无效仅这些区域的工作区映射到文档的修改后的部分。  
  
 `UpdateAllViews`类的成员函数**CDocument**和`OnUpdate`类的成员函数`CView`让传递描述文档的哪些部分已修改的信息。 此"提示"机制，可以将限制视图必须重绘的区域。 `OnUpdate`采用两个"提示"参数。 首先， `lHint`，类型的**LPARAM**，允许传递任何数据，第二个， `pHint`，类型的`CObject`*，允许将指针传递到派生自的任何对象`CObject`。  
  
 Windows 时视图将变得无效，将其发送`WM_PAINT`消息。 该视图的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)处理程序函数响应消息通过创建类的设备上下文对象[CPaintDC](../mfc/reference/cpaintdc-class.md)并调用你的视图`OnDraw`成员函数。 你通常无需编写重写`OnPaint`处理程序函数。  
  
 A[设备上下文](../mfc/device-contexts.md)是包含有关的绘制特性以显示或打印机等设备的信息的 Windows 数据结构。 所有的绘图调用都通过设备上下文对象。 在屏幕上，绘制的`OnDraw`传递`CPaintDC`对象。 对于在打印机上进行绘制，它传递[CDC](../mfc/reference/cdc-class.md)为当前的打印机设置的对象。  
  
 代码视图中绘制首先检索指向文档，然后通过设备上下文的绘图调用。 以下是一个简单`OnDraw`示例阐释了过程：  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 在此示例中，会定义`GetData`作为您的派生的文档类的成员函数。  
  
 示例输出它会从文档中，视图的中间获取任何字符串。 如果`OnDraw`调用是针对屏幕绘制`CDC`传入的对象`pDC`是`CPaintDC`已调用其构造函数`BeginPaint`。 对绘图函数的调用都通过设备上下文指针。 有关设备上下文和绘图调用的信息，请参阅类[CDC](../mfc/reference/cdc-class.md)中*MFC 参考*和[使用窗口对象](../mfc/working-with-window-objects.md)。  
  
 有关如何编写的更多示例`OnDraw`，请参阅[MFC 示例](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用视图](../mfc/using-views.md)

