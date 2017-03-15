---
title: "属性表和属性页 (MFC) | Microsoft Docs"
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
  - "CPropertyPage 类, 属性表和页"
  - "CPropertySheet 类, 属性表和页"
  - "MFC 对话框, 选项卡"
  - "属性页, 属性表"
  - "属性表, 属性页"
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 属性表和属性页 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 可利用 [对话框](../mfc/dialog-boxes.md)“选项卡”对话框查找通过将属性表和属性页。  调用“属性表”在 MFC 中，此类对话框，类似于在 Microsoft Word 的许多，Excel，对话框，并且将 Visual C\+\+，会包含堆栈选项卡式表，就像从堆栈上看到的文件夹或返回的级联"窗口中为组。  在之前选项卡的控件可见；仅标记的选项卡为显示在后方选项卡。  属性表所针对管理很简洁地设置为多个组有大量属性或将尤其有用。  通常，一个属性表可以替换多个单独对话框为用户简化界面。  
  
 自 MFC 4.0 版中，属性表和属性页实现使用附带了 Windows 95 和 Windows NT 3.51 版和更高版本中的公共控件。  
  
 属性表实现带有 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)[CPropertyPage](../mfc/reference/cpropertypage-class.md) \(描述类和" *MFC 参考*\)。  `CPropertySheet` 定义整体对话框，可以包含基于 `CPropertyPage`”的多个页。“  
  
 有关创建和使用属性表一起使用的信息，请参见主题 [属性表](../mfc/property-sheets-mfc.md)。  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [MFC 中的属性表和属性页](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [交换数据](../mfc/exchanging-data.md)   
 [创建无模式属性表](../mfc/creating-a-modeless-property-sheet.md)   
 [处理应用按钮](../mfc/handling-the-apply-button.md)