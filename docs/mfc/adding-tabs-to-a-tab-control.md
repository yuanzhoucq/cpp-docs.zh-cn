---
title: "向选项卡控件添加选项卡 | Microsoft Docs"
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
  - "CTabCtrl 类, 添加选项卡"
  - "在 CTabCtrls 上放置选项卡"
  - "选项卡控件, 添加选项卡"
  - "选项卡, 添加到 CTabCtrl 类"
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 向选项卡控件添加选项卡
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在创建选项卡控件之后 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\)，添加许多选项卡，则需要。  
  
### 添加选项卡  
  
1.  可以 [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) 结构。  
  
2.  调用 [CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md)，传递此结构。  
  
3.  重复步骤1，2可以得到额外选项。  
  
 有关详细信息，请参阅[创建选项卡控件](http://msdn.microsoft.com/library/windows/desktop/bb760550) in the [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)