---
title: "MFC 中的属性表和属性页 | Microsoft Docs"
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
  - "控件 [MFC], 属性表"
  - "属性页, MFC"
  - "属性表, MFC"
  - "选项卡对话框"
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC 中的属性表和属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性表，也称为对话框选项卡，是包含属性页"对话框。  基于每个属性页对话框模板资源并包含控件。  它用上带有选项卡的页面位于顶部。  选项卡命名页并指示其用途。  用户单击属性表的选项卡选择一组控件。  
  
 使用组合页在属性表的控件到有意义的集合。  包含属性表通常具有自己的一些控件。  这些应用于所有页。  
  
 属性表基于类。[CPropertySheet](../mfc/reference/cpropertysheet-class.md) 属性页类基于 [CPropertyPage](../mfc/reference/cpropertypage-class.md)。  
  
 属性表是一般用于修改某些外部对象的属性特定的对话框，如视图的当前选择。  属性表有三个主要部分：包含的对话框、一个或多个属性页显示一次一个选项卡中的用户单击选择该页的每个页面顶部。  属性表可将多个更改的组或选项类似的情况下是很有用的。  属性表组合一种轻松了解信息的方式。  
  
> [!NOTE]
>  使用 `CPropertySheet::DoModal`时，在您尝试查看表属性，系统可能发生首次异常。  这发生异常，因为系统会尝试更改对象的 [窗口样式](../mfc/reference/window-styles.md)，在对象之前创建的。  有关此异常的更多信息，以及如何避免它或处理它，请参见 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md)。  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)