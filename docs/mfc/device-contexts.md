---
title: "设备上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26d4a0e32a8b24a72447cf4227be128659316c0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="device-contexts"></a>设备上下文
设备上下文是 Windows 数据结构，它包含一个显示或打印机等设备绘制属性相关信息。 所有的绘图调用都通过一个设备上下文对象，它封装 Windows Api 用于绘制线条、 形状和文本。 设备上下文允许在 Windows 中进行独立于设备的绘制。 设备上下文可以用于绘制到屏幕，打印机，或图元文件。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)对象将封装的 Windows 中，调用的常见惯用语法`BeginPaint`函数，然后绘制在设备上下文中，然后调用`EndPaint`函数。 `CPaintDC`构造函数调用`BeginPaint`，和析构函数调用`EndPaint`。 简化的过程是创建[CDC](../mfc/reference/cdc-class.md)对象绘制，，然后销毁`CDC`对象。 在框架中，即使此过程的大部分进行自动编辑。 具体而言，你`OnDraw`函数传递`CPaintDC`尚未准备好 (通过`OnPrepareDC`)，并只需绘制到它。 由框架销毁和基础设备上下文从调用返回后释放到 Windows 你`OnDraw`函数。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)对象将封装表示窗口工作区的设备上下文的工作。 `CClientDC`构造函数调用`GetDC`函数和析构函数调用`ReleaseDC`函数。 [CWindowDC](../mfc/reference/cwindowdc-class.md)对象将封装的设备上下文中表示整个窗口中，包括其框架。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)对象将封装到 Windows 图元文件绘制。 与此相反`CPaintDC`传递给`OnDraw`，在这种情况下，必须调用[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)自己。  
  
## <a name="mouse-drawing"></a>鼠标绘图  
 在框架程序中的大多数绘制-和大多数设备上下文工作 — 在视图中完成`OnDraw`成员函数。 但是，仍可以使用用于其他目的的设备上下文对象。 例如，若要提供的视图中的鼠标移动跟踪反馈，你需要直接绘制到视图而不等待`OnDraw`调用。  
  
 在这种情况下，你可以使用[CClientDC](../mfc/reference/cclientdc-class.md)要直接到视图中绘制的设备上下文对象。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [设备上下文 （定义）](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
-   [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [直线和曲线](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [实心的形状](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [字体和文本](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [颜色](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [坐标空间和转换](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

