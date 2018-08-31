---
title: 设备上下文 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efda2666a1d7cf47a485a9e1ceb53c09f4966989
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203827"
---
# <a name="device-contexts"></a>设备上下文
设备上下文是包含显示器或打印机等设备的信息的绘制特性的 Windows 数据结构。 所有绘图调用都是通过设备上下文对象，封装 Windows Api，可用于绘制线条、 形状和文本。 设备上下文允许在 Windows 中的独立于设备的绘图。 用于绘制到屏幕、 打印机或图元文件设备上下文。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)对象将封装 Windows，调用的常规用法`BeginPaint`函数，然后绘制在设备上下文中，然后调用`EndPaint`函数。 `CPaintDC`构造函数调用`BeginPaint`，和析构函数调用`EndPaint`。 简化的过程是创建[CDC](../mfc/reference/cdc-class.md)对象和绘制，然后销毁`CDC`对象。 在 framework 中，即使此过程的大部分可以自动完成。 具体而言，你`OnDraw`函数传递`CPaintDC`已准备好 (通过`OnPrepareDC`)，并只需绘制到它。 由框架销毁和基础设备上下文从调用返回时发布到 Windows 应用`OnDraw`函数。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)对象将封装表示一个窗口的工作区的设备上下文的工作。 `CClientDC`构造函数调用`GetDC`函数和析构函数调用`ReleaseDC`函数。 [CWindowDC](../mfc/reference/cwindowdc-class.md)对象将封装表示整个窗口，其中包括其框架的设备上下文。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)对象封装到 Windows 图元文件绘制。 与此相反`CPaintDC`传递给`OnDraw`，在这种情况下，必须调用[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)自己。  
  
## <a name="mouse-drawing"></a>鼠标绘制  
 框架程序中的大多数绘图，和大多数设备上下文工作 — 在视图中完成`OnDraw`成员函数。 但是，仍可以使用用于其他用途的设备上下文对象。 例如，若要在视图中的鼠标移动提供跟踪反馈，您需要绘制直接到视图而无需等待`OnDraw`调用。  
  
 在这种情况下，你可以使用[CClientDC](../mfc/reference/cclientdc-class.md)直接到视图中绘制的设备上下文对象。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息  
  
-   [设备上下文 （定义）](https://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
-   [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [直线和曲线](https://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [实心的形状](https://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [字体和文本](/windows/desktop/gdi/fonts-and-text)  
  
-   [颜色](https://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [坐标空间和转换](https://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

