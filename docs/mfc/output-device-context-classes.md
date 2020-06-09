---
title: 输出（设备上下文）类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: b15f5034604f9d6b67574288140b79b144692478
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615362"
---
# <a name="output-device-context-classes"></a>输出（设备上下文）类

这些类封装了 Windows 中可用的不同类型的设备上下文。

以下大多数类封装 Windows 设备上下文的句柄。 设备上下文是一个 Windows 对象，其中包含有关设备（例如显示器或打印机）的绘图属性的信息。 所有绘图调用都通过设备上下文对象进行。 派生自的其他类 `CDC` 封装专用设备上下文功能，包括对 Windows 图元文件的支持。

[CDC](reference/cdc-class.md)<br/>
设备上下文的基类。 直接用于访问整个显示器和访问 nondisplay 上下文（如打印机）。

[CPaintDC](reference/cpaintdc-class.md)<br/>
在 windows 的成员函数中使用的显示上下文 `OnPaint` 。 `BeginPaint`在构造和 `EndPaint` 析构上自动调用。

[CClientDC](reference/cclientdc-class.md)<br/>
Windows 的客户端区域的显示上下文。 例如，用于在对鼠标事件的即时响应中进行绘制。

[CWindowDC](reference/cwindowdc-class.md)<br/>
整个窗口的显示上下文，包括客户端和非工作区。

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Windows 图元文件的设备上下文。 Windows 图元文件包含一系列图形设备接口（GDI）命令，可通过重播这些命令来创建映像。 对的成员函数的调用 `CMetaFileDC` 记录在图元文件中。

## <a name="related-classes"></a>相关类

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保留坐标 (x, y) 对。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保留距离、相对位置或匹配的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保留矩形区域的坐标。

[CRgn](reference/crgn-class.md)<br/>
封装用于处理窗口中的椭圆形、多边形或不规则区域的 GDI 区域。 与类中的剪辑成员函数结合使用 `CDC` 。

[CRectTracker](reference/crecttracker-class.md)<br/>
显示并处理调整和移动矩形对象的用户界面。

[CColorDialog](reference/ccolordialog-class.md)<br/>
提供用于选择颜色的标准对话框。

[CFontDialog](reference/cfontdialog-class.md)<br/>
提供用于选择字体的标准对话框。

[CPrintDialog](reference/cprintdialog-class.md)<br/>
提供用于打印文件的标准对话框。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
