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
ms.openlocfilehash: 6bddebb17663e8d22a4bf784d2a9d08a2f912e59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651823"
---
# <a name="output-device-context-classes"></a>输出（设备上下文）类

这些类封装了不同类型的 Windows 中可用的设备上下文。

大多数以下类封装 Windows 设备上下文的句柄。 设备上下文是一个 Windows 对象，包含显示器或打印机等设备的信息的绘制特性。 所有绘图调用都是通过设备上下文对象。 其他类派生自`CDC`封装专用的设备上下文的功能，包括对 Windows 图元文件的支持。

[CDC](../mfc/reference/cdc-class.md)<br/>
设备上下文的基类。 用于直接访问整个显示和访问 nondisplay 上下文，如打印机。

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
在中使用的显示上下文`OnPaint`windows 的成员函数。 将自动调用`BeginPaint`构造和`EndPaint`析构。

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Windows 的客户端区域显示上下文。 例如，用于绘制鼠标事件即时响应。

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
整个 windows，包括客户端和非工作区显示上下文。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Windows 图元文件设备上下文。 Windows 图元文件包含一系列图形设备接口 (GDI) 命令来创建映像，可以重播。 对成员函数的调用`CMetaFileDC`中图元文件记录。

## <a name="related-classes"></a>相关的类

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保留坐标 (x, y) 对。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保留距离、相对位置或匹配的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保留矩形区域的坐标。

[CRgn](../mfc/reference/crgn-class.md)<br/>
封装用于操作的时间段内的椭圆，多边形，或不定期区域的 GDI 区域。 与类中的剪辑成员函数结合使用`CDC`。

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
显示和处理调整大小和移动矩形对象的用户界面。

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
提供的标准对话框用于选择一种颜色。

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
提供用于选择字体的标准对话框。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供用于打印文件的标准对话框。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

