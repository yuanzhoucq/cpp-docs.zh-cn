---
title: "列表项和图像列表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CImageList 类, 和列表项"
  - "CListCtrl 类, 图像列表"
  - "图像列表 [C++], 列表项"
  - "列表项, 图像列表"
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 列表项和图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列表控件\([CListCtrl](../mfc/reference/clistctrl-class.md)\)中的一个“项” ，包括图标、标签和其他任何可能的信息\(“子项”\)。  
  
 列表控件项的图标包含在图像列表中。  图像列表包含了用作图标视图的全尺寸的图标。  第二，选项，图像列表包含了更小的版本中用于控件其他视图的相同图标。  第三个选项列表中包含了“状态”图像，比如在某些视图里，用于在小图标之上显示的复选框。  第四个选项列表包含了列表控件中，在独立的标头项里显示的图片。  
  
> [!NOTE]
>  如果列表视图控件是用 `LVS_SHAREIMAGELISTS` 样式创建的，那么当不再使用时，您有义务将图像销毁。  如果您将相同的图像列表分配给多个列表视图控件，请指定此样式；否则，多个控件可能尝试销毁同一图像列表。  
  
 有关列表项的详细信息，请参见 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的[列表视图图像列表](http://msdn.microsoft.com/library/windows/desktop/bb774736) [项和子项](http://msdn.microsoft.com/library/windows/desktop/bb774736) 。  请参见*MFC参考* 中的[CImageList](../mfc/reference/cimagelist-class.md) 类和[使用 CImageList](../mfc/using-cimagelist.md)等一系列文章 。  
  
 为了创建一个列表控件，当您插入新的项到列表中时，您需要提供要使用的图像列表。  下面的示例演示了此过程，`m_pImagelist` 是 `CImageList` 类型的指针，`m_listctrl` 是 `CListCtrl` 数据成员。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/CPP/list-items-and-image-lists_1.cpp)]  
  
 但是，如果您不打算在列表视图或列表控件中显示图标，则不需要图像列表。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)