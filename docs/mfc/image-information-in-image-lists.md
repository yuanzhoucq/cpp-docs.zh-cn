---
title: "图像列表中的图像信息 | Microsoft Docs"
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
  - "CImageList 类, 图像信息"
  - "图像列表 [C++], 图像信息"
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 图像列表中的图像信息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CImageList](../mfc/reference/cimagelist-class.md) 由图像列表检索信息的函数。  [GetImageInfo](../Topic/CImageList::GetImageInfo.md) 成员函数信息填充的 `IMAGEINFO` 结构。单个图像，包括图像和蒙板位图、数量以及颜色图面和每像素位数和图像的边框的句柄在位图图像中  使用该信息可以直接操作图像的位图。  
  
 [GetImageCount](../Topic/CImageList::GetImageCount.md) 成员函数检索图像数在图像列表中。  
  
 可以创建基于应用蒙板的图像和图标图像列表通过使用 [ExtractIcon](../Topic/CImageList::ExtractIcon.md) 成员函数。  函数返回新的图标的句柄。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)