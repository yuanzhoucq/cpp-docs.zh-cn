---
title: "输出 （设备上下文） 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.output
dev_langs: C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db7080c263ee6e98d458381d59446263490dfd7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="output-device-context-classes"></a>输出（设备上下文）类
这些类封装了不同类型的 Windows 中可用的设备上下文。  
  
 下面的类的大多数封装 Windows 设备上下文的句柄。 设备上下文是一个 Windows 对象包含有关的绘制特性的显示或打印机等设备的信息。 所有的绘图调用都通过设备上下文对象。 其他类派生自`CDC`封装专用的设备上下文的功能，包括对 Windows 图元文件的支持。  
  
 [CDC](../mfc/reference/cdc-class.md)  
 设备上下文的基类。 用于直接访问整个显示和访问 nondisplay 上下文，如打印机。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 在中使用的显示上下文`OnPaint`windows 的成员函数。 将自动调用`BeginPaint`构造和`EndPaint`上析构。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 用于 windows 的客户端区域的显示上下文。 例如，用于绘制鼠标事件即时响应。  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 整个 windows，包括客户端和非工作区显示上下文。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Windows 图元文件设备上下文。 Windows 图元文件包含一系列图形设备接口 (GDI) 命令可以重播创建映像的命令。 成员函数的调用`CMetaFileDC`记录在图元文件。  
  
## <a name="related-classes"></a>相关的类  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保留坐标 (x, y) 对。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保留距离、相对位置或匹配的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保留矩形区域的坐标。  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 封装用于操作的时间段内的椭圆、 多边形，或异常区域一个 GDI 区域。 与类中的剪辑成员函数一起使用`CDC`。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 显示并处理移动矩形对象和调整它们的用户界面。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 提供标准对话框中选择一种颜色。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 提供标准对话框中选择一种字体。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 为打印文件中提供的标准对话框。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

