---
title: "图像列表类型 | Microsoft Docs"
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
  - "CImageList 类, 类型"
  - "图像列表 [C++], 类型"
  - "列表 [C++], 图像"
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 图像列表类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有图像列表 \([CImageList](../mfc/reference/cimagelist-class.md)\) 的两种类型：nonmasked 和阴影。  “nonmasked 图像列表”包含一个或多个图像颜色的位图。  “被遮掩的图像列表”包括相等大小两个位图。  第一个是图像的位图包含颜色，并且，第二个是包含一系列蒙板 \- 一在第一个复制的每个图像的单色位图。  
  
 某一 **创建** 成员函数的重载采用标志指示图像列表是否被遮掩。\(其他重载生成被遮掩的图像列表中。\)  
  
 当一 nonmasked 绘制图像时，它复制到目标设备；上下文也就是说绘制到设备上下文的现有的背景色。  当一个应用蒙板的图像时，图像的位合并时，通常会在目标设备上下文背景色将变为显示的位图的位屏蔽的透明区域。  在绘制 Masked 映像时，可以指定一些绘图样式。  例如，您可以指定是抖动的图像指示选定对象。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)