---
title: "操作图像列表 | Microsoft Docs"
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
  - "CImageList 类, 操作"
  - "图像列表 [C++], 操作"
  - "列表 [C++], 图像"
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 操作图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[替换](../Topic/CImageList::Replace.md) 成员函数将新图像替换在图像列表 \([CImageList](../mfc/reference/cimagelist-class.md)\) 的图像。  如果需要动态增加图像数在图像列表的对象，该函数也很有用。  函数 [SetImageCount](../Topic/CImageList::SetImageCount.md) 动态将图像列表存储了图像的数目。  如果增大图像列表的范围，请调用 **替换** 将图像添加到图像新的槽。  如果是减小图像列表的跨度，超出新的范围之外的图像被释放。  
  
 [移除](../Topic/CImageList::Remove.md) 成员函数从图像列表中移除图像。  [复制](../Topic/CImageList::Copy.md) 成员函数可以复制或交换图像内的图像列表中。  此函数使您指示是否应当复制到目标项索引或应交换图像源和目标。  
  
 通过合并两个图像列表中创建一个新的图像列表，请使用 [创建](../Topic/CImageList::Create.md) 成员函数的适当重载。  **创建** 此重载合并现有的图像列表的第一个图像，存储在新图像列表对象的生成图像。  新图像通过绘制第二个图像创建透明在第一个。  新图像的掩码是执行逻辑或运算的结果。蒙板的位两个现有图像上。  
  
 这重复，直到所有图像组合并添加到新图像对象列表。  
  
 您可以写入图像信息到存档通过调用 [写入](../Topic/CImageList::Write.md) 成员函数，通过调用成员函数 [读取](../Topic/CImageList::Read.md) 读回它。  
  
 [GetSafeHandle](../Topic/CImageList::GetSafeHandle.md) [附加](../Topic/CImageList::Attach.md) [分离](../Topic/CImageList::Detach.md)、和成员函数可操作图像列表中处理附加到 `CImageList` 对象，[DeleteImageList](../Topic/CImageList::DeleteImageList.md)，而成员函数删除图像列表，而不销毁 `CImageList` 对象。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)