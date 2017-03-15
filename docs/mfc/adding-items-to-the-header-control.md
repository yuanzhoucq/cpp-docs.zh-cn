---
title: "向标题控件添加项 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 添加项"
  - "控件 [MFC], 标题"
  - "标题控件, 添加项"
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 向标题控件添加项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在创建标题控件之后 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 在其父窗口，根据您的需要，可以添加许多“标题项”，通常每列一个。  
  
### 添加一个标头项  
  
1.  准备一个[HD\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) 结构。  
  
2.  调用 [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md)，传递此结构。  
  
3.  重复步骤1，2可以得到额外项。  
  
 有关详细信息，请参阅 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的 [在标头控件中添加一个项。](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)