---
title: "实现列表控件中的工作区域 | Microsoft Docs"
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
  - "列表控件, 工作区域"
  - "列表控件中的工作区域"
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 实现列表控件中的工作区域
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，列表控件使所有项的标准网格方式。  但是，另一方法，支持操作范围，使项列表到矩形组。  有关实现操作范围列表的控件图像，请参见使用列表视图控件。[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
> [!NOTE]
>  只有当列表，控件处于图标或小图标模式时，操作范围内可见。  但是，所有操作当前范围中维护一个视图是切换到报表或列表模式。  
  
 操作范围。用于显示空的边界 \(在左侧，顶部和\/或正确项\)，或者使水平滚动条显示，如果通常没有一种。  另一个常见用途是创建项可以移动或删除多的操作范围。  此方法中，可以创建具有不同的含义在单个视图中的区域。  用户可通过它们放到然后类项在不同的区域。  此示例具有读写文件的区域和只读文件文件系统的其他区域的视图。  如果文件的项移至只读区域，将自动变为只读。  将只读区域的文件为读\/写区域将文件进行读\/可写。  
  
 `CListCtrl` 用于在列表控件的创建和管理的工作区域提供一些成员函数。  [GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md) 和 [SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md) 检索和设置数组或 `CRect` 对象 \( `RECT` 结构\)，存储列表控件的当前实现的操作范围。  此外，[GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md) 检索操作 Span 的当前数目列表控件 \(默认情况下，为零\)。  
  
## 项和操作大小  
 当操作范围创建时，在操作范围之间的项与其成员。  同样，如果某项操作移动，大小，它成为它移动操作 Span 的成员。  如果该项不在任何操作范围之间，则自动以适合第一个 \(index 0\) 来操作 Span 的成员。  如果您希望创建一项并将其放置在特定操作范围内，您需要创建项并将其与调用的操作所需范围到 [SetItemPosition](../Topic/CListCtrl::SetItemPosition.md)。  下面的第二个示例演示这一技术。  
  
 下面的示例将每个操作。操作范围实现四个范围 \(`rcWorkAreas`\)，使用一个 10 像素等于边框的大小，在列表控件 \(`m_WorkAreaListCtrl`\)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_1.cpp)]  
  
 到 [ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md) 的调用将区域调用获取所需的总估计显示区域的所有项。  估计此然后分为四个区域并用一个 5 个像素的边框。  
  
 下一个示例将现有列表的项到每个组 \(`rcWorkAreas`\) 以及刷新控件视图 \(`m_``WorkAreaListCtrl`\) 完成。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_2.cpp)]  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)