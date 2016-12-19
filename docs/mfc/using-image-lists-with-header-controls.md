---
title: "对标题控件使用图像列表 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 图像列表"
  - "标题控件, 图像列表"
  - "图像列表 [C++], 标题控件"
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对标题控件使用图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标题项能够显示在标题项中的图像。  此图像中，关联图像列表中，是 16 x 16 像素并且具有与在列表视图的图标图像控件的特性。  若要成功实现此行为，则必须首先建立和初始化图像列表，关联列表与标题控件，然后修改要显示图像标题项的特性。  
  
 下面的过程演示详细信息，使用指针对标题控件 \(`m_pHdrCtrl`\)、指向图像列表 \(`m_pHdrImages`\)。  
  
### 显示在标题项的图像  
  
1.  构造新的图像列表 \(或者使用现有的图像列表对象\)。[CImageList](../mfc/reference/cimagelist-class.md) 构造函数，即，存储提供的指针。  
  
2.  通过调用 [CImageList::Create](../Topic/CImageList::Create.md)初始化新图像列表对象。  以下代码是此调用的一个示例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_1.cpp)]  
  
3.  添加每个页眉项的图像。  下面的代码将两个预定义的图像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_2.cpp)]  
  
4.  将图像列表与调用的标题控件为 [CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md)。  
  
5.  修改标题项演示从关联的图像列表里的图像。  下面的示例将第一个图像，从 `m_phdrImages`，指向第一个标题项，`m_pHdrCtrl`。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_3.cpp)]  
  
 关于使用的参数值的详细信息，请参考 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)相关。  
  
> [!NOTE]
>  具有多个使用相同的控件图像的列表，也是可能的。  例如，在一标准列表视图控件，可能有两个 \(16 x 16 像素位图\) 所使用图像列表视图控件的小图标视图，并且列表视图的标题项控件。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)