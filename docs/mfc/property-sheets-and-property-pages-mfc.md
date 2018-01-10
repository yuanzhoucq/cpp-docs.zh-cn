---
title: "属性表和属性页 (MFC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 877d83a6833b9505c326bc5312d2f151add07cb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-and-property-pages-mfc"></a>属性表和属性页 (MFC)
MFC[对话框](../mfc/dialog-boxes.md)可以通过将合并属性表和属性页"选项卡对话框"查看对其执行。 MFC 中称为"属性表"，这种类型的对话框中，类似于在 Microsoft Word、 Excel 和 Visual c + +，许多对话框框中似乎包含选项卡式表，类似于文件文件夹前后或的级联的 windows 组中所示的堆栈的堆栈。 在前面的选项卡上的控件可见。;仅标记选项卡将在后面的选项卡上可见。 属性表的用处尤其显著管理大量的属性或相当整齐成若干个组的设置。 通常情况下，一个属性表可以通过将多个单独的对话框简化用户界面。  
  
 从 MFC 4.0 版开始属性表和属性页实现使用附带 Windows 95 和 Windows NT 版本 3.51 及更高版本的公共控件。  
  
 属性表在实现类[CPropertySheet](../mfc/reference/cpropertysheet-class.md)和[CPropertyPage](../mfc/reference/cpropertypage-class.md) (中所述*MFC 参考*)。 `CPropertySheet`定义总体对话框中，它可以包含多个"页"基于`CPropertyPage`。  
  
 有关创建和使用属性表的信息，请参阅主题[属性表](../mfc/property-sheets-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [属性表和 MFC 中的属性页](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [交换数据](../mfc/exchanging-data.md)   
 [创建无模式属性表](../mfc/creating-a-modeless-property-sheet.md)   
 [处理应用按钮](../mfc/handling-the-apply-button.md)

