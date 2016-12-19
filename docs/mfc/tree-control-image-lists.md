---
title: "树控件图像列表 | Microsoft Docs"
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
  - "CTreeCtrl 类, 图像列表"
  - "图像 [C++], 树控件中的列表"
  - "树控件, 图像列表"
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的每一项都能具有对位图的图像与它。  图像在项标签的左侧显示。  图像显示，在选择项时，同时，其他显示，当项未被选定时。  例如，打开一项可能显示文件夹，当控件选定和已关闭"时，如果未选择时。  
  
 若要使用项的图像，必须通过 [CImageList](../mfc/reference/cimagelist-class.md) 构造对象并使用 [CImageList::Create](../Topic/CImageList::Create.md) 函数生成将图像列表生成图像列表。  使用 [SetImageList](../Topic/CTreeCtrl::SetImageList.md) 成员函数，然后添加预期位图到列表，并将使用树控件列表。  默认情况下，所有项显示在图像列表的第一幅图选择和 nonselected 状态的。  通过指定选择和 nonselected 图像的索引更改特定项的默认行为，并添加到控件树使用 [InsertItem](../Topic/CTreeCtrl::InsertItem.md) 成员函数。  使用 [SetItemImage](../Topic/CTreeCtrl::SetItemImage.md) 成员函数，则可以在添加项后更改索引。  
  
 树的控件图像列表还包含会覆盖图像，在项图像设计会覆盖。  该位 8 至 11 的非零值树控件项的状态指定的覆盖图像从一开始的索引 \(0 指示没有覆盖图像\)。  由于，基于的索引使用 4 位，覆盖图像必须是在图像列表的前 15 图像中  有关树的详细信息请控制项状态，请参见本主题前面的 [树控件项要求概述](../mfc/tree-control-item-states-overview.md)。  
  
 如果状态图像指定列表，在每个项的左侧图标的树控件保留空间状态的图像。  应用程序可以使用状态图像，如检查和清除的复选框，指示应用程序定义的项的状态。  该位 12 至 15 的非零值指定状态图像的基于的索引 \(0 指示无状态图像\)。  
  
 通过指定而非图像的索引的 **I\_IMAGECALLBACK** 值，您可以延迟指定选中的内容或 nonselected 项，直到图像将绘制。  **I\_IMAGECALLBACK** 处理树控件来发送通知消息针对 [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) 查询索引的应用程序。  
  
 [GetImageList](../Topic/CTreeCtrl::GetImageList.md) 成员函数检索树控件的图像列表的句柄。  如果需要将多个图像。列表，此功能很有用。  有关图像列表的更多信息，请参见、[使用 CImageList](../mfc/using-cimagelist.md)[CImageList](../mfc/reference/cimagelist-class.md) " *MFC 参考*[图像列表](http://msdn.microsoft.com/library/windows/desktop/bb761389) 和 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)