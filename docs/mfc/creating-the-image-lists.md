---
title: "创建图像列表 | Microsoft Docs"
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
  - "CListCtrl 类, 创建图像列表"
  - "图像列表 [C++], 为 CListCtrl 创建"
  - "列表 [C++], 图像"
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建图像列表相同的是否使用 [CListView](../mfc/reference/clistview-class.md) 或 [CListCtrl](../mfc/reference/clistctrl-class.md)。  
  
> [!NOTE]
>  如果列表控件包括 `LVS_ICON` 样式，只需要图像列表。  
  
 使用 `CImageList` 类生成一个或多个图像列表 \(针对大图标、小图标和状态\)。  参见 [CImageList](../mfc/reference/cimagelist-class.md)，并查看在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [列表视图图像列表](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
 每个图像列表的调用；[CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md) 通过指针对相应的 `CImageList` 对象。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)