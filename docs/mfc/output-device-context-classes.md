---
title: "输出（设备上下文）类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "设备上下文, 类"
  - "输出类"
  - "绘制类"
  - "打印类"
  - "屏幕输出类"
  - "窗口绘制类"
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 输出（设备上下文）类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类封装这些设备上下文的不同类型的可用窗口中。  
  
 下面的大多数类封装Windows 设备上下文的句柄。  包含有关一设备绘图特性的信息如显示或打印机的设备上下文是窗口对象。  所有绘制调用通过设备上下文对象调用。  从 `CDC` 派生的其他类封装专用的设备上下文功能，包括 Windows 图元文件的支持。  
  
 [CDC](../mfc/reference/cdc-class.md)  
 设备上下文的基类。  使用直接用于访问整个演示以及访问不显示上下文 ，如打印机。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 在 `OnPaint` 窗口中的成员函数的上下文显示。  自动调用构造上使用的 `BeginPaint` 和 `EndPaint`。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 窗口的工作区显示一个上下文。  例如，用于绘制到鼠标事件的直接响应。  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 整个窗口中的显示上下文，包括工作区和非工作区。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Windows 元文件的设备上下文。  Windows 元文件包含图形设备接口中重播生成图像的 \(GDI\) 命令序列。  对 `CMetaFileDC` 的成员函数在元文件中记录。  
  
## 相关类  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保持坐标 \(x，y\) 对。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保持疏远，相对位置或匹配的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保留矩形区域坐标。  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 封装操作的椭圆形，或不多角形规则的区域的 GDI 区域窗口内。  与剪辑成员一起在类 `CDC`函数。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 显示和句柄调整和移动矩形对象的用户界面。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 用于选择颜色提供标准对话框。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 用于选择字体提供标准对话框。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 打印文件为提供标准对话框。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)