---
title: 设备上下文
ms.date: 11/04/2016
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
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508655"
---
# <a name="device-contexts"></a>设备上下文

"设备上下文" 是一种 Windows 数据结构, 其中包含有关设备 (例如显示器或打印机) 的绘图属性的信息。 所有绘图调用都通过设备上下文对象进行, 该对象封装用于绘制线条、形状和文本的 Windows Api。 设备上下文允许 Windows 中与设备无关的绘图。 设备上下文可用于绘制到屏幕、打印机或图元文件。

[CPaintDC](../mfc/reference/cpaintdc-class.md)对象封装 Windows 的常见用法, 调用`BeginPaint`函数, 然后在设备上下文中绘制`EndPaint` , 然后调用函数。 构造函数调用`BeginPaint` , 析构函数调用`EndPaint`。 `CPaintDC` 简化的过程是创建[CDC](../mfc/reference/cdc-class.md)对象, 绘制并销毁`CDC`对象。 在框架中, 大部分甚至是自动化的过程。 特别是, `OnDraw`您的`CPaintDC`函数已通过已准备好 ( `OnPrepareDC`通过), 您只需将其绘制到其中即可。 它由框架销毁, 基础设备上下文在从对`OnDraw`函数的调用返回时发布到 Windows。

[CClientDC](../mfc/reference/cclientdc-class.md)对象封装使用只表示窗口工作区的设备上下文。 构造函数调用函数, 析构函数调用`ReleaseDC`函数。 `GetDC` `CClientDC` [CWindowDC](../mfc/reference/cwindowdc-class.md)对象封装表示整个窗口的设备上下文, 包括其框架。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)对象将绘图封装到 Windows 图元文件中。 与传递到`OnDraw`的`CPaintDC`不同, 在这种情况下, 您必须自行调用[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) 。

## <a name="mouse-drawing"></a>鼠标绘制

框架程序中的大多数绘图 (以及大多数设备上下文工作) 都是在视图的`OnDraw`成员函数中完成的。 不过, 您仍可以将设备上下文对象用于其他目的。 例如, 若要为视图中的鼠标移动提供跟踪反馈, 需要直接在视图中进行绘制, 而无需`OnDraw`等待调用。

在这种情况下, 可以使用[CClientDC](../mfc/reference/cclientdc-class.md)设备上下文对象直接在视图中进行绘制。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [设备上下文 (定义)](/windows/win32/gdi/device-contexts)

- [在视图中绘制](../mfc/drawing-in-a-view.md)

- [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)

- [直线和曲线](/windows/win32/gdi/lines-and-curves)

- [实心形状](/windows/win32/gdi/filled-shapes)

- [字体和文本](/windows/win32/gdi/fonts-and-text)

- [颜色](/windows/win32/gdi/colors)

- [坐标空格和转换](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>请参阅

[窗口对象](../mfc/window-objects.md)
