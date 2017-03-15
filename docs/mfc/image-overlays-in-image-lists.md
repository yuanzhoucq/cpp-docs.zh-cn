---
title: "图像列表中的图像覆盖 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 类, 图像覆盖"
  - "图像列表 [C++], 图像覆盖"
  - "覆盖"
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 图像列表中的图像覆盖
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个图像列表 \([CImageList](../mfc/reference/cimagelist-class.md)\) 包括图像列表用作覆盖掩码。  掩码”是“覆盖图像透明地绘制通过另一个图像。  所有图像用作覆盖掩码。  可以指定每个图像列表四个覆盖的掩码。  
  
 使用 [SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) 成员函数，则将图像的索引。覆盖蒙板列表，图像的索引和覆盖蒙板的索引。  请注意文件掩码中的索引。基于而不是从零开始的。  
  
 可以绘制到图像中的覆盖蒙板使用单个调用 **绘制**。  包括参数绘制图像的索引和覆盖蒙板的索引。  必须使用 [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) 宏覆盖蒙板指定的索引。  当调用 [DrawIndirect](../Topic/CImageList::DrawIndirect.md) 成员函数时，还可以指定是否覆盖图像。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)